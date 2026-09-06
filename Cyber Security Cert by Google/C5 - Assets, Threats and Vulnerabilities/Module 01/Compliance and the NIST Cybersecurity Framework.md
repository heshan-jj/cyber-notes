---
tags:
  - cybersecurity
  - compliance
  - regulations
  - NIST
  - CSF
  - google-cert
  - module-01
  - course-05
aliases:
  - Compliance and NIST CSF
  - Security Compliance
  - NIST CSF Components
---

> [!abstract] Compliance and the NIST Cybersecurity Framework
> **Compliance** is the continuous process of adhering to internal standards and external government regulations. To establish, measure, and track compliance, organizations rely on voluntary frameworks like the **NIST Cybersecurity Framework (CSF)**, structured around three primary components: **The Core**, **Tiers**, and **Profiles**.

---

# Understanding Compliance & Regulations

Having a security plan is only the first step; organizations must ensure that everyone adheres to it.

> [!info] Definitions
> - **Compliance:** The process of adhering to internal standards (policies/procedures) and external regulations (laws).
> - **Regulations:** Mandatory rules established by a government or governing authority to dictate how something must be done.

### Why Compliance Matters

Maintaining compliance is critical, particularly in heavily regulated sectors like healthcare, finance, and energy:

| Driver | Impact & Significance |
| :--- | :--- |
| **Trust & Reputation** | Demonstrates credibility to clients, customers, and partners. |
| **Data Integrity & Safety** | Protects critical corporate and customer data from unauthorized exposure. |
| **Legal & Financial Penalties** | Non-compliance leads to devastating fines, sanctions, and lawsuits. |
| **Operational Longevity** | Avoids systemic business disruption caused by regulatory shutdowns. |

---

# The NIST Cybersecurity Framework (CSF)

The **NIST CSF** is a voluntary framework consisting of standards, guidelines, and best practices designed to help organizations manage and reduce cybersecurity risks to critical information and systems.

The CSF is composed of **three primary components**:

```
                 ┌────────────────────────────────┐
                 │     NIST CSF ARCHITECTURE      │
                 └───────────────┬────────────────┘
         ┌───────────────────────┼───────────────────────┐
         ▼                       ▼                       ▼
  ┌──────────────┐        ┌──────────────┐        ┌──────────────┐
  │   THE CORE   │        │    TIERS     │        │   PROFILES   │
  │ (Activities) │        │ (Maturity)   │        │ (Snapshots)  │
  └──────────────┘        └──────────────┘        └──────────────┘
```

---

## 1. The Core (Functions)

The **Core** provides a high-level, simplified checklist of security duties and desired outcomes, broken down into **five fundamental functions**:

| Function | Primary Focus | Relationship to Current Course |
| :--- | :--- | :--- |
| **Identify** | Understand and manage cybersecurity risk to systems, assets, data, and capabilities. | **Core of C5 Module 1:** Directly ties into asset inventory, classification, and risk assessment. |
| **Protect** | Develop and implement appropriate safeguards to ensure delivery of critical services. | **Next Focus:** Policies, access controls, data protection, and training. |
| **Detect** | Develop and implement activities to identify the occurrence of a cybersecurity event. | Continuous monitoring, log analysis, and intrusion detection. |
| **Respond** | Take appropriate action once an incident is detected. | Containment, incident mitigation, and analysis. |
| **Recover** | Restore capabilities or services that were impaired due to a cybersecurity incident. | Business continuity, disaster recovery, and system restoration. |

---

## 2. The Tiers (Measurement & Maturity)

> [!note] Measuring Performance
> **Tiers** provide a mechanism for organizations to measure how well their security practices align with each of the five Core functions.

Tiers are **not a simple pass/fail (yes/no) proposition**; they represent a spectrum of organizational maturity and risk management rigor:

| Tier Level | Designation | Characteristics |
| :--- | :--- | :--- |
| **Level 1** | **Partial / Passive** | Informal, reactive, bare-minimum standards; limited awareness of cybersecurity risk. |
| **Level 2** | **Risk-Informed** | Practices are approved by management, but not integrated organization-wide. |
| **Level 3** | **Repeatable** | Formal, organization-wide policies and standard operating procedures are consistently followed. |
| **Level 4** | **Adaptive** | Highly mature, proactive, and adaptive; continuous improvement informed by advanced threat intelligence. |

---

## 3. The Profiles (Snapshots in Time)

> [!info] Concept: Photos Over Time
> **Profiles** represent the alignment of an organization's requirements, objectives, risk appetite, and resources against the CSF Core.

- **Current State Profile:** A snapshot capturing the organization’s actual, present security posture ("where we are today").
- **Target State Profile:** A roadmap outlining the desired security posture ("where we want to be").
- **Gap Analysis:** Comparing profiles over time (like comparative photos of a growing tree) highlights progress, uncovered vulnerabilities, and areas needing resource reallocation.

---

# Exam Tips

> [!tip] Key Distinctions
> - **Compliance vs. Regulation:** Regulations are the government/industry laws; compliance is the act of obeying them.
> - **NIST CSF Triad:** **Core** (What you do) $\rightarrow$ **Tiers** (How maturely you do it) $\rightarrow$ **Profiles** (Snapshot of where you are vs. where you want to be).
> - **CSF Core Order:** **Identify $\rightarrow$ Protect $\rightarrow$ Detect $\rightarrow$ Respond $\rightarrow$ Recover** (IPDRR).
> - **Tiers are a spectrum (1 to 4):** Not a pass/fail grade; Level 1 is passive, Level 4 is adaptive.

---

## Related Notes

- [[NIST CSF Core Functions]]
- [[Elements of a Security Plan]]
- [[Assets, Threats, and Vulnerabilities]]
- [[Controls, Frameworks, and Compliance]]
- [[NIST Risk Management Framework]]
