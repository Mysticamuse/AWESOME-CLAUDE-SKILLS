---
name: new-product-development
version: 3.0
description: >
  Universal NPD framework for any product type across any industry domain — from idea to
  post-launch. Use this skill whenever a user mentions building a new product, launching
  something new, product ideation, go-to-market planning, MVP development, market testing,
  concept validation, or business case development. Covers both business/product track and
  software/technical track. Automatically applies domain-specific overlays for Industrial IoT,
  Healthcare, FinTech, Retail, AgriTech, EdTech, Logistics, Energy, Real Estate, and
  Government/Smart Cities. Trigger for any request involving product strategy, architecture,
  launch planning, technical implementation, or domain-specific compliance and rollout — at
  any stage of the NPD lifecycle.
---

# New Product Development (NPD) Skill — V3
### Universal Core + 10 Domain Overlays

This skill provides a **two-layer framework**:

- **Layer 1 — Core NPD**: The universal 8-stage process that applies to any product in
  any industry. Business + software engineering tracks at every stage.
- **Layer 2 — Domain Overlay**: When a specific industry is mentioned, Claude
  automatically loads the relevant domain reference file and applies domain-specific
  constraints, compliance requirements, technical patterns, and rollout considerations
  on top of the core framework.

---

## How Claude Should Use This Skill

1. **Detect the domain** from user context (explicit mention or inference)
2. **Load the domain overlay** from the references/domains/ folder
3. **Run the core NPD framework** with domain overlay applied at each stage
4. **Match technical depth to domain**: hardware-heavy domains (IoT, MedTech) get
   firmware/edge depth; pure software domains (FinTech, EdTech) get cloud/API depth
5. **Apply domain gate criteria** alongside universal gate criteria

**Domain detection keywords:**

| Domain | Trigger Keywords |
|---|---|
| Industrial IoT | CNC, shop floor, OPC UA, MTConnect, Modbus, PLC, edge device, factory, manufacturing, rugged |
| Healthcare | HIPAA, FDA, EHR, clinical, patient data, medical device, ICD-10, HL7, FHIR |
| FinTech | payments, banking, KYC, AML, PCI-DSS, lending, insurance, trading, wallet |
| Retail | e-commerce, POS, inventory, omnichannel, merchandising, loyalty, SKU |
| AgriTech | precision farming, crop, soil, drone, irrigation, livestock, harvest, field sensor |
| EdTech | LMS, learning, curriculum, assessment, student, SCORM, xAPI, classroom |
| Logistics | fleet, tracking, last-mile, warehouse, supply chain, shipment, route optimisation |
| Energy | grid, solar, wind, EV charging, SCADA, smart meter, microgrid, battery storage |
| Real Estate | property, PropTech, tenant, lease, building management, BMS, smart building |
| Government | smart city, citizen services, GovTech, public sector, open data, e-governance |

> When domain is detected, read the relevant file in `references/domains/` before responding.
> When no domain is detected, use the core framework only.

---

## NPD Process Overview (8 Stages)

```
Stage 1 → Idea Generation
Stage 2 → Idea Screening
Stage 3 → Concept Development & Testing
Stage 4 → Business Analysis
Stage 5 → Product Development / Prototyping
Stage 6 → Market Testing
Stage 7 → Commercialization / Launch
Stage 8 → Post-Launch Review & Iteration
```

At each stage, Claude applies:
- Universal activities (below)
- Domain-specific additions (from overlay file)

---

## Stage-by-Stage Core Framework

### Stage 1 — Idea Generation

**Business track**:
- Brainstorming: SCAMPER, How Might We, Jobs-to-be-Done
- Customer interviews and pain point mapping
- Competitive gap analysis, internal innovation sessions

**Technical track**:
- Engineering-led ideation: internal tools → external products
- OSS ecosystem gap analysis
- AI/ML opportunity mapping
- Platform thinking: what infrastructure can become a product?

**Deliverable**: Idea backlog with source, rationale, feasibility note
**Gate**: 5–10 distinct ideas documented

---

### Stage 2 — Idea Screening

**Business track**:
- Scoring matrix: strategic fit, market size, competitive advantage
- SWOT per idea; alignment with mission and resources

**Technical track**:
- Build vs. buy vs. integrate decision
- Stack and skills assessment
- AI/ML viability check
- Regulatory / compliance pre-check
- OSS dependency and licensing risk

**Deliverable**: Ranked shortlist + technical feasibility summary
**Gate**: Top idea passes scoring matrix on all dimensions including technical risk

---

### Stage 3 — Concept Development & Testing

**Business track**:
- Concept statement (problem / solution / user / benefit)
- 2–3 concept variants; concept tests; willingness-to-pay signals

**Technical track**:
- Time-boxed technical PoC (2–5 days) to validate core assumptions
- API / integration mapping
- LLM/AI concept validation (if applicable)
- Initial architecture sketch: monolith vs. microservices vs. serverless vs. edge
- Data availability check for AI/ML products

**Deliverable**: Concept brief + PoC findings + architecture sketch
**Gate**: Users desire concept AND PoC validates technical assumptions

> See `references/concept-testing.md` for validation methods
> See `references/technical-poc.md` for PoC patterns

---

### Stage 4 — Business Analysis

**Business track**:
- TAM / SAM / SOM market sizing
- Revenue model and pricing strategy
- Cost estimation: COGS, development, marketing
- Break-even, ROI, risk assessment

**Technical track**:
- Cloud cost model (compute, storage, networking, APIs at scale)
- LLM cost engineering (token cost × query volume)
- Build vs. buy TCO analysis
- Security and compliance cost estimation
- Engineering team sizing by role and duration

**Deliverable**: Business case + cloud cost model + engineering resource plan
**Gate**: ROI meets threshold; costs sustainable at scale; risks mitigable

> See `references/business-analysis.md` for financial templates
> See `references/cloud-cost-modeling.md` for infrastructure cost models

---

### Stage 5 — Product Development / Prototyping

**Business track**:
- MVP scope via MoSCoW prioritization
- Agile sprints; usability testing; QA feedback loops

**Technical track**:

*Architecture & System Design*:
- Cloud reference architecture selection (SaaS / AI / data platform / API / edge)
- ADRs for every major technology decision
- Database selection: OLTP / OLAP / vector / NoSQL
- Scalability: horizontal scaling, Redis caching, CDN, async queues
- API design: REST / GraphQL / gRPC + OpenAPI spec

*AI / LLM Engineering (where applicable)*:
- LLM selection: proprietary vs. open-source; evaluation rubric
- RAG pipeline: ingestion → chunking → embedding → retrieval → reranking → response
- Prompt engineering, versioning, and A/B testing
- LLMOps: observability, fallback strategy, eval suite
- Evaluation: faithfulness, relevance, groundedness, latency, cost per query

*DevSecOps*:
- CI/CD pipeline (GitHub Actions / GitLab CI / Cloud Build)
- Infrastructure as Code: Terraform / Pulumi; Helm for Kubernetes
- Secrets management; SAST/DAST in CI; zero-trust IAM
- Testing pyramid: unit → integration → contract → e2e → load

*Observability*:
- Logs + Metrics + Traces (OpenTelemetry standard)
- SLIs / SLOs / error budgets defined before launch
- Alerting runbooks for every alert
- LLM cost dashboards and quality monitoring

**Deliverable**: Working MVP + ADRs + CI/CD live + observability configured +
security baseline + eval suite passing + load test done
**Gate**: Core flows work; security clean; observability live; load test passed

> See `references/devSecOps.md` for patterns
> See domain overlay for hardware/firmware/edge specifics

---

### Stage 6 — Market Testing

**Business track**:
- Beta / limited release; pricing experiments; A/B testing
- NPS, activation, retention data collection

**Technical track**:
- Canary deployment: 1% → 5% → 25% → 50% → 100%
- Feature flag rollout with kill-switch
- Real-load performance monitoring (p50/p95/p99 latency)
- LLM quality review on production traces
- Cost validation: actual vs. projected
- Security penetration test
- Data pipeline validation; analytics trustworthiness check
- On-call readiness verification

**Deliverable**: Market test report + performance benchmark + cost validation +
security pen test sign-off
**Gate**: Metrics meet targets; error rate below threshold; security passed; cost within model

---

### Stage 7 — Commercialization / Launch

**Business track**:
- GTM plan: positioning, messaging, channels, pricing
- Sales and support enablement; PR and demand generation

**Technical track — Launch Checklist**:
- [ ] Auto-scaling configured and tested under synthetic peak load
- [ ] Rollback plan documented and executable in < 15 minutes
- [ ] Status page live
- [ ] On-call rota active with escalation paths
- [ ] Rate limiting and DDoS protection active
- [ ] All secrets rotated; IAM permissions audited
- [ ] GDPR / data privacy compliance verified
- [ ] Backups tested and recovery time confirmed
- [ ] LLM prompt versions locked; fallback model configured (if applicable)
- [ ] API reference and getting-started guide published (for API/platform products)

**Deliverable**: GTM plan + signed-off technical launch checklist + runbooks + docs
**Gate**: All teams ready; technical checklist 100%; rollback tested

> See `references/launch-planning.md` for GTM templates

---

### Stage 8 — Post-Launch Review & Iteration

**Business track**:
- KPI tracking vs. targets; win/loss analysis; customer feedback
- Backlog prioritization for v2

**Technical track**:
- DORA metrics baseline: deployment frequency, lead time, MTTR, change failure rate
- LLM performance review: cost trend, eval scores, model re-evaluation
- Technical debt register: document shortcuts; prioritise paydown
- Security posture review; credential rotation; next pen test scheduled
- FinOps review: top 3 cost drivers; reserved capacity opportunities

**Deliverable**: Post-launch review + DORA metrics + debt register + cost plan + v2 roadmap
**Gate**: Shipped; learnings captured; next cycle planned

---

## Quick-Reference: Stage Summary Table

| Stage | Business Deliverable | Technical Deliverable | Gate Criteria |
|---|---|---|---|
| 1. Idea Generation | Idea backlog | Feasibility notes | 5–10 ideas |
| 2. Idea Screening | Ranked shortlist | Build/buy/integrate decision | Passes matrix |
| 3. Concept Testing | Concept brief | PoC + arch sketch | Validated |
| 4. Business Analysis | Business case | Cost model + team plan | ROI threshold |
| 5. Prototyping | Working MVP | ADRs + CI/CD + observability | All criteria met |
| 6. Market Testing | Test report | Perf + security sign-off | Metrics pass |
| 7. Launch | GTM plan | Technical checklist 100% | All teams ready |
| 8. Post-Launch | Review + roadmap | DORA + debt register | Shipped + learned |

---

## Domain Overlays Available

Load the relevant file from `references/domains/` when a domain is detected:

| Domain | File | Key Additions |
|---|---|---|
| Industrial IoT / Manufacturing | `iot-manufacturing.md` | CNC protocols, edge, OT/IT security, fleet ops |
| Healthcare / MedTech | `healthcare-medtech.md` | FDA, HIPAA, HL7/FHIR, clinical validation |
| FinTech / Banking | `fintech-banking.md` | PCI-DSS, KYC/AML, open banking, fraud |
| Retail / E-commerce | `retail-ecommerce.md` | POS, inventory, omnichannel, personalisation |
| AgriTech / Food | `agritech-food.md` | Field sensors, precision farming, traceability |
| EdTech / Learning | `edtech-learning.md` | LMS, SCORM/xAPI, accessibility, assessments |
| Logistics / Supply Chain | `logistics-supplychain.md` | Fleet, last-mile, warehouse, route optimisation |
| Energy / CleanTech | `energy-cleantech.md` | Grid, SCADA, EV charging, smart meters |
| Real Estate / PropTech | `real-estate-proptech.md` | BMS, smart building, tenant, lease management |
| Government / Smart Cities | `government-smartcity.md` | GovTech, open data, citizen services, e-gov |

---

## Core Reference Files

- `references/concept-testing.md` — Stage 3 validation methods
- `references/business-analysis.md` — Financial modeling, Stage 4
- `references/cloud-cost-modeling.md` — Cloud + LLM cost engineering
- `references/launch-planning.md` — GTM and launch templates
- `references/technical-poc.md` — PoC patterns and LLM evaluation
- `references/devSecOps.md` — CI/CD, security, observability patterns
