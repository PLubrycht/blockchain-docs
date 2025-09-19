# Understanding Asymmetric Cryptography

[TOC]

## 1.Introduction

Asymmetric cryptography, also known as **public-key cryptography**, is a method of encryption tha uses a pair of keys: one public and one private.

The **public key** can be shared openly and is used to encrypt messages or verify signatures.

The **private key** is kept secret and is used to decrypt messages or to create signatures.

This design solves a main limitation of **symmetric cryptography**, where both parties must share the same secret key in advance. With asymmetric cryptography, anyone can communicate safely  and verify authenticity without ever sharing a private key.

This concept was first introduced in the 1970s and has since become the foundation of digital security.
In Bitcoin, asymmetric cryptography is used in:

* generating secure pairs of keys (often stored in a wallet application);
* proving ownership of funds using **digital signature**;
* verifying transactions across a decentralized network without trusting need of central authority.

## 2.Public and Private Keys

The core element of asymmetric cryptography are **key pairs**: one **private** and one **public**. These two keys are mathematically linked but serve different purpose.

* **private key**: a secret number, usually 256 bits long in Bitcoin. Anyone with access to this key is able to access the wallet and spend the funds in it;
* **public key**: derived from the private key using one way mathematical operations, and can be shared with anyone. It allows to verify digital signatures or create addresses to receive Bitcoin.

The connection between these two keys is only one-way. In Bitcoin, public keys are derived using elliptic curve multiplication. Other asymmetric systems, like RSA, rely on different mathematical problems but maintain the same property: deriving the public key is easy, reversing it to get the private key is infeasible.

### Example of process in Bitcoin

1. a wallet generates a random 256-bit **private key**;
2. the wallet computes the **public key** from the private one using elliptic curve multiplication;
3. the public key is then hashed with SHA-256 and RIPEMD-160 to create a **Bitcoin address**.

This system and process provides 3 key properties:

* **authentication** - only the holder of a private key can authorize spending the funds;
* **transparency** - public keys and addresses can be safely shared;
* **trustlessness** - anyone can verify transactions using public information, without need to trust another person.

## 3.Elliptic Curve Cryptography

Asymmetric cryptography can be built on different mathematical problems. Bitcoin specifically uses Elliptic Curve Cryptography (ECC), which provides strong security with much smaller keys. For example, a 256-bit ECC key offers comparable security level to a 3072-bit RSA key.

RSA is another public-key algorithm, based on the difficulty of factoring large numbers, rather than elliptic curve mathematics.

The efficiency makes ECC perfect for systems like Bitcoin, where performance and scalability and crucial.

### What is ECC?

ECC is based on mathematical curves described by equations like :

`y² = x³ + ax + b`

Bitcoin specifically uses the elliptic curve secp256k1, which is defined by precise mathematical parameters: a 256-bit prime field, and equation, and a special generator point (G). This generator point is fixed by the standard and serves as the basis for creating public keys. A private key is simply a large random 256-bit number, and the corresponding public key is derived by multiplying that private key with G.

This multiplication is easy in one direction, private -> public, but infeasible to reverse. This difficulty is called Elliptic Curve Discrete Logarithm Problem (ECDLP). It means that, given a public key(a point on the curve), it is computationally infeasible to figure out which private key(number) was used to generate it.

**Difference from symmetric cryptography**: in symmetric cryptography security relies on keeping shared secret safe. In ECC-based asymmetric systems, security relies on the mathematical difficulty of reversing elliptic curve operations.

### Advantages of ECC

* **efficiency:** ECC provides the same level of security as RSA but with much shorter keys. For example, a 256-bit ECC key ≈ 3072-bit RSA key. RSA is still widely used, but it's longer keys make it less efficient for systems like Bitcoin;
* **scalability:** shorter keys and signatures save storage and bandwidth, which is crucial in a global peer-to-peer network like Bitcoin;
* **security:** well studied elliptic curves like secp256k1 provide strong cryptographic guarantees.

### ECC in Bitcoin

* Bitcoin wallets use secp256k1 to generate public keys from private keys;
* in Bitcoin, digital signatures are implemented using ECDSA which is based on elliptic curves. Other digital signatures algorithms, like RSA do not rely on the same curve.

## 4,Digital Signatures

Digital signatures are a crucial component of asymmetric cryptography. They allow users to prove the **authenticity** and **integrity** of a message or transaction without revealing the private key.

### How digital signatures work?

1. **message preparation** - we start with the original message;
2. **hashing** - the message is passed through a cryptographic hash function like SHA-256. This produces a fixed-size **digest**(that how hashed message is named in this process) of the process. Hashing ensures that even the smallest change in the original message results in a completely different digest;
3. **signing** - the digest is then encrypted using the sender's **private key**. This produces the digital signature (an encrypted hash);
4. **verification** - anyone with access to the sender's **public key** can decrypt the signature back into a hash. they then re-hash the original message and compare both digest. If the values match, the signature is valid.

This process proves both that the message came from the holder of the private key and that it was not modified in transit.

### Security Properties ofDigital Signatures

Digital signatures provide the following guarantees:

* **integrity** - any change to the message after signing will cause a mismatch between the original and recalculated hash;
* **authentication** - the signature proves that the message was created by the holder of the private key;
* **non-repudiation** - the signer cannot later deny having created the signature, since only their private key could have generate it.

### Use of Digital signature

In Bitcoin every transaction input must be signed with the private key corresponding to the funds being spent.

Beyond Bitcoin:

* secure email;
* code signing for software distribution;
* secure connections (TLS certificate)

## 5.Summary

Asymmetric cryptography is at the core of modern digital security. By separating private and public keys, it enables secure communication, digital signatures and decentralized trust models. Its applications are used not only in blockchains like Bitcoin but widely in other areas, such as  secure email, VPN, and internet protocols like HTTPS.
