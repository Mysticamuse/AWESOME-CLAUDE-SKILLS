# Capability Module: Support Operating Model

Load when defining the post-launch support structure for a product, especially
field-deployed hardware or complex software.

---

## 1. Support Tier Model

### L1 — First Response (Customer / Operator)
- Self-service: online knowledge base, troubleshooting guides, FAQ
- Response time target: < 4 hours for operational issues; < 1 hour for critical
- Scope: common issues resolvable without engineering involvement
- Escalation trigger: issue not resolved within L1 SLA; customer requests escalation

### L2 — Technical Support (Internal Support Team)
- Scope: configuration issues, connectivity problems, data quality issues,
  non-critical software bugs
- Tools: remote access to device (VPN + SSH/agent); log retrieval; remote config push
- Response time target: < 8 hours for high; < 24 hours for medium
- Escalation trigger: hardware fault suspected; bug confirmed; data loss risk

### L3 — Engineering (Product / Field Engineering Team)
- Scope: firmware bugs, hardware failures, complex integration issues, data corruption
- Tools: full device access; firmware flashing; board-level diagnostics
- Response time target: < 24 hours for critical; < 3 days for high
- Escalation trigger: safety implication; data loss confirmed; systemic fleet issue

---

## 2. Field Service Model

### Spare Parts Strategy
- Identify all field-replaceable units (FRUs): battery, main PCB, display, enclosure
- Stock level formula: (annual failure rate × installed base × lead time weeks / 52) × 1.5
- Regional stocking: stock spares at regional depot for < 48h delivery to any site
- RMA process: fault diagnosis → RMA authorisation → shipment → receipt → repair/replace →
  return → close

### Site Troubleshooting Guide
Every support team member must be able to execute:
1. Verify device power (LED indicators, console output)
2. Verify network connectivity (ping, traceroute, agent heartbeat)
3. Retrieve device logs (remote pull or local USB)
4. Check firmware version and update status
5. Verify data completeness on dashboard
6. Execute factory reset procedure (last resort; data loss warning)

---

## 2. Support Tooling Requirements

- Remote access: secure, audited remote access to every deployed device
- Log aggregation: centralised log access per device and fleet-wide
- Diagnostic CLI: command-line interface for L2/L3 engineers via remote session
- Ticket system: SLA tracking, escalation routing, resolution time reporting
- Knowledge base: searchable; maintained by L3; updated after every new issue type

---

## Key Metrics
- First contact resolution rate (FCR): % issues resolved at L1 — target > 70%
- Mean time to resolve (MTTR): by tier and severity
- Customer satisfaction (CSAT): post-ticket survey score — target > 4.2/5
- Repeat contact rate: % customers who contact support again for same issue — target < 15%
- Escalation rate: % tickets escalated from L1 to L2 — benchmark against industry
