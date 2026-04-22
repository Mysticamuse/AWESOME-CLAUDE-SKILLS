# V4 — What Was Added on Top of V3 (and V1)

**V4 = V1 (baseline) + V3 additions + 5-Layer Orchestration Architecture**

This document describes every addition made in V4 relative to V3.
V1 remains the unchanged baseline. V3 additions are preserved in full.
V4 extends and systematises both.

---

## The Core Architectural Shift: V3 → V4

| V3 | V4 |
|---|---|
| Generic NPD + domain overlays | 5-layer expert orchestration system |
| Advisory reference library | Execution-ready operating framework |
| "Read domain file when relevant" | Explicit 4-dimension routing matrix |
| Domain organised only | Domain + system architecture layer |
| Good guidance | Prescriptive decisions + reusable artifacts |

---

## Addition 1: Explicit 4-Dimension Routing Logic in SKILL.md

V3 had keyword-based domain detection. V4 replaced it with a structured
routing model Claude must execute before every response:

**Dimension 1 — Product Type** (new in V4):
- Software-only → cloud architecture depth
- Physical device → device engineering capability module
- Connected device → connectivity + edge + firmware modules
- Regulated system → compliance-first at every gate
- Platform product → multi-tenant, ecosystem design patterns

**Dimension 2 — Domain** (improved from V3):
- Same 10 domains as V3 but with richer keyword matching table
- Cross-linked to capability modules (new in V4)

**Dimension 3 — Lifecycle Stage** (new in V4):
- Explicit stage-to-gate-focus mapping
- Ideation / Validation / Business Case / Prototype / Pilot / Launch / Scale

**Dimension 4 — Capability Lens** (entirely new in V4):
- Detects when a cross-cutting engineering topic is raised
- Routes to the matching capability module (see Addition 2)

---

## Addition 2: 8 Cross-Cutting Capability Modules (entirely new in V4)

These are independent engineering reference files that load regardless of domain.
The same capability may be needed across IoT, Healthcare, Energy, and Logistics.

| File | What it covers | Why it couldn't stay in domain overlays |
|---|---|---|
| `device-engineering.md` | IP ratings, battery sizing, thermal design, DFM, certification (BIS/CE/FCC) | Physical product constraints apply across all hardware domains |
| `firmware-edge-runtime.md` | OS selection, state machines, offline-first, OTA A/B partition, watchdog | Firmware patterns are universal; duplication in every domain was wasteful |
| `industrial-connectivity.md` | Protocol landscape table, device discovery, tag mapping, time sync, gateway architecture | Deep enough to deserve its own file; can't be compressed into domain overlay |
| `telemetry-data-contracts.md` | Canonical event schema, asset ID, timestamp rules, quality flags, time-series storage | Data contract discipline applies to any telemetry product |
| `ot-it-security.md` | IEC 62443 zone model, device identity, mTLS, audit logs, STRIDE per component | Too critical to bury inside a single domain; applies across IoT, Energy, PropTech |
| `fleet-operations.md` | Zero-touch provisioning, OTA rollout stages, fleet health dashboard, decommissioning | Fleet ops applies to any multi-device deployment |
| `reliability-validation.md` | HALT/HASS, environmental qualification test sequence, pilot acceptance criteria | Validation discipline needed for any hardware product |
| `support-operating-model.md` | L1/L2/L3 tiers, spare parts strategy, RMA process, support tooling | Support model design applies across all deployed products |

---

## Addition 3: 6 Decision Frameworks (entirely new in V4)

V3 described options. V4 makes decisions. Each framework is prescriptive —
it tells Claude (and the user) what to choose, not just what the options are.

| File | Decision it supports | Key mechanism |
|---|---|---|
| `protocol-selection.md` | OPC UA vs. Modbus vs. MTConnect vs. vendor API | Step-by-step decision tree; first match wins |
| `edge-vs-cloud-partitioning.md` | What logic runs locally vs. centrally | Decision matrix with ALWAYS/NEVER/OPTIONAL per function |
| `build-buy-partner.md` | Whether to build, license, or partner each component | Scoring matrix + TCO template + vendor evaluation scorecard |
| `pilot-readiness.md` | Whether the product is ready for a customer field trial | Readiness scorecard + full pre-pilot checklist |
| `launch-readiness.md` | Whether the product is ready for GA | Blocker classification + rollback decision tree + go/no-go meeting agenda |
| `security-design-tradeoffs.md` | Security controls vs. usability vs. cost | Trade-off matrix + STRIDE quick guide + security debt register |

---

## Addition 4: 8 Reusable Templates (entirely new in V4)

V3 could advise well but produced inconsistent outputs. V4 adds structured
templates Claude uses to generate the same high-quality artifact every time.

| File | What it produces | Key sections |
|---|---|---|
| `prd-template.md` | Product Requirements Document | Problem statement, personas, goals, user stories, NFRs, open questions |
| `pilot-charter-template.md` | Pilot agreement with customer | Objectives, scope, success criteria, RACI, exit criteria, signatures |
| `telemetry-schema-template.md` | Canonical data model for telemetry | Event schema, asset ID, timestamp rules, unit register, state enum |
| `threat-model-template.md` | Security threat assessment | Asset register, STRIDE per component, risk register, security debt |
| `validation-matrix-template.md` | Hardware + software validation tracker | Requirements, test methods, pass criteria, status, evidence |
| `gtm-industrial-template.md` | Go-to-market plan | Positioning, message house, channel strategy, launch timeline, metrics |
| `post-pilot-review-template.md` | Structured pilot debrief | Outcomes vs. criteria, technical findings, commercial signals, go/no-go |
| `factory-discovery-template.md` | Site survey for new deployments | Machine inventory, network topology, data access, installation constraints |

---

## Addition 5: Strengthened Core Lifecycle References

V3 carried over V1's original reference files largely unchanged.
V4 significantly deepened them:

| File | V1 / V3 content | Added in V4 |
|---|---|---|
| `business-analysis.md` | TAM/SAM/SOM, basic financials | SaaS/hardware unit economics, 3-year P&L template, sensitivity analysis, magic number |
| `concept-testing.md` | Testing methods, Van Westendorp | Assumption mapping matrix, PoC charter framework, full survey template with n guidance |
| `launch-planning.md` | GTM checklist, channel table | Message house structure, readiness scoring (1–5 per dimension), post-launch monitoring cadence |

---

## Addition 6: 5-Layer Architecture Declaration

V4 formally declares its architecture in SKILL.md so Claude always knows
what layer to consult for what type of question:

```
Layer 1: SKILL.md — Master Orchestrator (routing + stage gates)
Layer 2: Core Lifecycle References (concept-testing, business-analysis, launch-planning)
Layer 3: Domain Overlays (10 industry-specific files)
Layer 4: Capability Modules (8 cross-cutting engineering patterns)
Layer 5: Decision Frameworks (6) + Templates (8)
```

Progressive disclosure rule: **never load all files** — load only what
the current conversation needs.

---

## Complete File Count Comparison

| Version | Files | Content (bytes) | What's in it |
|---|---|---|---|
| V1 | 4 | ~18 KB | SKILL.md + 3 core references |
| V3 | 14 | ~85 KB | V1 + software engineering track + 10 domain overlays |
| V4 | 36 | ~142 KB | V3 + 8 capability modules + 6 decision frameworks + 8 templates + deepened core refs |

---

## What V4 Still Does NOT Include (Future V5 Candidates)

- Scripts for deterministic tasks (e.g. auto-generate telemetry schema JSON from template)
- Domain files for B2B SaaS, Developer Tools, or Consumer Mobile (not yet covered)
- LLMOps deep-dive capability module (currently embedded in Stage 5 of SKILL.md)
- Multilingual support guidance (beyond what's in EdTech and GovTech overlays)
- Competitive analysis framework
