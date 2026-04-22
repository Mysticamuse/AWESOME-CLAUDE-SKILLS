# Template: Validation Matrix

**Purpose**: Track all validation activities required before pilot or launch.
Every row must have a status before proceeding.

---

## Product / Software Requirements

| Requirement ID | Requirement | Validation method | Pass criteria | Status | Evidence / Notes |
|---|---|---|---|---|---|
| REQ-001 | Core function X | Functional test | All test cases pass | 🟡 IN PROGRESS | |
| REQ-002 | Performance SLO | Load test (k6) | p95 < 500ms at 1000 RPS | 🔴 NOT STARTED | |
| REQ-003 | Security baseline | Pen test | No critical/high findings | 🔴 NOT STARTED | |

## Hardware / Environmental (for physical products)

| Requirement ID | Requirement | Standard / Test | Pass criteria | Status | Evidence |
|---|---|---|---|---|---|
| HW-001 | IP65 ingress protection | IEC 60529 | No ingress after test | 🔴 NOT STARTED | |
| HW-002 | Operating temp -10°C to +55°C | IEC 60068-2-1/2 | Functional throughout | 🔴 NOT STARTED | |
| HW-003 | 1.2m drop onto concrete | IEC 60068-2-27 | No damage; functional | 🔴 NOT STARTED | |
| HW-004 | EMC emissions | CISPR 32 / applicable | Pass class B limits | 🔴 NOT STARTED | |

## Compliance Requirements

| Requirement | Certification / Standard | Owner | Status | Certificate / Reference |
|---|---|---|---|---|
| CE marking | RED + LVD + EMC | Hardware team | 🔴 NOT STARTED | |
| Data privacy | GDPR / DPDP | Legal / Engineering | 🟡 IN PROGRESS | |

## Status Key
- 🟢 PASS — validated; evidence on file
- 🟡 IN PROGRESS — validation underway
- 🔴 NOT STARTED — not yet begun
- ⛔ BLOCKED — waiting on dependency
- ❌ FAIL — failed; remediation required

---
