# What is Proof of Work in Bitcoin ?

## 1.Short introduction

Proof of Work, mostly reffered as PoW is a mechnism used in Bitcoin to secure the network and achive consensus in whole chain and all blocks. Miners, users trying to add blocks to the blockchain, to do so are required to do masive calculations by repeatedly changing a value called a NONCE and calculating the block header's hash until it meets required difficulty. Once a valid hash is found, the block is complete and can be added to the blockchain. By adding block, a miners are proving that they have done work to secure the network,therefore the name Proof of Work. 

## Block Header

Each block in Bitcoin blockchain contains a header that contains key informations.
Main components are:
* Previous block hash - hash of the previous block in the chain, which shows continuity of the chain.
* Merkle Root - hash representing transactions contained in the block.
* Timestamp - shows aprox. time the block was created. 
* Bits - are showing the difficulty target, defining how hard it is t ofind a valid hash. 
* Nonce - the only variable number that miners can change to try find a hash that meets the imposed difficulty.

## Transactions and Merkle Root

Transactions are transfers of BTC between users. Each transaction contains details abour sender, receiver, amount, and digital signatures. Pending transactions are stored in a pool called Mempool, they are there until a miner adds them to the chain as part of the block.

The Merkle Root is a 256-bit hash that summarizes all the transactions in one block. Likewise other hashes in Bitcoin, it is produced using SHA-256 function. It is constructed in a tree structure called Merkle tree, to represent all the transactions from a block, with a single 256-bit value. 

Even the smallest change in transactions will result in a complete change of a Markle Root, which will invalidate the whole block hash.

This way, it is impossible to change anything with transactions after the block is created. 

## The Proof of Work Process

The PoW process step by step:
1. The miner selects transactions from the Mempool and creates a block header.
2. The miner repeatedly guesses a value called NONCE and calculates the hash of the header.
3. The miner checks if the hash meets required difficulty.
The network sets a Difficulty target, which determines how hard it is to find a valid hash. In practice this means that the hash must start with certain number of zeros in binary(be lower than target value).
Because SHA-256 is unpredictable, miners cannot calculate which nonce will work, they have to try guessing until a correct hash is found.
5. Once the valid hash is found, the block is added to the blockchain.

## Rewards

To motivate miners, Bitcoin provides financial rewards for securing the network:
* Block reward - newly generated Bitcoin given to the miner who succesfully add a block. The rewards started at 50BTC per block and is halved every 210,000 blocks, right now the reward is 3.125 BTC.
* Transaction fees - users pay small fees for their transactions, and these fees are given to the miner.

Because of those rewards, miners are willing to dedicate their computing power to maintain the network.

## Verification, Security and Double Spending

Nodes in Bitcoin are verifying each new block:
* They recalculate the Merkle Root from the transactions i nthe block and check it with the one in the header.
* They calculate the hash of the header and verify if it meets the difficulty.
* They validate each transaction for correctness, including signatures and balances.

Proof of Work also Prevends double spending, because once a transaction is added to the blockchain, it becomes impossible to reverse or duplicate that same transaction. 
If someone would try to add a fraud block to the chain with already used coins would require more computing power than the entire rest of the network combined which is impossible.

## Conclusion

Proof of Work is a critical mechanism that secuires Bitcoin without a central authority. By requiring miners to perform costly calculations, PoW prevents cheating with transactions, stops double spending and protects integrity of the whole blockchain.
