# Domain Overlay: Logistics / Supply Chain

Apply when product involves fleet management, last-mile delivery, warehousing,
freight, route optimisation, or supply chain visibility.

## Key Stage Additions

**Stage 2 — Screening**:
- Integration complexity: existing TMS (Transport Management System), WMS
  (Warehouse Management System), ERP — assess API availability early
- GPS/telematics hardware: is hardware required or is BYOD (driver's phone) acceptable?
- Regulatory: vehicle fitness, driver licence validation, e-way bill (India GST)

**Stage 3 — Concept Testing**:
- Driver UX test: drivers use the app on the move — test one-handed operation,
  glanceability, and offline behaviour in low-signal areas
- Dispatcher workflow test: shadow dispatchers for a full shift before designing UI

**Stage 4 — Business Analysis**:
- Cost per delivery reduction model: route optimisation typically saves 10–20%
- Fleet utilisation improvement: asset tracking reduces idle time
- SLA breach penalty reduction: real-time ETA reduces customer escalations

**Stage 5 — Development**:
- Route optimisation: VRP (Vehicle Routing Problem) solver — use Google OR-Tools,
  Vroom, or OptaPlanner for open-source; HERE or Google Fleet Routing for managed
- Real-time tracking: WebSocket or SSE for live location push to customer;
  Kafka for high-volume event streaming from large fleets
- Geofencing: entry/exit events for depot, customer, and restricted zones;
  use H3 (Uber's hexagonal grid) for efficient geospatial indexing
- ETA prediction: ML model on historical trip data; factor in traffic, weather,
  driver behaviour
- Proof of delivery (POD): photo capture, e-signature, OTP confirmation;
  tamper-proof timestamped record
- Warehouse management: barcode / QR / RFID scanning; pick-pack-ship workflow;
  bin location management; cycle count automation
- e-Way Bill integration: GST e-way bill API (India) for goods movement compliance
- Driver app: offline-first mandatory; sync on reconnect; battery-efficient
  location polling (adaptive interval based on speed)

**Stage 7 — Launch**:
- [ ] Load test with peak vehicle count (festival season spike)
- [ ] GPS accuracy validated across urban, highway, and rural routes
- [ ] Driver app tested on low-end Android devices (target: Android 8+, 2GB RAM)
- [ ] e-Way Bill and GST compliance sign-off

**Key Standards**: AIS-140 (vehicle tracking standard, India), e-Way Bill (GST),
GDPR/DPDP (driver location data), ISO 28000 (supply chain security)
