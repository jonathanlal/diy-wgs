# Equipment: Thermocycler

**Decision status:** OPEN — sous vide is likely sufficient, evaluating Arduino option

---

## What It Does
Controls precise temperature for timed incubations. Used in:
1. Cell lysis: 55°C × 10 min (Proteinase K digestion)
2. Library prep (Ligation kit): multiple temperature holds
3. Library prep (Rapid kit): 30°C × 2 min, then 80°C × 2 min

---

## Temperature Requirements for Our Workflow
| Step | Temperature | Duration | Ramp speed needed? |
|------|-------------|----------|--------------------|
| Cell lysis | 55°C | 10 min | No — hold only |
| Rapid kit tagmentation | 30°C → 80°C | 2 min each | Moderate |
| Ligation kit end-prep | 20°C → 65°C | 5 min each | Moderate |
| Ligation kit adapter ligation | 20°C | 10 min | No |
| Ligation kit heat kill | 65°C | 10 min | No |

Key insight: **we only need simple temperature holds, not fast thermal cycling (PCR).**
This means inexpensive alternatives to a real thermocycler are viable.

---

## Options

### 1. Two Sous Vide Immersion Circulators — RECOMMENDED (cheapest viable)
Sous vide sticks circulate heated water to a precise temperature (±0.1°C accuracy).
Used by setting a beaker of water to the target temp and placing capped PCR tubes in it.

- Set one to 55°C (lysis temperature), one to 80°C (heat kill)
- Swap tubes between them for multi-step protocols
- Temperature accuracy is excellent for cooking — more than sufficient for our holds

**Models:**
- Inkbird ISV-100W: ~$50
- Anova Nano: ~$100
- Any basic sous vide will work — $50–100 each × 2 = **$100–200 total**

**Limitations:**
- Slower ramp time between temps than a real thermocycler
- Need to swap tubes manually between water baths
- Not ideal if you add PCR to the workflow later (though we're not doing PCR for WGS)

### 2. Budget Benchtop Thermocycler — RECOMMENDED if budget allows
Real thermocyclers on the used market:
- Bio-Rad T100: ~$300–500 used, excellent entry-level unit
- Eppendorf Mastercycler: ~$300–600 used
- Generic thermal cycler (PCR machine) on eBay: $150–300

Advantages over sous vide: faster ramp rates, programmable, works for any future PCR work.

### 3. Arduino + PID Controller + Heated Plate — DIY OPTION (evaluating)
A fully DIY thermocycler is possible:
- Arduino Uno or Nano: ~$5–10
- PID temperature controller module: ~$15
- Peltier element (heating + cooling): ~$10–20
- Aluminum block with wells for 0.2mL PCR tubes: ~$20 machined or 3D printed
- Thermistor or thermocouple: ~$5
- Power supply: ~$15
- **Total: ~$75–100**

This can be programmed to hold any temperature sequence. Several open-source designs exist (OpenPCR, PocketPCR). Accuracy is ±0.5–1°C — acceptable for our simple holds.

**This is worth investigating further.** The hold-only nature of our protocol makes this very feasible.
See: https://openpcr.org/ and https://pocketpcr.github.io/ for reference designs.

### 4. Bento Lab Pro — NOT RECOMMENDED
- $1,800 — includes thermocycler but we're paying for gel electrophoresis we don't need
- Great unit but terrible value for our use case

---

## Recommendation
**Short term:** Get 2× sous vide sticks (~$100–200). Works immediately, no setup.
**Long term / if doing more wet lab work:** Used Bio-Rad T100 (~$400) or DIY Arduino thermocycler (~$75).

The DIY Arduino thermocycler is a fun sub-project and genuinely viable. Worth a dedicated build
session before the main genome run — prototype and test it with water first.

---

## Verdict
**Decision still open.** Sous vide is the fastest path. Arduino DIY is the cheapest path if
we're willing to spend a few hours building it. Both are viable.
