---
tags:
  - cybersecurity
  - networking
  - hardening
  - SIEM
  - google-cert
  - course-03
  - module-04
aliases:
  - Network Hardening
  - Network Security Hardening
  - Port Filtering
  - Network Segmentation Security
---

> [!abstract] Network Hardening
> **Network hardening** focuses on network-specific security practices: **port filtering**, **network access privileges**, **encryption**, and **log analysis**. Unlike OS hardening (which targets individual devices), network hardening secures the infrastructure that connects them.

---

# Regular Network Hardening Tasks

These tasks are performed on an ongoing, recurring basis:

| Task | Description |
|------|-------------|
| **Firewall rules maintenance** | Regularly review and update rules to reflect current security policy — remove outdated rules, add new ones |
| **Network log analysis** | Examine network logs to identify events of interest, anomalies, or signs of intrusion |
| **Patch updates** | Apply software and firmware patches to network devices as vendors release them |
| **Server backups** | Regularly back up server data to enable recovery after an incident |

## Network Log Analysis & SIEM

> [!info] Network Log Analysis
> The process of examining network logs to identify events of interest — threats, anomalies, or compliance issues.

Security teams use:
- **Log analyzer tools** — dedicated tools for parsing and searching logs
- **SIEM tools** — aggregate logs from multiple sources and present them in a **single pane of glass** dashboard

> [!note] SIEM Priority Reporting
> SIEM reports list new or ongoing network vulnerabilities scaled by **priority (high to low)**. High-priority vulnerabilities have shorter deadlines for mitigation. See [[Network Security Applications]] for a full SIEM breakdown.

---

# One-Time Network Hardening Tasks

These are configured once and updated only as needed:

## Port Filtering

> [!info] Port Filtering
> A [[Firewalls|firewall]] function that blocks or allows specific port numbers to limit unwanted communication.

**Guiding principle:** Only ports that are actively needed should be open. Any port not used by normal network operations should be **blocked by default**.

This protects against:
- Port scanning attacks
- Exploitation of services listening on unnecessary ports

---

## Network Access Privileges

Control which users and devices can access which parts of the network, following the **principle of least privilege** — grant only the minimum access required for each role.

---

## Network Segmentation

> [!info] Network Segmentation
> Dividing a network into **isolated subnets** for different departments or security zones.

**Benefits:**
- Issues in one subnet don't automatically spread across the entire organization
- Only specified users can access the part of the network their role requires
- Restricted zones containing highly classified data are separated from the rest of the network

*Example: A marketing subnet and a finance subnet — even if one is breached, the other remains isolated.*

> [!warning] Restricted Zone Rule
> Any restricted zone containing **highly classified or confidential data** must be **physically and logically isolated** from the rest of the network.

---

## Encryption

All network communication should be encrypted using the **latest encryption standards**.

| Data Zone | Encryption Level |
|-----------|-----------------|
| General network traffic | Standard modern encryption |
| Restricted zones (classified data) | **Higher** encryption standards — more difficult to crack |

> [!tip] Wireless Protocol Currency
> Networks should always use the **most up-to-date wireless protocols** (e.g., WPA3). Older wireless protocols (e.g., WEP) should be **disabled**. See [[Wifi Protocols]] for the full evolution.

---

# Exam Tips

> [!tip] Key Distinctions
> - **OS hardening** → secures individual devices | **Network hardening** → secures the infrastructure connecting them
> - **Port filtering** → block everything not needed; only open what's required
> - **Network segmentation** → isolates departments/zones; limits blast radius of a breach
> - **SIEM** → aggregates logs, generates priority-ranked alerts
> - **Encryption** → all communication; higher standards in restricted zones

---

## Related Notes

- [[Security Hardening]]
- [[OS Hardening]]
- [[Network Security Applications]]
- [[Firewalls]]
- [[Subnetting]]
- [[Wifi Protocols]]