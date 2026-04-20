# DIY Whole Genome Sequencing

**Sequence your own genome at home. ~$4,000 all-in. Your DNA never leaves the house.**

A complete guide to DIY whole genome sequencing using Oxford Nanopore technology — from buccal swab to a Claude-built health dashboard. Optimized version of the [Vibe Genomics](https://vibe-genomics.replit.app/) approach, cutting costs by ~60%.

---

## Cost vs. the Original Approach

| Approach | First Genome | Notes |
|----------|-------------|-------|
| **This guide (optimized)** | **~$4,000** | Device only + ligation kit + used equipment |
| Vibe Genomics author | ~$10,000 | Bundle + Bento Lab Pro + no DNA quantification |
| Nebula/Dante (mail-in) | ~$200–300 | DNA leaves house, no privacy |

Key changes from the original:
- Buy **MinION device only** (~$1k) instead of the $5,200 bundle
- Use **Ligation kit (SQK-LSK114)** — 2–3× better yield than Rapid kit (fewer flow cells needed)
- Skip **Bento Lab Pro** — cheap used centrifuge + sous vide sticks work fine
- Add a **Qubit fluorometer** (used, ~$200) — prevents wasting $850 flow cells on bad loads
- Use **LongShot** for variant calling on Apple Silicon — free, CPU-only, no GPU needed

---

## The Process

| Phase | What happens | Time |
|-------|-------------|------|
| 1 — DNA Collection | Saline mouthwash → centrifuge cell pellet | ~15 min |
| 2 — DNA Extraction | Zymo kit → purified genomic DNA | ~1.5 hr |
| 3 — Library Prep | Ligate adapters → load flow cell | ~1 hr |
| 4 — Sequencing | MinION runs hands-off | 72 hr |
| 5 — Bioinformatics | minimap2 → LongShot → VCF → Claude dashboard | ~2–4 hr compute |

---

## Repo Structure

```
├── index.html                  ← Project website
├── style.css
├── PROGRESS.md                 ← Phase tracker with checklists
├── BUDGET.md                   ← Cost scenarios and spending tracker
│
├── equipment/
│   ├── 01-sequencer.md         ← MinION: why device-only beats the bundle
│   ├── 02-centrifuge.md        ← Used Eppendorf vs DIY (don't DIY this one)
│   ├── 03-thermocycler.md      ← Sous vide vs Arduino PID vs used unit
│   ├── 04-pipettes.md          ← Used Gilson Pipetman set
│   ├── 05-quantification.md    ← Qubit: why it's critical
│   └── 06-shopping-list.md     ← Master buy list with status tracking
│
├── protocols/
│   ├── 01-dna-collection.md    ← Buccal cell collection checklist
│   ├── 02-dna-extraction.md    ← Zymo miniprep step-by-step
│   ├── 03-library-prep.md      ← Ligation kit + SPRI cleanup + flow cell loading
│   ├── 04-sequencing.md        ← MinKNOW setup + run monitoring log
│   └── 05-bioinformatics.md    ← minimap2 → LongShot → VCF pipeline
│
├── reagents/
│   └── master-list.md          ← All reagents with storage temps and catalog numbers
│
├── bioinformatics/
│   ├── pipeline.md             ← Full copy-paste pipeline commands
│   ├── tools.md                ← Tool installation (macOS/Apple Silicon)
│   └── dashboard.md            ← Building the health dashboard with Claude
│
└── research/
    ├── build-vs-buy.md         ← Consolidated build vs buy analysis
    └── diy-extraction.md       ← CTAB protocol vs Zymo kit
```

---

## Open Decisions

- [ ] **Thermocycler:** sous vide sticks ($100–200) vs Arduino PID DIY (~$75)
- [ ] **DNA quantification:** buy used Qubit vs skip (strongly recommend Qubit)
- [ ] **Extraction:** Zymo for first run → evaluate DIY CTAB protocol after

---

## Disclaimer

For research and educational purposes only. Not medical advice. Genomic data is highly personal — keep your VCF file local and be thoughtful about where you share or upload it.

---

Inspired by [Vibe Genomics](https://vibe-genomics.replit.app/).
