<p align="center">
  <img src="./splash_small_glow.jpg" alt="Seatling Logo" width="350" height="350" />
</p>

<h1 align="center">Seatling</h1>

<p align="center">
  <strong>Developer-first software licensing, seat management, and telemetry for native desktop applications.</strong>
</p>

## Overview

**Seatling** is a modern software licensing and hardware-anchored seat management platform built specifically for native software creators. 

Whether you build **audio plugins (VST3, AU, AAX)**, **3D/VFX add-ons (Blender, Maya)**, **indie desktop apps (Tauri, Electron, Swift)**, **local-first AI toolchains**, or **developer CLIs**, Seatling delivers tamper-resistant device locking and offline grace periods without treating your users like criminals.

### Core Philosophy: Licensing, Not Malware

Traditional DRM relies on intrusive background daemons, kernel-level drivers, and brittle "always-online" tethering that fails the moment your customer opens your app on an airplane, in a recording studio, or on an isolated workstation.

Seatling replaces invasive DRM with **transparent, mathematically verifiable cryptography**:
- **Zero Kernel Bloat**: No background services, no root daemons, no invasive system snooping.
- **Zero OS Password Dialogs**: Completely silent execution. Uses native platform key wrapping (silent DPAPI on Windows, IOKit on macOS, DMI/machine-id on Linux) without triggering modal Keychain password popups or DAW sandbox crashes (`errSecMissingEntitlement`).
- **Offline-First Resilience**: Signed machine license tokens with configurable offline grace windows (7 to 90+ days).
- **Sub-Microsecond Verification**: Non-blocking, lock-free atomic snapshots (< 0.01ms / ~45–150ns) safe for 60/120 FPS render loops and hard real-time audio DSP threads.
- **Zero-Support Machine Transfers**: When customers upgrade their computer or reinstall their OS, they 1-click deactivate retired machines directly in the self-service portal—eliminating manual license-reset emails.

## Developer Resources

- 🌐 **Platform & Dashboard**: [www.seatling.app](https://www.seatling.app)
- 📖 **Developer Documentation**: [docs.seatling.app](https://docs.seatling.app)
- 🔒 **Security Disclosures**: [SECURITY.md](./SECURITY.md)
- 💬 **Support & Inquiries**: [mail@seatling.app](mailto:mail@seatling.app)
