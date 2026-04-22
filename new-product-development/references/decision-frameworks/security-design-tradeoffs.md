# Decision Framework: Security Design Trade-offs

Use when making security decisions that involve usability, cost, or performance trade-offs.

---

## Trade-off Matrix

| Security control | Security gain | Usability cost | Implementation cost | Recommended default |
|---|---|---|---|---|
| mTLS for device auth | High | None (transparent) | Medium | ✅ Always |
| Certificate rotation (90d) | High | None (automated) | Medium | ✅ Always |
| Network segmentation (OT/IT) | Very high | Low | Medium | ✅ Always |
| Hardware secure element | High | None | Low–Medium | ✅ For field devices |
| Encrypted storage | High | None | Low | ✅ Always |
| MFA for operator UI | High | Low | Low | ✅ Always |
| SAST in CI/CD | High | Low (build time) | Low | ✅ Always |
| Annual pen test | High | None | Medium | ✅ Always |
| End-to-end encryption | High | None | High | ✅ For sensitive data |
| Air-gap / data diode | Very high | Very high | High | Only if Zone 0/1 |
| Biometric device unlock | Medium | Low | High | Optional |
| FIDO2 hardware key | High | Medium | Medium | For privileged access |

## Hardening vs. Usability: Guiding Questions
1. Who is the attacker model? (insider threat vs. nation-state vs. opportunistic)
2. What is the blast radius if this control fails?
3. Is the control transparent to the operator, or does it add friction?
4. Can the control be automated away from the user entirely?

## Minimum Baseline (non-negotiable for any connected product)
- Unique device identity (certificate or hardware key)
- All traffic encrypted in transit (TLS 1.3)
- All data encrypted at rest (AES-256)
- No default or shared credentials
- Authenticated OTA updates only (code signing)
- Audit log for all authentication and configuration events
- Vulnerability disclosure policy published

---

## Threat Modelling Quick Guide (STRIDE per component)

For each major component in your architecture, ask:

| Question | Threat type |
|---|---|
| Can an attacker pretend to be a legitimate user or device? | Spoofing |
| Can an attacker modify data in transit or at rest? | Tampering |
| Can a user deny performing an action? | Repudiation |
| Can an attacker read data they should not see? | Information disclosure |
| Can an attacker make the system unavailable? | Denial of service |
| Can an attacker gain permissions beyond their role? | Elevation of privilege |

## Security Debt Register

Track security decisions made under time pressure:

| Decision | Security debt incurred | Risk level | Remediation plan | Due date |
|---|---|---|---|---|
| Using HTTP internally | Unencrypted internal traffic | Medium | Add TLS in Q2 | |
| Shared API key for all devices | No per-device revocation | High | Move to certificates in V1.1 | |

**Rule**: No HIGH security debt items at launch without explicit sign-off from security lead and documented acceptance of risk.

## Security Review Gates

| Stage | Minimum security review |
|---|---|
| Architecture design | Threat model review with security lead |
| Code complete | SAST scan; dependency audit; no critical/high findings |
| Pre-pilot | Internal penetration test or security assessment |
| Pre-launch | External penetration test by qualified firm |
| Annually | Full penetration test + access control audit |
