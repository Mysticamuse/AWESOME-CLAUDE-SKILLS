# V1 — Baseline NPD Skill (Original)

This is the **original baseline version** of the New Product Development Claude Skill.
All subsequent versions (V3, V4) are built on top of this foundation.
Do not modify these files — they serve as the reference baseline.

---

## What V1 Contains

| File | Purpose |
|---|---|
| `SKILL.md` | Master skill — 8-stage NPD framework, business track only |
| `concept-testing.md` | Stage 3: Concept validation methods |
| `business-analysis.md` | Stage 4: Financial modeling, TAM/SAM/SOM |
| `launch-planning.md` | Stage 7: GTM plan and launch checklist |

**Total: 1 skill file + 3 reference files = 4 files**

---

## What V1 Covers (Business Track Only)

```
Stage 1 → Idea Generation          [SCAMPER, JTBD, customer interviews]
Stage 2 → Idea Screening           [scoring matrix, SWOT, strategic fit]
Stage 3 → Concept Testing          [surveys, focus groups, landing page tests]
Stage 4 → Business Analysis        [TAM/SAM/SOM, revenue model, break-even]
Stage 5 → Prototyping              [MVP scope, agile sprints, usability testing]
Stage 6 → Market Testing           [beta program, A/B testing, NPS]
Stage 7 → Launch                   [GTM plan, channels, pricing, enablement]
Stage 8 → Post-Launch Review       [KPI tracking, win/loss, backlog]
```

---

## V1 Limitations (Why V3 and V4 Were Built)

| Gap | What was missing |
|---|---|
| No technical track | No software architecture, DevSecOps, or cloud guidance |
| No domain context | Same generic advice for every industry |
| No hardware/device guidance | No firmware, edge, connectivity, or OT/IT guidance |
| No decision frameworks | Descriptive only — did not help make choices |
| No templates | No structured outputs Claude could fill in |
| No routing logic | Claude had to guess what was relevant |

---

## How to Install V1

1. Download `new-product-development-v1.skill` from this folder
2. Go to claude.ai → Settings → Skills → Install Skill
3. Upload the file

**Recommended**: Install V4 instead — it is a superset of V1 with everything V1 has plus much more.
