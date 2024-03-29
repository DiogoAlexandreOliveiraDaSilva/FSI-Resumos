# Table of Contents

## [Transport Layer Security](#transport-layer-security)

- [Web Security Considerations](#web-security-considerations)
- [What is SSL?](#what-is-ssl)
- [SSL and TLS](#ssl-and-tls)
- [TLS Architecture](#tls-architecture)
- [Handshake Protocol](#handshake-protocol)
- [Change Cipher Spec Protocol](#change-cipher-spec-protocol)
- [Alert Protocol](#alert-protocol)
- [Heartbeat Protocol](#heartbeat-protocol)
- [Hearth Bleed](#hearth-bleed)
- [HTTPS](#https)

## [Secure Shell](#secure-shell)

- [Secure Shell Protocol](#secure-shell-protocol)
- [SSH Protocols](#ssh-protocols)
- [SSH Authentication Methods](#ssh-authentication-methods)
- [SSH Connection Protocol](#ssh-connection-protocol)
- [Chanel Types](#chanel-types)

## [Internet Protocol Security](#internet-protocol-security)

- [IP Security (IPSec)](#ip-security-ipsec)
- [IPSEC applications](#ipsec-applications)
- [Benefits](#benefits)
- [Scope - Two main functions](#scope---two-main-functions)
- [IPSEC Architecture](#ipsec-architecture)
- [Internet Key Exchange](#internet-key-exchange)
- [Features of IKE key agreement](#features-of-ike-key-agreement)
- [IKE phase 2 - IPSEC security Association](#ike-phase-2---ipsec-security-association)
- [SSL vs TLS](#ssl-vs-tls)

## Transport Layer Security

### Web Security Considerations

- The Web is a client/server application that can be exploited as a launching pad into an agency.

- Security Flaws may be hidden.

### What is SSL?

- SSL stands for Secure Socket Layer. It is a protocol that ensures the secure communication of data between a user's web browser and a website's server. SSL is used to encrypt the data transmitted between the user and the server, preventing unauthorized access or interception of the information.

### SSL and TLS

- General-purpose system implemented as a set of protocols that rely on TCP to ensure message delivery guarantees.

- Transport Layer Security evolved from SSL.

- Handshakes , Change Cipher Spec, Alert Protocol and Heartbeat Protocol.

### TLS Architecture

- TLS connection is a peer to peer transient one session connection.

- TLS session is an association between client and server by handshake protocol, protected by crypto security parameters, used to avoid constant connections and expensive negotiation stages.

### Handshake Protocol

- It's the most complex part of TLS, allows mutual authentication, encryption negotiation and MAC algorithms.

- Made in four stages:
  - Stage 1 - Hello
  - Certificat Exchange and Verification
  - Key Agreement
  - Cipher Specs and keys (Server does the same)

### Change Cipher Spec Protocol

- Single one byte message  responsible for signaling the transition from non-secure communication to encrypted communication.

### Alert Protocol

- Conveys TLS-related alerts to peer entity, with compressed and encrypted messages.
- Two byte messages
  - First = Severity
  - Second = Specifies

### Heartbeat Protocol

- A periodic signal is generated by hardware or software to indicate normal operation, or to synchronize with other parts of a system.

- Relies on heartbeat requests and responses.

### Hearth Bleed

- The vulnerability stemmed from a flaw in the Heartbeat extension, allowing attackers to read sensitive data from the memory of affected systems. Exploiting Heartbleed did not leave traces, making detection challenging.

- Fake heartbeat requests.

### HTTPS

- Combination of HTTP and SSL to implement secure communication between a Web browser and a Web server

## Secure Shell

### Secure Shell Protocol

- Authenticated encrypted path to the OS, to acess remote resources.
- Protects against spoofing attacks and the modfication of data.

### SSH Protocols

- Transport Layer - Server authentication, integrety and confidentiality.
- User Authentication Protocol - Authenticates the client-side user to the platform.
- Connection Protocol - multiplexes the encrypted tunnel into several logic channels.

### SSH Authentication Methods

- Public key, server receives pk signed with private key, the server receives checks key for authentication and checks signature.

- Password in plain text trough TLP.

- Hostbased Authentication is performed on the client’s host rather than
the client itself
- This method works by having the client send a signature created with the private key of its host.
- Instead of verifying the client identity, the host identity is checked wich provides group anonimity.

### SSH Connection Protocol

- Runs on top of the TLP (Transport Layer Protocol)
- Uses a channel mechanism.

### Chanel Types

- Session : Remote execution of a program that may be a shell, an application.

- X11 :  Window System, a computer software system and network protocol that provide a GUI for networked computers.

- Forward tcpip - Remote port forwarding

- Direct tcpip - Local port forwarding

## Internet Protocol Security

### IP Security (IPSec)

- Various application security mechanisms exist:
  - MIME
  - SSL / HTTPS
  - etc ...

### IPSEC applications

- IPSec thrives in applications where the same security is always necessary, and the same security techniques can be applied for all applications.

### Benefits

- When integrated into a firewall or router, this security measure fortifies the protection of all traffic traversing the network perimeter.

- This transparency enables the design of applications under the assumption of secure channels, albeit with potential limitations on flexibility.

- The system confronts challenges such as securely storing encrypted messages within applications and incorporates redundant security mechanisms.

### Scope - Two main functions

- The Internet Protocol Security (IPSec) framework encompasses two primary functions: Encapsulated Security Payload (ESP) and Authentication Header (AH). ESP serves as a multifunctional component, incorporating both authentication and encryption capabilities, as well as a key exchange function. On the other hand, AH is dedicated solely to authentication.

### IPSEC Architecture

- Key exchange Management (IKE)
- Two security header extensions ESP and AH
- Two Modes of Operation - Transport Mode and Tunnel Mode

- Transport mode = add information/security to the original packet.
- Tunnel mode = protect the original packet by encapsulating it into a new IP packet.

- In transport mode the ip header is visible to an attacker in contradiction to tunnel mode.

### Internet Key Exchange

- Two Stages IKE and IPSEC security association:
  - Phase 1 is comparable to SSL/TLS session - handshake, select cryptographic parameters,choose a master secret.
  - Phase 2 is comparable to SSL/TLS connection - ephemeral, uses Phase 1 to select encryption/MAC keys.

### Features of IKE key agreement

- Firstly, the utilization of cookies effectively thwarts clogging attacks, distinct from conventional HTTP cookies. Secondly, it meticulously specifies global parameters for the Diffie-Hellman process. A nonce is incorporated to guard against replay attacks, ensuring the integrity of the exchanged information. The algorithm facilitates the secure exchange of public key values within the Diffie-Hellman framework. Additionally, it includes authentication measures to counteract potential man-in-the-middle attacks, enhancing the overall robustness of the cryptographic system.

### IKE phase 2 - IPSEC security Association

- A one-way connection between a sender and a receiver that affords security services to the traffic carried on it.

- In any IP packet, the SA is uniquely identified by the Destination Address in the IPv4 and IPv6 header, and the Security Parameters Index in the extension head (ESP or AH).

- Three parameters:
  - Security parameters index - 32 bit unsigned integer
  - Security protocol identifier. (Extension Head)
  - IP destination adress.

### SSL vs TLS

- SSL/TLS operates within the socket layer in user space, providing functionalities such as encryption, integrity, and authentication. Its design is relatively simple, featuring an elegant(-ish) specification that facilitates secure communication over the internet. On the other hand, IPSec functions at the network layer within the operating system space. Similar to SSL/TLS, it encompasses encryption, integrity checks, authentication, and other security features. However, IPSec is known for its inherent complexity, involving intricate protocols and mechanisms to ensure comprehensive network security.

- IPSec: OS must be aware, but not the applications.
- SSL/TLS: Applications must be aware, but not the OS.
