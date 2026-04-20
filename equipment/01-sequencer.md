# Equipment: DNA Sequencer

**Decision status:** DECIDED — Buy Oxford Nanopore MinION Mk1D (device only or Pack)

> **Price update:** The MinION Mk1B is now a legacy product. The current model is the **MinION Mk1D** at **$3,150 device-only** — not ~$1,000 as originally estimated. See budget notes below.

---

## What It Does
Pulls DNA through nanopores, reads electrical resistance as each base passes through,
outputs raw signal files (POD5/FAST5) that get basecalled into sequence reads (FASTQ).

---

## Current Model: MinION Mk1D

The Mk1B was discontinued; the Mk1D is the current production device as of 2026.

**What changed Mk1B → Mk1D:**
- New chassis with status LEDs (run status at a glance)
- Peltier-based active temperature control (more reliable at ambient temps 10–35°C)
- Same USB-C laptop connection
- Same flow cell format (R10.4.1 compatible)
- Same MinKNOW software

**Same as before:**
- Plugs into any laptop/MacBook via USB-C
- Runs MinKNOW (free, requires ONT account)
- Flow cells: R10.4.1 (FLO-MIN114) — the current gold standard
- Read lengths: 20 bp to >4 Mb (ultra-long reads possible)
- Typical output: 15–35 Gb per flow cell

---

## Buying Options

| Option | Cost | What's Included | Notes |
|--------|------|----------------|-------|
| MinION Mk1D device only | **$3,150** | Device + standard support | Best if you're buying flow cells gradually |
| MinION Mk1D Pack | **$5,150** | Device + 5× R10.4.1 flow cells + Control Expansion Kit + 2× Wash Kit + sequencing kit | Best value — saves ~$2,800 vs buying separately |
| Used MinION Mk1B (eBay/reseller) | **$500–1,500** | Device only | Legacy but fully functional; R10.4.1 flow cells still work with Mk1B |

### Pack vs Device-Only Math
If you plan to sequence at ≥15× coverage (needs 2–4 flow cells), the Pack wins:
- Pack: $5,150 → includes device + 5 flow cells + sequencing kit
- Device-only + 5 flow cells + kit separately: $3,150 + $4,250 + $500 = **$7,900**
- Pack savings: **~$2,750**

The pack only makes sense if you'll use all 5 flow cells. If you're uncertain and want to start with just 1–2 runs, device-only is lower upfront risk.

### Used MinION Mk1B Strategy
The Mk1B is legacy but **not broken**. ONT still sells R10.4.1 flow cells that work with it. If you can source a used unit for under $1,000:
- Check eBay, BioSurplus, Labx, university surplus sales
- Verify the device connects cleanly and has been used < 50 flow cells total (ask seller)
- You'll still need to buy flow cells and library kits at full price

---

## Not Recommended: Other Sequencers

### Oxford Nanopore Flongle — NOT RECOMMENDED for WGS
- Smaller, cheaper adapter ($90/flow cell)
- Only ~1–2 Gb output per flow cell
- Human genome needs ~33 Gb for 10× coverage
- Would need 17–33 Flongle runs — completely impractical

### Oxford Nanopore PromethION — NOT RECOMMENDED
- Research-grade, high-throughput (~300 Gb/run)
- Recommended by ONT for "human and large genome sequencing"
- Cost: ~$35,000+
- Designed for institutional use, not available for home purchase

### Illumina-based approaches — NOT RECOMMENDED for home use
- No home-use instrument exists under $20,000
- Short reads (150–300 bp) make structural variant calling much harder

### PacBio — NOT RECOMMENDED
- Excellent long reads, very high accuracy
- Cheapest instrument: ~$150,000+

---

## Flow Cells — Key Details
- Model: **R10.4.1** (FLO-MIN114) — current generation
- Cost: ~$850 each
- Storage: **2–8°C refrigerator** (NOT freezer — freezing kills flow cells)
- Shelf life: ~3 months from manufacture
- Rated pore count: 800+ (always run flow cell check before loading DNA)
- Typical output: 15–35 Gb per flow cell (DNA quality and loading are the biggest variables)
- For 10× coverage: ~33 Gb needed → 1–3 flow cells depending on quality
- For 30× coverage: ~99 Gb needed → 3–7 flow cells

**Don't stockpile flow cells** — order 2–3 at a time and use them fresh.

---

## Software
- **MinKNOW**: ONT's sequencing control and basecalling software
  - Free, download from nanoporetech.com/downloads
  - Requires ONT account (free to create)
  - Real-time basecalling on Apple Silicon M-series Macs (HAC model)
- **Dorado**: ONT's standalone basecaller (faster, higher accuracy post-run re-calling)
  - Runs well on Apple Silicon

---

## Verdict
**Buy MinION Mk1D Pack at $5,150** if budget allows — it's dramatically better value than device-only + separate consumables if you plan to reach 15–30× coverage.

**Buy MinION Mk1D device-only at $3,150** if you want lower upfront spend and will add flow cells one at a time.

**Buy used MinION Mk1B** if you find a clean unit under $1,000 — it still works with current flow cells and kits.

This is the one piece of equipment with no viable alternative. There is no DIY sequencer.
