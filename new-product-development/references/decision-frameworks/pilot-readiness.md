# Decision Framework: Pilot Readiness

Use before committing to a customer field trial. Score each dimension.
Minimum score to proceed: 4/5 on all critical dimensions.

---

## Readiness Scorecard

### Technical Readiness (Critical)
| Criterion | 1 | 3 | 5 |
|---|---|---|---|
| Core function | Broken or unstable | Works with workarounds | Fully functional |
| Data quality | Frequent errors | Occasional errors | Clean and validated |
| Reliability | Crashes regularly | Occasional restart needed | Stable for 2+ weeks |
| Installation | Manual, complex | Some manual steps | Repeatable, documented |
| Connectivity | Frequent drops | Occasional drops | Stable in pilot environment |

### Operational Readiness (Critical)
| Criterion | 1 | 3 | 5 |
|---|---|---|---|
| Monitoring | No visibility | Basic logs only | Full observability |
| Support coverage | No on-call | Business hours only | 24/7 escalation path |
| Rollback | Manual, risky | Possible with effort | Rehearsed, < 30 min |
| Documentation | None | Partial | Complete for pilot scope |

### Commercial Readiness (Important)
| Criterion | 1 | 3 | 5 |
|---|---|---|---|
| Success metrics | Undefined | Partially defined | Quantitative, agreed with customer |
| Pilot agreement | Verbal only | Email agreed | Signed pilot charter |
| Feedback cadence | No plan | Ad hoc | Weekly structured review |

### Go/No-Go Rule
- Any critical dimension < 3 → do not proceed; fix first
- All critical dimensions ≥ 4 AND all important dimensions ≥ 3 → proceed
- Document readiness scores before every pilot start


---

---

## Pre-Pilot Checklist (must complete before site visit)

### Technical
- [ ] Core product function works end-to-end without engineering support
- [ ] Installation can be completed by a non-engineer following documentation
- [ ] Device / application stable for minimum 2 consecutive weeks in staging
- [ ] Monitoring active: you will know within 5 minutes if something breaks
- [ ] Rollback or recovery procedure documented and tested
- [ ] Data collection validated: confirm data is accurate vs. a reference source

### Operational
- [ ] On-call contact identified and briefed for pilot duration
- [ ] Pilot runbook written: what to do for the 5 most likely failure scenarios
- [ ] Customer escalation path defined and communicated
- [ ] Weekly check-in cadence agreed with customer

### Commercial
- [ ] Pilot charter signed by both parties
- [ ] Success criteria agreed in writing
- [ ] Commercial path post-pilot discussed (not a surprise conversation at the end)

### Site-Specific
- [ ] Site survey completed: network, power, physical access confirmed
- [ ] OT/IT team buy-in obtained (not just the business sponsor)
- [ ] Installation window scheduled and confirmed
- [ ] Spare hardware on-site or available within 24 hours

**Rule**: If any item in the Technical section is unchecked, do not start the pilot.
