# Chaguar

Chaguar is a high-performance, open-source distributed ledger platform for regulated digital asset ecosystems, built to support applications such as tokenized deposits, stablecoins, CBDCs, tokenized securities, and cross-border payments. 

Chaguar delivers more than 400,000 TPS under Byzantine fault tolerance ([Androulaki et al., 2026](https://dl.acm.org/doi/10.1145/3788853.3803092)), while providing privacy and transparency. Its modular architecture supports multiple programming models, including native smart contracts and EVM-compatible applications, on a shared ledger and settlement layer, enabling institutions to build interoperable, composable, and sovereign digital asset networks at scale. With institutional-grade governance, robust identity and access management, and support for advanced privacy technologies including zero-knowledge proofs that run at endorsement (off the critical path), Chaguar enables organizations to meet the compliance, trust, and operational requirements of regulated financial markets.

Chaguar was previously developed as Fabric-X under Hyperledger Fabric. A paper describing it was published in [SIGMOD 2026](https://dl.acm.org/doi/10.1145/3788853.3803092):

> Elli Androulaki, Marcus Brandenburger, May Buzaglo Rosenbaum, Angelo De Caro, Kaoutar Elkhiyaoui, Alexandros Filios, Liran Funaro, Yacov Manevich, Hagar Meir, Senthilnathan Natarajan, Manish Sethi, and Yoav Tock. 2026. *Fabric-X: Scaling Hyperledger Fabric for Asset Exchange.* In Companion of the International Conference on Management of Data (SIGMOD Companion ’26), May 31–June 5, 2026, Bengaluru, India. ACM, New York, NY, USA, 13 pages.


| Component | Language | Description |
|-----------|----------|-------------|
| [Umbrella repo](https://github.com/Chaguar/chaguar) | Go | Documentation, tools, integration tests and release coordination |
| [Orderer](https://github.com/Chaguar/orderer) | Go | Sharded BFT ordering service: routers, batchers (one group per shard), consenters (SmartBFT) and assemblers that produce a Fabric-compatible block stream |
| [Committer](https://github.com/Chaguar/committer) | Go | Decomposed validation and commit pipeline: sidecar, coordinator (dependency graph), signature verifiers, validator-committers (MVCC) and query service, backed by an SQL database (YugabyteDB or PostgreSQL) |
| [Endorser](https://github.com/Chaguar/endorser) | Go | Endorsement framework built on Fabric Smart Client. It replaces chaincode and supports threshold endorsements |
| [SDK](https://github.com/Chaguar/sdk) | Go | Client SDK for building and submitting transactions to Chaguar (and Fabric v3) |
| [Common](https://github.com/Chaguar/common) | Go | Shared protobuf APIs, MSP, policy and configuration libraries, and CLI tools |
| [Samples](https://github.com/Chaguar/samples) | Go | Sample networks and applications (devnet, tokens, custom endorser, EVM) |
| [Ansible collection](https://github.com/Chaguar/ansible-collection) | Ansible | Ansible collection (`hyperledger.chaguar`) for deploying Chaguar networks locally, on Kubernetes, or across multiple nodes |
| [Block explorer](https://github.com/Chaguar/block-explorer) | Go | Lightweight block explorer: ingests blocks from the committer sidecar, indexes them in PostgreSQL, and exposes a REST API and a Next.js web UI for browsing blocks, transactions and namespace policies |
| [EVM](https://github.com/Chaguar/evm) | Go | Runs Ethereum smart contracts on Chaguar (and Fabric v3) through a native EVM and an Ethereum JSON-RPC gateway |
| [RFCs](https://github.com/Chaguar/rfcs) | Markdown | Design proposals (RFCs) for the project |

More detail is in the
[orderer architecture](https://github.com/Chaguar/orderer/blob/main/docs/architecture.md) and
[committer architecture](https://github.com/Chaguar/committer/blob/main/docs/architecture.md)
documents.
