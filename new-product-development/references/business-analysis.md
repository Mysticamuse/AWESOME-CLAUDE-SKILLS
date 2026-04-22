# Business Analysis — Deep Dive (Stage 4)

## Purpose
Determine whether the product opportunity is financially viable and worth investing in.

---

## Market Sizing

### TAM / SAM / SOM Framework
- **TAM** (Total Addressable Market): Full global demand if you had 100% share
- **SAM** (Serviceable Addressable Market): Portion you can realistically serve
- **SOM** (Serviceable Obtainable Market): Realistic 3–5 year target share

**Two approaches**:
1. **Top-down**: Start from industry reports, apply % filters down to SOM
2. **Bottom-up**: Unit economics × number of target customers

---

## Revenue Model Options

| Model | Example | Key Metric |
|---|---|---|
| One-time purchase | Software license | Units sold |
| Subscription | SaaS | MRR / ARR |
| Freemium | Mobile app | Conversion rate |
| Usage-based | Cloud storage | Usage volume |
| Marketplace | Platform | GMV, take rate |
| Licensing | IP/Technology | Royalty % |

---

## Cost Structure

**Development costs (one-time)**:
- Engineering / design hours × rate
- Infrastructure setup
- Legal / compliance

**Ongoing costs (per year)**:
- COGS (hosting, support, delivery)
- Sales & marketing
- G&A overhead

---

## Key Financial Metrics to Calculate

| Metric | Formula |
|---|---|
| Gross Margin | (Revenue − COGS) / Revenue |
| LTV (Customer Lifetime Value) | ARPU × Avg. Customer Lifespan |
| CAC (Customer Acquisition Cost) | Sales + Marketing Spend / New Customers |
| LTV:CAC Ratio | LTV / CAC (target: ≥ 3x) |
| Payback Period | CAC / Monthly Gross Profit per Customer |
| Break-even | Fixed Costs / (Price − Variable Cost per Unit) |
| ROI | (Net Profit / Investment) × 100 |

---

## Business Case Document Structure

1. Executive Summary
2. Problem & Opportunity
3. Market Size (TAM/SAM/SOM)
4. Proposed Solution
5. Revenue Model & Pricing
6. Cost Estimates (Year 1–3)
7. P&L Projection (3 years)
8. Key Assumptions
9. Risk Assessment
10. Recommendation & Ask

---

## Risk Assessment Matrix

Rate each risk on **Likelihood** (1–5) and **Impact** (1–5):
- Risk Score = Likelihood × Impact
- High risk (≥ 15): Must have mitigation plan
- Medium risk (8–14): Monitor and plan
- Low risk (< 8): Accept

Common risks: technical feasibility, competitive response, regulatory, adoption, pricing.

---

## 3. Unit Economics Deep-Dive

### SaaS Unit Economics
- **ARR per customer** = seats × price per seat per year (or usage × rate)
- **Gross margin** = (ARR − hosting − support − third-party costs) / ARR; target > 70%
- **CAC payback period** = CAC / (MRR × gross margin %); target < 18 months
- **NRR (Net Revenue Retention)** = (starting ARR + expansion − churn − contraction) / starting ARR; target > 110%
- **Magic number** = (current quarter ARR − prior quarter ARR) × 4 / prior quarter S&M spend; target > 0.75

### Hardware + Software Unit Economics
- **Blended gross margin** = (software margin × software revenue + hardware margin × hardware revenue) / total revenue
- **Hardware margin floor**: below 30% hardware margin creates cash flow risk at scale
- **Attach rate**: % of hardware customers who also buy software/service; drives LTV
- **Field service cost per incident**: track and reduce; target < 5% of device ASP annually

---

## 4. Financial Model Structure (3-Year P&L)

| Line | Year 1 | Year 2 | Year 3 |
|---|---|---|---|
| Units sold / seats | | | |
| ASP / ARPU | | | |
| **Total Revenue** | | | |
| COGS (hardware + hosting + support) | | | |
| **Gross Profit** | | | |
| Gross Margin % | | | |
| R&D (engineering salaries + tools) | | | |
| Sales & Marketing | | | |
| G&A | | | |
| **Operating Loss / EBITDA** | | | |
| CAC | | | |
| LTV | | | |
| LTV:CAC ratio | | | |
| Months to payback | | | |
| Cash burn / runway | | | |

---

## 5. Sensitivity Analysis

Run three scenarios for every financial model:

| Variable | Bear (−20%) | Base | Bull (+20%) |
|---|---|---|---|
| ASP / price | | | |
| Sales cycle length | | | |
| Churn rate | | | |
| COGS per unit | | | |
| CAC | | | |

Document which variables have the highest impact on ROI — these are the assumptions to test first in pilots.
