# Outsourcing vs DIY: Honest Cost Comparison

**Research date:** 2026-04-20
**Bottom line:** Consumer services are 7–10× cheaper per genome than DIY MinION. DIY is only justified on privacy grounds, not cost.

---

## Consumer Services: What's Available

All three services return raw FASTQ + BAM + VCF files — not just a health report. You own the data.

| Service | Price | Coverage | Returns | Turnaround | Privacy |
|---------|-------|----------|---------|-----------|---------|
| **Dante Labs** | ~$180–200 | 30× | FASTQ, BAM, VCF | 6–8 weeks | OK — 10-year data retention post-cancellation |
| **Nebula Genomics** | $299 | 30× | FASTQ, BAM, VCF | ~4–6 weeks | ⚠️ Class-action suit filed Oct 2024 alleging sharing with Meta, Google, Microsoft |
| **Sequencing.com** | $399 | 30× | FASTQ, BAM, VCF | 2–10 weeks | "Never sell or share" policy stated; strongest claim |

All use Illumina short reads (150 bp paired-end). The resulting FASTQ/BAM files work with standard bioinformatics pipelines (BWA, GATK, DeepVariant).

### Privacy Warning: 23andMe Precedent (May 2025)

23andMe filed for bankruptcy in 2025 and its **entire genetic database was acquired by Regeneron Pharmaceuticals for $256 million**. Every customer's genome data, health questionnaires, and stored biological samples changed ownership involuntarily.

This illustrates the core risk of any consumer genetic service: the company's privacy promises only hold as long as the company survives in its current form. Bankruptcy, acquisition, or regulatory action can transfer your data to a new owner.

---

## Academic/Commercial Services: Send Extracted DNA, Get FASTQ

These services accept DNA you've already extracted and return raw sequencing data. No saliva collection kit, no health report — just sequencing as a service.

| Service | Technology | Turnaround | Privacy |
|---------|-----------|-----------|---------|
| **Novogene** | Illumina NovaSeq 6000, 150 bp PE | ~2 weeks | Institutional; no public data-sharing history |
| **BGI Americas** | DNBSEQ, 150 bp PE | 10 working days | Institutional; BGI is a Chinese company — consider jurisdiction |
| **SeqCenter** (Pittsburgh) | Illumina | 2-week guarantee | Academic-adjacent; strong research ethics culture |
| **Azenta/GENEWIZ** | Illumina | Contact for quote | Institutional; contact NGS@azenta.com |
| **Macrogen** | Illumina | Contact for quote | Korean company; institutional |

**Pricing:** None of these publish consumer prices for human WGS. They're academic-facing services. Based on historical quotes, expect **$400–800 for 30× human WGS** including library prep from extracted DNA.

**Key advantage:** They sequence DNA, not cells. You've already performed extraction at home, so there's no saliva sample. But the DNA molecules contain your full genome — re-identification risk is identical to any other method once sequenced.

### BGI Privacy Note
BGI is a Chinese genomics company. US legislators have raised concerns about genetic data security given Chinese data law requirements. Consider this if privacy jurisdiction matters.

---

## Hybrid: Extract at Home → Mail DNA → Get FASTQ

**The workflow:**
1. Collect buccal cells at home (saline mouthwash, ~15 min)
2. Extract DNA at home with Zymo kit (~1.5 hr, ~$54 in reagents)
3. Quantify with Qubit to confirm good yield
4. Mail DNA extract (~20–50 µL clear liquid in a tube) to sequencing service
5. 1–2 weeks later, download FASTQ files (30–50 GB)
6. Run bioinformatics pipeline at home

**Equipment needed for this route:**
- Used centrifuge: ~$150
- Used pipettes: ~$150
- Qubit 4 (used): ~$200
- Zymo kit + reagents: ~$150
- **Total equipment: ~$650**
- **Per-genome cost: ~$650 (extraction + service quote)**

This is a compelling middle ground: cheap, you control the analysis, and you avoid the consumer service data risk to some extent — though the DNA itself still leaves your house.

---

## The Brutal Cost Comparison

### Per-Genome Cost at 30× Coverage

| Route | First genome | Subsequent genomes | Notes |
|-------|-------------|-------------------|-------|
| **Dante Labs (consumer)** | **~$200** | **~$200** | DNA leaves house; short reads |
| **Nebula Genomics (consumer)** | **~$299** | **~$299** | ⚠️ Privacy lawsuit |
| **Sequencing.com (consumer)** | **~$399** | **~$399** | Best stated privacy of consumer services |
| **Hybrid (home extract + Novogene/SeqCenter)** | **~$850** (equipment + service) | **~$500** (service only) | DNA leaves house as extract; Illumina short reads |
| **DIY MinION Mk1D Pack** | **~$6,100** | **~$2,250** | DNA never leaves; long reads; ongoing capability |
| **DIY MinION + flow cell washing** | **~$5,700** | **~$1,800** | Same as above; wash kit extends flow cells |

### DIY Break-Even Analysis

When does DIY become cheaper than repeatedly using a consumer service?

| Compare to | DIY excess device cost | Savings per genome vs DIY | Break-even genomes |
|-----------|----------------------|--------------------------|-----------------|
| Dante Labs (~$200) | $5,900 | –$2,050 (DIY is MORE expensive) | **Never** |
| Nebula ($299) | $5,801 | –$1,951 (DIY is MORE expensive) | **Never** |
| Sequencing.com ($399) | $5,701 | –$1,851 (DIY is MORE expensive) | **Never** |
| Hybrid route (~$500/genome variable) | $5,600 | –$1,750 (DIY is MORE expensive) | **Never** |

**The variable cost of DIY sequencing ($2,250 per genome in flow cells + kit) already exceeds any consumer service price. DIY never pays back on cost alone, for any number of genomes.**

---

## So Why DIY?

The cost argument is gone. The remaining justifications for DIY are real, but they're not about money:

### 1. Privacy: Your data never leaves
- No company can sell your genome in a bankruptcy
- No class-action lawsuit can reveal your data was shared with Meta
- No Chinese government data-access law applies
- No breach can expose your VCF file
- This is the **only** justification that holds up to scrutiny

### 2. Long reads (Nanopore advantage)
Consumer services all use Illumina short reads (150 bp). Nanopore produces reads of 10–100 kb+. Long reads are better for:
- Structural variants (deletions, inversions, duplications >50 bp)
- Repeat-rich regions (telomeres, centromeres)
- Phasing (knowing which variants are on which chromosome copy)
- Methylation calling (epigenomics — Nanopore does this natively; Illumina can't)

For personal health SNP analysis and pharmacogenomics, short reads are fine. For structural genomics, phasing, or methylation, Nanopore is genuinely superior.

### 3. Ongoing capability
Once you own the MinION, you can sequence:
- Family members at ~$2,250 each (still more expensive than consumer services, but private)
- Environmental samples, gut microbiome, pathogens
- Re-sequence after new bioinformatics tools are published

### 4. No turnaround time
Run a sequencing experiment on a Tuesday, have results by Friday. No 6-week wait.

---

## Recommended Decision Framework

**Go DIY if:**
- Privacy is non-negotiable (data must never leave your hands)
- You want long-read data (structural variants, phasing, methylation)
- You plan to sequence multiple family members over time
- You want to learn the full end-to-end pipeline

**Go consumer service if:**
- You just want 30× WGS data for personal health insights at lowest cost
- Short reads are fine for your goals (most health SNPs, pharmacogenomics)
- You're comfortable with the privacy risk and have reviewed the company's terms

**Go hybrid (home extraction → Novogene/SeqCenter) if:**
- You want to avoid the consumer service data ecosystem
- You're OK with DNA leaving as an extract (not cells)
- You want Illumina short reads at lower cost than full DIY

---

---

## UiO NorSeq — ONT PromethION Service (Norway)

**URL:** https://www.sequencing.uio.no/ONT%20Services/

This is the Norwegian Research Council's national sequencing platform, run through the University of Oslo. It's a standout option for Norwegian-based users.

### What They Offer
- **Technology:** PromethION P2 Solo (up to **150 Gb per flow cell**)
- **Library prep:** Ligation kit V14 (SQK-LSK114) — the high-yield kit
- **Data delivery:** FASTQ files; POD5 on request; long reads (nanopore, not short reads)
- **Data retention:** Deleted after 2 months from delivery — no long-term storage
- **Privacy:** GDPR-protected (Norwegian public university); no commercial data sharing
- **Bioinformatics:** Optional mapping via EPI2ME or nf-core pipelines for a small fee

### Why This Is Compelling
One PromethION flow cell at 150 Gb covers 30× coverage of a human genome in a **single run** — no stacking multiple MinION flow cells. You get long reads with methylation calling, which is better than any consumer Illumina service.

Under GDPR, UiO has legal obligations around data processing that US consumer services don't have. Data gets deleted after 2 months regardless.

### Pricing
**Not publicly listed.** Contact required. As an academic facility they likely have:
- Norwegian academic rate (cheapest, requires UiO/Norwegian institutional affiliation)
- Nordic/international academic rate
- Commercial rate (highest)

### ⚠️ Critical Requirement: High Molecular Weight DNA

This is the hard part. UiO requires:
- **Fragment size >30 kb** (verified by pulsed-field gel, Bioanalyzer, or FEMTO Pulse)
- **Minimum 5 µg gDNA** for ligation prep
- **Purity:** A260/280 = 1.8, A260/230 = 2.0–2.2

Standard column-based extraction (e.g., Zymo Quick-DNA Miniprep) typically yields fragments of 5–20 kb — **likely failing the >30 kb requirement** due to shearing during column binding and elution.

To meet the HMW requirement you'd need a different extraction approach:

| Method | Fragment size | Cost | Notes |
|--------|--------------|------|-------|
| Zymo Quick-DNA (current plan) | 5–20 kb | ~$54 | ❌ Too short for NorSeq |
| **NEB Monarch HMW DNA Kit** | 50–150 kb | ~$150 | ✅ Good for buccal/saliva samples |
| **Circulomics Nanobind Tissue** | >100 kb | ~$200 | ✅ Ultra-long; premium option |
| **CTAB with gentle handling** | 20–100 kb+ | ~$20 in reagents | ✅ Possible if done carefully; see research/diy-extraction.md |

If you plan to send to NorSeq, switch extraction kit to **NEB Monarch HMW** or **Circulomics Nanobind** and verify fragment size before shipping.

### Submission
- Human samples → OUS node (Oslo University Hospital)
- Non-human → CEES node
- They do **not** perform DNA isolation — you extract at home and ship the DNA
- Accepted in 1.5 mL Safelock Eppendorf tubes
- No dried/precipitated samples; TE buffer recommended for long-term storage

### Summary
| | UiO NorSeq |
|-|-----------|
| Technology | PromethION (long reads) |
| Coverage in one run | 30× in one flow cell |
| Privacy | GDPR; data deleted after 2 months |
| Pricing | Contact required; likely €200–600 for academic users |
| Catch | Need HMW DNA extraction (>30 kb); standard Zymo won't work |
| Eligibility | Likely prioritises academic/institutional users |

---

## Devices to Watch

**ONT PromethION:**
ONT announced a pathway to **<$345 per 30× genome** on the PromethION Plus flow cell (announced at ASHG 2025, broader availability 2026). This would be competitive with consumer services — with long reads. But the PromethION device costs $35,000+. Not for home use.

The long-term trajectory: nanopore sequencing costs are falling toward consumer service prices. A PromethION in a community lab / biohacker space could eventually offer privacy + cost parity.
