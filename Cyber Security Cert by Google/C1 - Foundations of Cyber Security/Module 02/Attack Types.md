---
tags:
  - cybersecurity
  - attacks
  - attack-types
  - google-cert
  - module-02
aliases:
  - Attack Categories
  - Types of Cyber Attacks
---
> [!abstract] About This Note
> Cyberattacks can target passwords, people, physical devices, AI systems, supply chains, or cryptographic protocols. Each attack type maps to one or more **CISSP security domains**. See [[CISSP Domains]] for the full domain breakdown.

---

# Password Attacks

> [!info] Definition
> An attempt to gain unauthorized access to password-protected systems, accounts, or networks.

| Attack | Mechanism |
|--------|-----------|
| **Brute Force** | Tries every possible combination until the correct password is found |
| **Rainbow Table** | Uses a precomputed table of password hashes to crack passwords quickly |

**Prevention:** Strong passwords, MFA, account lockout policies, password managers

`CISSP Domain` — Communication & Network Security

---

# Social Engineering Attacks

> [!info] Definition
> Manipulating people into revealing confidential information or performing insecure actions.

| Attack | Channel |
|--------|---------|
| Phishing | Email |
| Smishing | SMS |
| Vishing | Voice call |
| Spear Phishing | Targeted email |
| Whaling | Executives specifically |
| Social Media Phishing | Social platforms |
| Business Email Compromise (BEC) | Impersonates business contacts |
| Watering Hole Attack | Compromised trusted websites |
| USB Baiting | Physical USB devices |
| Physical Social Engineering | In-person impersonation |

`CISSP Domain` — Security & Risk Management

---

# Physical Attacks

> [!info] Definition
> Attacks that involve physical devices or direct physical access to systems.

| Attack | Description |
|--------|-------------|
| Malicious USB Cable | Contains hidden attack hardware inside a normal-looking cable |
| Malicious Flash Drive | Delivers malware when plugged into a computer |
| Card Cloning | Copies magnetic stripe data from a payment card |
| Card Skimming | Steals card data using a reader hidden on a terminal |

`CISSP Domain` — Asset Security

---

# Adversarial Artificial Intelligence

> [!info] Definition
> Manipulating AI or machine learning systems to produce incorrect or harmful results.

- Fooling image recognition systems with subtle input changes
- Poisoning training datasets to corrupt model behaviour
- Bypassing AI-based threat detection tools

`CISSP Domains` — Communication & Network Security, Identity & Access Management

---

# Supply Chain Attacks

> [!info] Definition
> Attacks that compromise software, hardware, or services through trusted third-party vendors.

**Targets:** software updates, hardware manufacturers, cloud providers, third-party libraries

> [!warning] Why These Are Dangerous
> Supply chain attacks are difficult to detect because they exploit **trust in already-vetted vendors**. A single compromised supplier can impact hundreds of downstream organizations simultaneously.

`CISSP Domains` — Security & Risk Management, Security Architecture & Engineering, Security Operations

---

# Cryptographic Attacks

> [!info] Definition
> Attacks that target encryption algorithms or cryptographic protocols.

| Attack | What It Does |
|--------|-------------|
| **Birthday Attack** | Exploits hash collisions — two different inputs produce the same hash |
| **Collision Attack** | A specific form of birthday attack targeting hash functions |
| **Downgrade Attack** | Forces a system to use a weaker, older encryption protocol |

`CISSP Domain` — Communication & Network Security

---

# Attack Summary

| Attack Type | Main Target | CISSP Domain |
|-------------|-------------|--------------|
| Password Attack | User credentials | Communication & Network Security |
| Social Engineering | People | Security & Risk Management |
| Physical Attack | Physical devices | Asset Security |
| Adversarial AI | AI systems | Communication & Network Security, IAM |
| Supply Chain Attack | Third-party vendors | Multiple |
| Cryptographic Attack | Encryption | Communication & Network Security |

---

# Exam Tips

> [!tip] Key Distinctions
> - **Brute Force** → try everything &nbsp;|&nbsp; **Rainbow Table** → use precomputed hashes
> - **Social Engineering** → the attacker manipulates a *person*, not a system
> - **Supply Chain** → you trust the vendor; they're the vulnerability
> - **Birthday Attack** → about hash functions, not brute force
> - **Downgrade Attack** → forces weaker encryption

---

## Related Notes

- [[Common Cyber Security Attacks]]
- [[Threat Actors]]
- [[CISSP Domains]]
