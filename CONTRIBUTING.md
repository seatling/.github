# Contributing to Seatling

Thank you for your interest in contributing to the Seatling ecosystem! We welcome contributions to our open-source client SDKs, platform bindings, starter templates, and developer documentation.

---

## 📌 Scope: Open Source vs. Commercial Platform

Before submitting code, please keep in mind the structure of the Seatling ecosystem:

- **Open Source & Community Contributions Welcome**:
  - Official Client SDKs: [`seatling-sdks`](https://github.com/seatling/seatling-sdks) (unified Rust core and N-API bindings), [`seatling-sdk-node`](https://github.com/seatling/seatling-sdk-node), and [`seatling-go`](https://github.com/seatling/seatling-go).
  - Integration Blueprints & Starter Templates: Tauri, Electron, JUCE/VST3, Blender, and Python tooling.
  - Developer Documentation & OpenAPI 3.1.0 specifications.
- **Proprietary Commercial Infrastructure**:
  - The Seatling cloud licensing engine, checkout webhook ingestion pipelines (Gumroad, Polar, Stripe, Lemon Squeezy), Creator Dashboard, and Customer Self-Service Portal are closed-source commercial services.
  - For feedback, feature requests, or suggestions regarding the cloud platform, please open a discussion on GitHub or reach out to **[mail@seatling.app](mailto:mail@seatling.app)**.

---

## Contents

- [Code of Conduct](#code-of-conduct)
- [Support & Questions](#support--questions)
- [Reporting Bugs & Filing Issues](#reporting-bugs--filing-issues)
- [Cryptographic & Performance Invariants](#cryptographic--performance-invariants)
- [Code Style & Toolchain Standards](#code-style--toolchain-standards)
- [Submitting Pull Requests](#submitting-pull-requests)
- [Writing Commit Messages](#writing-commit-messages)
- [Developer Certificate of Origin (DCO)](#developer-certificate-of-origin-dco)

---

## Code of Conduct

Please review our [Code of Conduct](./CODE_OF_CONDUCT.md). It is in effect across all Seatling repositories and community spaces. We expect all contributors and maintainers to foster a welcoming, respectful, and harassment-free environment.

---

## Support & Questions

If you have questions about using Seatling or need help integrating an SDK:
- Consult the official developer documentation at **[docs.seatling.app](https://docs.seatling.app)**.
- For usage questions or discussions, please use the **GitHub Discussions** tab in the relevant repository.
- Review our [Support Guide](./SUPPORT.md) for more details.

---

## Reporting Bugs & Filing Issues

When filing a bug report:
1. **Search Existing Issues**: Ensure the issue has not already been reported or resolved in a recent release.
2. **Provide System Details**: Include your OS version (Windows, macOS, Linux), hardware architecture (`x86_64`, `aarch64`), and compiler/runtime version.
3. **Include a Minimal Reproducible Example**: Provide the smallest self-contained code snippet or test case that reproduces the issue.
4. **Security Vulnerabilities**: **DO NOT** report security issues or hardware anchor bypasses in public issues. Refer to [SECURITY.md](./SECURITY.md) and email **[mail@seatling.app](mailto:mail@seatling.app)**.

---

## Cryptographic & Performance Invariants

Seatling client SDKs are engineered to run inside demanding native desktop applications, real-time audio plugins (VST3/AU), and game engines. Any pull request touching core SDK logic must adhere to the following invariants:

1. **Zero OS Password Dialogs (100% Silent Execution)**:
   - Hardware key sealing must never invoke OS APIs that trigger user authentication dialogs or require host developer entitlements (no modal macOS Keychain popups, no Secure Enclave crashes across un-entitled audio DAWs, and silent DPAPI semantics on Windows).
2. **Lock-Free Read Operations**:
   - Runtime authorization checks (`is_authorized()`, entitlement lookups) must read from lock-free atomic snapshots with zero heap allocations, zero mutex contention, and zero disk/network I/O (~45–150 nanoseconds benchmarked). They must remain safe for 60/120 FPS render loops and real-time audio threads.
3. **Deterministic Hardware Quorum Scoring**:
   - Changes to Layer 1 HWID calculation or weighted quorum fuzzy matching must pass all cross-platform unit tests across Windows, macOS, and Linux fixtures without breaking backward compatibility for active leases.
4. **Offline Resilience**:
   - The SDK must never block application launch or fail silently when network access is unavailable, provided the local lease token remains within its valid offline grace window.

---

## Code Style & Toolchain Standards

All code submissions must pass standard linter and formatting checks before merge.

### Rust (`crates/seatling`, `crates/seatling-node`)
```bash
# Format check
cargo fmt --all -- --check

# Linter checks (zero warnings allowed)
cargo clippy --all-targets -- -D warnings

# Run all test suites
cargo test --all
```

### Node.js / TypeScript (`seatling-sdk-node`, `@seatling/sdk`)
```bash
# Linting & Formatting
npm run lint
npm run format:check

# Run test suites
npm test
```

### Go (`seatling-go`)
```bash
# Format check
gofmt -s -l .

# Run linter
golangci-lint run

# Run tests
go test -v -race ./...
```

---

## Submitting Pull Requests

1. **One Focus per Pull Request**: Keep pull requests focused on a single bug fix, optimization, or feature. Avoid bundling unrelated formatting or refactoring changes.
2. **Branch from Default Branch**: Create your feature or bugfix branch from `main`.
3. **Include Unit / Integration Tests**: Every new feature or bug fix must be accompanied by relevant test coverage.
4. **Maintain Documentation**: Update inline documentation comments, API references, or Markdown guides as applicable.
5. **Ensure CI Passes**: All pull requests must pass continuous integration checks across supported platforms (Ubuntu, macOS, Windows).

---

## Writing Commit Messages

We enforce the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification.

Format your commit message as:
```text
<type>(<optional scope>): <description>

[optional body]

[optional footer(s)]
```

Common types:
- `feat`: A new feature or capability
- `fix`: A bug fix
- `perf`: A code change that improves runtime performance
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `docs`: Documentation-only updates
- `test`: Adding missing tests or correcting existing tests
- `chore`: Changes to build tooling, dependencies, or configuration

Example:
```text
feat(anchor): add normalized CPU model fallback for virtualized environments

Improves quorum scoring stability on virtualized Linux dev containers 
without affecting physical machine HWID digests.

Signed-off-by: Jane Developer <jane@example.com>
```

---

## Developer Certificate of Origin (DCO)

To ensure clear provenance of open-source contributions, we require all commits to include a `Signed-off-by` trailer in accordance with the [Developer Certificate of Origin 1.1](https://developercertificate.org/):

```text
Signed-off-by: Jane Developer <jane@example.com>
```

You can automatically add this line to your commits using git:
```bash
git commit -s -m "feat(cache): optimize atomic lease snapshot lookup"
```

---

## Credits

Many principles and guidelines in this document were inspired by best practices from the Rust, Go, and open-source systems programming communities. We thank all contributors who help improve Seatling!
