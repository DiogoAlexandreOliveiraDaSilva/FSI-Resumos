# Table of Contents

- [What is Encryption?](#what-is-encryption)
- [Classical Ciphers](#classical-ciphers)
  - [Ceaser Cipher](#ceaser-cipher)
  - [Substitution Ciphers](#substitution-ciphers)
  - [Frequency Letters Attacks](#frequency-letters-attacks)
  - [Rotor Machines](#rotor-machines)
  - [The One Time Pad](#the-one-time-pad)
  - [Kerckhoffs Principle](#kerckhoffs-principle)
  - [Never Use Your Own Crypto](#never-use-your-own-crypto)
- [Block Ciphers](#block-ciphers)
  - [What is a Block Cipher?](#what-is-a-block-cipher)
  - [Advanced Encryption Standards (AES)](#advanced-encryption-standards-aes)
  - [Internal of AES](#internal-of-aes)
  - [Modes of Operation](#modes-of-operation)
    - [Insecure Scheme with Secure Block Cipher](#insecure-scheme-with-secure-block-cipher)
      - [Electronic Code Book Mode (ECB)](#electronic-code-book-mode-ecb)
      - [Cipher Block Chaining](#cipher-block-chaining)
      - [Padding](#padding)
      - [Counter Block Mode](#counter-block-mode)
- [Keys and Randomness](#keys-and-randomness)
  - [Keys](#keys)
    - [Symmetric Crypto](#symmetric-crypto)
    - [Asymmetric Crypto](#asymmetric-crypto)
  - [Storage and Generation](#storage-and-generation)
    - [External Secure Hardware](#external-secure-hardware)
    - [Key Wrapping](#key-wrapping)
  - [Random](#random)
  - [Randomness Distribution](#randomness-distribution)
  - [Linux Systems](#linux-systems)
  - [Concrete Numbers](#concrete-numbers)
  - [Quantifying Security](#quantifying-security)

## What is Encryption?

- Encryption is one form of cryptography. There are many others.

- Encryption guarantees confidentiality.

- There are many kinds of encryption:
  - Symmetric = Same Key in both ends
  - Asymmetric
  - Authenticated
  - Homomorphic

- Encryption = Plaintext + Key -> CipherText

## Classical Ciphers

### Ceaser Cipher

- The key is a number

- To cypher we shift the letters in the alphabet by the Key.

- To decrypt we do the reverse shift by the same key.

- This is not secure because there are a `small number of keys`.

### Substitution Ciphers

- We can use different shifts on each letter.

- This will give us a larger number of keys to deal with.

- This is still not safe and will lead us to `Frequency letters attacks`

### Frequency Letters Attacks

- We use the frequency of the most used letters in the alphabet of a `specific language` we are decrypting.

- By gathering many ciphertexts and counting the frequency of the letters and mathcing with the frequency of the language. The letters can be matched together and the text deciphered.

### Rotor Machines

- Seems uninportant must watch a video on it.

### The one time pad

- You and the person you're communicating with each have a copy of a key.

- This thecnique combines each character of your message with the corresponding character in the key. This is usually done using XOR (exclusive OR) operation, where each bit in the message is combined with the corresponding bit in the key.

- The process of decryption is the same as the encryption.

- A problem of this method is the key's size easily expands. So how can we preshare it with someone and keep it stored.

### Kerckhoffs Principle

- Security through obscurity wich is a bad idea.

- This principle states that the methods must be public except the Key.

- This will make it easier to find errors and mistakes that can be fixed and promotes open source research.

### Never use your own crypto

- Very easy to make mistakes and very hard to find them.

## Block Ciphers

### What is a Block Cipher ?

- Block ciphers are a type of symmetric key encryption algorithm that processes input data in fixed-size blocks, typically of 64 or 128 bits instead of entire message.

- A key defines a permutation.

### Advanced Encryption Standards (AES)

- Is the most used block cipher since 2000 because of its performance and resistance to cryptanalysis.

### Internal of AES

- 128 bits block size.
- 4 * 4 arrays of 16-bits.

- There are different steps:
  
  - Substitute Bytes
  - Shift Rows
  - Mix Columns

### Modes of Operation

- Block Ciphers are primitive, not very useful.

- Encryption schemes have their own security definitions that can be built by block ciphers.

- That are secure assuming the block cipher is secure.

### Insecure Scheme with Secure Block Cipher

#### Electronic Code Book Mode (ECB)

- Break Message into plain text blocks p0,...,pn

- Last Block may need padding (problem)

- Let's imagine we cipher a photo there will be traces of the photo because all blocks are ciphered in the same manner so it will left traces...

### Cipher Block Chaining

- Cipher Block Chaining has an initialization vector (IV).

- Blocks depend on each other and are ciphered based on the previous block.

#### Padding

- Some schemes require message to be a multiple of blocks to cipher.

- To avoid ambiguity padding is always added.

### Counter Block Mode

- N that is the nonce must be unique.

- Here the block cipher is not applied to the message.

- The block to be XOR with the message is generated with the nonce.

- Any part of the data can be accessed efficiently

- Decryption/encryption can be parallelized.

## Keys and Randomness

### Keys

#### Symmetric Crypto

- Generated Uniformly at random.

- Or with Key Derivation Function takes an input (often a secret key or password) and produces a derived key. KDFs are designed to be computationally intensive and resistant to various attacks, including brute force and precomputation attacks.

#### Asymmetric Crypto

- Key generation = key pair.

- Private key holder generates both keys; publishes public key.

- Asymmetric keys are typically much larger.

### Storage and Generatiom

- Most sensitive material that are stored in different ways.

#### External Secure Hardware

- Hardware Security Module (HSM) -> Physical Device to safeguard and manage digital keys.

- Smart Card and criptography tokens.

#### Key Wrapping

- The process involves encrypting the key with another key, typically referred to as a wrapping key or key-encryption key (KEK).

- Password-based encryption (low security)
- Wrap with HW-protected master key (standard security)
- Master key stored in trusted hardware (high security)

### Random

- Randomness is a property of the key creation and not the key itself.

### Randomness Distribution

- In the context of randomness distributions, the uniform distribution over a finite set S represents a situation where each element in the set is equally likely to be chosen.

- Statistical Tests over distributions are not sufficient.

### Linux Systems

- dev/random
- This device file provides a stream of pseudorandom numbers. It is non-blocking and continuously reseeds itself from its internal entropy pool. It is suitable for most cryptographic purposes, and its output is typically considered secure for general use.

### Concrete Numbers

- A common size for keys is 128 bits , it's more likely to win the lotery then finding the key by bruteforce.

### Quantifying Security

- Lower bound on the work required for a successful attack.

- For n-bits security the best attack to break the scheme requires 2n steps.
