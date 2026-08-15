---
tags:
  - cybersecurity
  - networking
  - cloud
  - hardening
  - google-cert
  - course-03
  - module-04
aliases:
  - Cloud Security Considerations
  - Cloud Security Challenges
  - Shared Responsibility Model
---

> [!abstract] Cloud Security
> Securing cloud environments introduces unique challenges that differ from traditional on-premise networks. Security analysts must understand cloud-specific risks — from identity misconfigurations to zero-day exploits — and know where the organization's responsibility begins and ends.

---

# Key Cloud Security Challenges

## 1. Identity Access Management (IAM)

> [!info] What is IAM?
> **Identity Access Management (IAM)** is a collection of processes and technologies that manages digital identities and controls how users can access cloud resources.

> [!warning] Common IAM Risk
> **Loose configuration of cloud user roles** is a frequent mistake. Improperly configured roles allow unauthorized users access to critical cloud operations — one misconfiguration can expose sensitive data or entire systems.

---

## 2. Configuration

Every cloud service must be **precisely configured** to maintain security and compliance. This challenge intensifies during **cloud migrations**, where every migrated process must be correctly reconfigured.

> [!caution] Misconfiguration = Breach
> Misconfigured cloud services are one of the **most frequent sources of security breaches** in cloud environments. Network administrators and architects must apply meticulous attention during setup and ongoing management.

---

## 3. Attack Surface

Each additional CSP service or application added to a network introduces its own set of risks and **expands the organization's attack surface**.

| Fact | Detail |
|------|--------|
| More services = more entry points | Each service is a potential vector for malware or unauthorized access |
| Offsetting factor | CSPs often use more secure defaults than traditional on-premise networks and face more rigorous scrutiny |
| Design matters | A well-designed cloud network using multiple services does **not** necessarily create more entry points |

---

## 4. Zero-Day Attacks

> [!info] What is a Zero-Day Attack?
> A **zero-day attack** exploits a previously unknown vulnerability — one for which no patch exists yet.

- CSPs are often **faster to learn about zero-day attacks** than traditional IT organizations
- CSPs can patch hypervisors and **migrate workloads** to other VMs to protect customers without downtime
- OS-level patching tools are also available for organizations to apply independently

---

## 5. Visibility and Tracking

| Aspect | On-Premise | Cloud |
|--------|------------|-------|
| Traffic visibility | Full — admins can sniff and inspect all packets | Partial — flow logs and packet mirroring tools available, but CSP server traffic is off-limits |
| Audits | Internal | CSPs pay for **third-party audits** to verify cloud security and identify vulnerabilities |

> [!note] Third-Party Audits
> CSP audits help organizations identify whether vulnerabilities originate from on-premise infrastructure or the CSP — and whether the CSP is meeting compliance standards.

---

## 6. Rapid Change

CSPs constantly update their platforms. These updates can affect:
- **Connection configurations** that organizations rely on
- **Security settings** that need to be re-evaluated after changes
- **IT processes** that must adapt to align with the CSP's new approach

> [!tip] Implication
> Each additional cloud service adds **complexity to the security profile** of the organization. More services = more security personnel and monitoring required.

---

# The Shared Responsibility Model

> [!important] Core Principle
> The **shared responsibility model** defines who is responsible for what in a cloud environment:
> - **CSP** → responsible for securing the **cloud infrastructure** (physical data centers, hypervisors, host OSes)
> - **Organization** → responsible for the **assets and processes** they store or operate *in* the cloud (configurations, applications, data)

> [!caution] Common Misconception
> Organizations sometimes assume the CSP handles security they haven't actually agreed to cover. A key example: **cloud application configuration** is the **organization's responsibility**, not the CSP's — even though the CSP secures the underlying infrastructure.

---

# Exam Tips

> [!tip] Key Distinctions
> - **IAM misconfiguration** → unauthorized users get access to cloud resources
> - **Attack surface** → grows with each added service; design matters
> - **Zero-day** → unknown exploit; CSPs patch hypervisors/migrate workloads
> - **Shared responsibility** = CSP secures the cloud *itself*; org secures what they put *in* it
> - **Third-party audits** → how CSPs prove their security posture to customers

---

## Related Notes

- [[Cloud]]
- [[Cryptography and Cloud Security]]
- [[Network Security in the Cloud]]
- [[Security Hardening]]
- [[OS Hardening]]
- [[Firewalls]]