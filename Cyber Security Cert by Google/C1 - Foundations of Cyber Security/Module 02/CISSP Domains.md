---
tags:
  - cybersecurity
  - CISSP
  - google-cert
  - module-02
aliases:
  - CISSP
  - Eight Security Domains
---
![[Pasted image 20260802192521.png]]
> [!abstract] About This Note
> The **CISSP** (Certified Information Systems Security Professional) framework defines 8 security domains that collectively cover every aspect of an organization's security program. These domains are referenced throughout the Google Cybersecurity Certificate.

---

# The 8 CISSP Security Domains

## 1. Security & Risk Management

Defines the security goals, policies, and risk management practices of an organization.

**Covers:** Security governance, compliance, legal and regulatory issues, business continuity planning (BCP), risk frameworks

---

## 2. Asset Security

Protects physical and digital assets throughout their entire lifecycle.

**Covers:** Data classification, ownership and handling, privacy, secure disposal

---

## 3. Security Architecture & Engineering

Focuses on designing systems and infrastructure with security built in from the start.

**Covers:** Secure design principles, cryptography, security models, vulnerability assessment

---

## 4. Communication & Network Security

Protects the networks and transmission channels through which data moves.

**Covers:** Network architecture, firewalls, VPNs, IDS/IPS, wireless security, encrypted communications

---

## 5. Identity & Access Management (IAM)

Ensures only the right people can access the right systems and data.

**Covers:** Authentication (passwords, MFA, biometrics), authorization, access control models (RBAC, MAC, DAC), Single Sign-On (SSO)

---

## 6. Security Assessment & Testing

Identifies weaknesses before attackers can exploit them.

**Covers:** Penetration testing, security audits, vulnerability scanning, log review and analysis

---

## 7. Security Operations

Handles day-to-day security monitoring, investigation, and incident response.

**Covers:** Incident response, digital forensics, disaster recovery, threat intelligence, SIEM

---

## 8. Software Development Security

Embeds security into the software development lifecycle (SDLC) so vulnerabilities are caught early.

**Covers:** Secure coding practices, code review, DevSecOps, application vulnerabilities (SQL injection, XSS, etc.)

---

# Quick Reference

| # | Domain | Core Question |
|---|--------|--------------|
| 1 | Security & Risk Management | What are our policies and how do we manage risk? |
| 2 | Asset Security | What do we own and how do we protect it? |
| 3 | Security Architecture & Engineering | Are our systems designed securely? |
| 4 | Communication & Network Security | Is our data safe in transit? |
| 5 | Identity & Access Management | Who can access what, and how do we verify them? |
| 6 | Security Assessment & Testing | Where are our weaknesses? |
| 7 | Security Operations | How do we detect and respond to incidents? |
| 8 | Software Development Security | Is our code built securely? |

---

# Attack Types Mapped to Domains

> [!note] Cross-Reference with [[Attack Types]]
> Each attack type in the course corresponds to one or more CISSP domains.

| Attack Type | CISSP Domain |
|-------------|-------------|
| Password Attacks | Communication & Network Security |
| Social Engineering | Security & Risk Management |
| Physical Attacks | Asset Security |
| Adversarial AI | Communication & Network Security, IAM |
| Supply Chain Attacks | Risk Management, Architecture, Operations |
| Cryptographic Attacks | Communication & Network Security |

---

# Exam Tips

> [!tip] How to Remember the Domains
> - **Domain 1** → policies and laws
> - **Domain 2** → classify and protect data
> - **Domain 3** → build it right from the start
> - **Domain 4** → protect data on the wire
> - **Domain 5** → authentication and authorization
> - **Domain 6** → find the weaknesses first
> - **Domain 7** → the SOC — monitor, detect, respond
> - **Domain 8** → security belongs in every line of code

---

## Related Notes

- [[Attack Types]]
- [[Common Cyber Security Attacks]]
- [[Threat Actors]]
- [[CISSP 8 Security Domains]]

