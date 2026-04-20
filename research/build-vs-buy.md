# Build vs Buy — Consolidated Analysis

**Last updated:** 2026-04-20

---

## Summary Table

| Item | Buy Option | Buy Cost | Build Option | Build Cost | Verdict |
|------|-----------|---------|--------------|-----------|---------|
| Sequencer (MinION) | MinION Mk1B device | ~$1,000 | No viable alternative | N/A | **BUY** |
| Centrifuge | Used Eppendorf 5415D | ~$150 | DIY — dangerous at 8,000×g | N/A | **BUY** |
| Thermocycler | Used Bio-Rad T100 | ~$400 | Arduino PID thermocycler | ~$75 | **BUILD or sous vide** |
| Pipettes | Used Gilson Pipetman set | ~$150 | Not viable for µL accuracy | N/A | **BUY** |
| DNA quantification | Used Qubit 4 | ~$200 | DIY fluorometer (Arduino) | ~$150 | **BUY used Qubit** |
| DNA extraction kit | Zymo miniprep kit | ~$54 | CTAB DIY protocol | ~$15 | **EVALUATE** — see diy-extraction.md |
| Compute / bioinformatics | Mac M-series (already own) | $0 | N/A | N/A | **USE WHAT YOU HAVE** |

---

## Detailed Reasoning

### Sequencer — BUY ($1,000)
No alternative exists for home long-read nanopore sequencing. The MinION is the only
consumer-accessible nanopore sequencer. The Flongle is too low throughput for WGS.
Illumina has no home product. PacBio is $150K+.

**Risk of building:** Nanopore sequencing requires nanofabricated flow cells with biological
protein pores. This is not DIY-buildable.

### Centrifuge — BUY ($150 used)
At 8,000–14,000 × g, a centrifuge rotor spins at 10,000–14,000 RPM. A rotor failure at
these speeds sends shards outward with significant kinetic energy. Commercial units are
engineered with containment for exactly this failure mode. DIY centrifuges that exist online
are designed for lower speeds (PCR tube balance checks, etc.) or are genuinely dangerous.

For $150 on eBay, this is not worth building.

### Thermocycler — BUILD or sous vide ($75–200)
**This is the clearest build opportunity.** Our protocol only needs simple temperature holds,
not fast cycling. Two options:

**Option 1: Sous vide sticks (~$100–200 total)**
- Fastest to set up, available tomorrow
- ±0.1°C accuracy at the water level
- Limitation: manual tube transfer between temps, slower ramp

**Option 2: Arduino PID thermocycler (~$75)**
- Arduino Nano + PID controller + Peltier element + machined aluminum block
- Reference designs: OpenPCR, PocketPCR (open-source, well-documented)
- Can be programmed for any temperature sequence
- Fully owned, expandable
- Build time: ~4–6 hours

Recommendation: Start with sous vide to unblock the project. Build the Arduino thermocycler
as a parallel project. If it works well, use it for subsequent runs.

### Pipettes — BUY ($150 used)
Calibrated liquid transfer at sub-microliter scale is not practical to DIY. Commercial pipettes
use precision-machined pistons with calibrated springs. The cost of used name-brand pipettes
is low enough that building an alternative makes no sense.

### DNA Quantification — BUY used Qubit ($200)
A DIY fluorometer is technically possible (photodetector + LED at 650nm + Qubit dye) but
calibration against known DNA standards is complex. For $200, a used Qubit is reliable,
fast, and saves $850 flow cells from bad loads. Build time and calibration hassle not worth it.

### DNA Extraction — EVALUATE (Zymo vs CTAB)
See `research/diy-extraction.md` for full analysis.
Short version: CTAB protocol costs ~$15 in reagents vs $54 for Zymo kit.
Yield and purity are comparable. Worth trying for subsequent runs if first run uses Zymo.

### Bioinformatics — FREE
All tools are free, open-source, and run on Apple Silicon.
No cloud needed unless using DeepVariant (and LongShot is a fine alternative).

---

## Things NOT to Build
- Anything involving nanofabrication (flow cells)
- High-speed spinning components (centrifuge rotor)
- Precision liquid dispensing (pipettes)

## Things Worth Building
- Thermocycler (if interested in the project — Arduino PID is genuinely fun)
- Dashboard / analysis tools (Claude + open-source bioinformatics)
- Custom analysis scripts for specific SNP queries
