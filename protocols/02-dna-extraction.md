# Protocol 2: DNA Extraction (Zymo Quick-DNA Miniprep Plus)

**Time:** ~1.5–2 hours (the kit says 20 min — it lies)
**Prerequisites:** Cell pellet from Protocol 01, Zymo kit, thermocycler/sous vide, centrifuge
**Output:** ~50 µL of purified genomic DNA in elution buffer, stored at −20°C

---

## One-Time Setup: Reconstitute Proteinase K

Do this once when you first receive the Zymo kit.

- [ ] Add 1,040 µL Proteinase K Storage Buffer to the lyophilized Proteinase K tube
- [ ] Mix vigorously: flick 30–40 times, pipette up/down 20× with P1000
- [ ] Brief pulse spin (balance with 1 mL water tube), ~2,000 × g, 5–10 sec
- [ ] Label 8–10 clean 0.2mL PCR tubes with "PK" + date
- [ ] Aliquot 100 µL per PCR tube (~10 aliquots)
- [ ] Store aliquots at −20°C (each aliquot = ~5 extractions, 20 µL per extraction)

**Note:** Avoid freeze-thaw cycles — Proteinase K loses ~10% activity per cycle.

---

## Day-Of Setup

- [ ] Thaw one Proteinase K aliquot at room temperature (~1 min). Keep on ice once thawed.
- [ ] Label tubes: three 0.2mL PCR tubes ("1", "2", "3"), one clean 1.5mL tube ("FINAL DNA")
- [ ] Set thermocycler/sous vide to 55°C (preheat now)
- [ ] Set aside one Zymo column + collection tube as dedicated balance for centrifuge steps

---

## Step 1: Resuspend Pellet for Lysis

- [ ] Flick pellet tube to loosen
- [ ] Pipette up/down with P200 until fully homogeneous — no clumps
- [ ] Check volume of resuspended cells
- [ ] If less than 200 µL, add DNA Elution Buffer or PBS to bring to exactly **200 µL**

---

## Step 2: Lyse Cells

⚠️ Time-sensitive: proceed within 30 min of cell collection, or 30 min from refrigerator.

- [ ] To the 200 µL resuspended cells, add:
  - 200 µL BioFluid & Cell Buffer (Red cap)
  - 20 µL Proteinase K (from thawed aliquot)
- [ ] Mix: flick tube 20×, then pipette vigorously ~20×
- [ ] Split evenly into PCR tubes 1, 2, 3 (~140 µL each)
- [ ] Cap all three tubes securely
- [ ] Place in thermocycler/sous vide at **55°C for 10 minutes**

**After this step, nucleases are denatured — time pressure is relieved.**
Get lysate onto the column within 30–60 minutes.

- [ ] Recombine lysate from three PCR tubes into one clean 1.5mL tube (~380–400 µL total)

---

## Step 3: Bind DNA to Column

- [ ] Add **1× volume Genomic Binding Buffer** (equal to your lysate, ~400 µL) to the lysate tube
- [ ] Mix: flick 20×, pipette up/down 15×
- [ ] Transfer entire mixture to a Zymo-Spin IIC-XLR Column in a collection tube
- [ ] Add ~800 µL water to your balance column
- [ ] Centrifuge: **8,000 × g, 2 minutes**
- [ ] Discard flow-through and collection tube

---

## Step 4: Wash

- [ ] Place column in a **new** collection tube
- [ ] Add 400 µL **DNA Pre-Wash Buffer** → spin **8,000 × g, 2 min** → pour out flow-through
- [ ] Add 700 µL **g-DNA Wash Buffer** → spin **8,000 × g, 2 min** → pour out flow-through
- [ ] Add 200 µL **g-DNA Wash Buffer** → spin **8,000 × g, 2 min** → discard collection tube

---

## Step 5: Elute DNA

- [ ] Transfer column to your labeled **FINAL DNA** 1.5mL tube
- [ ] Add **50 µL DNA Elution Buffer** directly onto the white membrane
- [ ] Incubate at room temperature for **5 minutes** (set a timer)
- [ ] Centrifuge: **8,000 × g, 2 minutes**
- [ ] Reload the eluate back onto the same column
- [ ] Incubate 3 minutes at room temperature
- [ ] Centrifuge: **8,000 × g, 2 minutes** — this is your purified DNA

---

## Step 6: Quantify DNA

- [ ] Run Qubit dsDNA BR assay on 2 µL of your eluted DNA
- [ ] Record: ______ ng/µL × 48 µL remaining = ______ ng total
- [ ] Target: ≥1,000 ng total (ideally 2,000–5,000 ng) for Ligation kit
- [ ] If yield is low, consider running a second extraction and pooling

---

## Step 7: Aliquot and Store

- [ ] Label 4–6 clean 0.2mL PCR tubes with initials + date + aliquot number
- [ ] Gently pipette DNA up/down 5× to mix (do NOT vortex — shears gDNA)
- [ ] Distribute: 4× 10 µL aliquots + 1× working stock for library prep
- [ ] Store at **−20°C** (long term) or **4°C** (use within 1 week)
- [ ] Use one aliquot per library prep — avoid thawing and refreezing others

---

## Troubleshooting

| Problem | Likely cause | Fix |
|---------|-------------|-----|
| Low DNA yield (<500 ng total) | Poor lysis, or column overloaded | Run second extraction, pool both |
| DNA looks degraded on gel (smear) | Nuclease activity before lysis | Work faster, keep on ice |
| Qubit reads zero | Sample too dilute, or pipetting error | Re-run assay with fresh 2 µL |
| Column clogged during wash | Sample contained too much protein/lipid | Pre-spin lysate before loading |
