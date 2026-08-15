---
tags:
  - cybersecurity
  - cloud
  - hardening
  - networking
  - google-cert
  - course-03
  - module-04
aliases:
  - Cloud Network Hardening
  - Hardening Cloud Networks
  - Server Baseline Image
---

> [!abstract] Network Security in the Cloud
> Cloud networks require the same security hardening principles as traditional on-premise networks — but with key differences in approach. This note covers what makes cloud network hardening distinct and why organizations must still take responsibility even when using a CSP.

---

# Cloud vs. On-Premise Network Hardening

> [!important] Key Distinction
> Even though cloud servers are hosted by a CSP, **CSPs cannot prevent all intrusions** — especially from malicious actors, both internal and external to an organization. Cloud network hardening remains the organization's responsibility.

| Aspect | Traditional Network | Cloud Network |
|--------|---------------------|---------------|
| Physical control | Organization-owned | CSP-managed |
| Hardening responsibility | Fully the organization's | **Shared** (CSP + organization) |
| Key hardening tool | Baseline config per device | **Server baseline image** for all cloud server instances |
| Separation of data | Physical and logical | Logical (by service category) |

---

# Server Baseline Image

> [!info] Server Baseline Image
> A **server baseline image** is a standardized, secure snapshot of a cloud server's configuration that is applied to **all server instances** in the cloud environment.

**Purpose:**
- Provides a consistent security baseline across all cloud servers
- Allows you to **compare current cloud server data against the baseline** to detect unauthorized or unverified changes
- An unverified change (drift from baseline) may indicate an **intrusion or compromise**

> [!note] Baseline Image vs. OS Baseline
> In OS hardening, a baseline is a per-device configuration reference. In cloud hardening, a **server baseline image** is used at scale — applied uniformly across all cloud server instances. Same principle, cloud-native implementation.

---

# Data Separation in the Cloud

Similar to OS hardening, cloud data and applications must be kept **separated by service category**:

| Separation Rule | Why It Matters |
|-----------------|---------------|
| Old applications separate from new applications | Prevents legacy vulnerabilities from spreading to modern services |
| Internal functions separate from front-end applications | Limits user-facing exposure of back-end systems |

This mirrors the **network segmentation** principle used in traditional networks — isolate categories to limit blast radius.

---

# The Organization's Responsibility

> [!warning] Shared Responsibility ≠ No Responsibility
> The [[Cloud Security|shared responsibility model]] means the CSP secures the underlying infrastructure. But the **organization must still**:
> - Apply server baseline images and monitor for drift
> - Separate data and applications by category
> - Configure their cloud services securely
> - Monitor cloud operations for intrusions

> [!tip] Think of It This Way
> Just because you're renting a building doesn't mean you don't need locks on your own office doors.

---

# Exam Tips

> [!tip] Key Points
> - Cloud networks need hardening — CSPs can't prevent all intrusions
> - **Server baseline image** = the cloud equivalent of a per-device baseline config
> - Data separation in the cloud mirrors network segmentation
> - Shared responsibility = CSP handles the building; org handles what's inside
> - Drift from baseline = potential sign of intrusion

---

## Related Notes

- [[Cloud Security]]
- [[Cryptography and Cloud Security]]
- [[Security Hardening]]
- [[OS Hardening]]
- [[Network Hardening]]
- [[Cloud]]