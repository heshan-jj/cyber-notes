---
tags:
  - cybersecurity
  - access-controls
  - AAA-framework
  - authentication
  - MFA
  - SSO
  - biometrics
  - google-cert
  - module-02
  - course-05
aliases:
  - Authentication and the AAA Framework
  - AAA Framework - Authentication
  - Authentication Factors SSO and MFA
  - Multi-Factor Authentication and SSO
---

> [!abstract] Authentication and the AAA Framework
> **Access controls** regulate how users, systems, and devices interact with organizational resources to preserve the **CIA Triad**. These controls are structured around the **AAA Framework** (Authentication, Authorization, and Accounting). **Authentication** serves as the critical first barrier, verifying identity using three fundamental authentication factors, often paired with **Single Sign-On (SSO)** and **Multi-Factor Authentication (MFA)**.

---

# The AAA Framework Overview

Access controls manage access, authorization, and accountability across an enterprise through three interconnected functions:

```
┌────────────────────────┐      ┌────────────────────────┐      ┌────────────────────────┐
│     AUTHENTICATION     │ ───► │     AUTHORIZATION      │ ───► │       ACCOUNTING       │
│    "Who are you?"      │      │  "What can you do?"    │      │  "What did you do?"    │
└────────────────────────┘      └────────────────────────┘      └────────────────────────┘
```

| Component | Core Question | Primary Function |
| :--- | :--- | :--- |
| **Authentication** | *"Who are you?"* | Verifies the claimed identity of a user, service, or device attempting to access resources. |
| **Authorization** | *"What can you do?"* | Determines specific permissions, privileges, and access rights granted to an authenticated identity. |
| **Accounting** | *"What did you do?"* | Tracks, logs, and audits user activities and resource usage for accountability and compliance. |

---

# Authentication Systems

> [!info] Definition
> **Authentication** is the access control process that confirms whether a user, device, or application is genuinely who or what they claim to be by validating submitted credentials against records on file.

- **Match:** Access is granted.
- **Mismatch:** Authentication fails and access is denied.

---

# The Three Factors of Authentication

To prove identity, authentication systems rely on three primary factor categories:

| Factor Type | What It Represents | Examples | Security Strengths & Weaknesses |
| :--- | :--- | :--- | :--- |
| **Knowledge** | *Something you know* | Passwords, PINs, security questions | **Weakness:** Susceptible to brute force attacks, credential stuffing, phishing, and password reuse. |
| **Ownership** | *Something you have* | One-Time Passcodes (OTP) via SMS/Email, authenticator apps, hardware tokens, smart cards | **Strength:** Harder to steal remotely. Requires physical possession of the device or token. |
| **Characteristic** | *Something you are* | Biometrics: fingerprint scans, facial recognition, iris/retina scans | **Strength:** Extremely difficult to mimic, forge, or share. Provides high assurance of physical presence. |

---

# Single Sign-On (SSO)

> [!info] Definition
> **Single Sign-On (SSO)** is an access control technology that enables a user to log in once with a single set of credentials and gain access to multiple connected applications, websites, and services.

### Benefits of SSO
- **User Convenience:** Eliminates "password fatigue" and avoids repetitive re-authentication across different tools.
- **Operational Efficiency:** Reduces IT support overhead for forgotten password resets.
- **Centralized Revocation:** Disabling an account in the central directory instantly revokes access across all integrated services.

### The Critical Vulnerability of Standalone SSO
> [!warning] Single Point of Failure
> If an SSO implementation relies solely on a single factor (e.g., a username and password), a compromised password gives an attacker unrestricted access to **every system** connected to that SSO identity.

---

# Multi-Factor Authentication (MFA)

> [!important] Multi-Factor Authentication (MFA)
> A security measure requiring a user to verify their identity using **two or more independent authentication factors** before gaining access.

```
                    ┌─────────────────────────┐
                    │  MFA = 2+ Distinct      │
                    │      Factor Categories  │
                    └────────────┬────────────┘
         ┌───────────────────────┼───────────────────────┐
         ▼                       ▼                       ▼
┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐
│  Something You   │    │  Something You   │    │  Something You   │
│       KNOW       │ ┼  │       HAVE       │ ┼  │       ARE        │
│    (Password)    │    │   (Phone / OTP)  │    │   (Fingerprint)  │
└──────────────────┘    └──────────────────┘    └──────────────────┘
```

> [!danger] Common Exam Pitfall: Independent Factors
> Using two passwords or a password plus a security question is **NOT** MFA—both belong to the **Knowledge** factor (Two-Step Verification with 1 factor). True MFA mandates at least **two distinct categories** (e.g., Knowledge + Ownership).

### Layered Defense: Combining SSO with MFA
When deployed together, **SSO and MFA create an optimal security posture**:
- **SSO** provides convenience and seamless user workflows.
- **MFA** provides a robust, multi-layered defense ensuring that even if credentials are leaked, unauthorized access is blocked without the physical device or biometric factor.

---

# Exam Tips

> [!tip] Key Distinctions
> - **AAA Framework:** **Authentication** (*Who you are*) $\rightarrow$ **Authorization** (*What you can do*) $\rightarrow$ **Accounting** (*Tracking actions*).
> - **Authentication Factors:**
>   - **Knowledge** = *Something you know* (password, PIN).
>   - **Ownership** = *Something you have* (OTP token, smartphone, smart card).
>   - **Characteristic** = *Something you are* (biometrics, fingerprint, facial scan).
> - **MFA Requirement:** Must combine **two or more different factors** (e.g., password + OTP).
> - **SSO Benefit & Risk:** Seamless convenience, but creates a **single point of failure** unless secured with **MFA**.

---

## Related Notes

- [[Security Controls and Data Privacy]]
- [[Cryptography and Public Key Infrastructure]]
- [[Privacy Regulations, Audits, and Assessments]]
- [[Cybersecurity Fundamentals]]
- [[Common Security Tools]]
