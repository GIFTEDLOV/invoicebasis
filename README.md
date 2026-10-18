# InvoiceBasis

Determine invoice eligibility from frozen terms and evidence, then derive a bounded payable basis with deterministic integer arithmetic.

**Package:** v4.0.0-rc.1 · **Network:** Studionet `61999` · **Contract:** [`0x3C066b25aa1BaF2374F9b1540f99594C737caf8a`](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a)

## Description

InvoiceBasis creates a consent-bound invoice case with immutable eligibility terms, bounded gross minor units and a fixed rational rate. A distinct designated attestor wallet signs the evidence digest. GenLayer validators independently assess invoice class, exclusions and evidence sufficiency; the contract calculates the provisional payable basis using integer floor division and never transfers funds. Challenges and second-round deliberation precede finalization.

## Deployment provenance

- RPC: `https://studio.genlayer.com/api`
- Exact deployed-source SHA-256: `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`
- Independently recomputed ABI schema SHA-256: `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`
- `getContractCode` parity: exact match with `contracts/invoicebasis.py`.

## Existing live case

Case `GLV4-invoicebasis-39138804500` reached `FINALIZED`, round 2, with terminal verdict **REVIEW_REQUIRED**. Evidence is in `evidence/invoicebasis-live.json`; the recorded run is [39142055216](https://github.com/GIFTEDLOV/driftproof/actions/runs/39142055216) for NoticeClock and [39138804500](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138804500) for the other projects. Run 39138804500 as a whole failed because NoticeClock disagreed; the three case artifacts preserved here individually report `PASS`. Source evidence is synthetic and labeled.

## Release status

The existing deployed V4 contract is preserved and byte-verified. **This package is not submission-qualified as a complete release yet.** ParcelCourt and ShiftFair production URLs still serve older read-only bundles. Their updated source in `web/` is not deployed, and signing remains disabled (`RELEASE_QUALIFIED=false`) until a funded ephemeral-signer browser transaction passes actual GenVM receipt and canonical-state checks. No live positive verdict is claimed.

## Run checks

Requirements: Python 3.12+, Node.js 22+, npm.

```powershell
python -m pip install -r requirements-dev.txt
python -m pytest -q
python -m genvm_linter.cli lint contracts/invoicebasis.py
npm ci
npm run verify:live
```

For the two frontend repos: `cd web; npm ci; npm run check; npm test; npm run build; npm audit --audit-level=high`. Python tests use an explicit local API fixture; they are regression tests, not live consensus proof. The read-only verifier independently checks code bytes, ABI, receipt summaries, canonical state and history through GenLayerJS 1.1.8.

See [Security](docs/SECURITY.md), [Deployment](docs/DEPLOYMENT.md), [Rejection prevention](docs/REJECTION_PREVENTION.md), [Submission dossier](docs/SUBMISSION.md) and [Release status](docs/RELEASE.md). MIT license in `LICENSE`.
