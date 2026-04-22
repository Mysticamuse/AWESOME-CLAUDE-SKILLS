# ⚡ New Product Development (NPD) Skill for Claude
### A Universal Expert Orchestration System — V1 Baseline → V3 → V4
<img width="1264" height="848" alt="Gemini_Generated_Image_b1c3ucb1c3ucb1c3" src="https://github.com/user-attachments/assets/b59902d6-6c91-4066-a827-08252e5a2a07" />

> From a simple 8-stage business framework to a 5-layer execution operating system
> covering any product type across 10 industries. Built incrementally on a stable V1 baseline.

---

## 🏗️ Version Architecture

This skill is built in layers. **V1 is the stable baseline. V3 and V4 add on top without removing anything from V1.**

```
V4  ┌─────────────────────────────────────────────────────────┐
    │  + 8 Capability Modules  + 6 Decision Frameworks        │
    │  + 8 Reusable Templates  + Explicit 4D Routing Logic    │
    │  + Deepened Core References                             │
V3  ├─────────────────────────────────────────────────────────┤
    │  + Software / Technical Engineering Track               │
    │  + 10 Industry Domain Overlays                          │
    │  + Dual-track deliverables per stage                    │
V1  ├─────────────────────────────────────────────────────────┤
    │  8-Stage NPD Framework (Business Track)                 │
    │  Idea → Screen → Test → Analyse → Build → Test → Launch │
    │  concept-testing · business-analysis · launch-planning  │
    └─────────────────────────────────────────────────────────┘
```

---

## 📦 Install

| Version | Install file | Who should use it |
|---|---|---|
| **V1** — Baseline | `new-product-development-v1.skill` | PMs and founders wanting structured NPD |
| **V4** — Full ⭐ | Extract from `AWESOME-CLAUDE-SKILLS-NPD-v4.zip` | Engineers, architects, domain specialists |

> **Recommended**: Install V4 — it is a complete superset of V1 and V3.

---

## 🗂️ Repository Structure

```
new-product-development/
│
├── SKILL.md                          ← V4 Master Orchestrator (active version)
├── new-product-development-v1.skill  ← V1 installable skill file
├── AWESOME-CLAUDE-SKILLS-NPD-v4.zip  ← V4 complete package
│
├── v1-baseline/                      ← Original V1 files (read-only reference)
│   ├── README.md                     ← What V1 contains and its limitations
│   ├── SKILL.md
│   ├── concept-testing.md
│   ├── business-analysis.md
│   └── launch-planning.md
│
├── v3-additions/
│   └── README.md                     ← Every addition V3 made on top of V1
│
├── v4-additions/
│   └── README.md                     ← Every addition V4 made on top of V3
│
└── references/                       ← V4 active reference files
    ├── concept-testing.md            ← Deepened in V4
    ├── business-analysis.md          ← Deepened in V4
    ├── launch-planning.md            ← Deepened in V4
    │
    ├── domains/                      ← Added in V3, carried into V4
    │   ├── iot-manufacturing.md
    │   ├── healthcare-medtech.md
    │   ├── fintech-banking.md
    │   ├── retail-ecommerce.md
    │   ├── agritech-food.md
    │   ├── edtech-learning.md
    │   ├── logistics-supplychain.md
    │   ├── energy-cleantech.md
    │   ├── real-estate-proptech.md
    │   └── government-smartcity.md
    │
    ├── capabilities/                 ← NEW in V4
    │   ├── device-engineering.md
    │   ├── firmware-edge-runtime.md
    │   ├── industrial-connectivity.md
    │   ├── telemetry-data-contracts.md
    │   ├── ot-it-security.md
    │   ├── fleet-operations.md
    │   ├── reliability-validation.md
    │   └── support-operating-model.md
    │
    ├── decision-frameworks/          ← NEW in V4
    │   ├── protocol-selection.md
    │   ├── edge-vs-cloud-partitioning.md
    │   ├── build-buy-partner.md
    │   ├── pilot-readiness.md
    │   ├── launch-readiness.md
    │   └── security-design-tradeoffs.md
    │
    └── templates/                    ← NEW in V4
        ├── prd-template.md
        ├── pilot-charter-template.md
        ├── telemetry-schema-template.md
        ├── threat-model-template.md
        ├── validation-matrix-template.md
        ├── gtm-industrial-template.md
        ├── post-pilot-review-template.md
        └── factory-discovery-template.md
```

---

## 🔄 What Changed at Each Version

### V1 → V3 (key additions)
- Added full **Software / Technical Engineering track** at every stage
- Added **10 industry domain overlays** (auto-detected from conversation context)
- Added **dual-track deliverables** (business + technical per stage)
- Added **LLMOps, DevSecOps, Observability** guidance in Stage 5
- Added **DORA metrics** in Stage 8

👉 Full details: `v3-additions/README.md`

### V3 → V4 (key additions)
- Added **explicit 4-dimension routing logic** (product type · domain · lifecycle · capability lens)
- Added **8 cross-cutting capability modules** (device engineering, firmware, connectivity, telemetry, OT security, fleet ops, reliability, support)
- Added **6 prescriptive decision frameworks** (protocol selection, edge vs cloud, build/buy/partner, pilot readiness, launch readiness, security trade-offs)
- Added **8 reusable templates** (PRD, pilot charter, telemetry schema, threat model, validation matrix, GTM plan, post-pilot review, factory discovery)
- **Deepened** core reference files with unit economics, sensitivity analysis, assumption mapping, message house, and post-launch monitoring cadence

👉 Full details: `v4-additions/README.md`

---

## 🧠 How Domain Auto-Detection Works

Claude reads your conversation and loads the matching domain overlay automatically:

| Say this... | Claude loads... |
|---|---|
| "OPC UA", "shop floor", "Modbus", "manufacturing" | `iot-manufacturing.md` |
| "HIPAA", "patient data", "FDA", "clinical" | `healthcare-medtech.md` |
| "payments", "KYC", "PCI-DSS", "banking" | `fintech-banking.md` |
| "e-commerce", "POS", "inventory", "retail" | `retail-ecommerce.md` |
| "precision farming", "soil sensor", "irrigation" | `agritech-food.md` |
| "LMS", "SCORM", "assessment", "learning" | `edtech-learning.md` |
| "fleet", "last-mile", "route optimisation" | `logistics-supplychain.md` |
| "solar", "EV charging", "smart meter", "grid" | `energy-cleantech.md` |
| "BMS", "building", "tenant", "smart building" | `real-estate-proptech.md` |
| "smart city", "citizen", "e-governance" | `government-smartcity.md` |

---

## 📊 Version Comparison Table

| Dimension | V1 | V3 | V4 |
|---|---|---|---|
| Target audience | PMs, founders | PMs + engineers | PMs, engineers, domain specialists |
| Architecture | Single file | Core + domain overlays | 5-layer orchestration system |
| Business track | ✅ | ✅ | ✅ |
| Technical/engineering track | ❌ | ✅ | ✅ |
| Domain overlays | 0 | 10 | 10 (improved) |
| Capability modules | 0 | 0 | 8 |
| Decision frameworks | 0 | 0 | 6 |
| Reusable templates | 0 | 0 | 8 |
| Explicit routing logic | Basic | Keyword detection | 4-dimension matrix |
| India-specific compliance | ❌ | ✅ | ✅ |
| Hardware / device guidance | ❌ | Partial | Full (capability modules) |
| Total files | 4 | 14 | 36 |
| Total content | ~18 KB | ~85 KB | ~142 KB |

---

## 💡 Example Prompts (after installing V4)

```
"I have a B2B SaaS idea. Help me validate it using the NPD framework."
"We're at Stage 4. Build a business case with cloud cost model."
"Help me choose between OPC UA and Modbus for our factory integration."
"Is our product ready for a customer pilot? Run the readiness check."
"Generate a PRD for our MVP using the standard template."
"Create a threat model for our connected device."
"Build a GTM plan for our Q3 launch."
```

---

## 🤝 Contributing

1. Fork the repository
2. Make improvements to any reference file or add new capability modules
3. Submit a pull request describing what you changed and why
4. For new domain overlays, follow the standardised structure in existing domain files

---

## 📄 Licence

MIT — free to use, modify, and distribute.

---

*Part of the [AWESOME-CLAUDE-SKILLS](https://github.com/Mysticamuse/AWESOME-CLAUDE-SKILLS) collection.*
