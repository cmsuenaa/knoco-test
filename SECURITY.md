# Security Policy & GDPR Compliance Framework (DEP-2026)

At AERA, our commitment to clean, conscious, and non-destructive operations extends directly to how we safeguard our users' digital data[cite: 1]. This document outlines our active security policies, vulnerability reporting procedures, and the technical measures we employ to enforce absolute compliance with global data privacy frameworks (such as GDPR in Europe and equivalent APAC regulations)[cite: 1].

---

## 1. Security Architecture & Threat Mitigation

### 1.1 Data Encryption Standards
*   **Data in Transit:** All connections to AERA's web and mobile application endpoints are strictly encrypted using TLS 1.3. Legacy protocols (TLS 1.0, 1.1, and unencrypted HTTP) are rejected at the edge gateway layer.
*   **Data at Rest:** All databases, user credentials, and transaction records are encrypted utilizing the AES-256 cryptographic standard.
*   **Tokenization:** Payment card data is never processed or stored directly on AERA servers. Payment details are fully tokenized at the client level and routed directly to PCI-DSS Level 1 compliant payment partners (Stripe / Adyen).

### 1.2 Access Control & Infrastructure Security
*   **Zero Trust Architecture:** Access to production infrastructure, deployment pipelines, and backend databases is restricted via strict Multi-Factor Authentication (MFA) and Key-Based SSH access.
*   **Secret Management:** API keys, third-party credentials, and database passwords must never be committed to this repository. All credentials are dynamically injected at runtime using encrypted secret managers.

---

## 2. Multi-Jurisdictional Privacy & Compliance

### 2.1 GDPR (European Union) & Regional APAs Compliance
*   **Physical Database Isolation:** To comply with EU data sovereignty laws, all personally identifiable information (PII) for European users is physically stored and processed on isolated servers located within our Frankfurt, Germany cloud node.
*   **Zero Third-Party Marketing Tracking:** Consistent with AERA’s minimalist visual philosophy, our platforms do not deploy third-party advertising cookies, retargeting pixels, or demographic data-harvesting trackers[cite: 3].
*   **Right to Be Forgotten / Portability:** Automated API endpoints are available for users to immediately request complete deletion of their PII or download a portable JSON file of their transaction history.

### 2.2 APAC Data Privacy Alignment
*   Our platforms comply with Australia's Privacy Act 1988 (APPs) and Japan's Act on the Protection of Personal Information (APPI). All APAC user records are processed securely within dedicated local nodes in Tokyo and Sydney[cite: 1].

---

## 3. Vulnerability Reporting & Disclosure Policy

We welcome security research and appreciate responsible disclosure of potential vulnerabilities in our applications.

### 3.1 Reporting a Vulnerability
If you discover a security flaw or data-exposure vector within AERA's digital platform, please report it immediately:
1.  **Contact Email:** Send an encrypted email to `security@aera-skincare.com`.
2.  **PGP Key:** Use our public PGP Key (Fingerprint: `AE20 26DF B992 C062 EF12 8841 C7B1 A00F`) to encrypt your submission.
3.  **Include Details:** Provide a clear description of the vulnerability, steps to reproduce it, and any proof-of-concept (PoC) code.

### 3.2 Rules of Engagement
To protect our users and operations, we ask that you adhere to the following guidelines during your research:
*   **No Data Disruption:** Do not perform actions that could degrade, disrupt, or crash our live production platforms.
*   **No Unauthorized Extraction:** Do not attempt to view, modify, copy, or delete private user account data or transaction records.
*   **Coordinated Disclosure:** Allow the AERA Digital Experience & Platforms (DEP) security team a minimum of 30 days to investigate, patch, and verify the vulnerability before disclosing it publicly.

---

## 4. Automated Security Testing & CI/CD Guardrails

This repository runs continuous automated security checks on every pull request (PR) to prevent vulnerable code from reaching production:
*   **Static Application Security Testing (SAST):** Automated code scanners check every commit for pattern-based vulnerabilities (such as SQL injection, XSS vectors, or hardcoded secrets).
*   **Dependency Auditing:** Daily automated checks scan our software packages to flag and patch outdated or compromised third-party code libraries.
