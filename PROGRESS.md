# Project Progress Tracker

**Last updated:** 2026-04-20
**Current phase:** Phase 1 — Research & Planning

---

## Phase 1: Research & Planning
- [x] Read Vibe Genomics article and understand the full process
- [x] Identify key equipment and consumables
- [x] Identify cost inefficiencies in author's approach
- [x] Create project folder and planning structure
- [ ] Finalize buy-vs-build decisions for each equipment item
- [ ] Finalize library prep kit choice (Ligation vs Rapid)
- [ ] Finalize DNA quantification approach
- [ ] Finalize extraction method (Zymo vs DIY CTAB)
- [ ] Lock in budget scenario
- [ ] Set up purchasing plan (what to order first)

## Phase 2: Equipment Procurement
- [ ] Order sequencer (MinION Mk1B device)
- [ ] Order/build centrifuge
- [ ] Order/build thermocycler (or set up sous vide)
- [ ] Order pipette set
- [ ] Order/source DNA quantification device
- [ ] Verify all equipment arrived and functional
- [ ] Run ONT MinKNOW software, connect MinION, check firmware
- [ ] Run flow cell check (800+ pores = good)

## Phase 3: Reagents & Consumables
- [ ] Order ONT library prep kit (Ligation SQK-LSK114)
- [ ] Order flow cells (R10.4.1) — minimum 2, aim for 3
- [ ] Order Zymo Quick-DNA Miniprep Plus Kit (or CTAB reagents)
- [ ] Order Proteinase K (if not included in Zymo kit)
- [ ] Order micropipette tips (three sizes — burn through fast)
- [ ] Order 1.5mL microcentrifuge tubes (×100 minimum)
- [ ] Order 0.2mL PCR tubes (×100 minimum)
- [ ] Order BSA (50 mg/mL) for flow cell priming
- [ ] Verify all reagents stored correctly (flow cells 2–8°C, library kit frozen)

## Phase 4: Lab Setup
- [ ] Designate clean work area
- [ ] Install MinKNOW software on sequencing computer
- [ ] Create ONT account
- [ ] Set up tube grid system (reference protocol 01/02)
- [ ] Install bioinformatics tools (see `bioinformatics/tools.md`)
- [ ] Test run a Bento bioengineering practice kit (optional but recommended)
- [ ] Prepare and label all tubes before Day 1

## Phase 5: DNA Collection & Extraction (Day 1)
- [ ] Do not eat/drink (except water) for 30 min before
- [ ] Reconstitute Proteinase K (one-time setup)
- [ ] Prepare saline mouthwash
- [ ] Collect buccal cells (mouthwash, centrifuge)
- [ ] Wash cell pellet
- [ ] Lyse cells (BioFluid Buffer + Proteinase K, 55°C × 10 min)
- [ ] Bind DNA to Zymo column
- [ ] Wash column (3×)
- [ ] Elute DNA (50 µL)
- [ ] Quantify DNA (Qubit or NanoDrop)
- [ ] Aliquot DNA into 4–6 × 10 µL tubes
- [ ] Store at −20°C (long term) or 4°C (within 1 week)

## Phase 6: Library Prep & Sequencing (Day 2)
- [ ] Thaw one DNA aliquot on ice
- [ ] Run flow cell check in MinKNOW
- [ ] Prepare library (tagmentation or ligation per chosen kit protocol)
- [ ] Prime flow cell with FCF + BSA + FCT
- [ ] Load library onto flow cell (SpotON port, dropwise)
- [ ] Start 72-hour sequencing run in MinKNOW
- [ ] Monitor pore count and output at 1h, 6h, 24h checkpoints
- [ ] (Optional) Run second flow cell if yield low at 48h mark

## Phase 7: Bioinformatics & Dashboard
- [ ] Confirm all FAST5/POD5 files are present post-run
- [ ] Basecall reads (HAC model in MinKNOW, or Guppy/Dorado post-run)
- [ ] Align reads to reference genome (minimap2, GRCh38)
- [ ] Sort and index BAM (samtools)
- [ ] Add read groups (samtools addreplacerg)
- [ ] Call variants (LongShot on Mac, or DeepVariant on GPU)
- [ ] Filter VCF to PASS variants
- [ ] (Optional) Liftover 23andMe data GRCh37→GRCh38 for comparison
- [ ] Build health/traits dashboard with Claude
- [ ] Review dashboard results

---

## Issues / Blockers Log
_Record problems encountered here so future agents have context._

| Date | Issue | Resolution |
|------|-------|------------|
| — | — | — |
