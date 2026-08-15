---
tags:
  - cybersecurity
  - networking
  - firewalls
  - google-cert
  - course-03
  - module-01
aliases:
  - Firewall Types
  - Stateful Stateless Firewall
  - NGFW
---

> [!abstract] Firewalls
> A **firewall** is a network security device that monitors traffic to and from a network, allowing or blocking it based on a defined set of security rules. Firewalls are a foundational layer of network defense.

---

# Firewall Types by Form Factor

| Type | Description |
|------|-------------|
| **Hardware Firewall** | A physical device that inspects data packets before they enter the network. The most basic form of network defense. |
| **Software Firewall** | A software program installed on a computer or server. Costs less than hardware and takes no physical space, but adds processing overhead to the host device. |
| **Cloud-Based Firewall** | Software firewalls hosted by a CSP (Firewall as a Service / FaaS). Rules are configured via the CSP's interface. Also protects cloud-hosted assets. |

> [!note] Software Firewall Scope
> - Installed on a **single computer** → protects only that machine
> - Installed on a **server** → protects all devices connected to that server

---

# Stateful vs. Stateless Firewalls

| Property | Stateful | Stateless |
|----------|----------|-----------|
| Tracks connection state | ✅ Yes | ❌ No |
| Filters based on behavior | ✅ Yes — proactively identifies suspicious patterns | ❌ No — only follows preconfigured rules |
| Stores analyzed data | ✅ Yes | ❌ No |
| Security level | Higher | Lower |

> [!warning] Stateless Firewalls Are Less Secure
> A **stateless firewall** only acts on rules set by the admin — it cannot detect suspicious trends or evolving threats. **Stateful firewalls** are preferred in most enterprise environments.

---

# Next Generation Firewalls (NGFW)

> [!info] NGFW
> A **Next Generation Firewall** provides everything a stateful firewall does, plus additional in-depth security capabilities.

Additional NGFW capabilities:
- **Deep Packet Inspection (DPI)** — examines the actual content of packets, not just headers
- **Intrusion Protection System (IPS)** — actively blocks detected threats
- **Cloud Threat Intelligence** — some NGFWs connect to cloud services to update rules against emerging threats in real time

---

# Port Filtering

Firewalls use **port filtering** to block or allow traffic based on port numbers, limiting unwanted communications.

| Port | Protocol | Common Use |
|------|----------|------------|
| 443 | HTTPS | Secure web traffic |
| 80 | HTTP | Unsecured web traffic |
| 25 | SMTP | Email transmission |
| 22 | SSH | Secure remote access |

> [!tip] Exam Tip
> Port filtering rules are configured by the organization's **security policy** — firewalls enforce the rules, they don't define them.

---

# Exam Tips

> [!tip] Key Distinctions
> - **Hardware** → physical device at the network edge
> - **Software** → installed on a host, protects that host or its connected devices
> - **Cloud-based** → hosted by a CSP, protects cloud assets too
> - **Stateless** → rule-based only, no memory
> - **Stateful** → tracks sessions, detects patterns
> - **NGFW** → stateful + DPI + IPS + threat intelligence

---

## Related Notes

- [[Network and Components]]
- [[Cloud]]
- [[Network Protocols]]
- [[OS Hardening]]
- [[Security Hardening]]