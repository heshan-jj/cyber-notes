---
tags:
  - cybersecurity
  - cryptography
  - encryption
  - PKI
  - symmetric-encryption
  - asymmetric-encryption
  - digital-certificates
  - google-cert
  - module-02
  - course-05
aliases:
  - Cryptography and PKI
  - Public Key Infrastructure
  - Symmetric and Asymmetric Encryption
  - Ciphers and Digital Certificates
---

> [!abstract] Cryptography and Public Key Infrastructure
> **Cryptography** is the practice of transforming plaintext into ciphertext to prevent unauthorized access to sensitive information. Modern digital communications secure data and solve the key management and trust dilemmas through **Public Key Infrastructure (PKI)**, combining **symmetric encryption**, **asymmetric encryption**, and **digital certificates** issued by trusted **Certificate Authorities (CAs)**.

---

# Fundamentals of Cryptography

> [!info] Core Definitions
> - **Cryptography:** The process of transforming information into a form that unintended readers cannot understand.
> - **Plaintext:** Data in its original, readable, unencrypted form.
> - **Ciphertext:** Scrambled, unreadable data produced after encryption.
> - **Cipher:** The specific mathematical algorithm used to encrypt and decrypt information.
> - **Cryptographic Key:** A specific string of bits or secret mechanism that unlocks, scrambles, or unscrambles data within a cipher.

```
       ┌─────────────┐       Encryption (Cipher + Key)       ┌──────────────┐
       │  PLAINTEXT  ├──────────────────────────────────────►│  CIPHERTEXT  │
       │  "Readable" │                                       │ "Unreadable" │
       └─────────────┘◄──────────────────────────────────────┴──────────────┘
                             Decryption (Cipher + Key)
```

---

# Historical Foundations: Caesar's Cipher

Named after Julius Caesar in the 1st century BC, this is one of the earliest known shift ciphers.

- **How it Works:** Letters in the alphabet are shifted forward by a fixed key number (e.g., a shift key of **3** converts `"hello"` into `"khoor"`).
- **Major Flaws:**
  1. **Small Keyspace / Vulnerable to Brute Force:** With only 26 possible letter shifts in the English alphabet, an attacker can test all permutations in seconds using a **brute force attack** (trial-and-error guessing).
  2. **Single Key Distribution Problem:** Relies on a single shared secret key. If intercepted, stolen, or shared insecurely, all communication is instantly compromised.

> [!warning] Key Management Rule
> Cryptographic keys must never be stored in publicly accessible locations and must always be transmitted across a separate, secure channel away from the ciphertext itself.

---

# Modern Encryption: Symmetric vs. Asymmetric

Modern cryptography addresses historical flaws by employing two main encryption architectures:

```
    ┌─────────────────────────┐               ┌─────────────────────────┐
    │  SYMMETRIC ENCRYPTION   │               │  ASYMMETRIC ENCRYPTION  │
    │    (One Secret Key)     │               │    (Public/Private)     │
    └────────────┬────────────┘               └────────────┬────────────┘
                 ▼                                         ▼
         ┌───────────────┐                         ┌───────────────┐
         │ Fast & Simple │                         │ Secure & Open │
         └───────────────┘                         └───────────────┘
```

## 1. Symmetric Encryption (Single Key)
- Uses a **single shared secret key** for both encryption and decryption.
- **Analogy:** A lockbox with a single key. The sender uses the key to lock the box; the recipient must have a copy of that exact same key to open it.
- **Strength:** Extremely fast and computationally lightweight.
- **Weakness:** Secure key distribution—how to securely share the secret key across the open internet without an attacker intercepting it.

## 2. Asymmetric Encryption (Key Pairs)
- Uses a mathematically linked **key pair**:
  - **Public Key:** Freely distributed and accessible to anyone. Used exclusively to *encrypt* messages or data.
  - **Private Key:** Kept strictly secret by the owner. Used exclusively to *decrypt* data encrypted by the corresponding public key.
- **Analogy:** A drop-slot mailbox. Anyone on the street can drop a letter into the public slot, but only the homeowner with the private physical key can open the door and retrieve the mail.
- **Strength:** Eliminates the need to exchange private keys across unsecured channels.
- **Weakness:** Computationally expensive and significantly slower than symmetric algorithms.

---

# Comparison: Symmetric vs. Asymmetric Encryption

| Feature | Symmetric Encryption | Asymmetric Encryption |
| :--- | :--- | :--- |
| **Number of Keys** | 1 Shared Secret Key | 2 Mathematically Linked Keys (Public & Private) |
| **Speed** | Very fast (ideal for bulk data) | Slower (computationally intensive) |
| **Primary Use** | Bulk data transfer, file/database encryption | Initial handshakes, key exchange, digital signatures |
| **Key Distribution** | Difficult (must securely share the secret) | Simple (public keys are published openly) |

### The Hybrid Approach in Practice
Modern protocols (such as **HTTPS/TLS** and secure messaging apps) utilize a **hybrid approach**:
1. **Asymmetric encryption** secures the initial connection and safely negotiates a shared secret session key.
2. Once verified, **symmetric encryption** takes over for the remainder of the session to maximize transmission speed.

---

# Public Key Infrastructure (PKI) & Digital Certificates

While asymmetric encryption solves the key exchange problem, it introduces the **Trust Problem**: *How does a computer verify that a public key actually belongs to the authentic sender and not an imposter?*

> [!info] Public Key Infrastructure (PKI)
> An overarching framework of policies, hardware, software, and procedures that enables the secure creation, management, distribution, and revocation of digital keys and certificates.

---

## Digital Certificates & Certificate Authorities (CAs)

> [!info] Digital Certificate
> A tamper-proof digital credential (like a digital passport or ID badge) that formally binds a public key to the verified identity of an individual, organization, or website.

### How PKI Establishes Trust

```
 ┌──────────────┐   1. Requests Cert + Sends Public Key   ┌───────────────────────┐
 │ Organization ├────────────────────────────────────────►│ Certificate Authority │
 │  (Web Server)│                                         │         (CA)          │
 └──────┬───────┘                                         └───────────┬───────────┘
        │                                                             │
        │ 3. Installs Signed Certificate                              │ 2. Verifies ID &
        │◄────────────────────────────────────────────────────────────┘    Signs with CA's
        ▼                                                                  Private Key
 ┌──────────────┐        4. Sends Certificate during TLS Handshake    ┌───────────────┐
 │ Web Visitor  │◄────────────────────────────────────────────────────┤ Server Public │
 │  (Browser)   │───► Browser verifies signature using trusted CAs    │  Certificate  │
 └──────────────┘                                                     └───────────────┘
```

1. **Application:** An organization sends their domain details, business registration, and public key to a trusted **Certificate Authority (CA)**.
2. **Verification & Signing:** The CA verifies the organization's legal identity. Once validated, the CA encrypts the details and public key using the **CA's own private key**, creating a **digital signature**.
3. **Issuance:** The resulting **digital certificate** contains the site's public key, expiration date, and the CA's digital signature.
4. **Validation:** When visitors access the site, their web browser checks the certificate against pre-installed trusted root CAs to confirm authenticity.

---

# Exam Tips

> [!tip] Key Distinctions
> - **Plaintext $\rightarrow$ Ciphertext:** Scrambled via *Encryption*; restored via *Decryption*.
> - **Cipher vs. Key:** Cipher is the algorithm/rule; Key is the secret value that drives it.
> - **Caesar's Cipher:** 1st century BC shift cipher vulnerable to *brute force attacks* (only 26 possible keys).
> - **Symmetric:** 1 key, fast, used for bulk data (risk: key distribution).
> - **Asymmetric:** 2 keys (Public encrypts, Private decrypts), slower, solves key exchange.
> - **Hybrid Model:** Asymmetric sets up the connection; Symmetric does the heavy data lifting.
> - **Digital Certificate:** Digital ID badge verifying who owns a public key, signed by a trusted **Certificate Authority (CA)**.

---

## Related Notes

- [[Security Controls and Data Privacy]]
- [[Privacy Regulations, Audits, and Assessments]]
- [[Compliance and the NIST Cybersecurity Framework]]
- [[Cybersecurity Fundamentals]]
- [[Common Security Tools]]
