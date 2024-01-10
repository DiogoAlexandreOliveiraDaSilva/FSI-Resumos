# Table Of Contents

- [Authenticating Public Keys](#authenticating-public-keys)
  - [Why Public Keys Infrastructures?](#why-public-keys-infrastructures)
  - [Context for PKI](#context-for-pki)
  - [Simple Explanation](#simple-explanation)
  - [Trusted Computing Base](#trusted-computing-base)
- [Public Key Certificates](#public-key-certificates)
  - [What?](#what)
  - [Concreteness of Certificates](#concreteness-of-certificates)
  - [Verifying Certificates](#verifying-certificates)
- [Public Key Infrastructures](#public-key-infrastructures)
  - [What?](#what-1)
  - [Operational Transactions/Management](#operational-transactionsmanagement)
  - [Meeting the Requirements](#meeting-the-requirements)
  - [Initializing PKI's](#initializing-pkis)
  - [Certificate Chains](#certificate-chains)
  - [Certificate Revocation](#certificate-revocation)
  - [Certificate Revocation Lists](#certificate-revocation-lists)
  - [Alternative: Pretty Good Privacy](#alternative-pretty-good-privacy)
- [Authentication](#authentication)
  - [Access Control](#access-control)
  - [Authentication Methods](#authentication-methods)
  - [Protocols](#protocols)
  - [Authentication Protocols](#authentication-protocols)
  - [Replays Attacks](#replays-attacks)
  - [Challenge Response](#challenge-response)
- [Attacks](#attacks)
  - [Password Attacks](#password-attacks)
  - [Password Guessing](#password-guessing)
  - [Phishing](#phishing)

## Authenticating Public Keys

### Why Public Keys Infrastructures ?

- Public key criptography presuposes authentic public keys.
- Otherwise we get Man-In-The-Middle Attacks.
- This can be solved with Public Key Infrastructures.

### Context for PKI

- PKI provides a framework for managing digital certificates, which are crucial for authentication and encryption in secure communication. Legal coverage is often necessary to establish the validity and enforceability of digital signatures and certificates in legal contexts.

### Simple Explanation

- Bob sends pkB and a certificate.
- Certificate signed by Charlie, says that pkB is owned by Bob.
- Alice trusts Charlie ⇒ Alice trusts pkB is Bob's.

### Trusted Computing Base

- The Trusted Computing Base (TCB) is the foundational set of hardware, firmware, and software components in a computer system responsible for enforcing a security policy. It comprises critical elements like the operating system, kernel, and hardware, working to isolate and protect against unauthorized access. The TCB is designed to be minimal, undergoes security evaluation, and is crucial for maintaining the overall integrity and security of a computing system.

- It's a security assumption.

## Public Key Certificates

### What?

- A public key certificate, often simply referred to as a digital certificate, is a digital document that binds a cryptographic key pair to an individual, device, or entity.

### Concreteness of Certificates

- Signing a message is never enough.
- Certificate Authority must fix and validate all data reffered to in the certificate.

### Veifying Certificates

- Verify if PK and identity match the certificate.
- Verify if current time is within validity window.
- Verify MetaData
- Verify if CA is trusted.
- Obtain the pkCA and verify certificate signature.

## Public Key Infrastructures

### What ?

- Allows user identity to be ensured by certificate, produced by a trusted CA.
- Binds pk to User.
- Well defined responsibilities for all Users.

### Operational Transactions/Management

- Certificates are distributed and stored:
  - In public repositories or included by applications and OS.
  - Transfered by protocols HTTPS,FPT,MIME.
  - Must be encoded in a way to ensure interoperability.(It ensures that diverse systems can understand, interpret, and interact with each other)

### Meeting the Requirements

- Users must establish connection with the CA.
- User gets pkCA from another certificate and can use it to verify signatures to be able to use the according pk.

### Initializing PKI's

- OS's come wit allot of CA certificates pre-installed.

### Certificate Chains

- Root certificates are the baseline for trust, they are self assigned. It starts the chain of certificate verifications.

- Anyone can generate a root certificate, so the CA must be trusted.

### Certificate Revocation

- Certificates are always invalid after their validity period.
- We may need to revoke a certificate if Secret keys are lost, CA's become compromised or Metadata stops being valid.

### Certificate Revocation Lists

- Revoking can be done by Certificate revocation lists, this are black-lists published by the CA.

- Trusted Service Provider List (TSL)
  - Frequently updated certificate white-list, used in small comunities like banking.
- Online Certificate Status Protocol (OCSP)
  - Secure server checks revocation, used in organizational contexts.
- Certificate pinning
  - Individually managed by webservers/browsers/apps.

### Alternative: Pretty Good Privacy

-Pretty Good Privacy (PGP) is a cryptographic software suite that addresses privacy and authentication in data communication. It employs a decentralized "web of trust" model where users establish trust through direct secure channels or indirect vetting by trusted individuals. PGP uses short public key fingerprints, often printed on business cards, to facilitate authentication

## Authentication

### Access Control

- Determines whether an user should be allowed access to a system.
- Deciding what actions a user can perform in the system.

### Authentication Methods

- Passwords and Security Questions

- SmartCards and CryptoTokens

- FingerPrint and Other Biological Data

### Protocols

- Human protocols - Rules followed in human interactions.
- Networking protocols - Rules followed in networked communication systems.
- Security Protocol - the (communication) rules followed in a security application.

### Authentication Protocols

- ATM machine Protocol
  - Insert ATM card.
  - Enter Pin
  - Is the Pin Correct?

- Enter the NSA
  - Insert badge into reader
  - Enter Pin
  - Is the Pin Correct?

### Replays Attacks

- A replay attack is a type of network attack in which an attacker intercepts and retransmits data that was previously captured, often with the aim of impersonating the legitimate user.

### Challenge Response

- Implement challenge-response mechanisms where the server challenges the client with a random value, and the client includes this value in its response. This helps ensure that the communication is real-time and not a replay of a previous interaction.

## Attacks

### Password Attacks

- In person, keylogger, packet snifing, server hacking.

### Password Guessing

- Keyloggers
- Dictionary Attacks

### Phishing

- HTTP - URL tampering to present an incorrect server, without the certificate.

- HTTPS - Change website to a “similar looking one"
