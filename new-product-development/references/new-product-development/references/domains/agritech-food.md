# Domain Overlay: AgriTech / Food

Apply when product involves precision farming, crop monitoring, soil sensing,
drone application, irrigation, livestock management, or food traceability.

## Key Stage Additions

**Stage 2 — Screening**:
- Connectivity in rural areas: 2G/3G only in many farm locations; LoRaWAN or
  satellite (Starlink) as fallback for remote fields
- Seasonal usage pattern: product may have 3-month peak; model accordingly
- Subsidy and government scheme eligibility: PM-KISAN, NABARD, state agri schemes

**Stage 3 — Concept Testing**:
- Farmer literacy level: voice interface or vernacular language UI may be required
- Field trial: test sensors in real soil, weather, and crop conditions — lab results
  do not predict field performance

**Stage 4 — Business Analysis**:
- Input cost savings model: fertiliser, water, pesticide reduction as primary ROI
- Yield improvement model: % yield increase × crop price × acreage
- Aggregator / FPO (Farmer Producer Organisation) as distribution channel — model
  B2B2C unit economics

**Stage 5 — Development**:
- Sensor integration: soil moisture (capacitive), NPK sensors, weather stations,
  drone NDVI imagery — validate calibration drift over time
- LoRaWAN / NB-IoT: low-power wide-area protocols for rural field coverage;
  use TTN (The Things Network) or private LoRa gateway
- Offline-first mobile app: Flutter or React Native with local SQLite sync;
  mandatory for poor connectivity zones
- Crop disease detection: CNN image classification on drone/phone camera imagery;
  train on local crop varieties — do not use global datasets without validation
- Food traceability: blockchain or centralised ledger for farm-to-fork tracking;
  QR code on packaging linking to batch provenance

**Stage 7 — Launch**:
- [ ] Field pilot across at least 3 agro-climatic zones before national launch
- [ ] Vernacular language support for top 3 regional languages in target geography
- [ ] Partnership with KVK (Krishi Vigyan Kendra) or agri-university for credibility

**Key Standards**: FSSAI (food safety, India), APEDA (export), ISO 22000 (food safety
management), eNAM integration (India national agri market)
