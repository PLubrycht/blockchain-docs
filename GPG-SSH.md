# Understanding GPG and SSH keys and their differences

[TOC]

## 1.Introduction

Public-key cryptography enables secure communication and authentication using key pairs: a public key and a private key. Two commonly used systems are **GPG** and **SSH**.

* **GPG** is mainly used for encrypting, signing data and verifying authenticity;
* **SSH** is used for secure access to remote systems, replacing passwords and encrypting connections.

## 2.What are GPG keys?

**GPG (GNU Privacy Guard)** is an implementation of the OpenPGP standard, which defines a protocol for encrypting, decrypting and signing data using public-key cryptography. OpenPGP ensures confidentiality, integrity and authenticity of messages and files.

Purpose of GPG is to protect confidentiality of data and to verify authenticity and integrity through digital signatures.

How it works:

* a pair of keys consists of a private key (kept in secret) and a public key (shared);
* data encrypted with a recipient's public key can only be decrypted using their private key;
* digital signatures are created with a private key and verified with the corresponding public key.

**GPG** is commonly used in:

* secure email communication;
* signing software releases or Git commits;
* encrypting files for confidential storage.

## 3.What are SSH keys?

**SSH (Secure Shell)** is a network protocol designed to provide secure remote access over unsecured network. It encrypts all communication between client and server, ensuring confidentiality, integrity, and authentication. SSH keys are used to replace or complement password based authentication, making logins more secure.

Purpose of SSH keys is to provide secure login to servers, encrypt data in transit and enable automated or script based access.

How it works:

* a pair of keys consists of a private key (kept secret) and a public key (stored on server);
* when connecting, the server challenges the client, the client proves possession of the private key without sending it;
* after authentication, SSH encrypts all communication between client and server.

**SSH** is commonly used in:

* logging into remote servers;
* connecting Git clients to repositories;
* automated deployments and CI/CD pipelines.

## 4.Technical and Operational Differences

| Aspect | GPG Keys | SSH Keys |
|--------|----------|----------|
| Main purpose | encrypting/signing data | authenticating  access and encrypting session |
| Protocol/Standard | OpenPGP | SSH protocol |
| Key Pair | private + public keys | private + public keys|
| Common use | email encryption, signing commits and files | Server login, Git - VS Code authentication, CI/CD deployments |
| Identity proof | Proves authorship of data/messages | Proves user access to host |
| Lifespan | long term keys possible | short to medium term, managed per user |
| Revocation | revocation certificates and expiration | manual removal, SSH certification |
| Perfect Forward Secrecy | not provided | YES, temporary session keys |

## 5.Security Properties

| Security Property | GPG Keys | SSH Keys |
|-------------------|----------|----------|
| Confidentiality | YES, protects data at rest and in transit | YES, protects sessions |
| Integrity | YES, ensures file integrity | YES, ensures session integrity |
| Authentication | YES, verifies authorship/signature | YES, authenticates user login |
| Non-repudiation | YES, if public key is authentic and private was secure | NO |

## 6.Practical Recommendations

### Using GPG

* generate a revocation certificate immediately;
* use subkeys instead of your master key;
* protect your private key with strong passphrase;
* send your public key using trusted channels.

### Using SSH

* use ssh keys instead of passwords;
* add a passphrase to your ssh private key;
* use SSH certificates or key management in large setups;
* regularly rotate keys;
* limit key usage per service.

### 7.General Recommendations

* **store private keys securely**: hardware tokens (YubiKey, smartcards) act like vaults to keep the key locked inside and only release signatures;
* **backup keys responsibly**: losing a private key without a backup may results in losing data forever;
* **stay updated**: both GPG and SSH evolve, it's important to keep software updated and current to avoid known vulnerabilities.

## 8.Summary

GPG and SSH keys both rely on public-key cryptography but serve different purposes: GPG protects and signs data, while SSH secures remote access and communication.
Understanding their differences helps in applying each tool effectively, while following best practices keeps them reliable and secure.
