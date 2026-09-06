---
tags:
  - cybersecurity
  - vulnerability-management
  - CVE
  - CVSS
  - NVD
  - MITRE
  - CNA
  - google-cert
  - module-03
  - course-05
aliases:
  - CVE and CVSS
  - Common Vulnerabilities and Exposures
  - NIST NVD and CVSS
  - CVE Numbering Authority
---

> [!abstract] Common Vulnerabilities, Exposures, and CVSS
> Vulnerability management is a global effort supported by open, publicly accessible repositories. The **Common Vulnerabilities and Exposures (CVE)** list, maintained by the **MITRE Corporation** and vetted by **CVE Numbering Authorities (CNAs)**, standardizes known security flaws. The **NIST National Vulnerability Database (NVD)** enriches these records using the **Common Vulnerability Scoring System (CVSS)** to quantify severity on a 0–10 scale.

---

# Vulnerabilities vs. Exposures

While closely related, cybersecurity draws a specific distinction between these two concepts:

| Term | Definition | Real-World Analogy |
| :--- | :--- | :--- |
| **Vulnerability** | An internal weakness or systemic flaw inherent to an asset. | An important paper document is fragile and easily misplaced. |
| **Exposure** | An operational mistake, misconfiguration, or action that leaves an asset accessible to a threat. | Placing that document next to an open window, exposing it to wind. |

---

# The CVE List & MITRE Corporation

> [!info] Definition
> The **Common Vulnerabilities and Exposures (CVE)** list is an openly accessible, standardized dictionary of publicly known cybersecurity vulnerabilities and exposures.

- **Created By:** The **MITRE Corporation** in 1999 (a U.S. government-sponsored non-profit R&D center).
- **Purpose:** Provides a universal, standardized identifier (CVE ID, e.g., `CVE-2023-XXXXX`) so vendors, researchers, and security teams worldwide can reference the exact same flaw without confusion.
- **Reporting:** Submitted by technology vendors, ethical hackers, security researchers, and the general public.

---

# CVE Numbering Authorities (CNAs)

> [!info] Definition
> A **CVE Numbering Authority (CNA)** is an authorized organization (e.g., major tech vendors, research labs, national CERTs) that volunteers to investigate, verify, assign IDs to, and publish eligible CVE records.

### The 4 Criteria for Assigning a CVE ID
To be assigned a formal CVE identifier, a reported flaw must strictly satisfy **four criteria**:

```
┌────────────────────────────────────────────────────────────────────────┐
│                      4 CRITERIA FOR A CVE ID                           │
├────────────────────────────────────────────────────────────────────────┤
│ 1. INDEPENDENCE     ── Can be patched independently of other bugs.    │
│ 2. RECOGNIZED RISK  ── Formally acknowledged as a potential hazard.   │
│ 3. EVIDENCE         ── Submitted with actionable proof / reproduction. │
│ 4. SINGLE CODEBASE  ── Impacts only one program's source code.        │
└────────────────────────────────────────────────────────────────────────┘
```

1. **Independence:** The vulnerability can be remediated on its own without requiring secondary fixes to other issues.
2. **Recognized Risk:** Acknowledged as a credible security hazard by the reporter or software vendor.
3. **Supporting Evidence:** Submitted with verifiable evidence (such as a proof of concept or reproduction report).
4. **Single Codebase:** The flaw specifically affects only one program's codebase (e.g., a bug in desktop Chrome that does not exist in the Android Chrome codebase).

---

# NIST NVD & CVSS Scoring

Once published to the CVE list, vulnerabilities are analyzed by databases such as the **NIST National Vulnerability Database (NVD)**.

> [!info] Common Vulnerability Scoring System (CVSS)
> A standardized vendor-neutral metric system used to calculate the severity, technical impact, and urgency of a vulnerability on a scale from **0.0 to 10.0**.

### CVSS Base Score
- **Base Score:** Measures the intrinsic qualities and potential severity of a vulnerability at the moment it is evaluated.
- **Immutable:** The base score does not change over time or vary across user environments.

### CVSS Severity Ratings

| Score Range | Severity Level | Operational Priority & Response |
| :--- | :--- | :--- |
| **0.0 – 3.9** | **Low** | Low threat; does not warrant emergency action; addressed during regular maintenance cycles. |
| **4.0 – 6.9** | **Medium** | Moderate risk; requires scheduled patching and system monitoring. |
| **7.0 – 8.9** | **High** | Significant danger; requires expedited remediation and prioritized patching. |
| **9.0 – 10.0** | **Critical** | **Immediate, urgent risk**; actively dangerous to organizational assets; requires immediate patching/workarounds. |

---

# Practical Use in Vulnerability Management

Security analysts rely on the CVE dictionary and CVSS metrics to answer two essential operational questions:
1. *"Is this vulnerability dangerous to our organization and assets?"*
2. *"How quickly must our team patch or mitigate it?"*

By combining CVSS severity ratings with their own **asset classification** (from C5 Module 1), analysts establish clear remediation priorities—patching critical-rated flaws on high-value databases before addressing low-rated cosmetic bugs.

---

# Exam Tips

> [!tip] Key Distinctions
> - **Vulnerability vs. Exposure:** Vulnerability = *systemic flaw*; Exposure = *operational mistake/misconfiguration*.
> - **CVE:** Created by **MITRE** in 1999; standardized dictionary of known vulnerabilities.
> - **CNA (CVE Numbering Authority):** Authorized entities that verify flaws and issue CVE IDs.
> - **4 CVE Criteria:** **Independent**, **Recognized risk**, **Supporting evidence**, **Single codebase**.
> - **CVSS Scale:** **0.0 to 10.0** (Managed by NIST NVD).
>   - **< 4.0** = Low risk (no emergency intervention).
>   - **$\ge$ 9.0** = Critical risk (urgent emergency patch needed).
> - **CVSS Base Score:** Intrinsic score evaluated at the time of discovery; does **not** change over time.

---

## Related Notes

- [[Vulnerability Management and Exploits]]
- [[Defense in Depth]]
- [[Assets, Threats, and Vulnerabilities]]
- [[Compliance and the NIST Cybersecurity Framework]]
- [[NIST Risk Management Framework]]
- [[Common Threats, Risks, and Vulnerabilities]]
