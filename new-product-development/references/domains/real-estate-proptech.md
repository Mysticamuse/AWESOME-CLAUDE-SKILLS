# Domain Overlay: Real Estate / PropTech

Apply when product involves property management, smart buildings, tenant experience,
lease management, facility management, or construction technology.

## Key Stage Additions

**Stage 2 — Screening**:
- BMS integration: building management systems (Siemens Desigo, Johnson Controls
  Metasys, Honeywell) use BACnet, LonWorks, or Modbus — assess compatibility
- RERA compliance (India): Real Estate Regulation and Development Act implications
  for any product touching property transactions

**Stage 3 — Concept Testing**:
- Stakeholder mapping: property owner, facility manager, tenant, and broker have
  different needs — test with all four personas separately
- Physical environment test: smart building sensors must be validated in the
  actual building environment — HVAC noise, RF interference, concrete attenuation

**Stage 4 — Business Analysis**:
- OpEx reduction model: energy savings + maintenance cost reduction + tenant
  retention improvement = total building ROI
- AUM (Assets Under Management) as scaling metric for property management software
- Proptech revenue models: per-seat SaaS, per-unit/per-building, transaction fee

**Stage 5 — Development**:
- BACnet/IP and BACnet MS/TP: primary protocol for HVAC, lighting, access control
  in commercial buildings; use open-source BACpypes or commercial BACnet stack
- Digital twin: 3D building model (BIM / IFC format) linked to live sensor data;
  Autodesk Forge / Speckle for BIM integration
- Access control integration: OSDP (Open Supervised Device Protocol) for card readers;
  Wiegand (legacy); API integration with HID, Lenel, CCURE
- Energy management: ASHRAE 90.1 compliance reporting; automated demand response;
  tenant sub-metering and billing
- Tenant experience app: visitor management, amenity booking, maintenance requests,
  parcel notifications; push notifications via FCM/APNs
- Lease management: document storage, rent escalation automation, lease expiry
  alerts, CAM (Common Area Maintenance) charge calculation

**Stage 7 — Launch**:
- [ ] BMS integration tested in live building environment (not just lab)
- [ ] RERA compliance verified for transaction features
- [ ] Data privacy for tenant PII compliant with DPDP Act
- [ ] Physical security of IoT devices in common areas assessed

**Key Standards**: BACnet (ASHRAE 135), RERA 2016 (India), IGBC / LEED green
building, IFC (Industry Foundation Classes) for BIM, OSDP, ISO 41001 (facility management)
