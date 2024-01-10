# Table of Contents

- [Classifying Intruders](#classifying-intruders)
  - [Cyber Criminals](#cyber-criminals)
  - [State-Sponsered Organizations](#state-sponsered-organizations)
  - [Activists](#activists)
  - [Intruder Skill Activists](#intruder-skill-activists)
- [Denial of Service](#denial-of-service)
  - [What?](#what)
  - [Flooding Ping](#flooding-ping)
  - [Botnets](#botnets)
  - [UPD Flood attack](#upd-flood-attack)
  - [Reflection Attacks](#reflection-attacks)
  - [Echo Chargen](#echo-chargen)
  - [Smurf Attacks](#smurf-attacks)
  - [SYN Spoofing Attacks](#syn-spoofing-attacks)
  - [DNS Amplification Attack](#dns-amplification-attack)
  - [Karpersky DoS report](#karpersky-dos-report)
  - [Contermeasures](#contermeasures)
- [Firewalls](#firewalls)
  - [What?](#what-1)
  - [Managing what comes and goes](#managing-what-comes-and-goes)
  - [Capabilities and Limits](#capabilities-and-limits)
  - [Packet Filtering vs IPSEC](#packet-filtering-vs-ipsec)
  - [Stateful Packet Filter](#stateful-packet-filter)
  - [Application Proxy](#application-proxy)
  - [Firewall Policies](#firewall-policies)
- [Intrusion Detection System](#intrusion-detection-system)
  - [What is?](#what-is)
  - [Host Based IDS](#host-based-ids)
  - [Network Based IDS](#network-based-ids)
  - [IDS Methodologies](#ids-methodologies)
  - [Signature Detection](#signature-detection)
  - [Anomaly Detection](#anomaly-detection)

## Classifying Intruders

### Cyber Criminals

- Individuals or members of an organized crime group, with the goal of financial reward.

### State-Sponsered Organizations

- Groups of hackers sponsored by governments to conduct espionage or sabotage activities.

### Activists

- Individuals motivated by social or political cause.

### Intrueder Skill Activists

- Apprentice - Hackers with minimal technical skill, who primarily use existing
attack toolkits, known as script-kidies.

- Journeyman - Hackers with sufficient technical skills to modify and extend attack toolkits to use newly discovered, or purchased, vulnerabilities.

- Master - Attackers with high-level technical skills capable of discovering
brand new categories of vulnerabilities

## Denial of Service

### What ?

- Attack on the availability of services.
  - Such has network bandwiths
  - System resources
  - Applications resources

### Flooding Ping

- The goal of the attack is to overwhelm the capacity of the network connection to the victim organization.

- Traffic can be handled by higher capacity links on the path, but packets are discarded as capacity increases.

- Source of attacks are easily identifiable.

### Botnets

- A network of computers infected with malicious software (a.k.a. malware) that allows them to be controlled by an attacker (zombies).

- There exists attack as a service where people pay for Command and Control Servers to launch their attacks using computational power.

### UPD Flood attack

- Hacker sends UDP packets to a random port and generates illegitimate UDP packets that causes system to tie up resources sending back packets.

### Reflection Attacks

- Attacker sends packets to a known service on the intermediary with a spoofed source address on the actual victim.
- Intermediary responds to victim this will flood the link to the target system without alerting the intermediary.

### Echo Chargen

- Sends generated payload so that the victim sends back an echo in an endless loop.

- Requirement = Source adress spoofing

### Smurf Attacks

- Server broadcasts echo “from Alice” to the whole network, Alice is blasted by echo messages from a bunch of machines.

- Requirements = Source adress Spoofing and access to a server within a network.

### SYN Spoofing Attacks

- The attacker initiates a SYN flood attack by sending a SYN (synchronization) packet with a spoofed source address, which does not correspond to an actual existing source. As a result, the targeted server, upon receiving the SYN packet, responds with a SYN-ACK (synchronization-acknowledgment) expecting a final acknowledgment (ACK) from the supposed source. However, since the source does not exist and won't reply, the server experiences a timeout waiting for the ACK

### DNS Amplification Attack

- DNS requests with spoofed src IP address as the target this results in requests to multiple connected servers, flooding the target.

### Karpersky DoS report

- Kaspersky regularly publishes reports with statistical information.

### Contermeasures

- Prevention - Policies for resource consumption and backup resources.

- Attack detection and Filtering - Filter packets from the attacker.

- Attack traceback and identification

- Attack Reaction - Cleanup the system

## Firewalls

### What?

- Firewall decides what goes in and out of an internal network.

### Managing what comes and goes

- Based on access policy, types of traffic, adress ranges and protocols, Applications and content types.

### Capabilities and Limits

- Intrusion detection systems, firewalls, and Denial of Service (DoS) protection mechanisms play vital roles in network security, each with its distinct capabilities and limitations. Firewalls, as a first line of defense, define a single choke point in the network, serving as a crucial location for monitoring security events. Additionally, they provide a convenient platform for various internet functions, such as Network Address Translation (NAT). Firewalls can also serve as a foundation for IPSec in tunnel mode, enhancing overall network security. However, these security measures have their limitations. Firewalls, for instance, may be unable to protect against attacks that bypass their defenses. Furthermore, they might not offer comprehensive protection against internal threats, as devices like laptops, PDAs, or portable storage devices could be infected outside the corporate network and later introduced internally. Similarly, the vulnerability increases when dealing with improperly secured wireless LANs, as they can be accessed from outside the organization, posing a potential security risk.

### Packet Filtering vs IPSEC

- The incompatibility arises because IPsec encapsulates packets, adding an additional layer of headers for security purposes. These added headers may alter the original packet's characteristics, making it challenging for traditional packet filtering rules to accurately inspect and filter IPsec-protected traffic based solely on its outermost layer.

### Stateful Packet Filter

- Can do everything a packet filter can and keeps track on ongoing connections and misbheaviours.

### Application Proxy

- An application proxy, also known as an application layer proxy or application-level gateway, is a security component that operates at the application layer of the OSI (Open Systems Interconnection) model. It serves as an intermediary between client devices and the target server, managing communication on behalf of the clients. The primary purpose of an application proxy is to enhance security by providing advanced inspection and control over application-layer protocols.

### Firewall Policies

- Permissive = Allows by default and blocks some, easy to make mistakes.

- Restrictibe = Block by default; allow some , more secure but may affect availability.

## Intrusion Detection System

### What is ?

- An Intrusion Detection System (IDS) is a security technology designed to monitor and analyze network or system activities for signs of malicious behavior or unauthorized access. The primary purpose of an IDS is to identify and respond to security incidents, helping to ensure the confidentiality, integrity, and availability of information within a computer network.

### Host Based IDS

- Monitors Host activities for known attacks and suspicious behaviours, such as Buffer Overflow or Escalation of priviliges.

- Litle or no view of network activity.

### Network Based IDS

- Monitor activity at selected points of the network for known attacks.
- Examines network transport and application level protocols for attacks such as DoS, network probes, malformed packets.

### IDS Methodologies

- Signature Detection identifies known attacks with same known pattern or rule.
- Anomaly Detection that involves the collection of data relating to the behavior of
legitimate users over a period of time to find anomalies.

### Signature Detection

- Detects common known threats and is eficient but signatures must be kept up to date.

### Anomaly Detection

- Must measure during representative behavior
  - Cannot be measured during an attack
  - Normal is the statistical mean  
  - Must also allow for variance to know what is abnormal.
