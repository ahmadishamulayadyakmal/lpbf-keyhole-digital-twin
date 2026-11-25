# Keyhole porosity and in-situ defect detection in LPBF (C09)

> Workspace folder: `e09-lpbf-melt-pool-am-bench` · Suggested GitHub repository: `metallurgy-lpbf-am-bench`
> Epic: E09 · Weeks: W35–W38 · Evidence level: **A**
> Master specification: [`CASES.md`](https://github.com/ahmadishamulayadyakmal/metallurgy-project/blob/main/CASES.md) §4 · Download the papers: [`JOURNALS.md`](https://github.com/ahmadishamulayadyakmal/metallurgy-project/blob/main/JOURNALS.md)

## Industrial problem

In laser powder bed fusion of IN718, excessive energy density creates a vapour depression (keyhole) and pores; post-build CT finds defects only after the part is scrapped.

**Why it happens.** Keyhole instability, spatter, denudation and absorption variation; the physics is multi-scale and expensive to simulate inline.

## Data (no plant data)

Open data only: NIST AM-Bench 2022 Challenge 3 single-track IN718 measurements (R30/Y2R15/D06), seven power/speed/spot conditions, public with uncertainty annotations; AM-Bench IN625/Ti-6Al-4V data for the classifier. Evidence level A.

> The author cannot supply factory data. This project uses **only open datasets and
> credible peer-reviewed journals**. If this is a B-level case, the case report
> must contain the exact disclaimer from `CASES.md` §1 and must **never** claim
> plant validation.

## Tool chain

Fortran FVM heat flow, simplified laser absorption, Rosenthal analytical verification, calibration, GCI, PINN surrogate, PyTorch CNN-LSTM classifier, conformal calibration, per-class error analysis.

## Journal references

- **R27** — melt-flow / pore / spatter physics.
- **R28** — conduction -> keyhole transition.
- **R29** — analytical weld-pool solution used for VERIFICATION (compound: 2 papers).
- **R30** — NIST AM-Bench ground truth and measurement IDs.
- **Y2R09** — high-fidelity model deviations, quoted as external literature.
- **Y2R10** — digital-twin classifier results, quoted as external literature.
- **Y2R15** — AM-Bench data and challenge definition.
- **D06** — AM-Bench 2022 Challenge 3 IN718 measurement IDs and checksums.

Each reference above is listed with its DOI or stable URL, access status and
manual download route in [`JOURNALS.md`](https://github.com/ahmadishamulayadyakmal/metallurgy-project/blob/main/JOURNALS.md) §4, and in the shared
BibTeX library `papers/references.bib`. Do not cite a paper you have not been
able to obtain; if it is inaccessible, record that in `JOURNALS.md` §8.

## Deliverables

`cases/ambench_keyhole/`, `cases/am_defect_twin/`; seven-condition comparison table; calibrated heat-source parameters; per-class F1 table; confusion matrix; ablation against a physics-free baseline.

## Validation & claims

>= 1 condition held out from calibration; per-condition errors (not only the mean); GCI; class imbalance handled; >= 1 physics feature shown to change classifier performance; all AM-Bench IDs and checksums recorded.

## Limitations

Simplified absorption, no powder-scale stochasticity. Latency measured on our own hardware or not claimed. No plant sensor stream.

## Definition of Done

1 merged PR · green tests · 1 new artefact · 1 README paragraph · 1 sprint note
`docs/sprints/wNN.md` · tag `wNN`. Before the case tag `c09` is created,
this README must contain all six sections: Industrial problem, Data (no plant
data), Tool chain, Journal references, Validation & claims, Limitations.

## Repository skeleton

Shared files: `CONTRIBUTING.md` (sprint contract), `.github/` (issue, PR and
CI templates), `docs/sprints/wNN.md`, `docs/vv_template.md` and
`docs/model_card.md`. `CASES.md`, `JOURNALS.md` and `REPOSITORIES.md` are in a
separate planning repository; their links above remain valid after this folder
is pushed as its own repository.

The real industrial case dossier is in `case/`: `README.md` (full case card),
`evidence.md`, `sources.md` and `week_plan.md`.

## Push this folder to GitHub

This folder is prepared but is **not** a Git repository yet:

```bash
cd e09-lpbf-melt-pool-am-bench
git init
git branch -M main
git remote add origin https://github.com/<your-user>/metallurgy-lpbf-am-bench.git
git add .
git commit -m "Initial import: C09 · W35–W38"
git push -u origin main
```

Use weekly tags `wNN` and one case tag `c09` inside this repository.
Never commit API keys, raw downloaded datasets or publisher PDFs.

## Language

All artefacts in this repository are written in **English**.
