# Mainnet and Testnet

[TOC]

## 1.Introduction

In blockchain, networks are divided into **mainnet** and **testnet** environments.

* the **mainnet** is the primary blockchain where transactions with real economic value takes place, backed by secure consensus and decentralization;
* the **testnet** is a parallel network for experimentation, where tokens have no real value and developers can test applications without cost and safely.

The division ensures innovation and security without exposing users to unnecessary risk.

## 2.Bitcoin Networks

Bitcoin supports several networks that serve different purposes:

* **Bitcoin mainnet**: the production blockchain where real BTC is transferred and mined;
* **Bitcoin testnet**: an alternative blockchain where coins have no value, used for development and experimentation. Testnet BTC can be obtained from faucets;
* **Bitcoin regtest**: a private, local testing environment where developers can instantly generate blocks and test applications without internet connection.

## 3.Ethereum Networks

Ethereum provides multiple networks as well:

* **Ethereum mainnet**: the production network where real ET is used for transactions, contracts, and dApps;
* **Ethereum testnets**:
  * **Sepolia**: currently the main testnet;
  * **Holesky**: introduced in 2023, designed for large scale testing, staking and stress simulations;
  * **Goerli**: and older testnet being phased out.
  
On testnets, developers can request free ETh from faucets to pay gas fees when deploying contracts or sending transactions.

## 4.How Testnets Are Built

Unlike mainnets, testnets often use alternative consensus mechanism to reduce costs and make testing easier:

* **weaker Proof of Work/Proof of Stake**: some testnets imitate the consensus of the mainnet but with lower difficulty or less security, which makes blocks easier to produce but also easier to revert;
* **Proof of Authority(PoA)**: in many testnets, blocks are validated by a small group of trusted validators. This model is highly centralized but ensures stability and predictability, which is useful for testing;
* **faucets and free tokens**: on testnets, tokens are not meant to carry real monetary value, so they are distributed for free via faucets.

This design allows developers to test contracts, transactions and protocol upgrades in the environment that acts similar to the mainnet but without the risk and costs of real assets.

## 5.Why Testnets Are Important

Testnets provide:

* **safety**: developers can safely test code, upgrades, and smart contracts without affecting the real blockchain or putting real users funds at risk;
* **cost efficiency**: transactions and tests use free tokens, so developers can simulate the mainnet conditions without spending actual money on fees or gas;
* **ecosystem preparation**: before major changes, testnets are used to simulate the upgrade in a safe environment, to provide smooth adaptation to update before it goes live on the mainnet.

## 6.Summary

Mainnets and testnets are key element for blockchain development and innovation. While mainnets ensure the real economy of BTC and ETH, testnets act as laboratories for developers, enabling secure and costless experimentation. Both are essential for the stability and evolution of whole blockchain ecosystem.
