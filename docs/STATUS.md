# Status and claim boundaries

Last updated: 27 August 2026.

Ura is under active Preprod development. This page separates observed behavior from planned integration.

## Demonstrated on Preprod

| Capability | Evidence boundary |
| --- | --- |
| Cardano deposit detection | Deposits have entered the bridge state machine |
| Mithril-gated progression | Strict progression waits for a verified CardanoBlocksTransactions proof |
| Midnight credit submission | Certified deposits have produced distinct Midnight submissions |
| Indexer-based confirmation | Expected credits have been observed before terminal CLAIMED state |
| Model B execution | Bounded sponsored execution and reconciliation have been exercised with operator-seeded capacity |
| Warm operator path | The execution path has remained available without rebuilding a wallet for every request |

## Integration in progress

| Capability | Current boundary |
| --- | --- |
| Generalized Model A onboarding | One complete holder-wallet redesignation transaction remains to be proven end to end |
| Wallet signing UX | Requires a supported wallet and SDK flow for holder review and signature |
| Distributed capacity accounting | Public accounting and provider settlement remain protocol work |
| Additional bridge assets | ETH, XRP, SOL, BNB and other routes are not part of the currently demonstrated ADA/tADA path |
| Mainnet | No production or mainnet deployment is claimed |

## Current blocker

The narrow supply-side blocker is wallet integration: a NIGHT holder must be able to sign a transaction that directs future DUST generation to Ura's receiver while NIGHT remains in the holder's wallet.

Ura's sponsored-execution path and warm operator do not solve that authorization step. Completing one controlled Preprod transaction with wallet and SDK engineers is the current proof target.

## Claim discipline

Ura does not classify any of the following as final proof:

- a wallet connection without a signed redesignation;
- transaction construction without wallet authorization;
- submission without chain or indexer observation;
- a local proof-server response without wallet invocation;
- a design document without a reproduced Preprod transaction.

## Production warning

The public Preprod interface is for development and testing. Nothing in this repository is an invitation to deposit mainnet assets or a representation that the system has completed an independent production security audit.
