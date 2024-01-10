# Table of Contents

- [Hash Functions](#hash-functions)
  - [What is an Hash Function](#what-is-an-hash-function)
  - [Secure Cryptographic Hash Functions](#secure-cryptographic-hash-functions)
  - [Finding collisions](#finding-collisions)
  - [Building Hash Functions](#building-hash-functions)
  - [Merkle-Damgård Construction](#merkle-damgård-construction)
  - [Sponge Construction](#sponge-construction)
- [Concrete Hash Functions](#concrete-hash-functions)
  - [MD5](#md5)
  - [Secure Hash Function (SHA)](#secure-hash-function-sha)
  - [SHA-1 Internals](#sha-1-internals)
  - [SHA-2 Family](#sha-2-family)
  - [SHA-3](#sha-3)
- [Keyed Hashing](#keyed-hashing)
  - [MACS as Keyed Hashing](#macs-as-keyed-hashing)
  - [MACS](#macs)
  - [Authentication and Message Integrity](#authentication-and-message-integrity)
  - [HMAC Construction](#hmac-construction)
  - [Building MACs From Block Ciphers](#building-macs-from-block-ciphers)
  - [CMAC Internals](#cmac-internals)
  - [Universal Hash Functions](#universal-hash-functions)
  - [Wegman Carter Construction](#wegman-carter-construction)
- [Authenticated Encryption](#authenticated-encryption)
  - [Why?](#why)
  - [Authenticated Encryption using MACs](#authenticated-encryption-using-macs)
    - [Encrypt and MAC](#encrypt-and-mac)
    - [MAC then Encrypt](#mac-then-encrypt)
    - [Encrypt then MAC](#encrypt-then-mac)
- [Optimized Authentication Code Constructions](#optimized-authentication-code-constructions)
  - [Authentication Encryption from Scratch](#authentication-encryption-from-scratch)
  - [Galois Counter  Mode](#galois-counter-mode)
  - [Efficiency](#efficiency)
  - [Offset Codebook (OCB)](#offset-codebook-ocb)
  - [OCB vs AEAD](#ocb-vs-aead)
  - [Security and Efficiency of OCB](#security-and-efficiency-of-ocb)
  - [Synthetic IV mode](#synthetic-iv-mode)
  - [Permutation Based AEs](#permutation-based-aes)

## Hash Functions

### What is an Hash Function

- Transforms content into an Hash of fixed lenght.

### Secure Cryptographic Hash Functions

- Unpredictable Outputs.

- Hard to find pre-images. (determining the original input(s) that resulted in that specific hash value.)

- Hard to find collisions.

- Are evaluted heuristicaly, the most recent is sha-3

### Finding collisions

- Collisions can be found with work √2n by computing values like a bruteforce and checking if a collision is found in a data structure indexed by image value.

### Building Hash Functions

### Merkle-Damgård Construction

- The basic idea is to break the input message into fixed-size blocks and process them iteratively.

- The Blocks are compressed using compressing function. The basic idea is to break the input message into fixed-size blocks and process them iteratively. Until final hash.

### Sponge Construction

- Divided into two phases Absorbing + Squeezing.

- The input message is divided into blocks, and each block is XORed with the rate portion of the internal state.

- The sponge alternates between absorbing and squeezing phases until enough output bits are obtained.

## Concrete Hash Functions

### MD5

- Most popular until it was broken in 2005. It takes seconds two find collisions nowadays.
- Similiar design to SHA family.

### Secure Hash Function (SHA)

- Standardize by NIST.

- SHA-0 and SHA-1 had 160 bit outputs, recent attacks reduced attack from 2⁶⁰ to 2³³

- Most Applications use SHA-2 wich has the same design principle but larger parameters.

- Future applications are adopting SHA-3 evolve to Sponge with flexible output!

### SHA-1 Internals

- Merkle Damgard with David Meyers compression.
- Uses Block Cypher in compressing function called SHACAL with 160 bits blocks.
- Messages blocks are 512 bits and 160 bit long hashes.
- Is now insecure, collisions in 2⁶³.

### SHA-2 Family

- SHA-224 and 256 still use 512 bit blocks (64 rounds = numbers of iterations), with diferent IV from 224 to 256.
- SHA-384 and 512 are similarly related but with 80 rounds.
- No non-generic attacks exist on these hash functions.

### SHA-3

- Different Design with benefit of varying sized outputs, also good to generater keys!
- Competition called for new design, if SHA-2 gets attacked with Keccack

## Keyed Hashing

### MACS as Keyed Hashing

- They are short summaries of messages called hash if everything is public.

- Message Authentication Codes guarantee that the message was produced by someone that knows the key. And implies that message wasn't modified since creation.

### MACS

- MACs are used in two party agreements with a common key, the MAC is produced and sent and the receiver produces it aswell and compares it with the received MAC.

- Message is public, because MACS give integrity not confidentility.

### Authentication and Message Integrity

- This means that the adversary cannot change the message, nor compute a fake one, because the computed MAC would be different.

### HMAC Construction

- HMAC is simply H((K ⊕ opad)||H((k ⊕ ipad)||m))

### Building MACs From Block Ciphers

### CMAC Internals

A Estudar, não percebi nada lol ...

### Universal Hash Functions

Não percebi também...

### Wegman Carter Construction

- The full MAC key is (k1, k2)
- UH(k1, m) ⊕ PRF(k2, n)
- n is a nonce

## Authenticated Encryption

### Why?

- Messages need to be confidential - With Encryption
- Messages need to be authentic - With MACs
- Messages should not be repeated/omitted/removed.

### Authenticated Encryption using MACs

#### Encrypt and MAC

- AE with k = (k1, k2) done with parallel processing.

- Potentially malicious c decrypted before authentication

#### MAC then Encrypt

- In the "MAC-then-Encrypt" approach, a MAC is generated over the plaintext, and then the combined data (plaintext and MAC) is encrypted. While this can provide integrity protection for the plaintext, it may expose the plaintext to certain types of attacks before encryption.

### Encrypt then MAC

- In the "Encrypt-then-MAC" approach, the data is first encrypted and then a MAC is generated over the ciphertext. This ensures that the integrity of the encrypted message is protected. If an attacker tries to tamper with the ciphertext, the MAC verification will fail, indicating potential tampering before decryption.

## Optimized Authentication Code Constructions

### Authentication Encryption from Scratch

### Galois Counter  Mode

- Encrypt then MAC
- AES uses Pseudo Random Function (PRF).

### Efficiency

- As parallelism like CTR mode.
- Ciphertext blocks are computed and authenticated on the fly.

### Offset Codebook (OCB)

- Offset depends on the key and the nonce
- Incremented for each new block
- Last offset computed from last plaintext block processed.

### OCB vs AEAD

- Very secure and efficient
- Implementations required licensing

### Security and Efficiency of OCB

- On nonce reuse, the attacker can identify block duplicates.

- Repeated nonces can break the authenticity of OCB. An attacker can combine blocks from messages authenticated with OCB to create another authenticated message.

### Synthetic IV mode

- In some cryptographic constructions, a synthetic IV is created using a deterministic function applied to a nonce (number used once) and other parameters. This synthetic IV is then used as the actual IV for encryption. This approach is used in some encryption modes, especially in cases where a nonce is used to ensure uniqueness, and a standard IV is not available.

### Permutation Based AEs

- Fast and Streamable because of decomposition.
- Unforgeability not affected
