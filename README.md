# captive-portal-security-analysis

Security assessment of MAC-based captive portal authentication systems. Demonstrates Weak Identity Binding between HTTP authentication (Layer 7) and MAC-based network authorization (Layer 2).

## Overview

This paper analyzes the architectural weakness of captive portals that use MAC addresses as the sole authorization factor after web authentication. The MAC address lacks every property required of a secure authenticator: it is not secret, not immutable, not cryptographically verifiable. The analysis includes a practical demonstration via MAC impersonation for proxy authentication, MITRE ATT&CK classification, detection analysis, and recommended mitigations.

## Key Findings

- MAC-based authorization constitutes a Weak Identity Binding — the authorized identity is not cryptographically bound to the authenticated device
- AP Isolation does not mitigate MAC impersonation attacks — the technique requires no direct client-to-client communication
- Effective security relies on client OS restrictions (e.g., macOS blocking MAC changes), not on architectural robustness — a pattern called "Security through Client Capability Limitation"
- A $15 microcontroller is sufficient to bypass enterprise-grade captive portal authentication

## MITRE ATT&CK Mapping

| ID | Technique |
|----|-----------|
| T1036 | Masquerading |
| T1036.005 | Match Legitimate Name or Location |

## Recommended Mitigations

- **WPA2/WPA3-Enterprise (802.1X)** — eliminates the problem by design
- **Cryptographic session binding (MAC + IP + HTTP cookie)** — reduces the attack window
- See the full paper for detailed analysis

## Paper

[captive-portal-bypass.md](captive-portal-bypass.md)

## License

MIT

## Disclaimer

This research was conducted on author-owned equipment for educational and architectural analysis purposes. No unauthorized access was obtained.
