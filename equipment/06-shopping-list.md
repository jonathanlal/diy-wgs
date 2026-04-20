# Master Shopping List

**Last updated:** 2026-04-20
**Status key:** ⬜ Not ordered | 🔄 Researching | 🛒 Ordered | ✅ Received

---

## Equipment (One-Time Purchases)

> **MinION price update:** Mk1B is legacy. Current model is Mk1D at $3,150 device-only, or $5,150 for the Pack (device + 5 flow cells + sequencing kit). See equipment/01-sequencer.md and BUDGET.md.

| Status | Item | Est. Cost | Source | Notes |
|--------|------|-----------|--------|-------|
| ⬜ | **Option A:** MinION Mk1D Pack | $5,150 | store.nanoporetech.com | Best value — includes device + 5 flow cells + kit; no need to buy sequencing consumables separately |
| ⬜ | **Option B:** MinION Mk1D device only | $3,150 | store.nanoporetech.com | Buy if starting with just 1–2 flow cells; add consumables separately |
| ⬜ | **Option C:** Used MinION Mk1B | $500–1,500 | eBay / BioSurplus / Labx | Legacy but works; R10.4.1 flow cells still compatible |
| ⬜ | Microcentrifuge (used, 10,000+ RPM) | ~$150 | eBay | Eppendorf 5415D or 5424 preferred |
| ⬜ | Thermocycler / sous vide × 2 | ~$100–200 | Amazon | See equipment/03-thermocycler.md |
| ⬜ | Micropipette set (P2, P20, P200, P1000) | ~$150 | eBay | Used Gilson Pipetman preferred |
| ⬜ | Qubit 4 fluorometer (used) | ~$200 | eBay / BioSurplus | Critical for flow cell protection |

**Equipment subtotal (Pack route): ~$5,850–5,950**
**Equipment subtotal (device-only route): ~$3,850–3,950**

---

## Sequencing Consumables (Per Run)

> If you buy the MinION Mk1D **Pack**, the 5 flow cells and sequencing kit are included — skip those rows below.
>
> **Key cost lever:** Flow Cell Wash Kit (EXP-WSH004) enables 3 reuses per $850 flow cell. Buy this — it's officially supported by ONT.

| Status | Item | Est. Cost | Source | Notes |
|--------|------|-----------|--------|-------|
| ⬜ | R10.4.1 Flow cells × 2 (device-only route) | ~$1,700 | store.nanoporetech.com | Order fresh, use within weeks; included in Pack |
| ⬜ | ONT Ligation Sequencing Kit (SQK-LSK114) | ~$500 | store.nanoporetech.com | Do NOT get Rapid (SQK-RAD114); included in Pack |
| ⬜ | **Flow Cell Wash Kit (EXP-WSH004)** | **~$250** | store.nanoporetech.com / LabMart | Enables 3–4 runs per flow cell; saves $1,000–1,700 in flow cells |
| ⬜ | BSA (50 mg/mL, molecular biology grade) | ~$30 | NEB (B9000S) or Sigma | For flow cell priming |

**Sequencing consumables subtotal (device-only route): ~$2,480**
**Sequencing consumables subtotal (Pack route): ~$280** (wash kit + BSA; flow cells and kit included in Pack)

---

## Extraction Consumables

| Status | Item | Est. Cost | Source | Notes |
|--------|------|-----------|--------|-------|
| ⬜ | Zymo Quick-DNA Miniprep Plus Kit (10 preps) | ~$54 | Zymo Research (D4068T) | Or buy 50-prep kit for better value |
| ⬜ | Qubit dsDNA BR Assay Kit (100 rxn) | ~$100 | Thermo Fisher | Works with used Qubit 4 |

**Extraction consumables subtotal: ~$154**

---

## General Lab Consumables

| Status | Item | Est. Cost | Source | Notes |
|--------|------|-----------|--------|-------|
| ⬜ | 1.5mL microcentrifuge tubes (×500) | ~$20 | Amazon | Burn through these fast |
| ⬜ | 0.2mL PCR tubes (×500) | ~$15 | Amazon | Strips or individual |
| ⬜ | Pipette tips — 10 µL filtered (×96) × 2 | ~$40 | Amazon | For P2/P20 |
| ⬜ | Pipette tips — 200 µL filtered (×96) × 2 | ~$40 | Amazon | For P200 |
| ⬜ | Pipette tips — 1000 µL filtered (×96) × 2 | ~$40 | Amazon | For P1000 |
| ⬜ | Non-iodized table salt (for mouthwash) | ~$2 | Grocery | For buccal collection |
| ⬜ | Bottled water | ~$2 | Grocery | For mouthwash and reagent prep |

**General consumables subtotal: ~$159**

---

## Totals

| Route | First genome | Subsequent genomes |
|-------|-------------|-------------------|
| Pack route (Mk1D Pack + used equipment) | **~$6,150** | ~$2,250 |
| Device-only route (Mk1D + 2 flow cells) | **~$6,350** | ~$2,250 |
| Used Mk1B route (eBay unit $500–1,500) | **~$4,450–4,950** | ~$2,250 |

---

## Not Buying / Decided Against

| Item | Why Not |
|------|---------|
| ONT MinION Mk1D Starter Bundle (~$5,200 old) | Replaced by Pack; Pack includes better flow cells (R10.4.1) |
| Bento Lab Pro (~$1,800) | We don't need the gel unit; cheaper alternatives exist |
| NanoDrop spectrophotometer | Overpriced used; Qubit is better for dsDNA quantification |
| Rapid Sequencing Kit (SQK-RAD114) | Lower yield than Ligation; more flow cells needed |
| DGX Spark / GPU workstation | LongShot runs fine on Apple Silicon Mac |

---

## Still Deciding

| Item | Decision needed | See |
|------|----------------|-----|
| Thermocycler type | Sous vide vs Arduino DIY vs used unit | equipment/03-thermocycler.md |
| DNA quantification | Qubit used vs skip | equipment/05-quantification.md |
| DNA extraction method | Zymo kit vs DIY CTAB | research/diy-extraction.md |
