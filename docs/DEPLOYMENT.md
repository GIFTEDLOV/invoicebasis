# Deployment and verification

## Contract

- Network: GenLayer Studionet, chain ID `61999`
- RPC: `https://studio.genlayer.com/api`
- Contract: [0x3C066b25aa1BaF2374F9b1540f99594C737caf8a](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a)
- Deployed-source SHA-256: `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`
- ABI schema SHA-256: `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`
- Source parity: exact `getContractCode` byte match with `contracts/invoicebasis.py`, verified using GenLayerJS 1.1.8.
- The existing verified V4 deployment is preserved. No replacement deployment was made.

## Live evidence

- Historic qualification case `GLV4-invoicebasis-39138804500` finalized `REVIEW_REQUIRED`; details and transaction hashes are in the checked-in evidence.
- Qualification Actions: [run 39138804500](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138804500).
- Latest exact-main qualification CI before release preparation: [run 39161811618](https://github.com/GIFTEDLOV/invoicebasis/actions/runs/39161811618).

This repository has no production app URL; it is intentionally a standalone contract submission.

## Verifier

`npm run verify:live` is read-only: it retrieves deployed bytes, checks the expected hash and ABI schema, checks receipt execution details, and reads canonical case state and history. It does not broadcast transactions. The signed browser lifecycle scripts perform writes only when explicitly guarded and never retry an uncertain broadcast.

## Reproduction

```powershell
python -m pip install -r requirements-dev.txt
python -m pytest -q
python -m genvm_linter.cli lint contracts/invoicebasis.py
npm ci
npm run verify:live
```
