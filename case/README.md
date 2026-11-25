# C09 · Keyhole porosity and in-situ defect detection in LPBF — W35–W38

> **Real industrial case dossier.** Copied from the authoritative case card in
> `CASES.md` §4 so this repository stays self-contained after it is pushed to
> GitHub. Planning links: [`CASES.md`](https://github.com/ahmadishamulayadyakmal/metallurgy-project/blob/main/CASES.md) ·
> [`JOURNALS.md`](https://github.com/ahmadishamulayadyakmal/metallurgy-project/blob/main/JOURNALS.md) ·
> [`WEEKLY_PLAN.md`](https://github.com/ahmadishamulayadyakmal/metallurgy-project/blob/main/WEEKLY_PLAN.md).
> **Evidence level: A** · No plant data is held in this repository.

**Repository:** `e09-lpbf-melt-pool-am-bench` · **Evidence: A** ·
**References:** R27, R28, R29, R30, Y2R09, Y2R10, Y2R15, D06.

**Industrial problem.** In laser powder bed fusion of IN718, excessive energy
density creates a vapour depression (keyhole) and pores; post-build CT finds
defects only after the part is scrapped (R27, R28, Y2R09, Y2R10).

**Why it happens.** Keyhole instability, spatter, denudation and absorption
variation; the physics is multi-scale and expensive to simulate inline.

**Data (open, no plant data).** NIST AM-Bench 2022 Challenge 3 single-track IN718
measurements (R30 / Y2R15 / D06), seven power/speed/spot conditions, public with
uncertainty annotations. AM-Bench IN625 / Ti-6Al-4V data for the classifier
(Y2R10).

**Tool chain.** Fortran FVM heat flow → simplified laser absorption →
Rosenthal analytical verification (R29) → calibration on single tracks →
held-out condition validation → GCI and error bars → PINN surrogate → CNN-LSTM
defect classifier → conformal calibration → per-class error analysis.

**What each reference validates.**
- R27, R28 — melt-flow / keyhole physics and conduction→keyhole transition.
- R29 — analytical weld-pool solution used for **verification**.
- R30, Y2R15, D06 — AM-Bench ground truth and measurement IDs.
- Y2R09 — high-fidelity model deviations, quoted as external literature.
- Y2R10 — digital-twin classifier results, quoted as external literature.

**Deliverables.** `cases/ambench_keyhole/`, `cases/am_defect_twin/`;
seven-condition comparison table; calibrated heat-source parameters; per-class
F1 table; confusion matrix; ablation against a physics-free baseline.

**Validation.** ≥ 1 condition held out from calibration; per-condition errors
(not only the mean); GCI; class imbalance handled; latency measured on our own
hardware or not claimed.

**Acceptance.** At least one physics feature shown to change classifier
performance; all AM-Bench measurement IDs and checksums recorded.

## Claim boundary

See [`evidence.md`](evidence.md) for the evidence level and the exact wording
that must be used when quoting literature numbers. All datasets and references
are listed in [`sources.md`](sources.md); the four-week execution plan is in
[`week_plan.md`](week_plan.md).
