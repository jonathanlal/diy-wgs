# Equipment: DNA Sequencer

**Decision status:** DECIDED — Buy Oxford Nanopore MinION Mk1B (device only)

---

## What It Does
Pulls DNA through nanopores, reads electrical resistance as each base passes through,
outputs raw signal files (POD5/FAST5) that get basecalled into sequence reads (FASTQ).

---

## Options

### Oxford Nanopore MinION Mk1B — RECOMMENDED
- The only portable nanopore sequencer on the market in this price range
- Size of a large USB drive, plugs into laptop via USB-C
- Runs MinKNOW software on Windows/Mac/Linux
- Flow cells: R10.4.1 (current generation, excellent accuracy)
- Read lengths: up to 100kb+ (long reads make assembly far easier than Illumina)

**Buying options:**
| Option | Cost | What's Included | Notes |
|--------|------|----------------|-------|
| MinION Mk1B device only | ~$1,000 | Device + USB cable only | Best value — buy reagents separately |
| MinION Starter Pack | ~$1,400 | Device + 2 flow cells + Rapid kit | Slightly better value than device-only if you need kick-start |
| MinION Sequencing Bundle | ~$5,200 | Device + 5 flow cells + Rapid kit | Author's choice — overpriced for our needs |

**Recommendation:** Buy **device only** at ~$1,000, source flow cells and kits separately.
The bundle forces you into the Rapid kit (lower yield) and you overpay for flow cells.

### Oxford Nanopore Flongle — NOT RECOMMENDED for WGS
- Smaller, cheaper adapter ($90/flow cell)
- Only ~1–2 Gb output per flow cell
- Human genome needs ~33 Gb for 10x coverage
- Would need 17–33 Flongle runs per genome — completely impractical

### Oxford Nanopore PromethION — NOT RECOMMENDED
- Research-grade, high-throughput (~300 Gb/run)
- Cost: ~$35,000
- Overkill, not available for personal purchase without institutional affiliation

### Illumina-based approaches — NOT RECOMMENDED for home use
- Short reads (150–300 bp) vs. Nanopore's multi-kb reads
- No home-use sequencer exists in this price range
- iSeq 100: ~$20,000 — and still short reads
- Short reads make variant calling harder for structural variants

### PacBio — NOT RECOMMENDED
- Excellent long reads, very high accuracy
- Cheapest instrument: ~$150,000
- Not remotely viable for home use

---

## Flow Cells — Key Details
- Model: **R10.4.1** (current generation as of 2026)
- Cost: ~$850 each
- Storage: **2–8°C refrigerator** (NOT freezer — freezing kills flow cells instantly)
- Shelf life: ~3 months from manufacture, degrades with time
- Rated pore count: 800+ (run flow cell check before committing DNA)
- Output: 10–50 Gb per flow cell (highly variable, depends on DNA quality + loading)
- For 10x coverage: need ~33 Gb → 1–2 fresh flow cells
- For 30x coverage: need ~99 Gb → 3–6 flow cells

**Don't stockpile flow cells** — order 2–3 at a time and use them fresh.

---

## Software
- **MinKNOW**: Oxford Nanopore's sequencing control and basecalling software
  - Free, download from nanoporetech.com/downloads
  - Requires ONT account (free to create)
  - Handles real-time basecalling on Apple Silicon M-series Macs (HAC model)
- **Dorado**: ONT's newer standalone basecaller (faster than Guppy, runs on Apple Silicon)
  - Can re-basecall at higher accuracy after the run

---

## Verdict
**Buy MinION Mk1B device only. ~$1,000.**
Do NOT buy the bundle. Source flow cells and library kits separately.
This is the one piece of equipment with no viable alternative.
