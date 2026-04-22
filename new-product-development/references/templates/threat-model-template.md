# Template: Threat Model

**Purpose**: Identify, assess, and mitigate security threats before they become
vulnerabilities in production.

---

## System Description
- Product name:
- Deployment context:
- Trust boundaries: (list all boundaries where trust changes)
- Data flows: (list all data flows across trust boundaries)

## Assets to Protect
| Asset | Sensitivity | Impact if compromised |
|---|---|---|
| Customer operational data | High | Operational disruption, liability |
| Device credentials | Critical | Full device compromise |
| OTA firmware updates | Critical | Arbitrary code execution on device |
| User PII | High | Privacy violation, regulatory penalty |

## Threat Analysis (STRIDE)

For each trust boundary or data flow, apply STRIDE:

| Threat type | Description | Example | Mitigation |
|---|---|---|---|
| **S**poofing | Attacker impersonates a legitimate entity | Fake device sends data | mTLS device authentication |
| **T**ampering | Attacker modifies data or firmware | Man-in-middle modifies commands | Code signing; TLS for all traffic |
| **R**epudiation | Actor denies performing an action | Admin denies config change | Immutable audit log |
| **I**nformation disclosure | Data exposed to unauthorised parties | API returns data from other tenant | Tenant isolation; authorisation checks |
| **D**enial of service | Service made unavailable | Flood device with requests | Rate limiting; input validation |
| **E**levation of privilege | Attacker gains higher access than authorised | Operator escalates to admin | RBAC; least privilege; session management |

## Risk Register
| Threat | Likelihood (1–5) | Impact (1–5) | Risk score | Mitigation | Residual risk |
|---|---|---|---|---|---|

## Open Security Questions
| Question | Owner | Due date |
|---|---|---|

---
