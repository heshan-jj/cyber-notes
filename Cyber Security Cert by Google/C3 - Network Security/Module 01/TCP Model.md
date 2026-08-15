---
tags:
  - cybersecurity
  - networking
  - TCP-IP
  - OSI
  - google-cert
  - course-03
  - module-01
aliases:
  - TCP/IP Model
  - OSI Model
  - Network Layers
---

> [!abstract] The TCP/IP Model
> The **TCP/IP model** is a four-layer framework used to visualize how data is organized and transmitted across a network. It helps analysts identify which layer an attack or disruption affects. The **OSI model** is a related 7-layer model used for communication between network professionals.

---

# The Four Layers of TCP/IP

## Layer 1 — Network Access Layer

> [!info] Also called the Data Link Layer
> Deals with the **physical transmission** of data packets — cables, hubs, modems, and NICs.

- Handles creation and transmission of data packets on the physical network
- **ARP (Address Resolution Protocol)** operates here — maps IP addresses to MAC addresses for local communication
- MAC addresses are used to identify hosts on the same physical network

---

## Layer 2 — Internet Layer

> [!info] Also called the Network Layer
> Responsible for **routing packets** between different networks using IP addresses.

Key protocols at this layer:

| Protocol | Purpose |
|----------|---------|
| **IP (Internet Protocol)** | Addresses and routes packets from source to destination across networks |
| **ICMP (Internet Control Message Protocol)** | Reports errors and status of data packets; used for `ping` and network diagnostics |

---

## Layer 3 — Transport Layer

> [!info] Responsible for end-to-end delivery between two systems.

| Protocol | Type | Characteristics |
|----------|------|-----------------|
| **TCP** | Connection-oriented | Reliable, uses 3-way handshake, retransmits lost data — used when accuracy matters |
| **UDP** | Connectionless | Fast, no connection setup, no retransmission — used for real-time applications like video streaming |

### TCP 3-Way Handshake

```
Client → Server : SYN
Server → Client : SYN/ACK
Client → Server : ACK
```

---

## Layer 4 — Application Layer

> [!info] Corresponds to the Application, Presentation, and Session layers of the OSI model.
> Defines how network applications communicate and how data packets interact with receiving devices.

Common protocols at this layer:

| Protocol | Port | Use |
|----------|------|-----|
| HTTP | 80 | Web traffic (insecure) |
| HTTPS | 443 | Web traffic (secure) |
| SMTP | 25 / 587 | Email sending |
| SSH | 22 | Secure remote access |
| FTP | 21 | File transfer |
| DNS | 53 | Domain name resolution |

---

# TCP/IP vs. OSI Model

| TCP/IP Layer | OSI Equivalent Layers |
|---|---|
| Application | Application (7), Presentation (6), Session (5) |
| Transport | Transport (4) |
| Internet | Network (3) |
| Network Access | Data Link (2), Physical (1) |

> [!note] When to Use Which Model
> - **TCP/IP** — practical model used in real network implementation and this course
> - **OSI** — used by network professionals to **communicate about threats and incidents** at a specific layer

---

# Exam Tips

> [!tip] Layer Mnemonics and Key Facts
> - **Network Access** → physical hardware, ARP, MAC addresses
> - **Internet** → IP addresses, routing, ICMP
> - **Transport** → TCP (reliable) vs. UDP (fast)
> - **Application** → protocols your apps use (HTTP, DNS, SSH)
> - TCP = connection, reliability | UDP = speed, no guarantee
> - Security disruptions are analyzed by layer — knowing which layer is affected tells you what was targeted

---

## Related Notes

- [[Network Protocols]]
- [[Operations at the Network Layer]]
- [[Network and Components]]
- [[Firewalls]]