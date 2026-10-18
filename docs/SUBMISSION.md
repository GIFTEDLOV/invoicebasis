# GenLayer submission dossier — InvoiceBasis

## Project name

InvoiceBasis

## Short description

Determine invoice eligibility from frozen terms and evidence, then derive a bounded payable basis with deterministic integer arithmetic.

## Detailed description

InvoiceBasis creates a consent-bound invoice case with immutable eligibility terms, bounded gross minor units and a fixed rational rate. A distinct designated attestor wallet signs the evidence digest. GenLayer validators independently assess invoice class, exclusions and evidence sufficiency; the contract calculates the provisional payable basis using integer floor division and never transfers funds. Challenges and second-round deliberation precede finalization.

## Problem solved

Invoice eligibility can be semantically ambiguous while payment arithmetic, rates and rounding must remain fixed and reproducible.

## Why this requires a GenLayer Intelligent Contract

Semantic consensus evaluates the meaning of frozen eligibility terms and evidence. Deterministic code alone cannot decide a nuanced invoice-class or exclusion question. Amount, rate, actors and rules remain contract-controlled.

## Genuine semantic-consensus behavior

Leader and validators independently classify the exact eligibility vector in gl.vm.run_nondet_unsafe. Strict vector validation and validator rerun are required; disagreement aborts adjudication. Deterministic code derives ELIGIBLE, INELIGIBLE or REVIEW_REQUIRED and provisional payable amount.

## GitHub repository URL

[https://github.com/GIFTEDLOV/invoicebasis](https://github.com/GIFTEDLOV/invoicebasis)

## Production app URL

Not applicable: standalone Intelligent Contract; no app is claimed.

## Studionet deployment

- Chain 61999, RPC `https://studio.genlayer.com/api`
- Contract: [0x3C066b25aa1BaF2374F9b1540f99594C737caf8a](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a)
- Explorer: [https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a)
- Verified source SHA-256: `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`
- ABI schema SHA-256: `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`

## Live demonstration evidence

- Case `GLV4-invoicebasis-39138804500` finalized at round 2; recorded verdict **REVIEW_REQUIRED**.
- First and second semantic transaction hashes and finalization hash are preserved in `evidence/invoicebasis-live.json`.
- [GitHub workflow run 39138804500](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138804500); exact transaction explorer links are included in the source artifact.
- Qualification source records are synthetic and labelled; this proves GenLayer behavior, not a real-world issuer’s identity or the truth of a physical record.

## Security and qualification summary

The deployed V4 source is byte-identical to the repository source; the deployed ABI matches the locally generated schema. The local regression suite covers role separation, state transitions, source hashes, strict semantic schemas, validator disagreement, prompt injection, challenge fairness, deadlines, duplicates/replay, numeric bounds, address-serialization compatibility and history integrity. Live workflow evidence records transaction status, GenVM execution and canonical readback.

This standalone contract has no browser-signing acceptance criterion.

## Instructions for reviewers

1. Inspect `contracts/invoicebasis.py` and verify its hash and ABI using `npm run verify:live`.
2. Run `python -m pytest -q`, `python -m genvm_linter.cli lint contracts/invoicebasis.py`, `npm ci`, and `npm run verify:live`.
3. Read `evidence/invoicebasis-live.json`; preserve the terminal verdict shown above.
4. For apps, open the production URL read-only; wallet signing is deliberately disabled until its real signed-browser qualification completes.

## Known limitations and external trust assumptions

An attestor signature proves control of the designated wallet, not issuer identity, invoice origin or source-record truth. Amounts are determinations only; the contract does not escrow or transfer funds. Live qualification references use synthetic source data.

Public case creation has no global lifetime cap. Pagination limits each page to 100 records, but total storage and the legacy `get_case_ids()` view can grow. Semantic execution depends on available non-deterministic model services and validator execution; disagreement is not approval. Invoice/minute outputs do not settle assets.
