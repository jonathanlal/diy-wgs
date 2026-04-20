# Equipment: DNA Quantification

**Decision status:** OPEN — Qubit (used) strongly recommended

---

## Why It Matters
Loading the wrong amount of DNA onto a flow cell is the #1 cause of poor sequencing yield.
- Too little DNA → few reads, low coverage, wasted $850 flow cell
- Too much DNA → pores clog, run dies early, wasted $850 flow cell
- Correct loading: 1–5 µg DNA for Ligation kit (sweet spot around 2–3 µg)

The Vibe Genomics author **skipped quantification entirely** and noted this as one of the
main reasons for variable results across flow cells. One flow cell gave half the yield of another.

**A $200 used Qubit protecting a $850 flow cell is an obvious investment.**

---

## Options

### 1. Qubit 4 Fluorometer — RECOMMENDED
Thermo Fisher's fluorescent DNA quantification system. Uses dye that only fluoresces when
bound to double-stranded DNA — gives accurate mass concentration (ng/µL) regardless of
RNA, protein, or other contaminants.

- New: ~$500–600
- Used (eBay, BioSurplus): ~$150–250
- Consumables: Qubit dsDNA BR Assay Kit (~$100 for 100 reactions — enough for years)
- Protocol: mix 2 µL sample + 198 µL working solution, read in 2 min

**This is the standard tool for this purpose.** Fast, accurate, easy.

### 2. NanoDrop — ADEQUATE but less accurate
NanoDrop measures UV absorbance at 260nm. Simple and fast.
- Measures all nucleic acid (DNA + RNA + single-stranded), not just dsDNA
- Overestimates concentration if sample has RNA or degraded DNA
- Useful for rough checks and purity ratios (260/280 for protein contamination)
- NanoDrop Lite: ~$3,000 new (overpriced for us)
- NanoDrop 1000 used: ~$500–800 — expensive for our use
- **Not recommended** unless you already have access to one

### 3. Spectrophotometer (generic) — POOR ACCURACY
A basic UV spectrophotometer can measure A260:
- Uses Beer-Lambert law: concentration = A260 × 50 ng/µL per A260 unit
- Same accuracy issues as NanoDrop — measures everything, not just dsDNA
- Cheap units ($100–200) have poor accuracy at low concentrations
- Not recommended

### 4. Agilent TapeStation / Bioanalyzer — OVERKILL
- Measures concentration AND fragment size distribution
- Great for QC but ~$15,000–40,000 instrument cost
- Fragment size check can be done visually on a gel instead

### 5. Gel Electrophoresis (fragment size check only) — FREE if you have Bento
- Run a quick gel to verify DNA is high molecular weight (not degraded)
- Does NOT give you a concentration
- Useful as a secondary check alongside Qubit
- Not useful for quantification alone

### 6. Skip Quantification — RISKY
- Author did this and got variable results
- Acceptable if you're willing to accept the risk of a wasted flow cell
- Can partially compensate by doing the extraction twice and pooling
- Not recommended when Qubit costs $200 used

---

## Protocol (with Qubit)
1. Prepare working solution: 199 µL Qubit Buffer + 1 µL Qubit Reagent per sample
2. Add 2 µL of your DNA sample to 198 µL working solution
3. Vortex gently, incubate 2 min at room temperature
4. Read in Qubit fluorometer
5. Result: ng/µL concentration
6. Calculate total yield: ng/µL × volume (µL) = total ng
7. Target: >1,000 ng total for Ligation kit (ideally 2,000–5,000 ng)

---

## Verdict
**Buy a used Qubit 4 on eBay. ~$150–250. Add one Qubit dsDNA BR kit (~$100).**
This is the single highest-ROI purchase in the project relative to cost.
Without it, you're gambling $850 flow cells on unknown DNA concentration.
