# Launch Planning — Deep Dive (Stage 7)

## Launch Strategy Options

| Type | Description | Best For |
|---|---|---|
| Soft Launch | Limited audience, low noise | De-risking, gathering early data |
| Phased Rollout | Geographic or segment-by-segment | Ops-heavy products, large scale |
| Big Bang | Full simultaneous launch with PR push | Consumer products, strong brand |
| Beta → GA | Invite-only → open | SaaS, developer tools |

---

## GTM Plan Components

### 1. Positioning & Messaging
- **Target customer**: Primary persona(s)
- **Core problem**: The pain you solve
- **Value proposition**: The #1 benefit
- **Differentiator**: Why you vs. alternatives
- **Proof points**: Evidence (data, testimonials, case studies)

### 2. Pricing & Packaging
- Final pricing tiers
- Freemium / trial strategy
- Discounting rules

### 3. Channel Strategy
| Channel | Role | Metrics |
|---|---|---|
| Organic search / SEO | Long-term awareness | Organic traffic |
| Paid ads | Demand capture | CAC, ROAS |
| Content marketing | Education | Leads, MQLs |
| Partnerships | Distribution | Partner-sourced revenue |
| Sales (direct/PLG) | Conversion | Win rate, ACV |
| PR / media | Credibility | Coverage, share of voice |

### 4. Launch Execution Checklist

**Product**
- [ ] Feature-complete for launch scope
- [ ] Critical bugs resolved
- [ ] Onboarding flow tested
- [ ] Pricing live in product

**Marketing**
- [ ] Website / landing page live
- [ ] Launch email sequence ready
- [ ] Social content scheduled
- [ ] PR assets prepared (press kit, embargo lifted)

**Sales**
- [ ] Sales deck updated
- [ ] Demo environment ready
- [ ] Pricing objection handling trained
- [ ] CRM set up for new pipeline

**Customer Success / Support**
- [ ] Help docs published
- [ ] Support queue ready
- [ ] Escalation paths defined

**Operations**
- [ ] Billing / provisioning working end-to-end
- [ ] Monitoring & alerting live
- [ ] Runbook for launch-day incidents

---

## Launch KPIs to Track (Week 1–4)

| KPI | Target (define before launch) |
|---|---|
| Signups / installs | _____ |
| Activation rate | _____ % |
| Day-7 retention | _____ % |
| Revenue / MRR | $_____ |
| NPS | _____ |
| Press mentions | _____ |
| Support ticket volume | < _____ /day |

---

## Post-Launch Cadence

- **Day 1**: Monitor real-time metrics, fix critical issues
- **Week 1**: Daily standup on launch metrics
- **Week 2–4**: Weekly review vs. targets
- **Month 2**: Full post-launch review (see Stage 8)

---

## 4. Messaging Architecture

### Message House Structure
Build one message house per launch. Everything written for the launch derives from this.

**Headline** (10 words max): The single most important thing the product does.

**Value proposition** (2 sentences): Problem + solution + primary outcome.

**Three supporting pillars** (one sentence each):
1. Pillar 1: [key benefit / capability]
2. Pillar 2: [key benefit / capability]
3. Pillar 3: [key benefit / capability]

**Proof points per pillar** (data, customer quotes, demonstrations):

**Persona-specific messages**: different emphasis for each buyer / user / influencer persona.

---

## 5. Launch Readiness Scoring

Score each dimension 1–5. Any dimension < 3 = launch blocker.

| Dimension | 1 | 3 | 5 | Your score |
|---|---|---|---|---|
| Product stability | Crashes regularly | Occasional bugs | Stable for 4+ weeks | |
| Pricing confirmed | Not decided | Internally agreed | Customer-tested | |
| GTM motion clear | No plan | Draft plan | Trained and ready | |
| Support ready | No coverage | Business hours | 24/7 SLA defined | |
| Monitoring live | No visibility | Basic metrics | Full observability | |
| Legal cleared | Not started | In review | Signed off | |

**Minimum to launch**: all dimensions ≥ 3; sum ≥ 24/30.

---

## 6. Post-Launch Monitoring Cadence

| Period | Cadence | Metrics reviewed | Owner |
|---|---|---|---|
| Day 1 | Hourly | Error rate, latency, sign-ups, support tickets | Engineering + PM |
| Week 1 | Daily | Activation, revenue, NPS responses | PM + Sales |
| Month 1 | Weekly | Retention, CAC, conversion, churn signals | PM + Growth |
| Quarter 1 | Monthly | ARR, LTV:CAC, NRR, DORA metrics | Leadership |
