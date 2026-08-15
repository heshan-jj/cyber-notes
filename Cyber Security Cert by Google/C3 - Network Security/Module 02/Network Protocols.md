---
tags:
  - cybersecurity
  - networking
  - protocols
  - google-cert
  - course-03
  - module-02
aliases:
  - Network Protocols
  - Communication Protocols
  - Security Protocols
  - Port Numbers
---

> [!abstract] Network Protocols
> A **network protocol** is a set of rules that governs how two or more devices communicate on a network — defining the order, structure, and timing of data exchange. Protocols are the "common language" that allows all devices worldwide to communicate.

> [!warning] Security Implication
> Some protocols have exploitable vulnerabilities. For example, **DNS** can be hijacked to redirect users from legitimate websites to malicious ones. Understanding protocols helps analysts identify where attacks may occur.

---

# The Three Protocol Categories

## 1. Communication Protocols

Govern the exchange, timing, and structure of data in transit.

| Protocol | Layer | Port | Description |
|----------|-------|------|-------------|
| **TCP** | Transport | — | Connection-oriented; uses 3-way handshake; reliable, retransmits lost data |
| **UDP** | Transport | — | Connectionless; faster but less reliable; used for real-time apps like video streaming |
| **HTTP** | Application | 80 | Client-server web communication; **insecure** (being replaced by HTTPS) |
| **DNS** | Application | 53 (UDP/TCP) | Translates domain names to IP addresses; switches to TCP for large replies |

---

## 2. Management Protocols

Used to **monitor**, **manage**, and **troubleshoot** network devices and activity.

| Protocol | Layer | Description |
|----------|-------|-------------|
| **SNMP** | Application | Monitors/manages network devices; can reset passwords and check bandwidth usage |
| **ICMP** | Internet | Reports data transmission errors; used for `ping` and network diagnostics |

---

## 3. Security Protocols

Ensure data is sent and received **securely** using encryption.

| Protocol | Layer | Port | Description |
|----------|-------|------|-------------|
| **HTTPS** | Application | 443 | Secure web communication using **SSL/TLS** encryption |
| **SFTP** | Application | 22 (via SSH) | Secure file transfer using SSH and **AES** encryption; commonly used with cloud storage |

> [!note] What Encryption Doesn't Hide
> HTTPS and SFTP encrypt **data content** but do **not** conceal the source or destination IP addresses. A malicious actor intercepting traffic can still see basic network routing info.

---

# Additional Protocols

## NAT — Network Address Translation

Allows multiple devices on a private network to share a single public IP address when communicating with the internet.

| IP Type | Assigned By | Unique? | Cost |
|---------|-------------|---------|------|
| Private | Router | Only within the private network | Free |
| Public | ISP / IANA | Globally unique | Leased |

**Private IP ranges:**
- `10.0.0.0 – 10.255.255.255`
- `172.16.0.0 – 172.31.255.255`
- `192.168.0.0 – 192.168.255.255`

> [!note] NAT Location in TCP/IP
> NAT operates at **Layer 2 (Internet)** and **Layer 3 (Transport)** of the TCP/IP model.

---

## DHCP — Dynamic Host Configuration Protocol

Automatically assigns IP addresses and network config to devices on a network.

- Assigns: **unique IP**, **DNS server address**, **default gateway**
- **Server** listens on UDP port **67**; **Client** listens on UDP port **68**

---

## ARP — Address Resolution Protocol

Translates **IP addresses → MAC addresses** for local network communication.

- Operates at the **Network Access Layer** of TCP/IP
- Each device maintains an **ARP cache** (IP ↔ MAC lookup table)
- ARP has **no port number** (it's a Layer 2 protocol)

---

## Email Protocols

| Protocol | Direction | Port (Unencrypted) | Port (Encrypted) | Notes |
|----------|-----------|-------------------|-----------------|-------|
| **POP3** | Incoming | TCP/UDP 110 | TCP/UDP 995 (SSL/TLS) | Downloads mail locally; may delete from server; no multi-device sync |
| **IMAP** | Incoming | TCP 143 | TCP 993 (TLS) | Keeps mail on server; supports multi-device sync; partial reading |
| **SMTP** | Outgoing | TCP/UDP 25 | TCP/UDP 587 (TLS) | Routes email from sender to recipient; port 25 often used by spam |

---

## Telnet & SSH

| Protocol | Port | Security | Notes |
|----------|------|----------|-------|
| **Telnet** | TCP 23 | ❌ Cleartext — insecure | Remote system access; legacy tool |
| **SSH** | TCP 22 | ✅ Encrypted | Secure replacement for Telnet; uses AES and other ciphers |

---

# Complete Port Reference

| Protocol | Port |
|----------|------|
| DHCP (server) | UDP 67 |
| DHCP (client) | UDP 68 |
| ARP | None |
| Telnet | TCP 23 |
| SSH / SFTP | TCP 22 |
| HTTP | TCP 80 |
| HTTPS | TCP 443 |
| DNS | UDP/TCP 53 |
| POP3 | TCP/UDP 110 (plain) / 995 (TLS) |
| IMAP | TCP 143 (plain) / 993 (TLS) |
| SMTP | TCP/UDP 25 (plain) / 587 (TLS) |

---

# Exam Tips

> [!tip] Key Distinctions
> - **TCP** → reliable, ordered, connection-required | **UDP** → fast, no guarantee
> - **HTTP** → port 80, insecure | **HTTPS** → port 443, encrypted
> - **DNS** → port 53 (UDP default, TCP for large replies)
> - **SSH** → port 22, encrypted | **Telnet** → port 23, cleartext
> - **POP3** downloads and may delete | **IMAP** syncs across devices
> - **SNMP** manages devices | **ICMP** reports errors (ping)

---

## Related Notes

- [[TCP Model]]
- [[Operations at the Network Layer]]
- [[Firewalls]]
- [[VPN]]
- [[Wifi Protocols]]