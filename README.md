# Keyhole porosity and in-situ defect detection in LPBF (C09)

## Industrial problem

In laser powder bed fusion of IN718, excessive energy density creates a vapour depression (keyhole) and pores; post-build CT finds defects only after the part is scrapped.

**Why it happens.** Keyhole instability, spatter, denudation and absorption variation; the physics is multi-scale and expensive to simulate inline.

## Data (no plant data)

Open data only: NIST AM-Bench 2022 Challenge 3 single-track IN718 measurements (R30/Y2R15/D06), seven power/speed/spot conditions, public with uncertainty annotations; AM-Bench IN625/Ti-6Al-4V data for the classifier.

> Only open datasets and published literature are used. No plant or proprietary data are held here; plant numbers quoted from papers are external literature, not independently reproduced results.

## Tool chain

Fortran FVM heat flow, simplified laser absorption, Rosenthal analytical verification, calibration, GCI, PINN surrogate, PyTorch CNN-LSTM classifier, conformal calibration, per-class error analysis.

## Journal references

- **R27** — melt-flow / pore / spatter physics.
- **R28** — conduction -> keyhole transition.
- **R29** — analytical weld-pool solution used for VERIFICATION (compound: 2 papers).
- **R30** ([source](https://www.nist.gov/ambench)) — NIST AM-Bench ground truth and measurement IDs.
- **Y2R09** ([DOI](https://doi.org/10.1007/s40964-024-00702-0)) — high-fidelity model deviations, quoted as external literature.
- **Y2R10** ([DOI](https://doi.org/10.1038/s41598-026-58348-7)) — digital-twin classifier results, quoted as external literature.
- **Y2R15** ([source](https://www.nist.gov/ambench)) — AM-Bench data and challenge definition.
- **D06** ([source](https://www.nist.gov/ambench)) — AM-Bench 2022 Challenge 3 IN718 measurement IDs and checksums.

## Deliverables

`cases/ambench_keyhole/`, `cases/am_defect_twin/`; seven-condition comparison table; calibrated heat-source parameters; per-class F1 table; confusion matrix; ablation against a physics-free baseline.

## Validation & claims

>= 1 condition held out from calibration; per-condition errors (not only the mean); GCI; class imbalance handled; >= 1 physics feature shown to change classifier performance; all AM-Bench IDs and checksums recorded.

## Limitations

Simplified absorption, no powder-scale stochasticity. Latency measured on our own hardware or not claimed. No plant sensor stream.

## Repository layout

- `README.md` — case summary, data policy, method, results and limitations.
- `CONTRIBUTING.md` — how to propose changes.
- `docs/index.md` — documentation map.
- `docs/model_card.md` and `docs/vv_template.md` — reporting templates.
- `.github/workflows/ci.yml` — automated checks.

Only open data and published literature are used. No plant or proprietary data
are included. All artefacts are written in English.
