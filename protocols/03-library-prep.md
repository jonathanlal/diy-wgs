# Protocol 3: Library Preparation (ONT Ligation Kit SQK-LSK114)

**Time:** ~1.5 hours active
**Prerequisites:** Extracted DNA (≥1,000 ng), MinION connected, MinKNOW installed
**Output:** 75 µL sequencing-ready library, flow cell loaded

---

## Why Ligation Kit over Rapid Kit?
The Rapid Kit (SQK-RAD114) is faster (20 min) but:
- Uses a transposase that fragments DNA more aggressively
- Lower yield per flow cell (20–40% less data)
- Often results in shorter reads
The Ligation Kit takes longer but gives 2–3× better yield — fewer flow cells wasted.

---

## Reagents Needed (from SQK-LSK114 kit)
Store all frozen at −20°C until use. Thaw on ice.
- End-prep enzyme mix (NEBNext FFPE DNA Repair + End Repair/dA-Tailing)
- Ligation adapter (LA)
- Ligation Buffer (T4 DNA Ligase Buffer, 10×)
- T4 DNA Ligase
- Short Fragment Buffer (SFB)
- Elution Buffer (EB)
- Flow Cell Flush (FCF)
- Flow Cell Tether (FCT)
- Sequencing Buffer (SQB)
- Library Beads (LIB) — keep at 4°C, not frozen
- BSA (50 mg/mL) — can buy separately (NEB B9000S)

---

## Step 1: Thaw and Prepare

- [ ] Thaw all kit reagents on ice (30 min)
- [ ] Thaw one DNA aliquot on ice
- [ ] Prepare tube labels: "END-PREP", "LIGATION", "CLEANED LIBRARY"
- [ ] Preheat thermocycler: program two steps — 20°C × 5 min, then 65°C × 5 min, hold 4°C

---

## Step 2: DNA End-Prep (Repair + A-tailing)

- [ ] In a 1.5mL tube, mix:
  - Up to 1 µg DNA in ≤47 µL (top up with nuclease-free water if needed)
  - 3.5 µL Ultra II End-prep enzyme mix
  - 7 µL Ultra II End-prep reaction buffer
  - Nuclease-free water to 60 µL total
- [ ] Mix by flicking + brief spin
- [ ] Incubate in thermocycler: **20°C × 5 min → 65°C × 5 min → hold 4°C**
- [ ] Place on ice when done

---

## Step 3: SPRI Bead Cleanup of End-Prepped DNA

- [ ] Allow SPRI beads (Ampure XP or similar) to reach room temperature (10 min)
- [ ] Add 60 µL SPRI beads to the 60 µL end-prepped DNA → mix by pipetting 10×
- [ ] Incubate 5 min at room temperature
- [ ] Place on magnetic rack until solution clears (~3 min)
- [ ] Remove and discard supernatant
- [ ] Add 200 µL 80% ethanol (freshly prepared), incubate 30 sec, remove
- [ ] Repeat ethanol wash once more
- [ ] Air-dry beads 30 sec (don't over-dry — beads will crack)
- [ ] Remove from magnet, add 61 µL Elution Buffer, mix to resuspend
- [ ] Return to magnet, transfer ~60 µL eluted DNA to new tube

---

## Step 4: Adapter Ligation

- [ ] In a new 1.5mL tube, mix:
  - 60 µL cleaned end-prepped DNA
  - 25 µL Ligation Buffer (T4 × 10 — add LAST as it's viscous)
  - 10 µL NEBNext Quick Ligation Module
  - 5 µL Ligation Adapter (LA)
  - Total: 100 µL
- [ ] Mix gently by flicking (do NOT vortex)
- [ ] Incubate at **room temperature for 10 minutes**

---

## Step 5: SPRI Bead Cleanup of Ligated Library

- [ ] Add 40 µL SPRI beads → mix 10×, incubate 5 min
- [ ] Magnetic rack until clear (~3 min), remove supernatant
- [ ] Add 250 µL **Short Fragment Buffer (SFB)** — not ethanol — incubate 30 sec, remove
- [ ] Repeat SFB wash once (removes unligated adapters without losing short reads)
- [ ] Air-dry briefly, remove from magnet
- [ ] Add 15 µL Elution Buffer, resuspend beads, incubate 10 min room temp
- [ ] Magnetic rack, transfer ~15 µL to new tube — this is your **cleaned library**

---

## Step 6: Quantify Library

- [ ] Run Qubit dsDNA HS (high sensitivity) assay on 1 µL library
- [ ] Record concentration: ______ ng/µL
- [ ] Calculate input for loading:
  - Target: load 5–50 fmol of library
  - Approximate using: fmol = (ng/µL × 1000) / (660 × average fragment size in kb)
  - Typical loading: 5–15 µL of library
- [ ] Note: if Qubit HS assay kit not available, load 10 µL of library as reasonable default

---

## Step 7: Flow Cell Check

Before loading — run flow cell check in MinKNOW:

- [ ] Remove flow cell from fridge, let sit at room temperature for **20 minutes**
- [ ] Slide flow cell into MinION, press firmly
- [ ] In MinKNOW: device → flow cell → "Flow Cell Check" → wait ~5 min
  - 1,200+ pores: excellent
  - 800–1,200: good, proceed
  - <800: contact ONT, consider replacement

---

## Step 8: Prime Flow Cell

⚠️ Leave flow cell in MinION after check — do NOT remove it.

- [ ] Prepare Priming Mix: 1,170 µL FCF + 30 µL FCT + 5 µL BSA (50 mg/mL)
- [ ] Slide priming port cover clockwise to open
- [ ] Slowly draw back 20–30 µL with P1000 to check for air bubble — stop if you see membrane
- [ ] Slowly load **800 µL Priming Mix** into priming port — go slow, no bubbles
- [ ] Wait **5 minutes**

---

## Step 9: Prepare Final Loading Mix

While waiting for priming:

- [ ] Vortex Library Beads (LIB) gently, then pipette up/down 10×
- [ ] In a new 1.5mL tube, mix:
  - 37.5 µL Sequencing Buffer (SQB)
  - 25.5 µL Library Beads (LIB) — pre-mixed
  - 12 µL your cleaned library
  - Total: 75 µL

---

## Step 10: Load Flow Cell

- [ ] Open SpotON sample port
- [ ] Load **200 µL Priming Mix** into the **priming port** (not SpotON)
- [ ] Add **75 µL library** to the **SpotON port** dropwise:
  - Touch pipette tip gently to port edge
  - Release one drop, wait for it to be drawn in
  - Repeat until all 75 µL loaded — do NOT rush this
- [ ] Close SpotON port
- [ ] Close priming port
- [ ] Place light shield on flow cell

---

## Troubleshooting

| Problem | Likely cause | Fix |
|---------|-------------|-----|
| Low pore count on check | Flow cell too cold, or old stock | Let warm to RT fully, check storage temp |
| Air bubble introduced | Pipetting too fast | Start over with priming if needed |
| Library yield too low after cleanup | Over-dried beads, or SFB wash removed too much | Shorten bead dry time, check SFB wash |
