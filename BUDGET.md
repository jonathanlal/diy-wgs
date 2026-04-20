# Budget Tracker

**Last updated:** 2026-04-20

> **Price correction:** MinION Mk1B is legacy. Current device is **MinION Mk1D at $3,150** (not ~$1,000 as previously estimated). All scenarios below reflect accurate pricing.

---

## Scenarios

### Scenario A — UiO NorSeq Path (~$1,600–3,200 first genome) 🔍 Currently Investigating
Extract DNA at home, ship to UiO's PromethION service, get long-read FASTQ back.
See `protocols/uio-norseq.md` for full protocol.

| Item | Cost | Notes |
|------|------|-------|
| Used microcentrifuge | ~$150 | Eppendorf 5415D, eBay |
| Used micropipette set | ~$150 | Gilson Pipetman, eBay |
| Qubit 4 (used) + assay kit | ~$300 | Quantification before shipping |
| **NEB Monarch HMW DNA Kit (T3050)** | ~$150 | HMW extraction; >30 kb required by NorSeq |
| Misc consumables | ~$100 | Tubes, tips, etc. |
| **NorSeq PromethION sequencing** | **€800–2,000** | Quote required; library prep included |
| Shipping to OUS Ullevål | ~€60 | DHL Express with cold pack |
| **Total (first genome)** | **~$1,600–3,200** | Pending quote; 2–4× cheaper than full DIY |
| **Subsequent genomes** | **~€900–2,100** | Just service fee + shipping |

**Action required before committing:** Email post@sequencing.uio.no to confirm access for private individuals and get a quote. See `protocols/uio-norseq.md` Phase 0.

**Advantage vs. full DIY:** ~$3,000–4,500 cheaper on first genome. PromethION gives better reads than MinION (up to 150 Gb/flow cell vs 15–35 Gb). GDPR-protected; data deleted after 2 months.

---

### Scenario B — Pack Route (~$6,100 first genome)
Buy the MinION Mk1D Pack — dramatically better value than device + separate consumables.

| Item | Cost | Notes |
|------|------|-------|
| MinION Mk1D Pack | $5,150 | Device + 5× R10.4.1 flow cells + Control Expansion + 2× Wash Kit + sequencing kit |
| Used microcentrifuge | ~$150 | Eppendorf 5415D or 5424 from eBay |
| 2× sous vide sticks (thermocycler) | ~$150 | Works for simple temp holds |
| Used micropipette set | ~$150 | Gilson Pipetman P2/P20/P200/P1000 |
| Qubit 4 fluorometer (used) | ~$200 | Critical — prevents wasted $850 flow cells |
| Qubit dsDNA BR assay kit | ~$100 | Consumables |
| Zymo Quick-DNA Miniprep Kit (10 preps) | ~$54 | First extraction |
| Misc consumables (tips, tubes) | ~$150 | |
| **Total (first genome)** | **~$6,104** | Includes 5 flow cells — enough for 30× coverage |
| **Total (subsequent genomes)** | **~$2,254** | 3× flow cells + ligation kit + extraction |

**Why the Pack beats device-only:** 5 flow cells + sequencing kit purchased separately would cost ~$4,750. The pack bundles them for $2,000 over device-only = you save ~$2,750.

---

### Scenario B — Device-Only Route (~$6,400 first genome)
Lower upfront if you only want 2 flow cells to start.

| Item | Cost | Notes |
|------|------|-------|
| MinION Mk1D device only | $3,150 | Device + standard support |
| 2× R10.4.1 flow cells | ~$1,700 | For ~10–20× coverage (maybe enough) |
| Ligation Kit (SQK-LSK114) | ~$500 | Better yield than Rapid |
| Used microcentrifuge | ~$150 | |
| 2× sous vide sticks | ~$150 | |
| Used micropipette set | ~$150 | |
| Qubit 4 fluorometer (used) | ~$200 | |
| Qubit dsDNA BR assay kit | ~$100 | |
| Zymo Quick-DNA Miniprep Kit | ~$54 | |
| Misc consumables | ~$150 | |
| **Total (first genome)** | **~$6,354** | Only 2 flow cells — may need more for 30× |
| **Total (subsequent genomes)** | **~$2,254** | |

**Warning for 30× target:** 2 flow cells gives ~30–70 Gb. You need ~96 Gb for 30×. Either add 2 more flow cells ($1,700) or use the Flow Cell Wash Kit to get 3 runs per cell. The Pack route avoids this problem entirely.

---

### Scenario C — Used MinION Mk1B (~$4,000–5,000 if lucky)
If you find a clean used Mk1B unit, this route approaches the original $4k estimate.

| Item | Cost | Notes |
|------|------|-------|
| Used MinION Mk1B (eBay/reseller) | **$500–1,500** | Legacy but functional; check eBay, BioSurplus, Labx |
| 2–3× R10.4.1 flow cells | ~$1,700–2,550 | R10.4.1 works with Mk1B |
| Ligation Kit (SQK-LSK114) | ~$500 | |
| Used centrifuge | ~$150 | |
| Sous vide × 2 | ~$150 | |
| Used pipettes | ~$150 | |
| Qubit (used) | ~$200 | |
| Extraction + misc | ~$304 | |
| **Total (best case — cheap Mk1B)** | **~$4,454** | Requires finding $500 used unit |
| **Total (typical used Mk1B at $1,000)** | **~$4,954** | More realistic |

**Risk:** Used sequencer availability and condition vary. Verify the unit functions before buying.

---

### Scenario D — Mail-in (no privacy)
| Service | Cost | Coverage | Notes |
|---------|------|----------|-------|
| Nebula Genomics | ~$299 | 30× WGS | DNA leaves house |
| Dante Labs | ~$199 | 30× WGS | DNA leaves house |
| 23andMe | ~$99 | ~600K SNPs only | Not full WGS |

---

## Actual Spending Tracker
_Update this as items are ordered/received._

| Date | Item | Vendor | Cost | Status |
|------|------|--------|------|--------|
| — | — | — | — | — |

---

## Notes
- Flow cells are the biggest per-genome variable cost ($850 each)
- **Flow Cell Wash Kit (EXP-WSH004, ~$250):** enables 3–4 runs per flow cell — the single best cost lever on consumables. Officially supported by ONT. Cuts effective flow cell cost from $850/run to ~$280/run.
- Better library prep yield = fewer flow cells needed = second biggest lever
- Ligation kit (SQK-LSK114) vs Rapid kit is the single most important yield decision
- Qubit prevents the most common cause of wasted flow cells (bad DNA quantification)
- **Coverage target: 30×** — requires ~96 Gb total (3.2 Gb human genome × 30). At average MinION output (~25 Gb/flow cell): need 4 fresh flow cells, or 2 flow cells + 2 wash cycles (recommended).
- Pack route (5 flow cells) covers 30× comfortably — 5 × 25 Gb avg = 125 Gb = ~39× at average output
- Subsequent genome costs drop significantly once equipment is purchased
- Flow cells degrade over time — don't stockpile far ahead of use
- The Pack ($5,150) includes sequencing kit — no need to buy SQK-LSK114 separately

## DIY Sequencer?
**Not possible.** The MinION contains:
1. Proprietary nanopore protein (engineered CsgG) — not purchasable, patented
2. Custom ASIC chip — reads picoamp current changes; impossible to source or fab outside a semiconductor fab
3. Proprietary enzyme motor — controls DNA threading speed

Solid-state nanopores (academic DIY approach) require electron beam lithography equipment ($500k+) and are not WGS-ready. This is a ~5–10 year horizon for hobbyists.

**Alternatives researched and eliminated:**
- SmidgION (ONT smartphone sequencer): Still vaporware; no commercial release date
- AxBio: Startup, no product available
- MGI DNBSEQ-E25: No consumer pricing; institutional
- Everything else: $20,000+
