# Table of Contents

## [Key Management](#key-management)

- [Public Key Criptography](#public-key-criptography)
- [Key Management](#key-management-1)
- [Key Management Closed Systems](#key-management-closed-systems)
- [Session Keys](#session-keys)
- [Limitations of Symmetric Criptography](#limitations-of-symmetric-criptography)

## [Assymetric Encryption and Digital Signatures](#assymetric-encryption-and-digital-signatures)

- [Public Key Encryption](#public-key-encryption)
- [Key Incapsulation Mechanisms](#key-incapsulation-mechanisms)
- [Building Public Key Encryption](#building-public-key-encryption)
- [The RSA Problem](#the-rsa-problem)
- [OAEP Encryption](#oaep-encryption)
- [Physical Signatures](#physical-signatures)
- [Digital Signatures](#digital-signatures)
- [Assymetric Message Encryption](#assymetric-message-encryption)
- [Assymetric Authenticity vs Message Authentication Codes](#assymetric-authenticity-vs-message-authentication-codes)
- [Application Context](#application-context)

## [Key Agreement](#key-agreement)

- [Setting](#setting)
- [Key Agreement Applications](#key-agreement-applications)
- [The Diffie-Hellman Protocol](#the-diffie-hellman-protocol)
- [Man in the Middle in the Real World](#man-in-the-middle-in-the-real-world)
- [Establishing Secure Channels](#establishing-secure-channels)
- [Instantiate Secure Channels](#instantiate-secure-channels)

## Key Management

### Public Key Criptography

- Is a type of cryptographic system that uses two key pairs: a public key and a private key. These keys are mathematically related, but information encrypted with one key can only be decrypted by the other key. The public key is shared openly, while the private key is kept secret.

### Key Management

- "Ad hoc" usually refers to a temporary or improvised solution. The expression n(n-1)/2 represents the number of unique pairwise connections between N participants, often used to calculate the number of keys needed in a fully connected network where each participant needs a unique key for communication.

- In symmetric cryptography, a common approach for multiple participants is to pre-distribute a set of secret keys. Each participant has a copy of the same set of keys.

### Key Management Closed Systems

- Centralized Solution wich means N participants = N keys.

### Session Keys

- Session keys =/= Long term keys

### Limitations of Symmetric Criptography

- If we can use symmetric criptography always it would be the best scenario.

- There are some problems with that:
  - Shared long term keys.
  - Non repudiation: Anyone with pre-shared key can produce an authenticated message.

## Assymetric Encryption and Digital Signatures

### Public Key Encryption

- Everyone with public key can encrypt, only the ones with secret key can decrypt.

### Key Incapsulation Mechanisms

- More ineficient then symmetric ciphers.
  - Thousands of bits vs 128 bits
  - Very small messages.

- Hybrid Paradigm:
  - 1. Sender generates symmmetric session key to encrypt p
  - 2. Sender gets pk, uses it to encrypt k
  - 3. Receiver gets two ciphertexts, corresponding to (1) and (2)

- This hybrid approach combines the efficiency of symmetric cryptography for bulk data encryption with the security of asymmetric cryptography for key exchange. It is commonly used in secure communication protocols like TLS.

### Building Public Key Encryption

- A one-way trapdoor function is a mathematical function that is easy to compute in one direction but computationally hard to invert.

- A trapdoor permutation is a specific type of one-way function where the function is also a permutation, meaning it is a one-to-one mapping.

- RSA is a well-known public key encryption algorithm that is based on the mathematical difficulty of factoring the product of two large prime numbers.

### The RSA Problem

- The public key consists of a modulus (product of two large primes) and an exponent.

- The private key consists of the same modulus and a different exponent, which is kept secret.

- Encrypting a message involves raising it to the public exponent modulo the modulus.

- Decrypting the ciphertext involves raising it to the private exponent modulo the modulus.

### OAEP Encryption

- The purpose of OAEP is to make the RSA encryption process more secure against certain cryptographic attacks, particularly those related to the mathematical properties of RSA. It adds randomness and complexity to the plaintext before encryption, making it more resistant to chosen plaintext attacks and other potential vulnerabilities.

### Physical Signatures

- Assurance of autorship and not tampering of message.

### Digital Signatures

- Same as phisical Signature, but entails some assumptions.

- Signature key must not be compromised and the algorithm most be secure.

### Assymetric Message Encryption

Only the one with sk can sign , anyone with pk can verify and the signature must go alongside the message.

### Assymetric Authenticity vs Message Authentication Codes

- They assure authenticity and integrity like MACs.

- But do not require a pre-shared secret key and so ensures not repudiation.

### Application Context

- Authentication and non-repudiation with digital signatures.

- Confidentiality with public key encryption.

## Key Agreement

### Setting

- Establish a cofidential session key (symmetric, authentic and confined).

- Compromised long term keys should not compromise confidential session keys.

### Key Agreement Applications

- Crucial for HTTPS.

- Private keys cannot be used to transport symmetric keys. (Forward Secrecy)

- Authentication by Digital Signatures.

### The Diffie-Hellman Protocol

- Both parties agree on public parameters, which include a large prime number (p) and a primitive root modulo p (g). These parameters are public and can be freely shared.

- Each party generates its private key:
  - Party A chooses a private key (a).
  - Party B chooses a private key (b).

- Each party computes its public key using the chosen private key and the public parameters:
  - Party A computes A=gamod  pA=gamodp and shares A publicly.
  - Party B computes B=gbmod  pB=gbmodp and shares B publicly.

- Both parties receive each other's public key. They can now compute the shared secret independently using their own private key and the received public key.

### Man in the Middle in the Real World

- Attacks are possible whenever public parameters are echanged via network.
- Attacks can happen to get PK, messages or parrameters such as the Diffie-Hellman.

### Establishing Secure Channels

- Secure channels entail Authenticated public keys → protect key agreement.
- Key Agreement protocols protect authenticity, ensures secrecy.
- Then we can use AEAD.

### Instantiate Secure Channels

- Designing a complete protocol is extremely complex even if components are secure.

- TLS 1.3 (soon) is the result of 30 years of evolution.
