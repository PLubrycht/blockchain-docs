# Understanding Asymmetric Cryptography

[TOC]

## 1.Introduction

Asymmetric cryptography, also known as **public-key cryptography**, is a method of encryption tha uses a pair of keys: one public and one private.

The **public key** can be shared openly and is used to encrypt messages or verify signatures.

The **private key** is kept secret and is used to decrypt messages or to create signatures.

This design solves a main limitation of **symmetric cryptography**, where both parties must share the same secret key in advance. With asymmetric cryptography, anyone can communicate safely  and verify authenticity without ever sharing a private key.

This concept was first introduced in the 1970s and has since become the foundation of digital security.
In Bitcoin, asymmetric cryptography is used in:

* generating secure wallets;
* proving ownership of funds using **digital signature**;
* verifying transactions across a decentralized network without trusting need of central authority.

## 2.Public and Private Keys

The core element of asymmetric cryptography are **key pairs**: one **private** and one **public**. These two keys are mathematically linked but serve different purpose.

* **private key**: a secret number, usually 256 bits long in Bitcoin. Anyone with access to this key is able to access the wallet and spend the funds in it;
* **public key**: derived from the private key using one way mathematical operations, and can be shared with anyone. It allows to verify digital signatures or create addresses to receive Bitcoin.

The connection between these two keys is only one-way. A public key is derived from the private key using elliptic curve multiplication, but reversing this process, trying to calculate private key form the public key is computationally infeasible.

### Example of process in Bitcoin

1. a wallet generates a random 256-bit **private key**;
2. the wallet computes the **public key** from the private one using elliptic curve multiplication;
3. the public key is then hashed with SHA-256 and RIPEMD-160 to create a **Bitcoin address**.

This system and process provides 3 key properties:

* **security** - only the private key have access to funds;
* **transparency** - public keys and addresses can be safely shared;
* **trustlessness** - anyone can verify transactions using public information, without need to trust another person.

## 3.Elliptic Curve Cryptography

Asymmetric cryptography can be built on different mathematical problems. Bitcoin specifically uses Elliptic Curve Cryptography (ECC), which provides strong security with much smaller keys. For example, a 256-bit ECC key offers comparable security level to a 3072-bit RSA key (different mathematical way of cryptography).  The efficiency makes ECC perfect for systems like Bitcoin, where performance and scalability and crucial.

### What is ECC?

ECC is based on mathematical curves described by equations like :

`y² = x³ + ax + b`

Bitcoin specifically uses the elliptic curve secp256k1, which is defined by precise mathematical parameters: a 256-bit prime field, and equation, and a special generator point (G). This generator point is fixed by the standard and serves as the basis for creating public keys. A private key is simply a large random 256-bit number, and the corresponding public key is derived by multiplying that private key with G.

This multiplication is easy in one direction, private -> public, but infeasible to reverse. This difficulty is called Elliptic Curve Discrete Logarithm Problem (ECDLP). It means that, given a public key(a point on the curve), it is computationally infeasible to figure out which private key(number) was used to generate it.

**Difference from symmetric cryptography**: in symmetric cryptography security relies on keeping shared secret safe. In ECC-based asymmetric systems, security relies on the mathematical difficulty of reversing elliptic curve operations.

### Advantages of ECC

* **efficiency:** ECC provides the same level of security  as RSA but with much shorter keys;
* **scalability:** shorter keys and signatures save storage and bandwidth, which is crucial in a global peer-to-peer network like Bitcoin;
* **security:** well studied elliptic curves like secp256k1 provide strong cryptographic guarantees.

### ECC in Bitcoin

* Bitcoin wallets use secp256k1 to generate public keys from private keys;
* ECC is the base of **digital signatures**, which allow users to prove ownership of their funds;

Without asymmetric cryptography like ECC it would be impossible to provide security in decentralized transactions like in Bitcoin.
