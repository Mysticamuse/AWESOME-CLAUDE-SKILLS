# V3 — What Was Added on Top of V1

**V3 = V1 (baseline) + Software Engineering Track + 10 Domain Overlays**

This document describes every addition made in V3 relative to V1.
V1 files are unchanged — V3 extends them, not replaces them.

---

## Addition 1: Software / Technical Track at Every Stage

V1 had only a business/product track. V3 added a parallel technical engineering
track at every stage of the 8-stage NPD process.

### What the technical track adds per stage:

| Stage | V1 (Business only) | V3 Added (Technical track) |
|---|---|---|
| Stage 1 — Idea Generation | Brainstorming, customer interviews | OSS gap analysis, AI/ML opportunity scan, platform thinking |
| Stage 2 — Idea Screening | SWOT, scoring matrix | Build/buy/integrate decision, TRL assessment, stack gap analysis, OSS licence risk |
| Stage 3 — Concept Testing | Surveys, focus groups, WTP | Technical PoC (2–5 days), API mapping, LLM concept validation, architecture sketch |
| Stage 4 — Business Analysis | TAM/SAM/SOM, revenue model | Cloud cost model, LLM cost engineering, build vs buy TCO, engineering team sizing |
| Stage 5 — Prototyping | MVP scope, agile sprints | Architecture + ADRs, LLMOps, DevSecOps, CI/CD, observability (logs/metrics/traces) |
| Stage 6 — Market Testing | Beta, NPS, A/B testing | Canary deployment, feature flags, real-load perf monitoring, LLM quality review |
| Stage 7 — Launch | GTM plan, channels | Technical launch checklist, secrets rotation, DDoS protection, rollback plan |
| Stage 8 — Post-Launch | KPI tracking, backlog | DORA metrics, LLM cost trend, technical debt register, FinOps review |

---

## Addition 2: 10 Industry Domain Overlays

V1 gave the same generic advice for every industry. V3 added auto-detection of
industry context and domain-specific overlays covering:

| Domain File | Industry | Key additions over V1 |
|---|---|---|
| `iot-manufacturing.md` | Industrial IoT / Manufacturing | OPC UA, Modbus, MTConnect, edge device, offline-first, OT/IT security, fleet |
| `healthcare-medtech.md` | Healthcare / MedTech | FDA pathways, HIPAA, HL7 FHIR, IRB, IEC 62304, clinical validation |
| `fintech-banking.md` | FinTech / Banking | PCI-DSS, KYC/AML, open banking, idempotency, ledger architecture |
| `retail-ecommerce.md` | Retail / E-commerce | POS integration, recommendation engine, inventory, peak load testing |
| `agritech-food.md` | AgriTech / Food | LoRaWAN, offline mobile, NDVI, food traceability, vernacular UI |
| `edtech-learning.md` | EdTech / Learning | SCORM/xAPI, LTI 1.3, adaptive learning, WCAG, COPPA |
| `logistics-supplychain.md` | Logistics / Supply Chain | VRP route optimisation, real-time tracking, geofencing, POD, e-Way Bill |
| `energy-cleantech.md` | Energy / CleanTech | SCADA, OCPP 2.0.1, DLMS/COSEM, demand response, BMS integration |
| `real-estate-proptech.md` | Real Estate / PropTech | BACnet, digital twin, access control, tenant app, RERA compliance |
| `government-smartcity.md` | Government / Smart Cities | Aadhaar/DigiLocker, GIGW, GeM, STQC, multilingual, RTI compliance |

---

## Addition 3: Enhanced Routing in SKILL.md

V1 had simple "identify the stage" routing. V3 added:
- Domain detection via keyword matching table
- Dual-track routing (business vs technical)
- Domain overlay loading instruction ("read domains/X.md when detected")

---

## Addition 4: New Stage Summary Table with Two Deliverable Columns

V1 had one deliverable per stage. V3 added a second column for technical deliverables:

| Stage | V1 Deliverable | V3 Added Technical Deliverable |
|---|---|---|
| 3. Concept Testing | Concept brief | PoC findings + architecture sketch |
| 4. Business Analysis | Business case | Cloud cost model + engineering resource plan |
| 5. Prototyping | Working MVP | ADRs + CI/CD + observability + security baseline |
| 6. Market Testing | Market test report | Performance benchmark + security pen test sign-off |
| 7. Launch | GTM plan | Technical launch checklist (100% complete) |
| 8. Post-Launch | Review + roadmap | DORA metrics + debt register + FinOps plan |

---

## What V3 Did NOT Add (Left for V4)

- No capability modules (device engineering, firmware, connectivity, etc.)
- No decision frameworks (protocol selection, edge vs cloud, etc.)
- No reusable templates (PRD, pilot charter, threat model, etc.)
- No explicit 4-dimension routing logic
- Domain files not internally standardised (each had a different structure)
