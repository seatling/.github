# Security Policy

At Seatling, cryptographic rigor, hardware isolation, and developer trust are our highest priorities. We welcome responsible security research and vulnerability disclosures across our client SDKs, cryptographic routines, and hosted services.

---

## Reporting a Vulnerability

**Please DO NOT open a public GitHub issue for security vulnerabilities.**

Send your encrypted or private report directly to:

📧 **[mail@seatling.app](mailto:mail@seatling.app)**

When submitting a report, please include:
1. **Target**: The affected repository, package name, release version, or API endpoint.
2. **Impact**: A concise summary of the security impact (e.g., license bypass, hardware anchor evasion, offline token replay, privilege escalation, or unauthorized seat release).
3. **Reproduction Steps**: A minimal proof-of-concept (PoC) or script demonstrating the vulnerability.

We will acknowledge receipt of your report within **48 hours** and provide a timeline for triage, remediation, and coordinated disclosure.

---

## Research Scope & Eligibility

### In Scope
- **Cryptographic Implementations**: Flaws in our Ed25519 signature verification, token parsing, HKDF key derivation, or AES-256-GCM encryption routines.
- **Hardware Anchor Evasion**: Novel bypasses against our Layer 1 weighted hardware quorum scoring or Layer 2 hardware-sealed key isolation (silent Windows DPAPI, macOS IOKit, Linux DMI).
- **Offline Token Replay / Tampering**: Attacks on the bounded offline grace window or lease validation logic.
- **Cloud API & Webhook Ingestion**: Vulnerabilities in checkout synchronization endpoints, customer self-service deactivation mechanisms, or creator isolation boundaries.

### Out of Scope
- Denial-of-service (DoS/DDoS) attacks against public endpoints or rate-limiting testing.
- Social engineering, phishing, or physical attacks against Seatling employees, creators, or infrastructure providers.
- Vulnerabilities within third-party payment processors (e.g., Stripe, Gumroad, Polar, Lemon Squeezy); please report these directly to the respective platform.
- Attacks requiring physical disassembly or memory injection (e.g., debugger-based binary patching) on end-user machines, as runtime client memory modification is outside the threat model of native software licensing.

---

## Supported Versions

Security fixes are prioritized and released for the latest major and minor releases:

| Component | In Scope | Current Channel |
| :--- | :--- | :--- |
| `seatling-sdks` (Rust Core & N-API) | ✅ Yes | Latest Major/Minor |
| `seatling-sdk-node` | ✅ Yes | Latest Major/Minor |
| `seatling-go` | ✅ Yes | Latest Major/Minor |
| Core API Services (`api.seatling.app`) | ✅ Yes | Continuous Deployment |

If you are using an older version of a client SDK, we strongly recommend updating regularly to maintain the latest cryptographic hardening and hardware anchoring updates.
