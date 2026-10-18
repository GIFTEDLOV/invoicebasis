# Release qualification — InvoiceBasis `v4.0.0-rc.1`

- Source SHA-256: `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`; deployed address: `0x3C066b25aa1BaF2374F9b1540f99594C737caf8a`; ABI SHA-256: `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`.
- Lifecycle case `GLV4-invoicebasis-39138804500` is `FINALIZED` with verdict `REVIEW_REQUIRED`; all three transactions are recorded in `evidence/invoicebasis-live.json`. Its source reference is synthetic and labeled.
- Run 39138804500 overall failed at NoticeClock majority disagreement; the three artifacts for other projects individually recorded PASS. NoticeClock’s later run 39142055216 passed its lifecycle and ended INCONCLUSIVE.
- Original deployment run 39138161003 concluded failure in live qualification after deployment and byte verification passed.

This standalone contract has no browser signing acceptance criterion.

**Status:** source and contract provenance are verified; this release candidate is not yet fully submission-ready. Do not enable `RELEASE_QUALIFIED` or submit a full-application readiness claim until the app acceptance criteria pass.
