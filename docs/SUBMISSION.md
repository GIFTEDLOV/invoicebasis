# GenLayer submission dossier ? InvoiceBasis

## Project name

InvoiceBasis

## Short description

Determine invoice eligibility from frozen terms and evidence, then derive a bounded payable basis with deterministic integer arithmetic.

## Detailed description

InvoiceBasis creates a consent-bound invoice case with immutable eligibility terms, bounded gross minor units and a fixed rational rate. A distinct designated attestor wallet signs the evidence digest. GenLayer validators independently assess invoice class, exclusions and evidence sufficiency; the contract calculates the provisional payable basis using integer floor division and never transfers funds. Challenges and second-round deliberation precede finalization.

## Problem solved

Invoice eligibility can be semantically ambiguous while payable arithmetic, rates and rounding must remain fixed and reproducible.

## Why this requires a GenLayer Intelligent Contract

Validators independently interpret an invoice category, exclusions and evidence sufficiency against frozen natural-language terms. Deterministic contract code then bounds and calculates the result. A conventional deterministic workflow cannot perform the semantic part credibly.

## Genuine semantic-consensus behavior

Leader and validators independently classify the exact eligibility vector inside gl.vm.run_nondet_unsafe. The strict boolean vector is validated; disagreement aborts adjudication. Contract code derives ELIGIBLE, INELIGIBLE or REVIEW_REQUIRED and computes the provisional payable amount using bounded integers and deterministic floor division.

The leader and validators independently execute the semantic evaluation. The result is schema-validated and contract code alone maps it to permitted outcomes. Evidence and challenge text are untrusted input. Disagreement and invalid output cannot silently become approval. Challenge periods and finalization use contract transaction time.

## GitHub repository

https://github.com/GIFTEDLOV/invoicebasis

## Production app

Not applicable: standalone Intelligent Contract.

## Studionet deployment

- Network: GenLayer Studionet
- Chain ID: `61999`
- Canonical RPC: `https://studio.genlayer.com/api`
- Contract: [0x3C066b25aa1BaF2374F9b1540f99594C737caf8a](https://explorer-studio.genlayer.com/address/0x3C066b25aa1BaF2374F9b1540f99594C737caf8a)
- Verified deployed source SHA-256: `5551281645d5f2e8f42cbc4a66404393f81a6daa40b0e315abf572bc0c47f1fc`
- ABI schema SHA-256: `da35a4c41e7fd7c652d4be8b403967c843eaa4ff64f274dc2d98b3d04bc73c54`

## Live demonstration and evidence

- Historic case: `GLV4-invoicebasis-39138804500`; status `FINALIZED`; terminal verdict **REVIEW_REQUIRED**.
- Qualification workflow: [run 39138804500](https://github.com/GIFTEDLOV/driftproof/actions/runs/39138804500).
- Deployed contract and source parity evidence: `evidence/live-verification.json`.
- The successful NoticeClock lifecycle is case `NCQUAL-39142055216`; the earlier workbench NoticeClock attempt is preserved as BLOCKED because its canonical adjudication state did not match.

## Security and qualification summary

Tests and CI cover party separation, frozen terms, bounded amount/rate arithmetic, floor rounding, string and SDK address serialization, invalid transitions, evidence hashes, strict semantic schema, prompt boundaries, validator disagreement, challenge timing, and finalization. The historical live case correctly finalized REVIEW_REQUIRED rather than forcing a positive result.

- Exact-main CI: [workflow run 39175260479](https://github.com/GIFTEDLOV/invoicebasis/actions/runs/39175260479) passed for the then-current main commit. The repository Actions history and versioned release provide the exact-HEAD and version-tag qualification results.
- CI covers Python tests, GenVM lint, ABI/schema, source provenance, security analysis and app SDK/build/browser tests where applicable.
- No unresolved Critical or High issue was identified in the release audit.
- The historic 39138804500 workbench is not represented as a four-project PASS: NoticeClock was BLOCKED; the other three project artifacts individually report PASS. NoticeClock's later case 39142055216 passed its lifecycle, with terminal verdict INCONCLUSIVE.

## Instructions for reviewers

1. Inspect `contracts/invoicebasis.py` and `release.json`.
2. Verify the deployed source and ABI against the hashes above using the checked-in read-only verifier.
3. Review the case and receipt evidence under `evidence/`; a FINALIZED label is not treated as proof without successful GenVM execution and canonical state readback.
4. Confirm this is a standalone contract submission; it does not claim a production app.
5. Treat all qualification cases and source records as synthetic test inputs; do not infer real-world events.

## Known limitations and external trust assumptions

The qualification evidence was synthetic and explicitly labeled. An attestor signature proves wallet control, not invoice issuer identity, invoice origin, or document truth. Payable values are determinations only; this contract does not escrow or transfer funds. Cases are append-only with no deletion or pruning interface.

## Portal status

The submission fields and evidence package are **prepared for immediate Portal entry**. The final Portal submission has **not** been made. It requires an authenticated Builder Portal session and explicit final-submit authorization; no claim of submission or steward approval is made.
