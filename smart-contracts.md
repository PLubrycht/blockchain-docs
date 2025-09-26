# What is a Smart Contract?

[TOC]

## 1.Introduction

A **smart contract** is a self-executing computer program stored on a blockchain. It automatically runs predefined instructions once specific conditions are met, without requiring intermediaries or centralized authorities. Smart contracts are immutable, transparent, and are crucial part of decentralized applications and Web3 ecosystem.

## 2.Smart Contracts in Ethereum

Ethereum is the first blockchain designed specifically to support smart contracts. It introduced the **Ethereum Virtual Machine (EVM)**, a decentralized runtime environment that executes contract code across network's nodes.

Smart contracts on Ethereum are primarily written in **Solidity** or **Vyper**, and they enable developers to builds a wide range of applications, such as:

* **decentralized Finance (DeFi)**: lending protocols, decentralized exchanges;
* **non-fungible tokens (NFTs)**: unique digital assets;
* **decentralized autonomous organizations (DAOs)**: community-governed structures;
* **automated payments and agreements**: escrow services, subscriptions.

The EVM ensures tha every contract executes deterministically and consistently across all nodes.

## 3.Bitcoin and Programmability

Unlike Ethereum, Bitcoin was not designed for smart contracts. However, it does include a limited, stack based scripting language called **Bitcoin Script**.

This language allows setting conditions for spending coins, like requiring multiple signatures or delaying spending until certain date. It is limited and predictable, so it cannot run arbitrary programs like Ethereum smart contracts.

Examples of programmability in Bitcoin:

* **multisignature transactions**: requiring multiple parties to sign;
* **timelocks**: restricting spending until a certain block height or timestamp;
* **hashed timelock contracts (HTLCs)**: used in the Lightning Network for conditional payments.

Therefore, even with ability to make programmable transactions, Bitcoin does not provide the same flexibility as Ethereum's EVM.

## 4.Advantages and Limitations

Advantages of smart contracts:

* automation of processes without intermediaries;
* transparency: code and outcomes are visible on the chain;
* security: execution guaranteed by the blockchain consensus.

Limitations:

* code immutability: bugs or vulnerabilities are difficult to fix;
* gas fees: cost of execution can be high on busy networks;
* complexity: secure development requires advanced knowledge.

## 5.Summary

Smart contracts are a major innovation in blockchain technology. Ethereum has become the leading platform in decentralized applications, while Bitcoin provides a more limited but secure form of programmability through Bitcoin Script. These two models show different approaches for applying automation in finance and technology.
