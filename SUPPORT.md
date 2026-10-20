# Support and Help

Welcome to the Seatling support guide! Whether you are an end-user managing an activated seat or a software creator integrating Seatling into your desktop application, here is how to get help quickly.

---

## 🚀 For End-Users & Software Buyers

**Need to move your license to a new computer, or reinstalling your operating system?**

You do not need to wait for email support or file an issue:

👉 **[Seatling Customer Self-Service Portal](https://portal.seatling.app)**

From the self-service portal, you can:
- View all active devices bound to your software licenses.
- **1-Click Deactivate** retired or upgraded machines to immediately free up a seat.
- Review remaining offline grace periods and license statuses.
- Access your license keys securely via magic link or verified purchase email.

---

## 🛠️ For Developers & Software Creators

### 1. Developer Documentation & Guides
Before troubleshooting or opening an issue, review our official guides:

📚 **[docs.seatling.app](https://docs.seatling.app)**

Key resources include:
- **Client SDK Quickstarts**: Rust (`seatling`), Node.js/TypeScript (`@seatling/sdk`), Go (`seatling-go`), C++/JUCE, and Python.
- **Architecture Deep Dives**: Zero-Prompt Ed25519 Hardware Anchoring (V7), weighted quorum scoring, and offline grace periods.
- **Checkout Webhook Ingestion**: Setting up instant webhook synchronization with Gumroad, Polar, Stripe, or Lemon Squeezy.
- **API Reference**: Authoritative OpenAPI 3.1.0 specifications.

### 2. Client SDK Bugs & Technical Issues
If you encounter a bug, compilation issue, or performance concern in our open-source client SDKs:
- Check existing issues in the appropriate repository:
  - [`seatling-sdks`](https://github.com/seatling/seatling-sdks) (Rust core engine & N-API bindings)
  - [`seatling-sdk-node`](https://github.com/seatling/seatling-sdk-node) (Node.js & TypeScript SDK)
  - [`seatling-go`](https://github.com/seatling/seatling-go) (Go client)
- Open a GitHub Issue on the respective repository with your OS version, architecture (x86_64 / aarch64), SDK version, and a minimal reproducible example.

### 3. Account, Billing & Direct Technical Assistance
For inquiries regarding your Creator Dashboard account, subscription tiers, custom seat limits, or confidential integration support:

📧 **[mail@seatling.app](mailto:mail@seatling.app)**

---

## 🔒 Security Vulnerabilities

Please **do not** report suspected security vulnerabilities through public GitHub issues. See our [Security Policy](./SECURITY.md) or email **[mail@seatling.app](mailto:mail@seatling.app)** directly.
