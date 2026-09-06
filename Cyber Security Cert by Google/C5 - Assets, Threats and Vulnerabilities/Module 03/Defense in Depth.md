---
tags:
  - cybersecurity
  - defense-in-depth
  - layered-defense
  - security-controls
  - castle-approach
  - google-cert
  - module-03
  - course-05
aliases:
  - The Castle Approach
  - Layered Defense
  - 5 Layers of Defense in Depth
  - DiD Model
---

> [!abstract] Defense in Depth
> **Defense in Depth (DiD)** is a security strategy that employs a **layered defense** model to protect assets and manage vulnerabilities. Borrowing from medieval castle architecture ("the castle approach"), DiD ensures that if an attacker breaches one protective barrier, subsequent defensive controls remain intact to block, detect, or delay the attack.

---

# The Castle Approach

In the Middle Ages, castles were designed with redundant, complementary defensive layers so no single breach compromised the stronghold:

```
┌─────────────────────────────────────────────────────────────┐
│  1. MOAT           ── Water barrier stops invading infantry │
│  2. STONE WALLS    ── Vertical barrier stops ground assault │
│  3. WATCH TOWERS   ── Elevated archers stop climbing/scaling│
└─────────────────────────────────────────────────────────────┘
```

> [!note] Core Philosophy
> No individual security control is 100% foolproof. Defense in depth assumes that individual defenses **will eventually fail**, requiring secondary and tertiary controls to prevent an incident from reaching critical data.

---

# The 5 Layers of Defense in Depth

In cybersecurity, organizations apply defense in depth across **five concentric layers** that information must navigate as it enters and leaves the environment:

```
                  ┌─────────────────────────────────────┐
                  │          1. PERIMETER LAYER         │
                  │   Authentication & Edge Filtering   │
                  └──────────────────┬──────────────────┘
                                     ▼
                  ┌─────────────────────────────────────┐
                  │           2. NETWORK LAYER          │
                  │     Authorization & Firewalls       │
                  └──────────────────┬──────────────────┘
                                     ▼
                  ┌─────────────────────────────────────┐
                  │          3. ENDPOINT LAYER          │
                  │     Host Devices & Antivirus        │
                  └──────────────────┬──────────────────┘
                                     ▼
                  ┌─────────────────────────────────────┐
                  │        4. APPLICATION LAYER         │
                  │      Software Logic & In-App MFA    │
                  └──────────────────┬──────────────────┘
                                     ▼
                  ┌─────────────────────────────────────┐
                  │            5. DATA LAYER            │
                  │  The Core Asset (PII, Cryptography) │
                  └─────────────────────────────────────┘
```

---

## 1. Perimeter Layer (External Access & Authentication)
- **Role:** The outermost defensive boundary separating internal corporate systems from the public internet.
- **Function:** Authenticates incoming user connections and filters out unauthorized external traffic.
- **Key Controls:** User credentials (usernames and passwords), perimeter edge routers, boundary gateways, DDoS mitigation.

---

## 2. Network Layer (Network Boundaries & Authorization)
- **Role:** Manages and restricts how traffic flows between internal segments and external networks.
- **Function:** Enforces authorization policies, prevents lateral movement, and monitors packet transit.
- **Key Controls:** Network firewalls, Network Intrusion Detection/Prevention Systems (NIDS/NIPS), Virtual Local Area Networks (VLANs), VPN tunnels.

---

## 3. Endpoint Layer (Device Protection)
- **Role:** Secures individual user workstations, physical machines, and compute resources connected to the network.
- **Function:** Protects vulnerable endpoints from malware execution, unauthorized local changes, and compromise.
- **Covered Devices:** Laptops, desktops, physical servers, virtual machines, and mobile devices.
- **Key Controls:** Antivirus (AV) software, Endpoint Detection and Response (EDR), host-based firewalls, device-level encryption.

---

## 4. Application Layer (Software Logic & Interfaces)
- **Role:** The software interfaces and platforms users directly interact with to access corporate tools and databases.
- **Function:** Embeds security controls directly into the application codebase and session workflow.
- **Key Controls:** In-app **Multi-Factor Authentication (MFA)** prompts (e.g., SMS/authenticator code verification), input validation, web application firewalls (WAF), secure session management.

---

## 5. Data Layer (The Core Asset)
- **Role:** The innermost layer housing the organization's "crown jewels"—the critical information itself.
- **Function:** Guarantees confidentiality, integrity, and availability even if all outer defensive rings are bypassed.
- **Protected Assets:** Personally Identifiable Information (PII), Sensitive PII (SPII), financial records, health records (PHI), and intellectual property.
- **Key Controls:** **Asset classification**, data-at-rest encryption, access control lists (ACLs), Data Loss Prevention (DLP) tools.

---

# Summary Table: The 5 Layers at a Glance

| Layer | Primary Focus | Core Function | Representative Controls |
| :--- | :--- | :--- | :--- |
| **1. Perimeter** | Edge & Entry | Authenticates external traffic | Usernames, passwords, boundary firewalls |
| **2. Network** | Traffic Routing | Authorizes internal/external flows | Network firewalls, VLANs, NIDS |
| **3. Endpoint** | User Devices | Shields laptops, desktops & servers | Antivirus, EDR, host firewalls |
| **4. Application** | Software Interfaces | Embeds security in app workflows | In-app MFA (SMS/OTP), input sanitization |
| **5. Data** | Crown Jewels | Protects sensitive data directly | Asset classification, encryption, DLP |

---

# Exam Tips

> [!tip] Key Distinctions & Quick Recall
> - **Castle Approach = Defense in Depth:** Multi-layered defense where failure of one control does not compromise the asset.
> - **The 5 Layers (Outside $\rightarrow$ Inside):**
>   1. **Perimeter** (Authentication / Edge)
>   2. **Network** (Authorization / Firewalls)
>   3. **Endpoint** (Laptops, Desktops, Servers / Antivirus)
>   4. **Application** (Software / In-app MFA)
>   5. **Data** (PII, Financials / Classification & Encryption)
> - **Layer Association Trap:**
>   - *Antivirus* belongs to the **Endpoint Layer**.
>   - *In-app SMS/OTP code prompt* belongs to the **Application Layer**.
>   - *Asset Classification & Encryption* belong to the **Data Layer**.

---

## Related Notes

- [[Vulnerability Management and Exploits]]
- [[Security Controls and Data Privacy]]
- [[Authentication and the AAA Framework]]
- [[Authorization, Separation of Duties, and OAuth]]
- [[Assets, Threats, and Vulnerabilities]]
- [[Cybersecurity Fundamentals]]
