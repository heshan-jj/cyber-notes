---
tags:
  - cybersecurity
  - networking
  - IDS
  - IPS
  - SIEM
  - firewalls
  - google-cert
  - course-03
  - module-04
aliases:
  - Network Security Tools
  - IDS IPS SIEM
  - Defense in Depth
  - Intrusion Detection System
  - Intrusion Prevention System
---

> [!abstract] Network Security Applications
> Network security is built in **layers** — a concept called **defense in depth**. Each tool added further hardens the network. This note covers the four key security tools: **Firewalls**, **IDS**, **IPS**, and **SIEM**, and explains how they work together.

> [!note] Defense in Depth
> Adding layers of security incrementally hardens a network — from the minimum (just a firewall) to maximum protection (firewall + IDS/IPS + SIEM monitoring).

---

# The Four Security Layers

## Layer 1 — Firewall

> [!info] Firewall
> Allows or blocks traffic based on a defined set of rules, inspecting packet **headers** (port numbers, IP addresses).

- Sits at the network **perimeter** — first line of defense
- Standard firewalls inspect headers only
- **NGFWs** can also inspect **packet payloads** (deep packet inspection)
- Every system should have its own firewall regardless of the network-level firewall

See [[Firewalls]] for a complete breakdown of types (hardware, software, cloud, stateful, stateless, NGFW).

---

## Layer 2 — Intrusion Detection System (IDS)

> [!info] IDS
> An application that **monitors** system activity and **alerts** administrators when it detects signs of a possible intrusion — based on known attack signatures and/or anomalies.

**How it works:**
- Sniffs and analyzes data packets as they move across the network
- Compares traffic to a database of known attack signatures
- Some IDS systems also detect **anomalies** (unusual patterns that don't match known attacks)
- When a threat is found → **sends an alert** to the network administrator

**Position in network:** Placed **behind the firewall**, before the LAN — so it only analyzes traffic that already passed the firewall (reduces false positives / "noise").

| ✅ Advantage | ❌ Limitation |
|------------|--------------|
| Adds a detection layer behind the firewall | Only detects known attacks or obvious anomalies |
| Alerts admins to investigate | Cannot stop incoming traffic — detection only, no action |
| Reduces firewall noise | Sophisticated new attacks may not be caught |

---

## Layer 3 — Intrusion Prevention System (IPS)

> [!info] IPS
> An application that **monitors** system activity and **actively stops** malicious or anomalous activity — unlike an IDS, which only reports it.

**How it works:**
- Searches for known attack signatures and data anomalies
- When detected → **blocks the sender** or **drops the suspicious packets**
- Reports anomalies to security analysts simultaneously

**Position in network:** Sits **between the firewall and the internal network** — inline with traffic flow.

| ✅ Advantage | ❌ Limitation |
|------------|--------------|
| Actively stops threats — doesn't wait for admin action | **Inline appliance** — if it fails, the connection between the network and internet breaks |
| Disrupts risky data streams before they reach sensitive areas | **False positives** can cause legitimate traffic to be dropped |

> [!warning] IPS as an Inline Appliance
> Because the IPS is inline with traffic, it is a **single point of failure**. If it breaks or is overwhelmed, the entire network connection can go down.

---

## Layer 4 — SIEM (Security Information and Event Management)

> [!info] SIEM
> An application that **collects and analyzes log data** from multiple sources across the network and presents everything in a **single pane of glass** dashboard for real-time monitoring.

**Data sources SIEM aggregates:**
- IDS alerts
- IPS alerts
- Firewall logs
- VPN logs
- Proxy logs
- DNS logs

**What SIEM does NOT do:** It does not take action — it only **reports** and alerts. Analysts use the dashboard to decide how to respond.

Common SIEM tools:
| Tool | Type | Notes |
|------|------|-------|
| **Google Chronicle** | Cloud-native | Designed to retain, analyze, and search data at cloud scale |
| **Splunk Enterprise** | Self-hosted | Full data analysis platform with detailed dashboards |
| **Splunk Cloud** | Cloud-hosted | Same features as Enterprise, vendor-managed |

> [!note] SIEM + SOC
> Security analysts typically work in a **Security Operations Center (SOC)**, monitoring the SIEM dashboard and using their expertise to determine when events should be **escalated** to oversight.

---

## Full Packet Capture Devices

> [!info] Full Packet Capture
> Devices that record and analyze **all data transmitted** over a network — not just headers. Incredibly useful for detailed network investigations and for analyzing IDS-generated alerts.

---

# Comparison Table

| Tool | What It Does | What It Can't Do |
|------|-------------|------------------|
| **Firewall** | Allows/blocks traffic based on rules (header inspection) | Cannot inspect packet payloads (unless NGFW) |
| **IDS** | Detects and alerts on known attacks and anomalies | Cannot stop traffic — detection only |
| **IPS** | Detects and **actively stops** threats | Inline failure risk; false positives can block legit traffic |
| **SIEM** | Aggregates logs, generates centralized alerts and dashboards | Does not take any action — reports only |

---

# Exam Tips

> [!tip] Key Distinctions
> - **Firewall** → filter at the perimeter | **IDS** → detect behind firewall | **IPS** → detect + stop inline | **SIEM** → aggregate + alert from everything
> - **IDS** → alerts only, admin must act | **IPS** → acts automatically
> - **IPS** inline = single point of failure risk
> - **IDS false positives** = noise/alerts | **IPS false positives** = dropped legitimate traffic (worse)
> - **SIEM** = single pane of glass; does NOT stop threats

---

## Related Notes

- [[Firewalls]]
- [[Network Hardening]]
- [[Security Hardening]]
- [[OS Hardening]]
- [[Logs and SIEM Tools]]
- [[SIEM Dashboards (Splunk & Chronicle)]]