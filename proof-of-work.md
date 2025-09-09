# What is Proof of Work in Bitcoin ?

## Table of Contents
[TOC]

## 1. Short introduction

Proof of Work, mostly referred as PoW is a mechanism used in Bitcoin to secure the network and achieve consensus across the entire blockchain. Miners, who are users trying to add blocks to the blockchain, are required to perform massive calculations by repeatedly changing a value called a NONCE and calculating the block header's hash until it meets required difficulty.The network sets a Difficulty target, which determines how hard it is to find a valid hash. In practice this means that the hash must start with certain number of zeros in binary (be lower than target value).

Because SHA-256 is unpredictable, miners cannot calculate which nonce will work, they have to try guessing until a correct hash is found. Once a valid hash is found, the block is complete and can be added to the blockchain. By adding block, a miners are proving that they have done work to secure the network.

One of the main challenges in digital currencies is the double spending problem, where a user might try to spend the same Bitcoin more than once. Bitcoin prevents this by using a shared public ledger and the Prof of Work mechanism, which makes double spending practically impossible. Each transaction is verified by multiple nodes before being added to a block, ensuring that funds cannot be reused.

## 2. Block Header

Each block in Bitcoin blockchain contains a header that contains key information.
Main components are:

- **Previous block hash** - hash of the previous block in the chain, which shows continuity of the chain;
- **Merkle Root** - hash representing transactions contained in the block;
- **Timestamp** - shows approx. time the block was created;
- **Bits** - are showing the difficulty target, defining how hard it is to find a valid hash;
- **Nonce** - the only variable number that miners can change to try find a hash that meets the imposed difficulty.

## 3. Transactions and Merkle Root

Transactions are transfers of BTC between users. Each transaction contains details about sender, receiver, amount, and digital signatures. Pending transactions are stored in a pool called Mempool, they are there until a miner adds them to the chain as part of the block.

The Merkle Root is a 256-bit hash that summarizes all the transactions in one block. Likewise other hashes in Bitcoin, it is produced using SHA-256 function. It is constructed in a tree structure called Merkle tree, to represent all the transactions from a block, with a single 256-bit value.

Even the smallest change in transactions will result in a complete change of a Merkle Root, which will invalidate the whole block hash.

This way, it is impossible to change anything with transactions after the block is created.

## 4. Difficulty

In Bitcoin, difficulty is a dynamic measure of how hard it is for miners to find a valid block hash that satisfies the Proof of Work condition. It determines the computational effort required to produce a hash that is lower than a target value, which is expressed as a 256-bit number. A lower target value corresponds to higher difficulty.

The target is encoded in a compact form called bits in the block header. Miners combine the block data — including the previous block hash, the Merkle root of all transactions, a timestamp, and a nonce — and hash it using SHA-256 twice `(SHA-256(SHA-256(block header)))`. The resulting hash is then compared to the current target. Only if the hash is numerically smaller than the target is the block considered valid.

The network adjusts the difficulty every 2016 blocks (approximately every two weeks) to maintain an average block interval of 10 minutes.
If the previous 2016 blocks were mined faster than expected, difficulty increases, and if they were mined slower, it decreases.

Because SHA-256 is cryptographically secure and deterministic, there is no shortcut — miners must brute-force different nonces until the hash meets the target.

By controlling the target and dynamically adjusting difficulty, Bitcoin ensures that the PoW system remains secure, prevents rapid block generation, and makes double spending practically impossible.

## 5. The Proof of Work Process

The PoW process step by step:

1. The miner selects transactions from the Mempool and creates a block header;
2. The miner repeatedly guesses a value called NONCE and calculates the hash of the header;
3. The miner checks if the hash meets required difficulty;
4. Once the valid hash is found, the block is added to the blockchain.

## 6. Types of Nodes in Bitcoin

In the Bitcoin network, nodes are computers running the Bitcoin software that maintain and verify the blockchain. There are several types of nodes:

- **Full nodes**: These nodes store the entire blockchain and independently validate all transactions and blocks according to the consensus rules. They form the backbone of the network, making sure that only valid blocks and transactions are shared across all nodes;
- **Mining nodes**: A subset of full nodes that also perform Proof of Work. They collect transactions from the mempool, build candidate blocks, and attempt to solve the cryptographic puzzle to add new blocks to the blockchain;
- **Lightweight nodes**: These nodes do not store the full blockchain. Instead, they download only block headers and rely on full nodes to provide Merkle proofs that transactions are included in a valid block. This allows devices with limited storage (like mobile phones) to participate in the Bitcoin network.  

Together, these nodes form a decentralized peer-to-peer network, ensuring transparency, immunity, and security of the Bitcoin system.

## 7. Rewards

To motivate miners, Bitcoin provides financial rewards for securing the network:

- **Block reward** - newly generated Bitcoin given to the miner who successfully add a block. The rewards started at 50BTC per block and is halved every 210,000 blocks, right now the reward is 3.125 BTC;
- **Transaction fees** - users pay small fees for their transactions, and these fees are given to the miner.

Because of those rewards, miners are willing to dedicate their computing power to maintain the network.

## 8. Coinbase Transaction

The **coinbase transaction** is the first transaction in every block, created by the miner who successfully mined that block. Its being made in the moment when miner chooses transactions from mempool, the coinbase then is added as first on the list, so it can be executed nly after adding the block to the blockchain. Unlike normal transactions, it does not have inputs referencing previous outputs. Instead it creates new bitcoin as a block reward and collects all transactions fees from the transactions included in that block. This is the only way new bitcoins are introduced into circulation. The output of the coinbase transaction can then be spent by the miner after a maturity period of 100 blocks, so only after 100 new blocks are created.

## 9. Halving

The **halving** is a scheduled event in the Bitcoin protocol that occurs every 210,000 blocks which is approximately every four years. During halving, the block reward given to miners for adding a new block is cut in half. For example, the reward started at 50 BTC in 2009, decreased to 25 BTC in 2012, and continues halving until the maximum supply of **21 million BTC** is reached around the year 2140. After that, miners will be rewarded only transaction fees, without block reward. Halving events are critical because they control the inflation rate of Bitcoin and ensure deficiency over time.

## 10. UTXO (Unspent Transaction Output)

Bitcoin uses the **UTXO model** to track ownership of coins. Every transaction consumes previous outputs (UTXOs) as inputs and creates new outputs that can be spent in the future.  

- An **Unspent Transaction Output (UTXO)** represents a certain amount of bitcoin that can be spent by the owner’s private key;  
- When you receive bitcoin, what you actually get is one or more UTXOs assigned to your address;  
- When you spend bitcoin, your wallet selects one or more UTXOs as inputs to a new transaction, and any leftover change is returned to you as a new UTXO.  

This model ensures that all bitcoins can be traced back to their origin (the coinbase transactions) and prevents double spending by making sure each UTXO can only be spent once.

## 11. Verification, Security and Double Spending

Nodes in Bitcoin are verifying each new block:

- They recalculate the Merkle Root from the transactions in the block and check it with the one in the header;
- They calculate the hash of the header and verify if it meets the difficulty;
- They validate each transaction for correctness, including signatures and balances.

Proof of Work also prevents double spending, because once a transaction is added to the blockchain, it becomes impossible to reverse or duplicate that same transaction.
If someone would try to add a fraud block to the chain with already used coins would require more computing power than the entire rest of the network combined which is impossible.

## 12. Conclusion

Proof of Work is a critical consensus mechanism that secures Bitcoin without a central authority. By requiring miners to perform costly calculations, PoW prevents cheating with transactions, stops double spending and protects integrity of the whole blockchain.
