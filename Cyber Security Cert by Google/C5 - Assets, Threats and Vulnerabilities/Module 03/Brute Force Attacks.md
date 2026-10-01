---
tags:
  - cybersecurity
  - brute-force
  - password-cracking
  - credential-stuffing
  - pass-the-hash
  - MFA
  - CAPTCHA
  - google-cert
  - module-03
  - course-05
aliases:
  - Brute Force Attacks Tactics and Tools
  - Dictionary Attacks and Credential Stuffing
  - Password Cracking Tools
  - Pass the Hash and Salting
---

> [!abstract] Brute Force Attacks
> **Brute force attacks** are repetitive, trial-and-error methods used by threat actors to guess passwords, encryption keys, or login credentials by exhausting combinations until a match is found. Organizations defend against these automated attacks using a combination of technical controls (such as **hashing with salting**, **MFA**, and **CAPTCHA**) and managerial controls like **account lockout policies**.

---

# What is a Brute Force Attack?

> [!info] Definition
> A **Brute Force Attack** is an algorithmic or manual trial-and-error technique used to crack passwords, bypass access controls, or decrypt ciphertext by systematically testing possibilities until the correct credentials or keys are discovered.

- **Analogy:** Trying every single numerical combination on a physical bike lock or safe dial until the lock clicks open.
- **The Modern Reality:** Because manual guessing could take decades, attackers deploy automated software and distributed botnets capable of submitting thousands of credential guesses per second.

---

# Brute Force Attack Tactics

Threat actors utilize distinct variations of brute force techniques based on the data and access available to them:

```
┌────────────────────────────────────────────────────────────────────────┐
│                      BRUTE FORCE ATTACK TACTICS                        │
├──────────────────────┬────────────────────────┬────────────────────────┤
│ SIMPLE BRUTE FORCE   │   DICTIONARY ATTACK    │ REVERSE BRUTE FORCE    │
│ Systematically tests │ Uses a pre-compiled    │ Tests ONE password     │
│ all character combos │ list of common words   │ across MANY accounts   │
├──────────────────────┼────────────────────────┼────────────────────────┤
│ CREDENTIAL STUFFING  │   PASS THE HASH (PtH)  │ EXHAUSTIVE KEY SEARCH  │
│ Reuses leaked breach │ Reuses stolen hashes   │ Systematically guesses │
│ pairs across sites   │ without cracking them  │ cryptographic keys     │
└──────────────────────┴────────────────────────┴────────────────────────┘
```

| Tactic | How It Works | Distinguishing Characteristic |
| :--- | :--- | :--- |
| **Simple Brute Force** | Systematically guesses all possible character, letter, number, and symbol combinations. | Pure trial-and-error without a pre-compiled wordlist. |
| **Dictionary Attack** | Tests passwords from a pre-compiled list of commonly used words, leaked credentials, or common phrases. | Much faster than simple brute force because it relies on human predictability. |
| **Reverse Brute Force** | Takes a single, common password (e.g., `Password123!`) and tests it across thousands of different usernames or systems. | Inverts the standard approach to bypass single-account lockout thresholds. |
| **Credential Stuffing** | Automatically injects stolen username/password pairs from previous external data breaches into other unrelated websites. | Exploits the widespread habit of **password reuse** across multiple platforms. |
| **Pass the Hash (PtH)** | Threat actors extract and reuse stolen, unsalted password hashes directly, bypassing the need to crack or decrypt the plaintext password. | Authenticates to network resources using the raw hash value itself. |
| **Exhaustive Key Search** | A brute force attack directed against encrypted ciphertext, systematically trying every possible mathematical decryption key. | Targets cryptography rather than account login forms. |

---

# Tools of the Trade

Security professionals and ethical hackers use standard password auditing and penetration testing tools to evaluate system resilience:

| Tool | Primary Purpose & Specialty |
| :--- | :--- |
| **Aircrack-ng** | A specialized network software suite used to assess Wi-Fi security and brute-force WEP/WPA/WPA2 handshakes. |
| **Hashcat** | An ultra-fast, GPU-accelerated password recovery and hash-cracking tool supporting hundreds of hashing algorithms. |
| **John the Ripper** | A versatile, command-line offline password security auditing tool and hash cracker. |
| **Ophcrack** | A Windows password cracker that leverages **Rainbow Tables** (precomputed hash lookup tables) to rapidly crack LM/NTLM hashes. |
| **THC Hydra** | A fast, multi-threaded network login brute-forcing tool supporting dozens of protocols (SSH, FTP, HTTP, Telnet, SMB). |

---

# Defensive & Prevention Measures

Organizations enforce defense in depth by combining technical mechanisms and administrative policies:

## 1. Hashing and Salting
- **Hashing:** A mathematical one-way function that transforms arbitrary data into a fixed-length string to verify integrity.
- **Salting:** An essential safeguard that appends a unique, randomly generated string of characters to a password **before** hashing.
  - *Why Salting Matters:* Ensures identical passwords produce completely different hash digests, rendering precomputed lookup tables (Rainbow Tables) and dictionary attacks ineffective.

```
Password ("Secret123") + Random Salt ("x9#vQ!") ──► Hashing Algorithm ──► Unique Salted Hash
```

---

## 2. Multi-Factor Authentication (MFA)
- Requires users to verify their identity using **two or more independent categories** (Something you know + Something you have/are).
- **Defense Impact:** Even if an attacker successfully brute forces a user's password, access is denied without physical possession of the second factor (e.g., hardware token, authenticator app OTP).

---

## 3. CAPTCHA (Challenge-Response)

> [!info] Definition
> **CAPTCHA** stands for **C**ompletely **A**utomated **P**ublic **T**uring test to tell **C**omputers and **H**umans **A**part.

- **Purpose:** Blocks automated brute-forcing scripts and bots by demanding challenges that require human perception.
- **Common Types:**
  1. *Distorted Text/Numbers:* Scrambled alphanumeric characters that a user must decipher and type into a box.
  2. *Image Grid Recognition:* Identifying and matching specific objects (e.g., crosswalks, traffic lights, buses) within a photo grid.

---

## 4. Password Policies & Account Lockouts
- **Managerial & Technical Controls:** Organizations enforce policies aligned with **NIST SP 800-63B-4** (Digital Identity Guidelines):
  - **Account Lockouts:** Automatically suspends an account after a specified number of consecutive failed attempts (e.g., 3–5 attempts), completely shutting down high-speed brute force scripts.
  - **Length & Complexity:** Enforcing minimum lengths (e.g., 8+ or 12+ characters) exponentially increases the keyspace and computational time required to crack a password.

---

# Exam Tips

> [!tip] Key Distinctions
> - **Attack Variations:**
>   - **Simple Brute Force:** Tries *all* combinations randomly/systematically.
>   - **Dictionary Attack:** Tries a *pre-compiled list* of common words.
>   - **Reverse Brute Force:** Tries *one password* against *many users*.
>   - **Credential Stuffing:** Reuses credentials stolen from *past external breaches*.
>   - **Pass the Hash:** Reuses the *raw password hash* without ever cracking the plaintext.
> - **Salting:** Appends random characters to passwords prior to hashing; defeats **Rainbow Tables**.
> - **CAPTCHA:** Automated Turing test designed specifically to block **automated bots/scripts**.
> - **Account Lockout:** The most effective operational control against real-time online brute force attempts.
> - **NIST SP 800-63B:** The primary federal benchmark for password and authentication guidelines.

---

## Related Notes

- [[Authentication and the AAA Framework]]
- [[Attack Vectors and the Attacker Mindset]]
- [[Cryptography and Public Key Infrastructure]]
- [[Security Controls and Data Privacy]]
- [[Common Cyber Security Attacks]]
- [[Attack Types]]
