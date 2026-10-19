# InvoiceBasis

Determine invoice eligibility from frozen terms and evidence, then derive a bounded payable basis with deterministic integer arithmetic.

**Release:** v4.0.0 ? **Network:** GenLayer Studionet (chain `61999`) ? **Contract:** [`0x3C066b25aa1BaF2374F9b1540f99594C737caf8a`](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a)

## What it does

InvoiceBasis creates a consent-bound invoice case with immutable eligibility terms, bounded gross minor units and a fixed rational rate. A distinct designated attestor wallet signs the evidence digest. GenLayer validators independently assess invoice class, exclusions and evidence sufficiency; the contract calculates the provisional payable basis using integer floor division and never transfers funds. Challenges and second-round deliberation precede finalization.

## Why GenLayer

Validators independently interpret an invoice category, exclusions and evidence sufficiency against frozen natural-language terms. Deterministic contract code then bounds and calculates the result. A conventional deterministic workflow cannot perform the semantic part credibly.

Leader and validators independently classify the exact eligibility vector inside gl.vm.run_nondet_unsafe. The strict boolean vector is validated; disagreement aborts adjudication. Contract code derives ELIGIBLE, INELIGIBLE or REVIEW_REQUIRED and computes the provisional payable amount using bounded integers and deterministic floor division.

## Deployment provenance

- Canonical RPC: `https://studio.genlayer.com/api`
- Exact deployed source SHA-256: `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`
- ABI schema SHA-256: `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`
- `getContractCode` source-byte parity: exact match with `contracts/invoicebasis.py`.
- Explorer: https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a

## Live qualification

- Historic case: `GLV4-invoicebasis-39138804500`, terminal `REVIEW_REQUIRED`; source data is synthetic and explicitly labeled.
- Historic qualification: [GitHub Actions run 39138804500](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138804500).
- Project exact-head CI: [run 39175260479](https://github.com/GIFTEDLOV/invoicebasis/actions/runs/39175260479).
- This is a standalone contract; no frontend app is claimed.

## Release and submission status

The v4.0.0 package source and submission materials are prepared in this independent repository. GitHub release publication follows exact-head CI. Submission fields and review instructions are in [docs/SUBMISSION.md](docs/SUBMISSION.md) and [docs/SUBMISSION_FIELDS.json](docs/SUBMISSION_FIELDS.json). The Portal entry is **prepared, not submitted**; a final Portal submission is an authenticated action.

## Checks

Requirements: Python 3.12+, Node.js 22+, npm.

```powershell
python -m pip install -r requirements-dev.txt
python -m pytest -q
python -m genvm_linter.cli lint contracts/invoicebasis.py
npm ci
npm run verify:live
```

Python tests and live verifier run in this repository. Unit and mocked integration tests are not a substitute for the live consensus evidence linked above.

See [security audit](docs/SECURITY.md), [deployment](docs/DEPLOYMENT.md), [rejection-prevention matrix](docs/REJECTION_PREVENTION.md), and [release qualification](docs/RELEASE.md). MIT License.
