# Bioinformatics Tools — Installation & Setup

**Platform:** macOS (Apple Silicon M-series) — primary target
**All tools are free and open-source.**

---

## Required Tools

| Tool | Purpose | Cost |
|------|---------|------|
| minimap2 | Align nanopore reads to reference genome | Free |
| samtools | BAM manipulation (sort, index, stats) | Free |
| bcftools | VCF filtering and manipulation | Free |
| LongShot | Variant calling (CPU, nanopore long reads) | Free |
| Dorado | Optional: re-basecall POD5 files at higher accuracy | Free |
| Python 3 + pyliftover | Optional: convert 23andMe coords from GRCh37 to GRCh38 | Free |

---

## Installation (macOS via Homebrew)

```bash
# Install Homebrew if not present
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Core tools
brew install minimap2
brew install samtools
brew install bcftools

# LongShot (install via Cargo — Rust package manager)
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
cargo install longshot

# Python + pyliftover (optional, for 23andMe comparison)
pip3 install pyliftover pandas
```

---

## Dorado (Oxford Nanopore's basecaller)

Used for re-basecalling at Super Accuracy (SUP) model after a run.

```bash
# Download from ONT GitHub releases — Apple Silicon (arm64) build:
# https://github.com/nanoporetech/dorado/releases
# Download the latest macOS arm64 release

# Add to PATH after download:
export PATH="/path/to/dorado/bin:$PATH"

# Download a basecalling model (run once):
dorado download --model dna_r10.4.1_e8.2_400bps_sup@v5.0.0

# Re-basecall:
dorado basecaller dna_r10.4.1_e8.2_400bps_sup@v5.0.0 pod5/ > reads.bam
```

---

## Optional: DeepVariant (GPU — higher accuracy variant calling)

Only needed if you have a GPU. On Apple Silicon, use LongShot instead.

**Option A: Google Cloud (cheapest for one-time use)**
- Spin up an n1-standard-8 + T4 GPU instance (~$0.50/hr)
- Google Cloud has DeepVariant available as a pre-built pipeline
- Estimated cost per genome: ~$10–15 in compute

**Option B: Local NVIDIA GPU**
```bash
# Requires NVIDIA GPU + Docker
docker pull google/deepvariant:1.6.1-gpu
run_deepvariant \
  --model_type ONT_R10 \
  --ref GRCh38.fna \
  --reads aligned_rg.bam \
  --output_vcf variants_dv.vcf \
  --num_shards 8
```

---

## Disk Space Requirements

| File | Approximate Size |
|------|-----------------|
| GRCh38 reference genome | ~11 GB |
| Raw FASTQ (10x coverage) | ~15–20 GB |
| Raw FASTQ (30x coverage) | ~50–60 GB |
| POD5 raw signal files | 2–3× FASTQ size |
| Aligned BAM | ~20–40 GB |
| VCF output | ~500 MB |
| **Total per run (10x)** | **~60–80 GB** |
| **Total per run (30x)** | **~150–200 GB** |

Recommendation: use an external SSD for sequencing runs. Keep reference genome on the main drive.

---

## Quick Test — Verify Installation

```bash
minimap2 --version    # Should print version number
samtools --version    # Should print version number
bcftools --version    # Should print version number
longshot --version    # Should print version number
```

---

## Performance Expectations (Apple Silicon M2/M3)

| Step | Time (10x coverage) |
|------|---------------------|
| FASTQ concatenation | <5 min |
| minimap2 alignment | 30–60 min |
| samtools sort + index | 10–20 min |
| LongShot variant calling | 60–120 min |
| bcftools filter | <5 min |
| **Total** | **~2–3 hours** |
