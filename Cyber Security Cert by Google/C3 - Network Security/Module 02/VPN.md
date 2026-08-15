---
tags:
  - cybersecurity
  - networking
  - VPN
  - encryption
  - google-cert
  - course-03
  - module-02
aliases:
  - Virtual Private Network
  - VPN Protocols
  - WireGuard
  - IPSec
---

> [!abstract] VPNs — Virtual Private Networks
> A **VPN (Virtual Private Network)** is a network security service that changes your public IP address, masks your virtual location, and **encrypts your data in transit** — allowing private, secure communication over public networks like the internet.

---

# How VPNs Work

## The Problem

When you connect to the internet without a VPN, your ISP receives all your network requests — including your **private IP address** and **location**. If traffic is intercepted, an attacker could link your internet activity to your physical location and personal information.

## The Solution: Encapsulation

> [!info] Encapsulation
> **Encapsulation** is the process where a VPN service wraps your original (sensitive) data packet inside another data packet that routers can read — while keeping your actual data encrypted and private.

**Why encapsulation is needed:**
- If you simply encrypt a packet, routers can't read the destination IP — they can't route it
- Encapsulation adds a readable outer layer for routing while keeping the inner payload encrypted

## The Encrypted Tunnel

- VPN creates an **encrypted tunnel** between your device and the VPN server
- The encryption is unbreakable without the cryptographic key
- Your real IP address and virtual location are hidden from malicious actors

---

# VPN Types

| Type | Used By | Description |
|------|---------|-------------|
| **Remote Access VPN** | Individual users | Creates a secure tunnel between a personal device and a VPN server over the internet |
| **Site-to-Site VPN** | Enterprises | Extends a company's private network to remote office locations; commonly uses **IPSec** |

> [!warning] Site-to-Site Complexity
> Site-to-site VPNs are powerful for global organizations but are **significantly more complex** to configure and manage than remote access VPNs.

---

# VPN Protocols: WireGuard vs. IPSec

| Property | WireGuard | IPSec |
|----------|-----------|-------|
| Age | Newer | Older / more established |
| Code size | Smaller codebase — easier to audit | Larger, more complex |
| Performance | ✅ Faster download speeds | Slightly slower |
| Configuration | ✅ Simpler to set up | More complex |
| Open Source | ✅ Yes | Varies by implementation |
| OS Support | Growing | Widely supported by most OSes |
| Best for | Streaming, large file downloads, speed | Legacy compatibility, extensive testing history |

> [!tip] Choosing a Protocol
> The best VPN protocol depends on: **connection speed needs**, **existing network infrastructure compatibility**, and **individual vs. business requirements**. Most VPN providers offer both.

---

# Exam Tips

> [!tip] Key Distinctions
> - **VPN** = IP masking + encryption + encapsulation
> - **Encapsulation** = wrapping encrypted data in a routable packet
> - **Remote Access VPN** = for individual users connecting remotely
> - **Site-to-Site VPN** = for connecting entire office networks
> - **WireGuard** = newer, faster, simpler, open source
> - **IPSec** = older, more widely supported, more complex

---

## Related Notes

- [[Network Protocols]]
- [[Firewalls]]
- [[Cloud]]
- [[Subnetting]]
- [[Wifi Protocols]]