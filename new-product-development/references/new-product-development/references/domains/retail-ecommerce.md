# Domain Overlay: Retail / E-commerce

Apply when product involves online or offline retail, point-of-sale, inventory,
merchandising, loyalty, or omnichannel customer experience.

## Key Stage Additions

**Stage 2 — Screening**:
- Channel strategy: D2C, marketplace (Amazon/Flipkart), omnichannel, or B2B wholesale?
- POS integration requirement: assess existing POS ecosystem (Shopify, WooCommerce,
  Magento, SAP Retail, Oracle Retail)
- Inventory management integration: ERP and WMS compatibility

**Stage 3 — Concept Testing**:
- A/B test product page or checkout flow variants before building
- Cart abandonment analysis: where do users drop off today?
- Customer lifetime value segmentation: which segments to target first?

**Stage 4 — Business Analysis**:
- GMV model: gross merchandise value projections by category and channel
- Take rate / commission model vs. SaaS subscription vs. per-transaction fee
- Logistics and fulfilment cost per order
- Return rate by category (apparel: 20–40%; electronics: 8–15%) — model this

**Stage 5 — Development**:
- Search and discovery: Elasticsearch or Algolia for product search; faceted filtering;
  personalised ranking using collaborative filtering or two-tower models
- Recommendation engine: frequently bought together, similar items, personalised
  homepage — use matrix factorisation or session-based models
- Inventory management: real-time stock updates; multi-warehouse routing;
  oversell prevention with optimistic locking or reservation pattern
- POS integration: Shopify POS API, Square, Razorpay POS — test card present flows
- Pricing engine: rule-based + dynamic pricing; promotion and coupon engine;
  bundle pricing logic
- Cart and checkout: idempotent order creation; payment gateway integration;
  address validation; tax calculation (GST in India, VAT in EU)
- Loyalty and rewards: points ledger (same double-entry pattern as FinTech);
  tier management; expiry logic
- CDN and image optimisation: product images are largest page weight; use WebP,
  lazy loading, and responsive images

**Stage 6 — Market Testing**:
- Peak load test: simulate Black Friday / Diwali sale traffic (10–50× normal load)
- Checkout conversion rate: baseline and target delta
- Search relevance: NDCG (Normalised Discounted Cumulative Gain) metric for search quality

**Stage 7 — Launch**:
- [ ] Payment gateway tested end-to-end with real cards (not just test mode)
- [ ] GST / tax engine validated with CA sign-off
- [ ] Returns and refund flow tested end-to-end
- [ ] CDN configured; page load < 3s on mobile 4G connection

**Key Standards**: PCI-DSS (payments), GST compliance (India), Consumer Protection
Act 2019 (India), GDPR/PDPB (data), ONDC integration (India open commerce network)
