---
tags:
  - cybersecurity
  - assets
  - threats
  - vulnerabilities
  - risk-management
  - google-cert
  - module-01
  - course-05
aliases:
  - Assets Threats and Vulnerabilities
  - Asset Management and Risk
  - Security Risk Factors
---

> [!abstract] Assets, Threats, and Vulnerabilities
> Security risk planning revolves around three foundational pillars: **Assets** (the what), **Threats** (the why), and **Vulnerabilities** (the how). Organizations protect these elements to preserve the **CIA Triad** (Confidentiality, Integrity, and Availability).

---

# Core Security Elements

All security risk plans are built upon analyzing how assets, threats, and vulnerabilities impact the CIA triad.

| Element | Security Role | Meaning | Analogy (Home Security) |
| :--- | :--- | :--- | :--- |
| **Asset** | The **What** | Any item perceived as having value to an organization | People, personal belongings, doors, windows |
| **Threat** | The **Why** | Any circumstance or event that can negatively impact assets | Burglar attempting entry, storms, stray ball |
| **Vulnerability** | The **How** | A weakness or flaw within an asset that can be exploited by a threat | Weak door lock, cracked wood, open window |

---

# Understanding Security Risk

> [!info] Definition
> **Risk** is anything that can impact the confidentiality, integrity, or availability of an asset.

### The Risk Formula

$$\text{Likelihood} \times \text{Impact} = \text{Risk}$$

- **Likelihood:** The probability or odds of a negative event occurring.
- **Impact:** The severity of damage or disruption if the event occurs.

> [!note] Analyst Focus
> While business impact depends on the asset and scenario, security analysts primarily focus on the **Likelihood** side of the equation by identifying, mitigating, and eliminating factors that increase the odds of a compromise.

### Why Organizations Calculate Risk

- Prevent costly and disruptive incidents
- Identify areas for process and system improvements
- Determine acceptable vs. tolerable levels of risk
- Prioritize high-value and critical assets for protection

---

# Risk Factors: Threats & Vulnerabilities

Risk occurs when a **threat** takes advantage of a **vulnerability**. Both are divided into two primary categories:

```
                  ┌──────────────────────┐
                  │     Risk Factors     │
                  └──────────┬───────────┘
            ┌────────────────┴────────────────┐
            ▼                                 ▼
   ┌─────────────────┐               ┌─────────────────┐
   │     Threats     │               │ Vulnerabilities │
   │ (Events/Causes) │               │ (Weaknesses)    │
   └────────┬────────┘               └────────┬────────┘
     ┌──────┴──────┐                   ┌──────┴──────┐
     ▼             ▼                   ▼             ▼
Intentional   Unintentional        Technical       Human
```

## 1. Categories of Threats

| Category | Description | Example |
| :--- | :--- | :--- |
| **Intentional** | Deliberate, purposeful malicious action | Malicious hacker exploiting a misconfigured web app |
| **Unintentional** | Accidental or environmental occurrence | An employee holding open a secure door (tailgating) |

## 2. Categories of Vulnerabilities

| Category | Description | Example |
| :--- | :--- | :--- |
| **Technical** | Flaws or misconfigurations in hardware, code, or systems | Unpatched software, misconfigured access permissions |
| **Human** | Behavioral mistakes, negligence, or lack of awareness | An employee misplacing an access badge in a parking lot |

---

# Asset Management & Inventories

> [!warning] The Fundamental Truth of Security
> **You can only protect the things you account for.**

- **Asset Management:** The continuous process of tracking organizational assets and the risks that affect them.
- **Asset Inventory:** A comprehensive catalog of all assets requiring protection (hardware, software, data, personnel, facilities).

### Purpose of an Asset Inventory
- **Resource Allocation:** Enables accurate provisioning of defenses and controls.
- **Anomaly Detection:** Alerts administrators when an asset goes missing or behaves unexpectedly.
- **Gap Identification:** Continuously uncovers unforeseen gaps in the security perimeter.

---

# Asset Classification

> [!info] Definition
> **Asset Classification** is the practice of labeling assets based on their sensitivity and organizational value. It governs whether an asset can be **disclosed**, **altered**, or **destroyed**.

| Classification Level | Access Scope | Description & Typical Data |
| :--- | :--- | :--- |
| **Public** | Anyone | Information intended for public distribution (marketing, press releases, website content). |
| **Internal-Only** | Organization-wide | Accessible to all employees, but prohibited from external sharing (company policies, internal directories). |
| **Confidential** | Project-specific | Restricted strictly to individuals working on a designated project (roadmap drafts, meeting minutes). |
| **Restricted** | Need-to-Know | Highly sensitive; unauthorized disclosure causes severe harm (Intellectual Property, PII, SPII, financial/health data). |

---

# Exam Tips

> [!tip] Key Distinctions & Quick Recall
> - **Risk Formula:** $\text{Risk} = \text{Likelihood} \times \text{Impact}$ (Analysts primarily reduce *Likelihood*).
> - **Asset = What** you protect | **Threat = Why** it's in danger | **Vulnerability = How** it can be breached.
> - **Threats:** *Intentional* (hackers) vs. *Unintentional* (accidents, bad weather).
> - **Vulnerabilities:** *Technical* (software bugs, misconfigurations) vs. *Human* (lost keys, phishing clicks).
> - **Asset Inventory:** Catalog of what exists (shepherd counting sheep).
> - **Asset Classification:** Sensitivity label determining disclosure, alteration, and disposal.

---

## Related Notes

- [[Cybersecurity Fundamentals]]
- [[Common Threats, Risks, and Vulnerabilities]]
- [[Threat Actors]]
- [[Controls, Frameworks, and Compliance]]
- [[NIST Risk Management Framework]]
