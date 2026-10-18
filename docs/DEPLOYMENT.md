# Deployment and source provenance

Existing deployment: [0x3C066b25aa1BaF2374F9b1540f99594C737caf8a](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a), GenLayer Studionet chain 61999, RPC `https://studio.genlayer.com/api`. GenLayerJS 1.1.8 `getContractCode` bytes match `contracts/invoicebasis.py` at SHA-256 `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`; the deployed ABI equals the schema generated from that file at SHA-256 `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`. No contract replacement was required.

The original workflow [39138161003](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138161003) failed in its later live qualification step after deployment and actual-byte verification succeeded. Do not call that workflow fully passed. The recorded live case and sanitized transaction/state evidence are in `evidence/invoicebasis-live.json`.

Not applicable: this standalone contract has no production app.

`npm run verify:live` is read-only: it hashes deployed bytes, compares ABI schemas, inspects recorded semantic/finalization receipts, reads canonical state and verifies history. It does not broadcast. Any replacement deployment requires a documented blocker, new address, byte/ABI verification, fresh lifecycle qualification, frontend binding update and exact-release CI.
