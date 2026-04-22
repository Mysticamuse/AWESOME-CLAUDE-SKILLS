# Domain Overlay: Healthcare / MedTech

Apply when product involves patient data, clinical workflows, medical devices,
hospital systems, or health insurance.

## Key Stage Additions

**Stage 2 — Screening**:
- FDA classification: Is this a medical device? (Class I / II / III)
- HIPAA applicability: does product touch PHI (Protected Health Information)?
- HL7 FHIR / EHR integration requirement: Epic, Cerner, Meditech compatibility
- CE Mark (EU MDR 2017/745) vs. FDA 510(k) vs. De Novo pathway — pick early

**Stage 3 — Concept Testing**:
- Clinical workflow validation: shadow clinicians, not just administrators
- IRB (Institutional Review Board) approval needed for any patient data in testing
- Usability engineering per IEC 62366: document use errors and mitigations

**Stage 4 — Business Analysis**:
- Reimbursement model: CPT code coverage, insurance reimbursement pathway
- Hospital procurement cycle: typically 12–18 months; budget year dependency
- HIPAA BAA (Business Associate Agreement) cost and legal review
- FDA submission cost: $50K–$500K+ depending on pathway and device class

**Stage 5 — Development**:
- HIPAA technical safeguards: encryption at rest (AES-256) and in transit (TLS 1.3),
  audit logs, minimum necessary access, automatic session timeout
- HL7 FHIR R4 API: standard for health data interoperability; use SMART on FHIR
  for EHR app launch and OAuth2 patient authorisation
- IHE profiles: XDS, PIX, PDQ for document sharing and patient identity
- Software as Medical Device (SaMD): IEC 62304 software lifecycle standard
- 21 CFR Part 11: electronic records and signatures compliance (FDA)
- Audit trail: every PHI access logged with timestamp, user, action — immutable log
- De-identification: HIPAA Safe Harbor or Expert Determination method

**Stage 6 — Market Testing**:
- IRB approval for clinical pilot if involving patient outcomes
- Pilot site: academic medical centre preferred (credibility) or community hospital (speed)
- Clinical validation metrics: sensitivity, specificity, NPV, PPV if diagnostic product

**Stage 7 — Launch**:
- [ ] BAA signed with all subprocessors handling PHI
- [ ] Penetration test by HIPAA-specialised firm
- [ ] FDA clearance or 510(k) in hand before marketing as medical device
- [ ] SOC 2 Type II report available for hospital procurement

**Key Standards**: HIPAA, HL7 FHIR R4, IEC 62304, IEC 62366, IEC 60601, FDA 21 CFR,
EU MDR 2017/745, SOC 2 Type II, ISO 13485 (QMS for medical devices)
