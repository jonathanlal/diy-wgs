# Protocol 4: Sequencing Run (MinKNOW)

**Time:** 72 hours hands-off after setup (~30 min to start)
**Prerequisites:** Flow cell loaded (Protocol 03), MinKNOW installed, ~100 GB free disk per flow cell
**Output:** FASTQ reads (basecalled) + POD5 raw signal files

---

## Before Starting

- [ ] Verify ≥100 GB free disk space on the sequencing computer (per flow cell)
- [ ] Connect MinION to computer via USB-C — verify MinKNOW detects it
- [ ] Ensure computer will not sleep during the run (disable sleep settings)
- [ ] Ensure computer will not run Windows Update / restart during the run
- [ ] Close unnecessary applications to free RAM for basecalling

---

## Step 1: Start Sequencing in MinKNOW

- [ ] Open MinKNOW → click on your MinION device
- [ ] Click **"Start Sequencing"**
- [ ] Experiment name: e.g., `WGS_Run1_[date]`
- [ ] Kit: select **SQK-LSK114** (Ligation kit)
- [ ] Barcode expansion: **None** (we're not multiplexing samples)
- [ ] Basecalling: **Enabled**
  - Model: **HAC (High Accuracy)** — works in real-time on Apple Silicon M-series
  - If using older Mac/PC: set to **Fast** for real-time, re-basecall to HAC post-run
- [ ] Run duration: **72 hours**
- [ ] Click **Start**

---

## Step 2: Monitor the Run

MinKNOW shows a live dashboard — check at these intervals:

**At 1 hour:**
- [ ] Active pore count should be ≥200 pores (ideally 400–800+)
- [ ] "Active" pores sequencing DNA (not just "available")
- [ ] Data rate: should be generating reads actively
- [ ] Estimated yield displayed — should be on track for ~10–15 Gb/day from good flow cell

**At 6 hours:**
- [ ] Cumulative yield so far — note in log below
- [ ] If very low (<1 Gb at 6h), something went wrong — check loading, pore count

**At 24 hours:**
- [ ] Total yield so far: ______ Gb
- [ ] Active pore count: ______ (will naturally decrease over time)

**At 48 hours:**
- [ ] Total yield: ______ Gb
- [ ] If yield is tracking low (<15 Gb total), consider loading a second flow cell
- [ ] If yield looks good (>15 Gb), you're on track for 10x+ coverage

**At 72 hours:**
- [ ] Run completes automatically
- [ ] Final yield: ______ Gb
- [ ] Coverage estimate: yield (Gb) ÷ 3.3 Gb = ______ × coverage

---

## Run Log

| Time | Active Pores | Cumulative Yield | Notes |
|------|-------------|-----------------|-------|
| 1h | | | |
| 6h | | | |
| 24h | | | |
| 48h | | | |
| 72h (final) | | | |

---

## Step 3: After the Run

- [ ] Verify output files are present in MinKNOW output folder
  - FASTQ files (basecalled reads) — in `fastq_pass/` subfolder
  - POD5 files (raw signal) — in `pod5/` subfolder
- [ ] Record total file size: ______
- [ ] Check read count and N50 in MinKNOW summary stats
- [ ] If using cloud GPU for DeepVariant later, start uploading FASTQ now (large files)

---

## Coverage Targets

| Coverage | Gb of reads needed | Flow cells needed (typical) | Use case |
|----------|-------------------|-----------------------------|---------|
| 10x | ~33 Gb | 2–3 | Minimum viable, OK for common SNPs |
| 15x | ~50 Gb | 3–4 | Good SNP calling, author's achievement |
| 30x | ~99 Gb | 5–7 | Clinical-grade, recommended for full analysis |

Start with 2 flow cells. If yield is good, that may be enough for 15x.

---

## Optional: Re-Basecall at Higher Accuracy Post-Run

If you ran Fast basecalling during the run:
- Use Dorado (ONT's standalone basecaller) to re-basecall POD5 files at SUP (Super Accuracy) model
- Command: `dorado basecaller sup pod5/ > reads.bam`
- Takes several hours on Apple Silicon, produces higher-quality reads
- Skip this if MinKNOW ran HAC or if compute is limited

---

## Troubleshooting

| Problem | Likely cause | Fix |
|---------|-------------|-----|
| Very few active pores at start | Air bubble in loading, or low DNA | Can't fix in-run; note for next run |
| Run stops early | Computer went to sleep, or disk full | Prevent sleep; check disk space before start |
| Low yield (<5 Gb total) | Old flow cell, under-loaded, or air damage | Check fresh flow cell next run, quantify DNA |
| MinKNOW crashes | Insufficient RAM or GPU memory | Close other apps, reduce basecalling threads |
