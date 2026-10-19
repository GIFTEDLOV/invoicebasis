# Release qualification ? InvoiceBasis v4.0.0

**Release dossier date:** 2026-10-19
**Release state:** Source, contract, and existing live qualification evidence are preserved. Portal dossier is prepared; final Portal submission is not made.

- Contract address: [0x3C066b25aa1BaF2374F9b1540f99594C737caf8a](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a).
- Deployed V4 source SHA-256: `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`; ABI schema SHA-256: `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`.
- Historic case `GLV4-invoicebasis-39138804500`: `FINALIZED / REVIEW_REQUIRED`; its source inputs are synthetic and labeled.
- Qualification workflow: [39138804500](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138804500).
- Exact-main CI on the release preparation baseline: [39175260479](https://github.com/GIFTEDLOV/invoicebasis/actions/runs/39175260479) passed.
- This is a standalone contract release; no production app is claimed.

The original V4 contract deployment is preserved. No contract redeployment or source-hash substitution occurred. The release-verification artifact distinguishes successful transaction finality from successful GenVM execution and canonical state.

**Submission:** prepared in [docs/SUBMISSION.md](SUBMISSION.md) and [docs/SUBMISSION_FIELDS.json](SUBMISSION_FIELDS.json); **not submitted to the Builder Portal**. No steward acceptance is claimed.

See [deployment evidence](DEPLOYMENT.md), [security review](SECURITY.md), [rejection-prevention matrix](REJECTION_PREVENTION.md), and [reviewer instructions](SUBMISSION.md).
