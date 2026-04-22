# Concept Testing — Deep Dive (Stage 3)

## What is Concept Testing?
Exposing a product concept (not yet built) to potential customers to assess desirability,
clarity, and willingness to pay before investing in development.

---

## Methods by Cost & Fidelity

| Method | Cost | Time | Best For |
|---|---|---|---|
| Concept survey | Low | 1–2 days | Quick desirability check |
| Focus group | Medium | 1 week | Qualitative depth |
| Landing page test | Low | 3–5 days | Demand signal |
| Prototype test | Medium | 1–2 weeks | UX validation |
| Wizard of Oz | Medium | 2–3 weeks | Simulating product before building |
| Fake door / Smoke test | Low | 1 week | Validating specific feature demand |

---

## Concept Statement Template

```
For [target customer]
Who has [problem or need],
[Product name] is a [product category]
That [key benefit / unique value].
Unlike [competitor or alternative],
Our product [key differentiator].
```

---

## Key Questions to Answer in Concept Testing

1. **Clarity**: Does the user understand what the product does?
2. **Relevance**: Does this solve a real problem they experience?
3. **Desirability**: Do they want this product?
4. **Credibility**: Do they believe it can deliver on its promise?
5. **Willingness to pay**: What would they pay? (Van Westendorp or Gabor-Granger)

---

## Willingness-to-Pay: Van Westendorp Price Sensitivity Meter

Ask 4 questions:
- At what price would this be **too cheap** (low quality)?
- At what price would this be a **bargain / great value**?
- At what price is this **getting expensive but still worth it**?
- At what price is this **too expensive**?

Plot the curves to identify the **Acceptable Price Range** and **Optimal Price Point**.

---

## Success Criteria (go/no-go thresholds — adjust per context)

- **Purchase intent**: ≥ 60% "definitely/probably would buy"
- **Concept clarity**: ≥ 80% can correctly describe what the product does
- **Problem relevance**: ≥ 70% confirm they experience this problem
- **NPS-style rating**: Mean ≥ 7/10

---

## 3. Assumption Mapping Before Testing

Before selecting any test method, list all assumptions and rank by risk:

| Assumption | Type | Risk if wrong | Test method | Status |
|---|---|---|---|---|
| Users experience this pain daily | Desirability | High — no market | User interviews | |
| Users will pay $X for this | Viability | High — no revenue | Van Westendorp | |
| Integration X is technically feasible | Feasibility | High — can't build | Technical PoC | |
| Users prefer UI pattern A over B | Usability | Medium — low adoption | Prototype test | |

Test highest-risk assumptions first. Stop testing if a critical assumption fails — fix it before proceeding.

---

## 4. Technical PoC Framework

A PoC is not a prototype. It answers one question: does the riskiest technical assumption hold?

**PoC Charter** (complete before starting):
- Question being tested:
- Pass criteria:
- Time box: [2–5 days maximum]
- Who runs it:
- What we will build:
- What we will NOT build:

**PoC outputs**:
- Finding: [assumption validated / invalidated / partially validated]
- Evidence: [what was observed, measured, or demonstrated]
- Confidence: [high / medium / low] with rationale
- Implication for architecture: [proceed as planned / modify approach / pivot]

**Common PoC failure modes**:
- Scope creep: PoC becomes a prototype; costs 3× the budget
- Success theatre: PoC designed to validate not to challenge the assumption
- Wrong question: PoC tests easy things, not the hardest assumption

---

## 5. Concept Test Survey Template

**Screener** (qualify respondents):
- Role / industry / company size check
- Do they currently experience the problem? (required: yes)

**Problem validation**:
- How often do you experience [problem]? (scale: never to daily)
- How painful is this problem? (1–10)
- What do you do today to address it?

**Concept exposure**: show concept statement or mockup

**Concept reaction**:
- How clearly does this concept address your problem? (1–10)
- What is your immediate reaction? (open text)
- What is most appealing? (open text)
- What concerns you? (open text)
- Purchase intent: definitely / probably / probably not / definitely not would buy

**Pricing** (Van Westendorp):
- At what price would this be too cheap?
- At what price would this be a bargain?
- At what price is this expensive but still worth it?
- At what price is this too expensive?

**Minimum n**: 30 respondents for directional signal; 100+ for statistical confidence.
