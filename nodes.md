# Understanding Blockchain Nodes: Full vs Light Nodes

[TOC]

## 1. Introduction

In blockchain, a **node** is a crucial component that helps maintain the network,verify transactions, and ensure decentralization. Every blockchain network relies on nodes to store and validate data, making them the core of the system. Without nodes, blockchains would not have their decentralized properties.

There are different types of nodes, mainly described as **full nodes** and **light nodes**, each serving a different purpose. Full nodes store the entire blockchain and independently verify all transactions, while light nodes store only essential information like block headers, and filters and rely on full nodes for additional  data.

## 2.Full Nodes

A **full node** is a computer that downloads and verifies the entire blockchain. It stores all blocks, all transactions, and maintains a mempool (a list of unconfirmed transactions). Full nodes are the base of blockchain network because they validate every rule of the protocol without relying on third parties.

Running a full node has several advantages:

* **security**: transactions are verified independently rather than trusted from others;
* **decentralization**: participation increases the resistance of the network;
* **independence**: users can broadcast and confirm transactions without intermediaries.

However, running a full node also have some cons:

* **storage requirements**: blockchains can consume hundreds of gigabytes of disc space;
* **bandwidth and CPU usage**: syncing and verifying data is resource-intensive.

### Bitcoin Full Node

The most widely used Bitcoin full node software is **Bitcoin Core**. It downloads and verifies the entire Bitcoin blockchain and allows users to interact with the network directly.

Example commands in Bitcoin Core:

* `getblockchaininfo`: shows blockchain state (height,verification progress);
* `getblock <blockhash>`: returns details of a given block;
* `gettransaction <txid>`: retrieves transaction information;
* `getnewaddress`: generates a new wallet address controlled by the node;
* `sendtoaddress <address> <amount>`: creates and broadcasts a transaction.

These commands illustrate how much a Bitcoin full node gives direct control over data and transactions.

### Ethereum Full Node

The most common Ethereum full node software is **Geth (Go Ethereum)**. A full node keeps the entire Ethereum sate and transaction history, enabling independent validation and participation in the Ethereum network. Running a full node requires a lot of disk space.

Example commands in the Geth console:

* `eth,blockNumber`: shows the current block height;
* `eth,getBlock("latest")`: retrieves the most recent block details;
* `eth.getTransaction("<txHash>")`: fetches transaction information;
* `personal.newAccount()`: creates a new Ethereum account;
* `eth.sendTransaction({...})`: sends a transaction from one account to another.

## 3.Light Nodes

**Light nodes**, also called as light clients or Simplified Payment Verification clients(SPV) maintain inly a minimal set of blockchain data, typically the block headers and cryptographic proofs, instead of the full transaction history or state database. Their primary purpose is to verify the inclusion of a transaction in the blockchain without requiring the storage and calculating power of a full node.

The security model of light nodes relies on the assumption that the majority of mining or validating power follow the consensus rules. Light clients validate proof of work or proof of stake headers and request specific transactions or state data from full nodes, checking that the provided Merkle proofs or compact block filters match the verified headers.

In Bitcoin, light clients implement SPV as described in the Bitcoin whitepaper, later extended by bloom filters and compact block filters. In Ethereum, light clients such as Geth Light and the more recent Helios client operate by downloading header, verifying consensus, and querying full nodes for state proofs on demand.

Light nodes significantly reduce disk usage, memory footprint, and bandwidth requirements, which makes them suitable for resource constrained environments  like mobile wallets. However, they trade full independence for reliance on external peers, making them more vulnerable to attacks or misinformation if connected to malicious full nodes.

## 4.Bitcoin Nodes

Bitcoin relies on Proof of Work (PoW) consensus, and it's node architecture is less fragmented than Ethereum's. Nodes can generally be divided in two categories: full nodes and light clients.

### Full Nodes

Full nodes download and validate the entire blockchain, enforcing all protocol rules without relying on third parties. They guarantee decentralization, censorship resistance, and security of the Bitcoin network.

The most widely used implementation is **Bitcoin Core**, maintained by the open-source community since Bitcoin launch. Other implementations still exist, like **btcd**, or **bcoin**, but Bitcoin Core remains the dominant choice due to it's reliability and active development.

Bitcoin Core also supports **pruned mode**, where older blocks are deleted after validation. This allows users to set a storage limit while still running a fully validating node. The limitation iin the result is that pruned nodes cannot serve historical block data to other peers.

### Light Clients (SPV Nodes)

Light clients, also known as SPV (Simplified Payment Verification) nodes, store only block headers rather than the full transaction history. They rely on full nodes for transaction data, using **Merkle proofs** to confirm if a transaction is included in a block.

To optimize this communication, several ideas were developed:

* **bloom filters (BIP-37)**: a probabilistic filtering method that lets SPV clients request only relevant transactions from a full node. However, it has some privacy issues, as full nodes can often guess which addresses belong to the client;
* **Compact block filters (BIP-157/158)**: a newer, more private and efficient alternative, where full nodes provide filters for each block, and the SPV client checks locally which blocks may contain relevant transactions.

Examples of commonly used Bitcoin light clients:

* **Electrum**: one of the most popular lightweight desktop and mobile wallets;
* **BitcoinJ**: a Java based library often used to build SPV applications;
* **Neutrino**: a modern light client implementation that uses compact block filters, used in Lightning Network.

Light clients are often used in mobile and lightweight desktop wallets, where reduced storage and bandwidth are crucial.

## 5.Ethereum Nodes

Ethereum uses a more complex node architecture compared to Bitcoin because of its transition to Proof of Stake in 2022. Nodes in Ethereum can be categorized into three groups, depending on their role in the network.

### Execution Clients

Execution clients are responsible for handling Ethereum state, transactions, and smart contracts. They manage the Ethereum Virtual Machine, validate and propagate transactions, and execute block data. Examples of widely used execution clients are:

* **Geth**: most popular execution client;
* **Nethermind**: written in .NET, known for performance and cross platform support;
* **Besu**: written in Java, often used in enterprise contexts.

### Consensus Clients

Consensus clients are required since transition to PoS. They are responsible for block validation, running the Beacon Chain, and finalizing blocks. Execution clients no longer secure the chain on their own, they must be paired with consensus clients.

Examples of consensus clients:

* **Lighthouse**: written in Rust;
* **Prysm**: written in Go;
* **Teku**: written in Java.
This split into execution and consensus clients ensures decentralization and specialization of tasks in the Ethereum network.

### Light Clients

Light clients connect to full nodes and rely on them for block headers and proofs. They do not store the full state or history but can still verify chain validity and query account balances. These clients are designed for resource constrained devices and are crucial for availability, particularly in mobile and embedded applications.

## 5.Conclusion

Blockchain network rely on different types of nodes to balance security, scalability, and accessibility. Full nodes preserve decentralization and data integrity, while light nodes make participation passible for devices with limited resources. The distinction between execution and consensus clients in Ethereum in the best example how node design evolves to meet the requirements of blockchain systems.
