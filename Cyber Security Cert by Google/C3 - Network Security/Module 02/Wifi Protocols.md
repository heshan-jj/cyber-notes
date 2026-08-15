---
tags:
  - cybersecurity
  - networking
  - wifi
  - wireless
  - google-cert
  - course-03
  - module-02
aliases:
  - WiFi Security
  - WEP WPA WPA2 WPA3
  - Wireless Protocols
  - IEEE 802.11
---

> [!abstract] Wireless Communication Protocols
> **Wi-Fi** is a set of communication standards (IEEE 802.11) for wireless LANs. Wireless security protocols have evolved over the years to address successive vulnerabilities — from the weak WEP to the modern WPA3.

---

# The Evolution of Wireless Security

| Protocol | Year | Key Technology | Status |
|----------|------|----------------|--------|
| **WEP** | 1999 | RC4 (flawed implementation) | ❌ Deprecated — high-risk |
| **WPA** | 2003 | TKIP (Temporal Key Integrity Protocol) | ⚠️ Vulnerable to KRACK |
| **WPA2** | 2004 | AES + CCMP | ✅ Current standard — still KRACK-vulnerable |
| **WPA3** | 2018 | SAE (Simultaneous Authentication of Equals) | ✅ Most secure — fixes KRACK |

---

# WEP — Wired Equivalent Privacy

> [!warning] Deprecated — Do Not Use
> WEP was designed to give wireless connections the same privacy as wired ones. However, its encryption was **fundamentally flawed** — malicious actors can break WEP encryption. It is considered a **high-risk protocol**.

- Developed in **1999**
- Still encountered on old routers or legacy devices that haven't been updated
- Security analysts should recognize it to identify vulnerable network configurations

---

# WPA — Wi-Fi Protected Access

WPA was developed in **2003** as an emergency fix for WEP's failures.

- Uses **TKIP** — larger secret keys than WEP, harder to guess by trial and error
- Includes a **message integrity check** — detects and rejects altered or replayed transmissions
- Intended as a transitional fix with **backwards compatibility** to older hardware

> [!warning] KRACK Vulnerability
> WPA (and WPA2) are vulnerable to **KRACK (Key Reinstallation Attack)**.
> An attacker inserts themselves into the WPA authentication handshake and replaces the dynamic encryption key with a static one (all zeros) — effectively removing encryption entirely.

---

# WPA2

WPA2 was released in **2004** and remains the **current industry security standard** for Wi-Fi.

- Uses **AES (Advanced Encryption Standard)** — stronger than TKIP
- Uses **CCMP (Counter Mode Cipher Block Chain Message Authentication Code Protocol)** — provides encapsulation, message authentication, and integrity

## WPA2 Personal vs. Enterprise

| Mode | Best For | Key Difference |
|------|----------|----------------|
| **Personal** | Home networks | Single global passphrase applied to all devices; simple to set up |
| **Enterprise** | Business networks | Individualized, centralized access control; admins grant/revoke access; users never see encryption keys |

> [!tip] Enterprise Mode Security Advantage
> In **WPA2 Enterprise**, individual users never have access to the encryption keys — this prevents attackers from recovering keys from individual compromised devices.

---

# WPA3

WPA3 was released in **2018** to address WPA2's KRACK vulnerability.

Key improvements over WPA2:

| Feature | WPA3 Improvement |
|---------|-----------------|
| **KRACK fix** | Uses **SAE (Simultaneous Authentication of Equals)** — prevents attackers from inserting into the handshake |
| **Password security** | SAE prevents offline dictionary attacks — attackers can't download captured handshakes and crack them later |
| **Encryption strength** | 128-bit standard; **192-bit optional** in Enterprise mode |

---

# Exam Tips

> [!tip] Key Distinctions
> - **WEP** → oldest, broken, avoid
> - **WPA** → fixed WEP via TKIP, but still vulnerable to KRACK
> - **WPA2** → uses AES + CCMP, current standard, still KRACK-vulnerable
> - **WPA3** → fixes KRACK via SAE, strongest available
> - **KRACK** → Key Reinstallation Attack — exploits the WPA/WPA2 handshake
> - **SAE** → WPA3's answer to KRACK — Simultaneous Authentication of Equals
> - **WPA2 Personal** = one passphrase for everyone | **WPA2 Enterprise** = per-user access control

---

## Related Notes

- [[Network and Components]]
- [[Network Protocols]]
- [[VPN]]