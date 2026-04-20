# Sequencer Alternatives & DIY Feasibility

**Research date:** 2026-04-20
**Verdict:** No cheaper commercial alternative exists. DIY is not feasible. Key cost levers are flow cell washing and lower coverage targets.

---

## Can We Build Our Own Sequencer?

**Short answer: No.**

Nanopore sequencing sounds like it should be DIY-able — push DNA through a hole, measure current. The reality is layered proprietary technology:

### What's Inside the MinION

| Component | What it does | Can we DIY? |
|-----------|-------------|-------------|
| Nanopore protein (CsgG/R10.4.1 pore) | The actual "hole" DNA threads through | ❌ Requires protein engineering; patented design |
| Enzyme motor | Controls DNA translocation speed | ❌ Proprietary engineered enzyme; not purchasable |
| Lipid bilayer membrane | Hosts the nanopores | ⚠️ Technically possible but fragile; ONT's polymer formulation is trade secret |
| ASIC (custom silicon chip) | Detects picoamp current changes across hundreds of channels simultaneously | ❌ Custom chip — can't buy, can't fab without cleanroom + millions |
| Temperature control (Peltier) | Keeps the reaction at optimal temp | ✅ This part is trivially DIY-able |
| USB interface / MinKNOW | Data transfer and basecalling | ✅ MinKNOW is free; open-source basecallers exist |

**The hard walls are the nanopore protein and the ASIC.** The protein is what actually reads the sequence. The ASIC is what detects the tiny (picoamp-level) current changes with enough resolution across hundreds of channels at once. Neither can be sourced or replicated outside an advanced R&D lab.

### What About Solid-State Nanopores?
Academic groups make solid-state nanopores (e.g., drilling through SiN membranes with electron beams). In theory this doesn't need engineered proteins. In practice:
- Requires electron beam lithography or focused ion beam — $500k+ equipment
- Current accuracy is nowhere near biological nanopores
- Not WGS-ready; still proof-of-concept only
- Best estimate: 5–10 years from hobbyist feasibility

**Verdict:** The sequencer is a black box you have to buy. Focus cost-reduction effort elsewhere.

---

## Open-Source Basecalling (Actually Useful)

Even though you can't DIY the hardware, you can avoid ONT's proprietary basecalling software:

| Tool | Status | Notes |
|------|--------|-------|
| **Dorado** (ONT official) | Free | Works well; GPU optional |
| **Slorado** | Open-source (2025) | Equivalent accuracy; runs on embedded devices to GPUs |
| **Openfish** | Open-source (2025) | Modular basecalling; heterogeneous hardware support |
| **UNCALLED** (Johns Hopkins) | Open-source | Real-time adaptive sampling |

You don't pay for basecalling software with any approach. This isn't a meaningful cost lever.

---

## Commercial Alternatives Evaluated

### Oxford Nanopore — Other Products

| Device | Cost | Notes |
|--------|------|-------|
| **MinION Mk1D** | $3,150 device / $5,150 pack | ← Our recommendation |
| **MinION Mk1C** | ~$4,900 | Older model with onboard compute; not better value |
| **SmidgION** | TBD — not released | Smartphone-connected device; ONT describes it as "a few hundred dollars" — still vaporware as of 2026 |
| **Flongle** | $90/flow cell | Needs a MinION or GridION to run — not standalone. 1–2 Gb output — useless for WGS |
| **GridION** | ~$25,000 | 5 flow cells simultaneously; way overkill |
| **PromethION** | ~$35,000+ | Institutional research; not for home use |

**SmidgION** is worth watching. If released at ~$500–700, it would change the calculus significantly. As of 2026, no commercial launch date has been confirmed.

### Other Sequencing Technologies

| Device | Cost | Notes |
|--------|------|-------|
| **Illumina iSeq 100** | ~$20,000 | Short reads only (150 bp); inferior for long-read structural variants |
| **MGI DNBSEQ-E25** | Contact MGI | Portable; no public consumer pricing; marketed to small labs |
| **Element Biosciences AVITI** | $289,000 | Benchtop; institution-only |
| **PacBio Revio** | ~$150,000 | High accuracy long reads; institution-only |
| **Ultima Genomics UG 100** | $1.5 million | Ultra-high throughput; institution-only |

**AxBio** (startup) is developing a hybrid nanopore/polymerase approach targeting low-cost sequencing. Not commercially available, no pricing announced. Founded 2024; worth monitoring in 12–18 months.

### Verdict: No Alternative
For home WGS in 2026, the MinION Mk1D is the only viable option. Every alternative is either:
- Requires a host device (Flongle)
- Not released yet (SmidgION, AxBio)
- $20,000+ (everything else)

---

## Flow Cell Washing — Real Cost Savings

This is the most underused lever. ONT officially supports flow cell reuse via the **Flow Cell Wash Kit (EXP-WSH004)**.

### How It Works
1. After a sequencing run, wash the flow cell with DNase I solution
2. DNase digests residual DNA library from the pores
3. Pores recover from "unavailable" back to "single pore" state
4. Re-use the flow cell for another run

### Expected Yield Recovery
| Wash number | Expected % of original pores | Notes |
|-------------|------------------------------|-------|
| Fresh (run 1) | 100% | ~800+ pores |
| After wash 1 (run 2) | 60–80% | Still useful for WGS |
| After wash 2 (run 3) | 40–60% | Lower yield but viable for a third pass |
| After wash 3 (run 4) | 20–40% | Diminishing returns; consider retiring |

**Conservative estimate: 3 usable runs per flow cell.**

### Economics

| Scenario | Flow cells | Cost | Total output |
|----------|-----------|------|-------------|
| No washing (1 run per cell) | 3 cells | $2,550 | 45–105 Gb |
| Washing (3 runs per cell) | 1 cell + 2 wash kits | $850 + $500 | ~45–105 Gb (spread across 3 runs) |

The wash kit (~$250 per kit) effectively triples your sequencing capacity per flow cell purchased. Over multiple genomes, this is a massive cost reducer.

**Note:** When reusing flow cells, barcode your libraries to keep runs separate. Some residual DNA from the previous run may persist despite washing.

### Where to Buy
- **Flow Cell Wash Kit (EXP-WSH004)**: ~$250, available from ONT store and distributors (LabMart, Government Scientific Source)

---

## Coverage vs. Cost: The 10x Question

The standard recommendation is 30× coverage for clinical WGS. But the science supports much lower for health insights:

| Coverage | What you get | Notes |
|----------|-------------|-------|
| **5–10×** | SNV calls in well-covered regions, polygenic risk scores (via imputation), basic CNV | Useful; needs imputation reference panel |
| **10–15×** | Better SNV confidence, decent pharmacogenomics, most BRCA coding regions | Good for personal genomics goals |
| **15–20×** | Near-clinical SNV quality, reliable pharmacogenomics | Reasonable for most health use cases |
| **30×** | Clinical standard; structural variants; de novo mutations | Required for formal medical diagnostics |

### What 1–2 MinION Flow Cells Gets You

One fresh R10.4.1 flow cell: 15–35 Gb
- Human genome = 3.2 Gb
- 15 Gb / 3.2 Gb = **~5× coverage** (low end)
- 35 Gb / 3.2 Gb = **~11× coverage** (high end)
- Average (25 Gb): **~8× coverage**

**Two flow cells: ~10–22× coverage**

### Imputation Closes the Gap
Low-coverage WGS (1–10×) + computational imputation against a reference panel (like the 1000 Genomes or HGDP) recovers most of the statistical power of 30× WGS for common variants. Studies show:
- Polygenic risk scores at 1× WGS + imputation perform similarly to 30× for common variants
- Pharmacogenomics at 20× is well within established clinical thresholds
- Ultra-low coverage (0.5×) + imputation still detects most actionable GWAS variants

### Coverage Target: 30×

30× requires ~96 Gb total (3.2 Gb × 30). Flow cell options:

| Approach | Flow cells | Wash kits | Cost | Expected output |
|----------|-----------|-----------|------|----------------|
| Fresh only | 4 cells | 0 | ~$3,400 | ~100 Gb → ~31× |
| **Wash strategy** | **2 cells** | **2 kits** | **~$2,200** | **~100–120 Gb → ~31–37×** |
| MinION Mk1D Pack | 5 included | 0 | included in $5,150 | ~125 Gb → ~39× avg |

**Recommended approach:** Buy the Pack (5 flow cells included) and use the wash kit to extend life. At average output you'll clear 30× with cells to spare.

---

## Summary: Actual Cost Levers

| Lever | Potential Savings | Confidence |
|-------|-----------------|------------|
| Used MinION Mk1B | $1,500–2,500 on device | Medium (eBay availability varies) |
| MinION Mk1D Pack vs device+consumables separately | ~$2,750 | High (confirmed pricing) |
| Flow cell wash kit (3× reuse) | ~$1,000–1,700 per genome | High (officially supported) |
| Target 15× instead of 30× | 1–2 fewer flow cells | High (science supports it) |
| Used lab equipment (centrifuge, pipettes, Qubit) | ~$1,000 vs retail | High (widely available used) |
| DIY sequencer | $0 savings | Not possible |
| Third-party flow cells | $0 savings | None available |

---

## Devices to Watch

| Device | Timeline | Why It Matters |
|--------|----------|---------------|
| SmidgION | Unknown (was "coming soon" in 2024) | If ~$500–700, changes home WGS economics entirely |
| AxBio sequencer | 2026–2027 at earliest | Startup targeting low-cost nanopore; no specs yet |
