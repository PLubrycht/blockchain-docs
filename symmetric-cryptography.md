# Understanding the Symmetric Cryptography

[TOC]

## 1.Introduction

**Symmetric cryptography** is a conventional form od encryption that uses a single **secret key** for both encrypting and decrypting data.

Encryption is the process of converting information into a coded format that can only be read by someone who has the right key.

If the key is kept secret, the information remains private. With the moment the key is exposed, all encrypted data are compromised.

Symmetric methods are fast and efficient, making them useful for tasks such as encrypted communication, hashing and data processing in various systems.

## 2.Symmetric Cryptography Examples

### Caesar Cipher

The **Caesar cipher** is a historical shift cipher where each letter of the message is shifted by a fixed number of positions in the alphabet.
It stands as early example of symmetric cryptography.
The same key (shift amount) is used for both encryption and decryption.

### ChaCha20

**ChaCha20** is a modern stream cipher designed for fast and secure encryption of digital data.
A **stream cipher** encrypts data one piece at a time (usually byte by byte), rather than waiting to gather a large block of data.
This allows it to start encrypting immediately and handle continuous stream of encrypted data, making it very fast for real-time communication.
It is symmetric because the same secret key is used to encrypt and decrypt the data.

### SHA-256 and Symmetric Primitives

In Bitcoin, symmetric cryptography is also represented by **symmetric primitives**, which is any deterministic function that processes data in a fixed, predictable way, using a secret instructions built into the algorithm.
Example of **symmetric primitive** is SHA-256 which is a cryptographic hash function. It converts input data into a fixed-length output. It is considered as **symmetric primitive** because it applies the same one-way function to all inputs, and anyone using the algorithm will get the same output for the same input data.

## 3.Use of Symmetric Cryptography

### General applications

Symmetric encryption is not only used in blockchain. It is widely applied in:

* **private communication** - messaging apps like Signal or WhatsApp use symmetric encryption to keep messages secret;
* **Virtual Private Networks (VPN)** - symmetric encryption secures data sent over the internet, ensuring privacy and speed;
* **file encryption** - protecting local or stored in cloud files with a secret key.

### Bitcoin Ecosystem

* **proof-of-Work**: miners use SHA-256 to hash block header until they find a valid result that meets the network difficulty target;
* **transactions ID and block headers**: every transaction and block header is hashed with SHA-256, what guarantees that data cannot be altered without detection.

In the **Lightning Network (LN)** - a second layer protocol that enables fast and low cost Bitcoin payments off the main chain:

* **ChaCha20** is used to encrypt the communication between nodes. This keeps payment channels private and efficient.

## 4, Key Exchange in Symmetric Cryptography

Symmetric encryption requires both parties to have the same secret key. Securely sharing this key is a challenge because it the key would be stolen, all communication can be read. Common methods to exchange keys are:

* **Pre-shared keys (PSK)** - the key is agreed on  in advance through a secure channel;
* **Diffie-Hellman key exchange** - a method to create a shared secret over an insecure channel;
* **TLS session key** - used in secure internet connections, a symmetric key is generated and shared securely for the whole session.

## 4.Security Properties of Symmetric Encryption

* **confidentiality** - symmetric encryption keeps data secret as long as the key is secure;
* **availability** - symmetric encryption foes not effect system availability.

## 4.Advantages and Limitations

**Advantages:**

* fast and efficient;
* deterministic and predictable;
* essential for hashing, encryption, and secure communication in Bitcoin ecosystem.

**Limitations:**

* requires secure key management, if the key is leaked, security is compromised;
* cannot provide digital signatures or public verifiability which are available with asymmetric cryptography.

## 5.Summary

Symmetric cryptography, from simple historical ciphers to modern solutions such as ChaCha20 and SHA-256, forms a crucial part of Bitcoin's cryptography. While it is efficient and secure for hashing and fast encryption, the lack of public and private keys, digital signatures and verifiability, means it has to be complemented by asymmetric cryptography.
