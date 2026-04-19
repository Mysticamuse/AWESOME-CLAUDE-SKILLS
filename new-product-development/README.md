# ⚡ New Product Development (NPD) Skill for Claude

> A universal, stage-gated NPD framework with 10 industry domain overlays — from idea to launch.

---

## 📦 Versions

| Version | Description | Install File |
|---------|-------------|-------------|
| V1 | Core 8-stage NPD framework (business track) | `new-product-development-v1.skill` |
| V2 | V1 + full software engineering track (LLMOps, DevSecOps, Observability) | `new-product-development-v2.skill` |
| V3 ⭐ | V2 + 10 domain overlays (IIoT, Healthcare, FinTech, Retail, AgriTech, EdTech, Logistics, Energy, PropTech, GovTech) | `new-product-development-v3.skill` |

**Recommended: Install V3** — it is a superset of V1 and V2.

---

## 🗂️ File Structure

```
new-product-development/
├── SKILL.md                              ← Master skill (V3 core framework)
├── new-product-development-v1.skill     ← Installable V1
├── new-product-development-v2.skill     ← Installable V2
├── new-product-development-v3.skill     ← Installable V3 (recommended)
│
└── references/
    ├── concept-testing.md               ← Stage 3: Validation methods
    ├── business-analysis.md             ← Stage 4: Financial modeling
    ├── launch-planning.md               ← Stage 7: GTM + launch templates
    │
    └── domains/                         ← 10 industry domain overlays
        ├── iot-manufacturing.md         ← CNC, OPC UA, Modbus, edge, OT/IT security
        ├── healthcare-medtech.md        ← HIPAA, FDA, HL7 FHIR, clinical validation
        ├── fintech-banking.md           ← PCI-DSS, KYC/AML, open banking
        ├── retail-ecommerce.md          ← POS, inventory, omnichannel, search
        ├── agritech-food.md             ← Field sensors, LoRaWAN, crop ML, traceability
        ├── edtech-learning.md           ← LMS, SCORM/xAPI, adaptive learning
        ├── logistics-supplychain.md     ← Fleet, last-mile, route optimisation
        ├── energy-cleantech.md          ← Grid, SCADA, EV charging, smart meters
        ├── real-estate-proptech.md      ← BMS, BACnet, digital twin, tenant app
        └── government-smartcity.md     ← GovTech, Aadhaar, DigiLocker, GIGW
```

---

## 🔄 How Domain Detection Works

Claude automatically detects your industry from conversation context and loads
the relevant domain overlay. No manual configuration needed.

| Say this... | Claude loads... |
|-------------|----------------|
| "CNC machine", "OPC UA", "shop floor" | `iot-manufacturing.md` |
| "HIPAA", "patient data", "EHR" | `healthcare-medtech.md` |
| "payments", "KYC", "PCI-DSS" | `fintech-banking.md` |
| "e-commerce", "POS", "inventory" | `retail-ecommerce.md` |
| "precision farming", "soil sensor" | `agritech-food.md` |
| "LMS", "SCORM", "learning outcomes" | `edtech-learning.md` |
| "fleet", "last-mile", "route" | `logistics-supplychain.md` |
| "solar", "EV charging", "smart meter" | `energy-cleantech.md` |
| "BMS", "building", "tenant" | `real-estate-proptech.md` |
| "smart city", "e-governance", "citizen" | `government-smartcity.md` |

---

## 🚀 Installation

1. Download the `.skill` file for your preferred version
2. Go to **claude.ai** → Settings → Skills → Install Skill
3. Upload the `.skill` file
4. Start a conversation — Claude will apply the framework automatically

---

## 📊 V1 vs V2 vs V3 — What's Different

| Feature | V1 | V2 | V3 |
|---------|----|----|-----|
| 8-stage NPD framework | ✅ | ✅ | ✅ |
| Business / product track | ✅ | ✅ | ✅ |
| Software engineering track | ❌ | ✅ | ✅ |
| LLMOps + RAG pipeline guidance | ❌ | ✅ | ✅ |
| DevSecOps + CI/CD | ❌ | ✅ | ✅ |
| Observability (SLOs, DORA) | ❌ | ✅ | ✅ |
| Domain auto-detection | ❌ | ❌ | ✅ |
| Industry domain overlays | 0 | 0 | 10 |
| India-specific compliance | ❌ | ❌ | ✅ |
| Industrial protocols (OPC UA, BACnet) | ❌ | ❌ | ✅ |
| Total reference files | 3 | 3 | 13 |

---

*Part of the [AWESOME-CLAUDE-SKILLS](https://github.com/Mysticamuse/AWESOME-CLAUDE-SKILLS) collection.*
