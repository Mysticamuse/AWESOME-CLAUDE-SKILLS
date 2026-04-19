# Domain Overlay: Energy / CleanTech

Apply when product involves renewable energy, smart grids, EV charging, smart
metering, energy storage, SCADA, or microgrid management.

## Key Stage Additions

**Stage 2 — Screening**:
- Grid interconnection requirement: products that connect to utility grid need
  DISCOM approval and CEA (Central Electricity Authority) compliance in India
- Safety classification: high-voltage products require IEC 61010 / IS standards;
  identify safety requirement before architecture
- DNO / utility partnership: distribution network operator partnership often required
  for grid-connected products

**Stage 3 — Concept Testing**:
- Grid simulation: test against simulated grid conditions (voltage sag, frequency
  deviation, islanding) before connecting to real grid
- Energy yield validation: solar/wind yield models must be validated against
  actual irradiance / wind data for the target geography

**Stage 4 — Business Analysis**:
- LCOE model (Levelised Cost of Energy): primary metric for energy product ROI
- Carbon credit / REC (Renewable Energy Certificate) revenue modelling
- DISCOM / utility offtake agreement structure and payment terms
- PM Kusum, PLI scheme, MNRE subsidy eligibility (India)

**Stage 5 — Development**:
- SCADA / DERMS integration: Modbus, DNP3, IEC 60870-5-104, IEC 61850 protocols
  for grid communication
- Smart meter integration: DLMS/COSEM protocol; HES (Head End System) API
- EV charging: OCPP 1.6J / OCPP 2.0.1 (Open Charge Point Protocol); smart
  charging / V2G (vehicle-to-grid) if applicable
- Energy data platform: time-series database (InfluxDB, TimescaleDB) for high-frequency
  metering data; 15-minute interval minimum; sub-second for grid stability
- Demand response: event-driven load control; VPP (Virtual Power Plant) aggregation
  logic; real-time dispatch optimisation
- Battery management system (BMS) integration: SOC, SOH, temperature, cell voltage
  monitoring; cycle count and degradation modelling
- Cybersecurity for OT: IEC 62443, NERC CIP (North America); air-gap or data diode
  for critical grid control systems

**Stage 7 — Launch**:
- [ ] CEA / DISCOM approval obtained for grid-connected products
- [ ] BIS certification for electrical equipment (India)
- [ ] Cybersecurity assessment per IEC 62443 completed
- [ ] Grid islanding protection tested and certified

**Key Standards**: IEC 61850, IEC 62443, OCPP 2.0.1, DLMS/COSEM, CEA regulations,
IS 13947, BIS certification, MNRE guidelines, ISO 50001 (energy management)
