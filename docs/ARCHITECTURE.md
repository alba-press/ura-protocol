# Architecture

This document describes Ura's public protocol boundaries. It is not a production deployment guide and intentionally excludes keys, infrastructure topology and security-sensitive operator implementation.

## Privacy Bridge

The strict route is:

`Cardano deposit → detected → Cardano confirmed → Mithril certified → Midnight submitted → Midnight confirmed → CLAIMED`

| Stage | Public invariant |
| --- | --- |
| Deposit detected | Observation starts tracking; it does not establish finality |
| Cardano confirmed | The source transaction is eligible for Mithril proof lookup |
| Mithril certified | A valid CardanoBlocksTransactions proof has been found and verified |
| Midnight submitted | A distinct Midnight transaction has been created |
| Midnight confirmed | The expected credit has been observed by the indexer |
| CLAIMED | Terminal success and a classified receipt are available |

A Cardano proof delay is not a Midnight failure. A successful submission is not a confirmed credit. Ura preserves these distinctions so retries and operator intervention remain bounded.

## Capacity Protocol

### Model A — capacity supply

Selected NIGHT UTXOs authorize future DUST generation to an external receiver. NIGHT remains in the holder's wallet. Model A is the supply layer.

The generalized holder-wallet signing flow is still integration work. Ura does not classify it as proven until a complete Preprod transaction is signed, submitted and independently observed.

### Model B — sponsored execution

Model B is the demand and execution layer. An operator:

1. authenticates a request;
2. applies application and method policy;
3. checks replay, expiry and budget constraints;
4. builds or accepts a bounded transaction intent;
5. submits through receiver-side DUST capacity;
6. records the result and reconciliation evidence.

Model B can initially operate from Ura's own operator-seeded capacity. Model A is intended to expand the available receiver-side capacity.

## Custody and control

| Asset or capability | Control boundary |
| --- | --- |
| Selected NIGHT | Remains controlled by the holder |
| Future DUST authorization | Signed by the holder through a supported wallet flow |
| Generated receiver-side DUST | Controlled by the receiver/operator key |
| Sponsored execution | Bounded by operator and application policy |
| Bridge deposit lifecycle | Classified by separate Cardano, Mithril and Midnight stages |

Non-custodial applies to NIGHT. It does not mean the provider controls DUST after that DUST is generated at an operator receiver.

## Accounting direction

Ura targets verifiable pool accounting:

- identifiable sponsorship requests;
- operator-signed receipts;
- on-chain inclusion evidence;
- receiver observation windows;
- append-only reconciliation;
- pool-level conservation.

The protocol does not claim per-coin DUST attribution.

## Non-public implementation

This repository excludes:

- wallet seeds, private keys and signatures;
- operator endpoints and deployment credentials;
- production source code;
- fraud-prevention thresholds;
- internal monitoring and incident data;
- unreleased contract implementation.
