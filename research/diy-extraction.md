# DIY DNA Extraction — CTAB Protocol vs Zymo Kit

**Decision status:** OPEN — use Zymo for first run, evaluate CTAB for subsequent runs

---

## Why Consider DIY?

The Zymo Quick-DNA Miniprep Plus Kit costs ~$54 for 10 preps = ~$5.40 per extraction.
While not expensive in absolute terms, the CTAB protocol costs ~$15 in reagents total for
dozens of extractions. More importantly, understanding the chemistry is educational.

---

## How DNA Extraction Works (Both Methods)

Both protocols do the same thing in 4 stages:
1. **Lyse cells** — break open cells to release DNA
2. **Remove proteins** — Proteinase K digests proteins; detergent/salt precipitates them
3. **Separate DNA** — either column-based (Zymo) or precipitation-based (CTAB)
4. **Elute/resuspend DNA** — recover pure DNA in buffer

---

## CTAB Protocol — DIY Method

CTAB (cetyltrimethylammonium bromide) is a detergent that binds DNA and precipitates it away
from polysaccharides and proteins when combined with salt. Classical plant/bacteria method,
works well for buccal cells.

### Reagents needed (~$15 total, reusable for many runs)
| Reagent | Source | Cost |
|---------|--------|------|
| CTAB (cetyltrimethylammonium bromide) | Sigma or Amazon, 25g | ~$15 |
| NaCl (table salt) | Grocery | ~$1 |
| EDTA | Online lab supplier, 100g | ~$5 |
| Tris-HCl (pH 8.0) | Online, or make from Tris base | ~$5 |
| Chloroform:isoamyl alcohol (24:1) | Lab supplier | ~$15 — this is the hard one |
| Isopropanol | Pharmacy (rubbing alcohol ≥91%) | ~$3 |
| 70% ethanol | Pharmacy | ~$3 |

**The chloroform step is the main complication.** Chloroform is a hazardous chemical requiring:
- Ventilation (work near an open window or outdoors)
- Nitrile gloves
- No open flames

Chloroform can be ordered from chemical suppliers with a business address.
(Claude noted in the article: forming an LLC gets you a legitimate business address for ordering.)

### CTAB Protocol (simplified for buccal cells)
1. Resuspend cell pellet in 500 µL CTAB buffer (2% CTAB, 100 mM Tris pH 8, 20 mM EDTA, 1.4 M NaCl)
2. Add Proteinase K (20 µL of 20 mg/mL), incubate 55°C × 30 min
3. Add equal volume chloroform:isoamyl (24:1), vortex, centrifuge 10,000 × g × 10 min
4. Transfer aqueous (top) phase to new tube
5. Precipitate DNA: add 0.7× volume isopropanol, mix, centrifuge 10,000 × g × 10 min
6. Discard supernatant, wash pellet with 70% ethanol
7. Air-dry pellet 5 min, resuspend in TE buffer or nuclease-free water

### CTAB Pros
- Cost: ~$15 upfront, essentially $0 per run after that
- No kit supplier dependency
- Educational — understand the chemistry
- Decent yield for buccal cells

### CTAB Cons
- Requires chloroform (hazardous, needs ventilation)
- More steps, more time (~2 hours vs 1.5 hours for Zymo)
- More variable yield — operator-dependent
- Harder to get consistent high-purity DNA
- Isopropanol precipitation can co-precipitate RNA (need RNase treatment)

---

## Zymo Kit — Pros and Cons

### Pros
- Consistent, reliable yield
- Clean DNA (silica column removes RNA automatically)
- Simple protocol, less skill required
- Good documentation, known quantities
- ~$5.40 per extraction — genuinely cheap

### Cons
- Proprietary, requires ongoing kit purchases
- Black-box chemistry
- If Zymo discontinues or raises prices, workflow is disrupted
- Shipping restrictions to non-business addresses (Zymo prefers business addresses)

---

## Recommendation

**First run:** Use the Zymo kit. Minimize variables on first attempt.
The reliability and simplicity are worth the $54 for a proof-of-concept run.

**Subsequent runs / after first success:** Try the CTAB protocol.
If you can replicate Zymo-comparable yield without chloroform concerns, switch.

**Alternative DIY approach to evaluate:** Magnetic bead-based extraction
- Uses silica-coated magnetic beads (similar chemistry to Zymo column, just magnetic)
- AMPure XP beads (already buying for library prep cleanup) can work for initial DNA cleanup
- No hazardous chemicals
- Cost: ~$0 additional if already have AMPure beads

---

## Alternative: Chelex-100 Extraction (ultra-simple)

Chelex-100 is an ion-exchange resin that chelates metal ions (which activate nucleases).
Simplest possible extraction for PCR-quality DNA:

1. Resuspend pellet in 200 µL 5% Chelex-100 solution
2. Boil at 95°C for 10 minutes
3. Centrifuge, take supernatant — that's your DNA

**Pros:** 3 steps, no hazardous chemicals, ~$20 for a large bottle of Chelex
**Cons:** DNA quality is lower, not suitable for long-read sequencing (fragments DNA)
**Verdict:** Not suitable for nanopore WGS — requires high molecular weight DNA

---

## Decision Checklist
- [ ] Buy Zymo kit for first run
- [ ] After first successful run, evaluate CTAB protocol on a test extraction
- [ ] Compare Qubit yield and run quality between CTAB and Zymo extractions
- [ ] If CTAB gives comparable results, switch to CTAB + Proteinase K for ongoing runs
