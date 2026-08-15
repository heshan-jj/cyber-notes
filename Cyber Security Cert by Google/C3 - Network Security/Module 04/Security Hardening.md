---
tags:
  - cybersecurity
  - hardening
  - network-security
  - google-cert
  - course-03
  - module-04
aliases:
  - Security Hardening
  - Attack Surface Reduction
  - Network Hardening
---

> [!abstract] Security Hardening
> **Security hardening** is the process of strengthening a system to reduce its vulnerability and **attack surface**. The attack surface is the total set of potential entry points that a threat actor could exploit. The goal is to minimize that surface as much as possible.

> [!note] Analogy
> Think of a network as a house. The attack surface is every door and window a robber could use. Security hardening is putting locks on all of them — and removing any that don't need to exist at all.

---

# What Can Be Hardened?

Security hardening applies to any system or device that can be compromised:

| Target | Examples |
|--------|---------|
| **Hardware** | Physical devices, servers, endpoints |
| **Operating Systems** | Windows, Linux, macOS configurations |
| **Applications** | Software settings, access permissions |
| **Networks** | Firewall rules, segmentation, port restrictions |
| **Databases** | Encryption standards, access controls |
| **Physical Spaces** | Security cameras, guards, badge access |

---

# Common Hardening Procedures

| Procedure | Description |
|-----------|-------------|
| **Patch Updates** | Apply software and OS updates to fix known security vulnerabilities |
| **Configuration Changes** | Tighten device or application settings to reduce the attack surface (e.g., longer password requirements, stronger encryption) |
| **Remove Unused Applications** | Eliminate software that isn't needed — each unused app is a potential vulnerability |
| **Disable Unused Ports** | Close network ports that don't need to be open — fewer open ports = smaller attack surface |
| **Reduce Access Permissions** | Grant users only the minimum access they need (principle of least privilege) |
| **Penetration Testing** | Simulate attacks to proactively identify and fix vulnerabilities |

> [!tip] Why Minimizing Helps
> Reducing the number of applications, devices, ports, and permissions also makes **network monitoring more efficient** — there's less to watch, and anomalies are easier to detect.

---

# Penetration Testing

> [!info] Pen Test
> A **penetration test (pen test)** is a simulated attack conducted to identify vulnerabilities in a system, network, website, application, or process.

- Results are documented in a **pen test report**
- The report tells security teams exactly where defenses failed and what type of vulnerabilities exist
- Organizations then build a **remediation plan** to address identified weaknesses

---

# Hardening as a Continuous Process

> [!important] Security Hardening is Ongoing
> Hardening is not a one-time setup. Security analysts perform **regular maintenance** to keep systems functioning securely as new vulnerabilities, software updates, and network changes emerge.

Regular hardening activities include:
- Reviewing and applying vendor patch updates
- Auditing access permissions and removing stale accounts
- Reviewing firewall rules and open ports
- Updating encryption standards for stored and transmitted data
- Running periodic penetration tests

---

# Exam Tips

> [!tip] Key Distinctions
> - **Attack surface** = all the ways an attacker could get in
> - **Hardening** = reducing the attack surface and strengthening defenses
> - **Patch** = update that fixes a known vulnerability
> - **Configuration change** = adjusting system settings to increase security
> - **Pen test** = simulated attack to find weaknesses *before* real attackers do
> - **Principle of least privilege** = give users only the access they need, nothing more

---

## Related Notes

- [[OS Hardening]]
- [[Firewalls]]
- [[Network and Components]]
- [[Subnetting]]