# Domain Overlay: Government / Smart Cities

Apply when product involves public sector services, e-governance, smart city
infrastructure, citizen engagement, or open data platforms.

## Key Stage Additions

**Stage 2 — Screening**:
- Tender / RFP process: government procurement in India goes through GeM (Government
  e-Marketplace), state tenders, or Smart Cities Mission RFPs — 6–18 month cycles
- GIGW compliance: Guidelines for Indian Government Websites — mandatory for all
  government-facing web products
- Data localisation: government data must stay within India (MeitY guidelines)

**Stage 3 — Concept Testing**:
- Citizen diversity: design for India's digital divide — support feature phones,
  IVR, assisted mode, and vernacular languages alongside smartphone app
- Government stakeholder mapping: elected official (vision), IAS officer (decision),
  department head (procurement), field worker (user) — all have different needs

**Stage 4 — Business Analysis**:
- Government funding sources: Smart Cities Mission, AMRUT, Digital India, state
  scheme budgets — identify the right scheme to align with
- Total cost of ownership over contract term: government contracts are typically
  5–7 years; model maintenance and support cost over full term
- SLA penalties: government contracts have strict uptime SLAs with financial penalties;
  model the risk

**Stage 5 — Development**:
- DigiLocker integration: citizen document verification via DigiLocker API
- Aadhaar / eKYC: Aadhaar-based authentication and eKYC for citizen identity
  (requires UIDAI AUA/KUA licence)
- UPI / BBPS: payment integration for government fee collection; BBPS for utility
  bill payments
- Open API / open data: publish data via open standards (JSON-LD, DCAT);
  integrate with data.gov.in for open datasets
- Accessibility: mandatory WCAG 2.1 AA; screen reader; high contrast mode;
  keyboard navigation — required for government contracts
- Multilingual: minimum 22 scheduled languages for national products; state-level
  products need local language as primary
- Audit and transparency: every government data action must be logged and auditable;
  RTI (Right to Information) compliance for public data

**Stage 6 — Market Testing**:
- Pilot city / district selection: choose a district with a cooperative Collector
  and functioning IT team — not the most complex urban ward
- Grievance redressal: CPGRAMS integration for citizen complaints is often mandated

**Stage 7 — Launch**:
- [ ] STQC (Standardisation Testing and Quality Certification) audit completed
- [ ] GIGW compliance verified
- [ ] NIC (National Informatics Centre) security audit completed
- [ ] GeM registration active for procurement eligibility
- [ ] Disaster recovery plan approved by government IT committee

**Key Standards**: GIGW, MeitY security guidelines, Aadhaar Act, IT Act 2000,
DPDP Act 2023, ISO 27001, GeM compliance, Smart Cities Mission standards,
OWASP Top 10 (mandatory for government applications)
