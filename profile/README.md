# Chaguar

## Architecture Overview

Fabric-X redesigns Fabric's architecture for digital assets such as central bank digital currencies, stablecoins, tokenized deposits and tokenized securities. It keeps Fabric's execute-order-validate model, X.509-based identities (MSP), endorsement policies and Broadcast/Deliver APIs. It replaces the monolithic peer with independently scalable microservices, and Fabric's ordering service with the **Orderer**, a sharded Byzantine-fault-tolerant ordering service that orders compact transaction digests. A transaction dependency graph enables parallel validation. This combination has demonstrated throughput above 100,000 transactions per second ([Fabric-X paper](2023-1717.pdf)).


![Fabric vs. Fabric-X](https://raw.githubusercontent.com/hyperledger/fabric-x/main/diagrams/Fabric_vs_Fabric-X.png)

| Component | Language | Description |
|-----------|----------|-------------|
| [Orderer](https://github.com/hyperledger/fabric-x-orderer) | Go | Sharded BFT ordering service: routers, batchers (one group per shard), consenters (SmartBFT) and assemblers that produce a Fabric-compatible block stream |
| [Committer](https://github.com/hyperledger/fabric-x-committer) | Go | Decomposed validation and commit pipeline: sidecar, coordinator (dependency graph), signature verifiers, validator-committers (MVCC) and query service, backed by an SQL database (YugabyteDB or PostgreSQL) |
| [Endorser](https://github.com/hyperledger/fabric-x-endorser) | Go | Endorsement framework built on Fabric Smart Client. It replaces chaincode and supports threshold endorsements |
| [SDK](https://github.com/hyperledger/fabric-x-sdk) | Go | Client SDK for building and submitting transactions to Fabric-X (and Fabric 3) |
| [Common](https://github.com/hyperledger/fabric-x-common) | Go | Shared protobuf APIs, MSP, policy and configuration libraries, and CLI tools |
| [Samples](https://github.com/hyperledger/fabric-x-samples) | Go | Sample networks and applications (devnet, tokens, custom endorser, EVM) |
| [EVM](https://github.com/hyperledger/fabric-x-evm) | Go | Runs Ethereum smart contracts on Fabric-X (and Fabric 3) through a native EVM and an Ethereum JSON-RPC gateway |
| [RFCs](https://github.com/hyperledger/fabric-x-rfcs) | Markdown | Design proposals (RFCs) for the project |
| [Umbrella repo](https://github.com/hyperledger/fabric-x) | Go | Documentation, tools, integration tests and release coordination |

More detail is in the
[orderer architecture](https://github.com/hyperledger/fabric-x-orderer/blob/main/docs/architecture.md) and
[committer architecture](https://github.com/hyperledger/fabric-x-committer/blob/main/docs/architecture.md)
documents.
