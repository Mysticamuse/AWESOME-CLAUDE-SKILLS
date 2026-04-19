# Domain Overlay: FinTech / Banking

Apply when product involves payments, lending, insurance, trading, digital wallets,
banking infrastructure, or financial data.

## Key Stage Additions

**Stage 2 — Screening**:
- Licensing requirement: payment institution, e-money licence, banking licence,
  NBFC registration — identify jurisdiction-specific requirement early
- Regulatory sandbox: RBI (India), FCA (UK), MAS (Singapore) sandbox availability
- Open banking readiness: PSD2 (EU), RBI Account Aggregator (India), CDR (Australia)

**Stage 3 — Concept Testing**:
- Compliance counsel review of product concept before any user testing
- KYC/AML flow validation: test identity verification and onboarding drop-off rate
- Fraud pattern modelling: identify top 5 fraud vectors before building

**Stage 4 — Business Analysis**:
- Interchange and payment scheme fees: Visa/Mastercard/UPI economics
- Regulatory compliance cost: legal, compliance officer, audit, reporting
- Fraud loss reserve: budget 0.5–2% of transaction volume for fraud losses
- Chargeback management cost

**Stage 5 — Development**:
- PCI-DSS Level 1: if storing/processing/transmitting card data — full audit required;
  use tokenisation (Stripe, Adyen, Braintree) to reduce PCI scope dramatically
- Encryption: end-to-end encryption for all financial data; HSM for key management
- KYC pipeline: document verification (OCR + liveness check) → sanctions screening
  (OFAC, PEP lists) → risk scoring
- AML transaction monitoring: rule-based + ML anomaly detection; SAR filing workflow
- Double-entry bookkeeping: ledger architecture must be immutable and auditable
- Idempotency: all payment APIs must be idempotent — duplicate request = same result
- Reconciliation: automated daily reconciliation against payment processor reports
- Rate limiting: strict per-user and per-IP limits on all financial endpoints
- 4-eyes principle: high-value operations require dual authorisation

**Stage 6 — Market Testing**:
- Regulatory approval before live money movement in any jurisdiction
- Penetration test by PCI-QSA approved firm
- Disaster recovery test: simulate payment processor outage; validate fallback

**Stage 7 — Launch**:
- [ ] PCI-DSS compliance certificate or SAQ completed
- [ ] RBI / SEBI / relevant regulator approval in hand
- [ ] Fraud monitoring live and alerting tested
- [ ] Customer grievance redressal mechanism in place (regulatory requirement)
- [ ] Data localisation compliance verified (RBI data localisation for India)

**Key Standards**: PCI-DSS, ISO 27001, RBI guidelines, SEBI regulations, PSD2,
GDPR/PDPB, SOC 2 Type II, SWIFT CSP (if applicable)
