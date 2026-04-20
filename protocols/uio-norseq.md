# Protocol: UiO NorSeq PromethION Path

**Decision status:** INVESTIGATING — preferred approach pending quote and access confirmation

**Why this path:**
- PromethION gives long reads (10–100 kb+) with methylation calling — better than consumer Illumina services
- GDPR-protected; University of Oslo is a Norwegian public institution
- Data deleted after 2 months from delivery
- "All users pay the same price" — no academic-only restriction stated
- You extract DNA at home; they do library prep + sequencing; you download FASTQ

**What you still do yourself:**
- Buccal/blood collection
- HMW DNA extraction (NEB Monarch T3050)
- DNA quantification (Qubit)
- Ship extract to Oslo
- Bioinformatics analysis at home

**What you skip entirely:**
- Sequencer purchase (~$3,150–5,150)
- Flow cells (~$850 each)
- Library prep reagents (~$500)
- Thermocycler

---

## Phase 0: Contact NorSeq First

Before buying anything, get confirmation and a quote.

**Email:** post@sequencing.uio.no (UiO node) or Genomics-Core@ous-research.no (OUS/Ullevål node — handles human samples)

**Send this enquiry:**
```
Subject: Quote request — PromethION human WGS, external user

Hi,

I'm an external user (private individual, not university-affiliated) interested in 
whole genome sequencing of a human DNA sample via your PromethION service.

Could you please confirm:
1. Whether external/private individuals can use your ONT service
2. A quote for one PromethION run targeting 30× human WGS (~96 Gb)
   - Library prep included (Ligation kit SQK-LSK114 preferred)
   - I will provide pre-extracted gDNA (~5–10 µg, target >30 kb fragments)
3. Your policy if a submitted sample fails fragment size QC (do I pay, can I resubmit?)
4. Preferred shipping method and address for the OUS Ullevål node

Thank you
```

**Note:** ONT work is invoiced by OUS (Oslo University Hospital), not UiO directly.
Billing entity: Oslo Universitetssykehus, Org. NO993467049MVA

- [ ] Email sent
- [ ] Quote received: _______ NOK / EUR
- [ ] Access confirmed: ☐ Yes ☐ No
- [ ] QC failure policy confirmed
- [ ] Submission address confirmed

---

## Phase 1: Equipment and Reagents

Equipment needed for the UiO path only (no sequencer, no flow cells, no thermocycler):

| Item | Cost | Source | Notes |
|------|------|--------|-------|
| Microcentrifuge (used, ≥12,000 × g) | ~$150 | eBay | Eppendorf 5415D or 5424 |
| Micropipette set (P2, P20, P200, P1000) | ~$150 | eBay | Used Gilson Pipetman |
| Qubit 4 fluorometer (used) | ~$200 | eBay / BioSurplus | For quantification before shipping |
| Qubit dsDNA BR Assay Kit | ~$100 | Thermo Fisher | |
| **NEB Monarch HMW DNA Extraction Kit (T3050)** | ~$150 | NEB (T3050L for multi-use) | For cells and blood; do NOT use Zymo for HMW |
| 1.5 mL Eppendorf Safelock tubes | ~$20 | Amazon | NorSeq requires Safelock tubes |
| Pipette tips (filtered, all sizes) | ~$80 | Amazon | |

**Total equipment: ~$850 one-time**
**NorSeq sequencing: €800–2,000 estimated** (no public price list; get a quote)
**Shipping: ~€50–80** (DHL Express cold, within Norway)

---

## Phase 2: DNA Collection

### Option A: Buccal Swab (simpler, lower yield)

Follow Protocol 01 (buccal saline mouthwash collection) but **collect more cells** than standard:
- Use 10 mL saline (1g non-iodized salt in 10 mL water)
- Vigorous swishing for **3 full minutes** (vs. the standard 60 sec)
- Spit into 50 mL Falcon tube
- Centrifuge **800 × g, 10 min** to pellet
- Remove supernatant; resuspend pellet in **200 µL PBS**
- Process immediately or store at −80°C

**Expected yield with Monarch T3050:** ~5–20 µg, fragments ~30–70 kb
**Risk:** Buccal samples contain apoptotic DNA and dead cell debris → possible smearing on QC gel. Fragments are less consistently >30 kb than blood.

### Option B: Whole Blood (better quality, recommended)

Blood gives more DNA, longer fragments, and more consistent HMW yield.

**Self-collection options:**
- Finger prick with a lancet (used for diabetic blood glucose monitoring): ~$5 for lancets, yields ~50–200 µL whole blood
- Dried blood spot cards: collect drops onto FTA or Whatman card, let dry, mail without cold chain — contact NorSeq to confirm they accept DBS cards

**For fresh blood collection:**
- Collect 100–200 µL whole blood via finger prick into a clean 1.5 mL tube with 5 µL of 0.5M EDTA (to prevent clotting)
- Process immediately or store at 4°C for up to 24 hours

**Expected yield:** 30–100+ µg, fragments typically 50–150 kb — easily clears the >30 kb threshold.

---

## Phase 3: HMW DNA Extraction (NEB Monarch T3050)

**Time:** ~1–1.5 hours  
**Centrifuge requirement:** 12,000–16,000 × g for final steps  
**Do NOT vortex or pipette aggressively** — shearing is the enemy of HMW DNA  
**Use wide-bore pipette tips or cut standard tips** to reduce shearing

### For Blood (recommended)

- [ ] Prepare fresh lysis solution per kit instructions (do not pre-mix in advance)
- [ ] Add blood to lysis buffer — **gently invert** to mix (do NOT vortex)
- [ ] Incubate at 56°C for 30 min (water bath or heat block — NOT thermocycler cycling)
- [ ] RNase A treatment: add 5 µL, incubate 5 min at room temperature
- [ ] Allow to cool to room temperature
- [ ] Add precipitation solution, mix by **gentle inversion** (20–30 slow inversions)
- [ ] Centrifuge 5,000 × g, 5 min — carefully remove supernatant with wide-bore tip
- [ ] Wash precipitate with 70% ethanol, **gentle inversion**
- [ ] Centrifuge 5,000 × g, 5 min — carefully remove ethanol
- [ ] Air-dry 10 min (do not over-dry)
- [ ] Elute in **200 µL TE buffer** or **10 mM Tris pH 8.0**
  - Add buffer, incubate at 37°C for 30–60 min with occasional **gentle inversion**
  - Do not pipette to mix — let it dissolve by diffusion + gentle rocking
- [ ] Transfer to clean 1.5 mL Safelock tube — **cut your pipette tip** to reduce shearing

### For Buccal Cells

Follow same protocol but substitute the blood input with your buccal cell pellet resuspended in 200 µL PBS. Note that buccal cell DNA integrity is inherently more variable.

### Critical HMW handling rules

| ❌ Never | ✅ Always |
|---------|---------|
| Vortex DNA | Invert gently |
| Pipette vigorously | Wide-bore or cut tips |
| Use standard filter tips | Cut tip opening wider |
| Run through a column | This is a precipitation-based method |
| Store in water | Use TE buffer or 10 mM Tris pH 8 |

---

## Phase 4: Quantification

- [ ] Run **Qubit dsDNA BR Assay** on 2 µL of extracted DNA
- [ ] Record concentration: ________ ng/µL
- [ ] Total volume: ________ µL
- [ ] Total yield: ________ µg
- [ ] **Minimum for submission: 5 µg (ligation prep)**; 10+ µg preferred for robustness
- [ ] Check purity with NanoDrop if available (A260/280 should be ~1.8; A260/230 ~2.0–2.2)

If yield is below 5 µg from one extraction, **do a second extraction and pool** before shipping.

**Do NOT try to verify fragment size at home.** Standard gels cannot resolve >10 kb reliably. NorSeq will perform PFGE or Bioanalyzer QC on arrival. Just focus on hitting the minimum quantity.

---

## Phase 5: Shipping to OUS Ullevål

- [ ] Confirm shipping address with NorSeq (email above)
- [ ] Complete the ONT submission form: https://www.sequencing.uio.no/ONT%20Services/3.%20Oxford%20nanopore%20submission%20form/
- [ ] Label tube: your name + date + "human gDNA — HMW extraction (T3050)"

**Packaging:**
1. DNA in 1.5 mL Safelock Eppendorf tube, sealed with Parafilm around cap
2. Place in a 15 mL Falcon tube as secondary container with absorbent paper
3. Place in a small insulated box with a frozen gel pack (4°C target during transit)
4. Include printed copy of submission form

**Shipping:**
- Carrier: **DHL Express** or **PostNord** within Norway
- Temperature: **4°C** (standard gel pack; 24–48 hr stability)
- Cost: ~€50–80
- Label tube and outer box: "Extracted DNA — Keep cold — Do not freeze"
- Use tracked shipping; share tracking number with NorSeq

- [ ] Tube prepared and labelled
- [ ] Submission form completed and printed
- [ ] Shipped: date ________, tracking number ________

---

## Phase 6: Data Delivery and Analysis

**What you receive:** FASTQ files (POD5 on request). Long reads, nanopore format.  
**Timeline:** Typically a few weeks after QC passes. Data stored for **2 months** then deleted by NorSeq.

**When FASTQ arrives:**
1. Download immediately; verify file integrity (MD5 checksums if provided)
2. Back up to a second drive before running any analysis
3. Proceed with the standard bioinformatics pipeline: `bioinformatics/pipeline.md`
   - minimap2 for alignment (works with nanopore long reads)
   - LongShot for variant calling on Apple Silicon
   - bcftools for VCF filtering

**Key advantage over consumer Illumina services:** PromethION reads are 10–100 kb+. This means:
- Structural variant detection is dramatically better
- Repeat regions and tandem repeats are resolvable
- Phasing: you can determine which variants are on which chromosome copy
- Methylation data available in the BAM file (5mC, 5hmC) without extra steps

---

## Summary: UiO Path vs Full DIY

| | UiO NorSeq | Full DIY (MinION Pack) |
|-|-----------|----------------------|
| Sequencer cost | $0 | $5,150 |
| Flow cells | $0 | Included (5×) |
| Library prep | Included in service | Included in pack |
| HMW extraction kit | ~$150 | $54 (Zymo, standard) |
| Lab equipment | ~$700 | ~$1,000 |
| Sequencing service | ~€800–2,000 | $0 (you do it) |
| Shipping | ~€60 | $0 |
| **Total first genome** | **~$1,600–3,200** | **~$6,100** |
| **Subsequent genomes** | **~€900–2,100** (service + shipping) | **~$2,250** (flow cells + kit) |
| Read type | Long reads (PromethION, 10–100 kb) | Long reads (MinION, 10–50 kb) |
| Privacy | GDPR, data deleted 2 months | DNA never leaves |
| Ongoing capability | No | Yes |

**The UiO path is 2–4× cheaper on first genome and likely cheaper per additional genome too**, unless you're sequencing many family members over years (where DIY amortizes the device cost).
