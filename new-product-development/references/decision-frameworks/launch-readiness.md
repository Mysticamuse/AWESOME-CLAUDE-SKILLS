# Decision Framework: Launch Readiness

Use before committing to general availability (GA) launch.
Every item must be GREEN. Any RED is a launch blocker.

---

## Launch Readiness Checklist

### Product
- [ ] All P0 (critical) and P1 (high) bugs resolved
- [ ] Performance meets SLO targets under expected peak load (load test passed)
- [ ] Security penetration test completed; all critical/high findings resolved
- [ ] Rollback plan documented and rehearsed
- [ ] Status page live; incident communication process defined

### Commercial
- [ ] Pricing and packaging finalised and approved
- [ ] GTM motion defined: channels, messaging, ICP (ideal customer profile)
- [ ] Sales and support team trained; demo environment ready
- [ ] Customer contracts / T&Cs reviewed by legal

### Operations
- [ ] On-call rota active with escalation chain
- [ ] Runbooks written for top 10 failure scenarios
- [ ] Monitoring and alerting live and tested
- [ ] Data backup and disaster recovery tested

### Legal / Compliance
- [ ] Data privacy compliance verified (GDPR/DPDP/applicable law)
- [ ] All required certifications in hand
- [ ] IP (patent, trademark, copyright) cleared
- [ ] Third-party licences audited and compliant

### Launch Type Recommendation
| Signal | Recommended launch type |
|---|---|
| First version, unknown demand | Soft launch to waitlist / invite only |
| Validated demand, ops untested | Phased rollout (10% → 50% → 100%) |
| High confidence, strong ops | Full launch with PR |
| Enterprise / regulated | Private beta → limited GA → full GA |


---

---

## Launch Blocker Classification

| Category | Blocker type | Example | Resolution path |
|---|---|---|---|
| P0 — Safety | Can cause harm or data loss | Unprotected PII endpoint | Fix before any launch |
| P0 — Legal | Regulatory non-compliance | Missing data processing agreement | Fix before any launch |
| P1 — Functional | Core feature broken | Primary user flow fails | Fix before GA; soft launch possible |
| P1 — Stability | Frequent crashes or data errors | > 1% error rate | Fix before GA |
| P2 — Experience | Usability issues | Confusing onboarding | Can launch; fix in first sprint |
| P3 — Polish | Minor visual or copy issues | Typos, misalignment | Can launch; fix ongoing |

## Rollback Decision Tree

If a critical issue emerges post-launch:

```
Error rate > 5% above baseline?
  YES → Immediate rollback
  NO  → Is it growing?
          YES → Schedule rollback within 1 hour
          NO  → Monitor; hotfix within 4 hours

Data loss or corruption?
  YES → Immediate rollback + incident declared

Security breach suspected?
  YES → Immediate rollback + security team escalated
```

## Go/No-Go Meeting Agenda (day before launch)

1. Review launch readiness checklist: any RED items? (10 min)
2. Review monitoring and alerting: confirmed live? (5 min)
3. Review on-call: who is covering launch day? (5 min)
4. Review rollback: rehearsed? Executable in < 15 min? (5 min)
5. Formal go/no-go vote: Engineering · PM · Sales · Legal (5 min)
6. Record decision and attendees in writing
