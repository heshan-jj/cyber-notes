---
tags:
  - cybersecurity
  - hardening
  - OS
  - brute-force
  - google-cert
  - course-03
  - module-04
aliases:
  - Operating System Hardening
  - Brute Force Attacks
  - OS Security
  - Patch Updates
---

> [!abstract] OS Hardening
> **OS hardening** is a set of procedures that maintains and strengthens operating system security. Because the OS is the first program loaded on a computer and acts as the interface between hardware and software, one insecure OS can compromise an entire network.

---

# OS Hardening Tasks

## Regular / Recurring Tasks

| Task | Description |
|------|-------------|
| **Patch Updates** | Apply OS and software updates from vendors as soon as they are released to fix known security vulnerabilities |
| **Baseline Configuration Updates** | After applying patches, update the **baseline image** to reflect the current secure state |
| **Hardware & Software Disposal** | Properly wipe old hardware; remove unused software applications to eliminate unnecessary vulnerabilities |
| **Password Policy Enforcement** | Regularly review and update password policies |

> [!warning] Patch Timing Is Critical
> When a vendor publishes a patch, malicious actors immediately know the vulnerability it fixes — and they target systems still running the unpatched version. Patch **as fast as possible**.

> [!info] Baseline Configuration
> A **baseline configuration** is a documented set of specifications for a system, used as a reference for all future builds, updates, and comparisons. If unusual activity is suspected, the current config is compared to the baseline to detect unauthorized changes.

---

## One-Time / Initial Setup Tasks

- Configuring device settings to meet a secure **encryption standard**
- Setting up **MFA (Multi-Factor Authentication)**
- Disabling unnecessary ports, services, and accounts

---

# Password Policies

Strong password policies are a core OS hardening control.

| Policy Element | Example |
|----------------|---------|
| Minimum length | 8+ characters |
| Complexity | Must include uppercase, number, and symbol |
| Account lockout | Account suspended after N failed login attempts |
| MFA requirement | Verify identity in 2+ ways |

> [!info] MFA — Multi-Factor Authentication
> MFA requires verification using **two or more** of the following:
> - **Something you know** — password, PIN
> - **Something you have** — ID card, hardware token, one-time password (OTP)
> - **Something you are** — fingerprint, facial recognition (biometrics)

---

# Brute Force Attacks

> [!warning] Definition
> A **brute force attack** is a trial-and-error method of discovering private credentials by systematically trying combinations until the correct one is found.

| Type | Method |
|------|--------|
| **Simple Brute Force** | Try every possible combination of usernames and passwords manually or with tools |
| **Dictionary Attack** | Use a curated list of common passwords and previously leaked credentials to guess faster |

---

# Assessing Vulnerabilities — VMs and Sandboxes

Before attacks occur, analysts use isolated environments to safely test suspicious files and simulate incidents.

## Virtual Machines (VMs)

> [!info] Virtual Machines
> VMs are **software-based versions of physical computers** that run in an isolated environment — preventing malicious code from affecting the host system.

**Benefits:**
- Run and contain potentially malicious code safely
- Can be deleted and replaced with a clean image after testing
- Easy to switch between multiple VMs
- Can revert to previous states

> [!warning] VM Risk
> There is a small risk that malware can **escape virtualization** and affect the host machine. Always treat VM-tested malware as potentially dangerous.

---

## Sandbox Environments

> [!info] Sandboxes
> A **sandbox** is a testing environment where software can be executed in isolation from the live network.

**Uses:**
- Testing patches before deployment
- Identifying and fixing bugs
- Evaluating suspicious software or files
- Simulating attack scenarios

> [!warning] Sandbox Evasion
> Sophisticated malware authors can detect sandbox and VM environments and **behave harmlessly** inside them — only activating on real systems.

---

# Brute Force Prevention Measures

| Measure | How It Helps |
|---------|-------------|
| **Salting & Hashing** | Hashing converts passwords to one-way values; **salting** adds random characters to increase hash complexity — making precomputed attacks (rainbow tables) ineffective |
| **MFA / 2FA** | Even with the correct password, the attacker can't access the account without the second factor |
| **CAPTCHA / reCAPTCHA** | Distinguishes human users from automated bots running brute force tools |
| **Password Policies** | Enforces complexity, rotation, reuse limits, and account lockout after failed attempts |

---

# Exam Tips

> [!tip] Key Distinctions
> - **Patch update** = software fix addressing a known vulnerability
> - **Baseline configuration** = documented reference state for a system
> - **Simple brute force** = try everything | **Dictionary attack** = use a wordlist of likely passwords
> - **VM** = isolated software computer | **Sandbox** = isolated test environment
> - **Hashing** = one-way | **Salting** = adds randomness to the hash
> - **MFA** = 2+ factors | **2FA** = exactly 2 factors

---

## Related Notes

- [[Security Hardening]]
- [[Firewalls]]
- [[Network Protocols]]
- [[Wifi Protocols]]