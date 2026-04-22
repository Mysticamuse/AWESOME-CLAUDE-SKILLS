---
name: new-product-development
description: >
  End-to-end framework for guiding teams through the New Product Development (NPD) process —
  from idea generation to post-launch review. Use this skill whenever a user mentions building
  a new product, launching something new, product ideation, go-to-market planning, MVP development,
  market testing, product roadmap, concept validation, business case for a new product, or anything
  involving taking an idea to market. Trigger even for partial requests like "we have an idea for
  a product" or "how do we validate this concept" — this skill covers all stages and can jump in
  at any point in the NPD lifecycle.
---

# New Product Development (NPD) Skill

This skill guides teams through structured, stage-gated new product development — from raw idea
to successful launch and beyond.

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

Claude should **identify where the user currently is** in this process, then provide targeted
help for that stage — while keeping the full pipeline in view.

---

## How to Use This Skill

1. **Identify the stage**: Ask the user where they are, or infer from context.
2. **Apply stage-specific guidance**: See stage details below.
3. **Use the right deliverable**: Each stage has a key output (see table).
4. **Apply gate criteria**: Before moving to the next stage, verify the go/no-go checklist.
5. **Reference the deep-dives**: For complex stages, read the relevant reference file.

---

## Stage-by-Stage Guide

### Stage 1 — Idea Generation
**Goal**: Collect a broad set of product ideas from diverse sources.

**Key activities**:
- Brainstorming (SCAMPER, How Might We, Jobs-to-be-Done)
- Customer interviews and pain point mapping
- Competitive gap analysis
- Internal innovation sessions

**Deliverable**: Idea backlog (documented list with source and brief rationale)

**Go/No-Go Gate**: At least 5–10 distinct ideas documented before moving to screening.

---

### Stage 2 — Idea Screening
**Goal**: Filter ideas down to 1–3 worth pursuing based on strategic fit and feasibility.

**Key activities**:
- Scoring matrix: strategic fit, market size, technical feasibility, competitive advantage
- SWOT analysis per idea
- Alignment check with company mission and resources

**Deliverable**: Ranked idea shortlist with scoring rationale

**Go/No-Go Gate**: Chosen idea scores above threshold on all critical dimensions.

---

### Stage 3 — Concept Development & Testing
**Goal**: Turn the idea into a concrete product concept and validate it with real users.

**Key activities**:
- Write concept statement (problem, solution, target user, key benefit)
- Develop 2–3 concept variants if uncertain
- Run concept tests: surveys, focus groups, landing page tests, Wizard of Oz prototypes
- Gather willingness-to-pay signals

**Deliverable**: Validated concept brief + customer feedback summary

**Go/No-Go Gate**: Target users understand and desire the concept; key objections are addressable.

> For detailed concept testing methods, see `references/concept-testing.md`

---

### Stage 4 — Business Analysis
**Goal**: Build the financial and strategic case for investing in this product.

**Key activities**:
- Market sizing (TAM / SAM / SOM)
- Revenue model and pricing strategy
- Cost estimation (COGS, development, marketing)
- Break-even and ROI analysis
- Risk assessment

**Deliverable**: Business case document with financial projections

**Go/No-Go Gate**: Projected ROI meets company threshold; risks are identified and mitigable.

> For financial modeling templates and guidance, see `references/business-analysis.md`

---

### Stage 5 — Product Development / Prototyping
**Goal**: Build the product (or MVP) and validate it technically and experientially.

**Key activities**:
- Define MVP scope (must-have vs. nice-to-have features)
- Agile sprints / iterative build cycles
- Usability testing with prototypes
- Internal QA and feedback loops
- Technical architecture decisions

**Deliverable**: Working MVP or prototype ready for external testing

**Go/No-Go Gate**: Core user flows work, critical bugs resolved, meets defined acceptance criteria.

---

### Stage 6 — Market Testing
**Goal**: Validate the product in real market conditions before full launch.

**Key activities**:
- Beta program / limited release to select users
- Pricing and packaging experiments
- Channel and messaging tests (A/B testing)
- Collect NPS, activation, retention data
- Iterate based on findings

**Deliverable**: Market test report with key metrics and go-to-market adjustments

**Go/No-Go Gate**: Key metrics (activation, retention, NPS) meet launch thresholds.

---

### Stage 7 — Commercialization / Launch
**Goal**: Bring the product to market at scale with a coordinated launch plan.

**Key activities**:
- Launch strategy: soft launch vs. full launch vs. phased rollout
- GTM plan: positioning, messaging, channels, pricing finalized
- Sales and support enablement
- PR, content, and demand generation
- Internal readiness: ops, CS, onboarding

**Deliverable**: GTM plan + launch execution checklist

**Go/No-Go Gate**: All cross-functional teams ready; launch criteria met.

> For GTM planning templates, see `references/launch-planning.md`

---

### Stage 8 — Post-Launch Review & Iteration
**Goal**: Measure launch success, learn, and plan the next iteration.

**Key activities**:
- Track KPIs vs. targets: revenue, activation, churn, NPS, feature usage
- Conduct win/loss analysis
- Gather ongoing customer feedback
- Prioritize product backlog for v2
- Document lessons learned

**Deliverable**: Post-launch review report + prioritized iteration roadmap

---

## Quick-Reference: Stage Summary Table

| Stage | Goal | Key Deliverable | Gate Criteria |
|---|---|---|---|
| 1. Idea Generation | Collect ideas | Idea backlog | 5–10 ideas documented |
| 2. Idea Screening | Filter to best idea | Ranked shortlist | Passes scoring matrix |
| 3. Concept Testing | Validate with users | Concept brief | Desired by target users |
| 4. Business Analysis | Build financial case | Business case doc | ROI meets threshold |
| 5. Prototyping | Build MVP | Working MVP | Core flows functional |
| 6. Market Testing | Real-world validation | Market test report | Metrics meet targets |
| 7. Launch | Go to market | GTM plan | All teams ready |
| 8. Post-Launch | Learn and iterate | Review + roadmap | Shipped; learnings captured |

---

## Common Deliverables Claude Can Help Create

- 📋 Idea scoring matrix
- 📄 Concept brief / one-pager
- 📊 Business case with financial model
- 🗺️ Product roadmap
- 📣 GTM (Go-To-Market) plan
- 📝 PRD (Product Requirements Document)
- 📈 Post-launch review report
- ✅ Stage gate checklists

---

## Key Frameworks to Apply (by context)

| Situation | Framework |
|---|---|
| Validating user need | Jobs-to-be-Done, Customer Journey Map |
| Sizing the market | TAM/SAM/SOM |
| Prioritizing features | MoSCoW, RICE scoring |
| Competitive positioning | Positioning Canvas, Blue Ocean |
| Launch readiness | RACI, GTM Checklist |
| Post-launch learning | OKRs, North Star Metric |

---

## Reference Files

Read these when going deep on a specific stage:

- `references/concept-testing.md` — Methods for Stage 3 concept validation
- `references/business-analysis.md` — Financial modeling for Stage 4
- `references/launch-planning.md` — GTM and launch templates for Stage 7
