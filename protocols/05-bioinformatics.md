# Protocol 5: Bioinformatics Pipeline

**Time:** 2–8 hours compute (mostly unattended), ~1 hour setup
**Prerequisites:** FASTQ reads from sequencing run, reference genome (GRCh38)
**Output:** Annotated VCF file with your genetic variants, ready for dashboard

---

## Overview

```
FASTQ reads
    ↓ minimap2 (align to reference genome)
Aligned BAM
    ↓ samtools sort + index + addreplacerg
Sorted BAM with read groups
    ↓ LongShot (CPU, Apple Silicon) OR DeepVariant (GPU)
Raw VCF
    ↓ bcftools filter (keep PASS variants)
Filtered VCF
    ↓ Claude (build dashboard + analyze SNPs)
Results dashboard
```

---

## One-Time Setup: Install Tools

See `bioinformatics/tools.md` for installation commands.
Required: minimap2, samtools, bcftools, LongShot (or DeepVariant)

---

## Step 1: Download Reference Genome

- [ ] Download GRCh38 reference genome (one-time, ~3 GB compressed)

```bash
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/001/405/GCA_000001405.15_GRCh38/seqs_for_alignment_pipelines.ucsc_ids/GCA_000001405.15_GRCh38_no_alt_analysis_set.fna.gz
```

- [ ] Decompress and index:
```bash
gunzip GCA_000001405.15_GRCh38_no_alt_analysis_set.fna.gz
mv GCA_000001405.15_GRCh38_no_alt_analysis_set.fna GRCh38.fna
samtools faidx GRCh38.fna
```

Reference file: ~11 GB uncompressed. Store permanently — reuse for every run.

---

## Step 2: Combine and Align Reads

If you have multiple FASTQ files from MinKNOW (it creates many small files):

- [ ] Combine all FASTQ files:
```bash
cat fastq_pass/*.fastq.gz > all_reads.fastq.gz
```

- [ ] Align to reference genome with minimap2:
```bash
minimap2 -ax map-ont -t 8 GRCh38.fna all_reads.fastq.gz | \
    samtools sort -o aligned.bam
```
`-t 8` = use 8 threads (adjust to your CPU count)

Time estimate: 30–90 min on Apple Silicon M2/M3+

---

## Step 3: Index BAM and Add Read Groups

- [ ] Index the BAM:
```bash
samtools index aligned.bam
```

- [ ] Add read group tags (required by variant callers):
```bash
samtools addreplacerg -r "@RG\tID:1\tSM:sample\tPL:ONT" \
    -o aligned_rg.bam aligned.bam
samtools index aligned_rg.bam
```

- [ ] Check alignment stats:
```bash
samtools flagstat aligned_rg.bam
```
Look for: `primary mapped` percentage should be ≥90%.

- [ ] Check coverage:
```bash
samtools coverage aligned_rg.bam | head -30
```
Average depth column should show your coverage across chromosomes.

---

## Step 4: Variant Calling

### Option A: LongShot (CPU, runs on any machine) — RECOMMENDED for Apple Silicon

LongShot is designed for nanopore long reads, CPU-only, good accuracy.

- [ ] Run LongShot:
```bash
longshot --bam aligned_rg.bam \
         --ref GRCh38.fna \
         --out variants_longshot.vcf \
         --min_cov 5 \
         --min_alt_count 3
```

Time: 1–3 hours on Apple Silicon

### Option B: DeepVariant (GPU, higher accuracy) — if GPU available

Requires NVIDIA GPU or cloud instance (Google Cloud has DeepVariant as a managed service).

```bash
# On Google Cloud / NVIDIA:
run_deepvariant \
  --model_type ONT_R10 \
  --ref GRCh38.fna \
  --reads aligned_rg.bam \
  --output_vcf variants_dv.vcf \
  --num_shards 8
```

Cloud cost estimate: ~$10–20 for a single genome on a GPU instance.

---

## Step 5: Filter VCF

- [ ] Keep only PASS variants:
```bash
bcftools filter -i 'FILTER="PASS"' variants_longshot.vcf > variants_filtered.vcf
```

- [ ] Count variants:
```bash
grep -v "^#" variants_filtered.vcf | wc -l
```
Expect: 3–5 million variants for a well-sequenced human genome.

---

## Step 6: Build Dashboard with Claude

Hand Claude your VCF file and ask it to:
1. Check specific SNPs against known health/trait databases (ClinVar, dbSNP, GWAS catalog)
2. Compare against 23andMe SNP list (if you have prior 23andMe data)
3. Build an interactive HTML dashboard showing traits, health markers, ancestry-informative SNPs
4. Flag high-confidence variants (GQ score filter — see note below)

**GQ score note:** From the Vibe Genomics article:
- GQ 20–39: 99.58–99.80% accuracy (use these)
- GQ 50+: paradoxically unreliable (RefCall artifacts — avoid)
- Filter to GQ 20–49 for best results

Useful prompt to start:
> "I have a VCF file from Oxford Nanopore whole genome sequencing. I want to build a health and traits dashboard. The VCF has [X] million PASS variants. Please check all SNPs listed in 23andMe's trait reports and build an interactive HTML dashboard grouping results by category (health risks, carrier status, traits, ancestry-informative markers)."

---

## Optional: Compare with 23andMe Data

If you have prior 23andMe raw data:
- [ ] Download your 23andMe raw data (txt file of ~600K SNPs)
- [ ] Convert 23andMe coordinates: SNPs are in GRCh37, VCF is GRCh38
  - Use pyliftover: `pip install pyliftover`
- [ ] Parse and compare — article author achieved 96.97% accuracy at 15x coverage

---

## File Organization

```
~/vibe-genomics-data/
├── GRCh38.fna              ← Reference genome (keep permanently)
├── GRCh38.fna.fai          ← Reference index
├── run1/
│   ├── fastq_pass/         ← Raw reads from MinKNOW
│   ├── all_reads.fastq.gz  ← Combined reads
│   ├── aligned.bam         ← Aligned reads
│   ├── aligned_rg.bam      ← With read groups
│   ├── aligned_rg.bam.bai  ← BAM index
│   └── variants_filtered.vcf ← Final variants
└── dashboard/
    └── results.html        ← Claude-built dashboard
```

---

## Troubleshooting

| Problem | Likely cause | Fix |
|---------|-------------|-----|
| Low mapping rate (<85%) | Bad reads, wrong reference, or reference mismatch | Verify reference is GRCh38, check read quality |
| Low coverage (<8x average) | Not enough reads, or alignment failed | Run more flow cells, check alignment |
| No PASS variants | VCF filter too strict, or LongShot params wrong | Check raw VCF first, adjust min_cov |
| minimap2 killed / OOM | Not enough RAM | Use `-t 4` instead of `-t 8` to reduce memory |
