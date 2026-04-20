# Dashboard: Building the Genome Results Viewer

**Goal:** An interactive HTML dashboard showing health/traits/ancestry from the VCF,
styled like 23andMe but with full-genome coverage.

---

## What to Build

### Sections (based on Vibe Genomics article + 23andMe categories)
1. **Summary** — coverage, total variants, data quality metrics
2. **Health Risks** — elevated/reduced risk variants (cancer, diabetes, heart, etc.)
3. **Carrier Status** — recessive condition carrier variants
4. **Traits** — eye color, hair, taste sensitivity, earwax type, etc.
5. **Ancestry-Informative Markers** — population-specific SNPs
6. **Drug Response** — pharmacogenomics (CYP450 genes, warfarin sensitivity, etc.)
7. **Structural Variants** (bonus) — requires higher coverage, shows deletions/insertions

---

## How to Generate the Dashboard with Claude

**Step 1:** Give Claude your filtered VCF and a summary of your run stats.

**Step 2:** Use a prompt like this:

> I have a filtered VCF file from Oxford Nanopore whole genome sequencing (Ligation kit,
> R10.4.1 flow cells, GRCh38 reference). I have approximately [X]x coverage and [Y] million
> PASS variants (GQ 20-49).
>
> Please build an interactive HTML dashboard with the following sections:
> 1. Run summary (coverage, variant count, data quality)
> 2. Health risks — check against ClinVar pathogenic/likely pathogenic variants and common
>    GWAS risk SNPs (include the specific rsID, position, and my genotype for each)
> 3. Carrier status — recessive disease carriers
> 4. Traits — the full list 23andMe reports (eye color, hair, taste, etc.)
> 5. Drug response — CYP2C9, CYP2C19, CYP2D6, SLCO1B1, VKORC1 and similar
>
> For each finding, show: rsID, chromosome:position, my genotype, reference population freq,
> and an explanation of what it means.
>
> Format as a standalone HTML file with tab navigation, clean styling similar to 23andMe.
> Use color coding: green = low risk / typical, yellow = elevated risk, red = significantly
> elevated risk / pathogenic.

**Step 3:** Claude will generate an HTML file. Open it in a browser to review.
Iterate with Claude to add more SNPs, fix styling, add hover tooltips, etc.

---

## Key SNPs to Check (starter list)

These are well-validated, commonly checked SNPs:

| rsID | Gene | What it affects |
|------|------|----------------|
| rs1801133 | MTHFR | Folate metabolism, neural tube defect risk |
| rs429358, rs7412 | APOE | Alzheimer's disease risk (APOE ε2/ε3/ε4) |
| rs1805007 | MC1R | Red hair, pale skin, melanoma risk |
| rs12913832 | HERC2/OCA2 | Blue vs brown eyes |
| rs4988235 | LCT | Lactose intolerance / lactase persistence |
| rs53576 | OXTR | Oxytocin receptor (social behavior / empathy) |
| rs1800562 | HFE | Hereditary hemochromatosis carrier |
| rs6025 | F5 | Factor V Leiden (clotting risk) |
| rs1801131 | MTHFR | Second MTHFR variant |
| rs1799945 | HFE | Hemochromatosis (second variant) |
| rs1801279 | CYP2D6 | Drug metabolism (codeine, many others) |
| rs762551 | CYP1A2 | Caffeine metabolism (fast vs slow) |
| rs4680 | COMT | Dopamine metabolism ("warrior vs worrier") |

---

## Validating Against 23andMe

If you have 23andMe raw data (txt file with ~600K SNPs):

```python
import pandas as pd
from pyliftover import LiftOver

# Load 23andMe data (GRCh37 coordinates)
df = pd.read_csv('23andme_raw.txt', sep='\t', comment='#',
                 names=['rsid','chrom','pos','genotype'])

# Convert to GRCh38
lo = LiftOver('hg19', 'hg38')
def convert(row):
    result = lo.convert_coordinate(f"chr{row['chrom']}", row['pos'])
    if result:
        return result[0][1]
    return None

df['pos_hg38'] = df.apply(convert, axis=1)
df = df.dropna(subset=['pos_hg38'])

# Now compare against your VCF...
```

Target accuracy at different coverages:
- 10x: ~95–97% agreement
- 15x: ~97–98% agreement (author's result: 96.97%)
- 30x: ~98.5%+ agreement

---

## Notes
- The dashboard HTML file can be opened locally — no server needed, data stays on your machine
- Avoid putting your full VCF into any cloud AI service if privacy is a concern
- Run Claude locally (Claude Code on your machine) or only share specific SNP positions, not the full VCF
