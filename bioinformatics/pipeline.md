# Bioinformatics Pipeline — Reference

Full pipeline from raw reads to variant calls. See `protocols/05-bioinformatics.md` for the
step-by-step checklist version.

---

## Complete Pipeline (Copy-Paste Commands)

```bash
# ── 0. Setup ─────────────────────────────────────────────────────────────────
# Set paths
REF="/path/to/GRCh38.fna"
FASTQ_DIR="/path/to/fastq_pass"
OUTDIR="/path/to/run_output"
mkdir -p $OUTDIR

# ── 1. Combine reads ─────────────────────────────────────────────────────────
cat $FASTQ_DIR/*.fastq.gz > $OUTDIR/all_reads.fastq.gz

# ── 2. Align to reference ────────────────────────────────────────────────────
minimap2 -ax map-ont -t 8 $REF $OUTDIR/all_reads.fastq.gz | \
    samtools sort -o $OUTDIR/aligned.bam

# ── 3. Index + add read groups ───────────────────────────────────────────────
samtools index $OUTDIR/aligned.bam

samtools addreplacerg \
    -r "@RG\tID:1\tSM:sample\tPL:ONT\tLB:LSK114" \
    -o $OUTDIR/aligned_rg.bam $OUTDIR/aligned.bam

samtools index $OUTDIR/aligned_rg.bam

# ── 4. QC checks ─────────────────────────────────────────────────────────────
samtools flagstat $OUTDIR/aligned_rg.bam
samtools coverage $OUTDIR/aligned_rg.bam | head -30

# ── 5a. Variant calling — LongShot (CPU, Apple Silicon) ──────────────────────
longshot \
    --bam $OUTDIR/aligned_rg.bam \
    --ref $REF \
    --out $OUTDIR/variants_longshot.vcf \
    --min_cov 5 \
    --min_alt_count 3

# ── 5b. Variant calling — DeepVariant (GPU, higher accuracy) ─────────────────
# run_deepvariant \
#   --model_type ONT_R10 \
#   --ref $REF \
#   --reads $OUTDIR/aligned_rg.bam \
#   --output_vcf $OUTDIR/variants_dv.vcf \
#   --num_shards 8

# ── 6. Filter variants ───────────────────────────────────────────────────────
bcftools filter \
    -i 'FILTER="PASS" && FORMAT/GQ[0] >= 20 && FORMAT/GQ[0] <= 49' \
    $OUTDIR/variants_longshot.vcf > $OUTDIR/variants_filtered.vcf

# Count results
echo "Total PASS variants (GQ 20-49):"
grep -v "^#" $OUTDIR/variants_filtered.vcf | wc -l

# ── 7. Optional: extract specific SNPs for dashboard ────────────────────────
# Pass variants_filtered.vcf to Claude for dashboard generation
```

---

## Key Parameter Notes

**minimap2 `-ax map-ont`**
The preset for Oxford Nanopore long reads. Sets appropriate gap and mismatch penalties for
the higher error rate of nanopore reads vs. Illumina.

**LongShot `--min_cov 5`**
Only call variants at positions with ≥5 reads covering them. Lower coverage = higher false positives.
At 10x coverage, most positions will have enough coverage; some may fall below 5x.

**GQ score filter (`GQ >= 20 AND GQ <= 49`)**
Key insight from Vibe Genomics article:
- GQ 20–49: 99.58–99.80% accuracy at these confidence tiers
- GQ 50+: paradoxically unreliable — these are RefCall artifacts that LongShot/DeepVariant
  mislabels as high-confidence. Filter them OUT.
- GQ < 20: low confidence, too many false positives

---

## Output VCF Format
Each line after the header represents one variant:
```
CHROM  POS       ID    REF  ALT  QUAL  FILTER  INFO  FORMAT  SAMPLE
chr1   925952    .     G    A    .     PASS    ...   GT:GQ   0/1:35
```
- `GT`: Genotype — `0/0`=homozygous ref, `0/1`=heterozygous, `1/1`=homozygous alt
- `GQ`: Genotype quality score (higher = more confident, but see note above)

---

## Handing Off to Claude for Analysis

Useful context to give Claude when building the dashboard:
1. The VCF file (or a path to it if running locally)
2. Coverage achieved (from samtools coverage output)
3. Total variant count
4. Whether you have 23andMe data to compare against
5. What you want: health risks, traits, ancestry, structural variants

The SNP database Claude can reference:
- ClinVar: pathogenic/likely pathogenic variants
- dbSNP: common variation catalog
- GWAS Catalog: trait associations
- PharmGKB: drug response variants
