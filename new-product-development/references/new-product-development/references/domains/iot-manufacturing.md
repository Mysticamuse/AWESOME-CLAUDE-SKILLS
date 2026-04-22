# Domain Overlay: Industrial IoT / Manufacturing

Apply this overlay on top of the core NPD framework when the product involves
shop floor connectivity, CNC machines, edge devices, factory automation, or
industrial data collection.

---

## Stage 1 — Idea Generation (IIoT additions)
- Map existing machine connectivity gaps on the shop floor
- Interview operators and maintenance technicians — not just managers
- Identify manual data collection workflows that can be automated
- Review OEM machine data availability: what does the machine already expose?
- Look for downtime patterns — predictive maintenance is a high-value entry point

---

## Stage 2 — Idea Screening (IIoT additions)
- **Protocol feasibility**: does the target machine support MTConnect, OPC UA,
  Modbus TCP/RTU, FANUC FOCAS, Siemens S7, Haas NGC, or serial/PLC gateway?
- **Network feasibility**: is the shop floor air-gapped? What is the OT network topology?
- **Environmental constraints**: temperature range, vibration, dust, coolant exposure —
  will COTS hardware survive? Do you need IP65/IP67/IP69K rated enclosures?
- **Operator literacy**: can shop floor workers use a touchscreen or is a ruggedised
  keypad required?
- **IT/OT boundary**: who owns the network — IT or OT team? Get both in the room early

---

## Stage 3 — Concept Testing (IIoT additions)
- **Protocol PoC**: connect to one real machine in a test environment; validate data
  quality, polling rate, and tag mapping before committing to architecture
- **Operator usability test**: run a paper prototype or mockup test with actual
  technicians on the shop floor — not office staff
- **Offline-first assumption test**: simulate network outage; verify device behaviour
  and data buffering logic
- **Latency requirement definition**: classify use cases by latency need:
  - Safety / real-time control: < 10ms (do not use cloud for this)
  - Process monitoring: 100ms–1s acceptable
  - Analytics and reporting: minutes to hours acceptable

---

## Stage 4 — Business Analysis (IIoT additions)
- **OEE impact model**: quantify improvement in Overall Equipment Effectiveness
  (availability × performance × quality) — this is the primary ROI metric in manufacturing
- **Downtime cost calculation**: (hourly production value) × (estimated downtime
  reduction %) = annual savings
- **Hardware BOM cost**: edge device, enclosure, mounting hardware, cabling, gateway
- **Connectivity cost**: SIM card / private LTE / Wi-Fi infrastructure per site
- **Field installation cost**: technician time per machine × number of machines
- **Firmware maintenance cost**: OTA update infrastructure, version management
- **Regulatory cost**: IEC 62443 (OT security), CE/UL marking, functional safety
  assessment if touching control systems

---

## Stage 5 — Product Development (IIoT additions)

### Connectivity & Protocol Integration
- **MTConnect**: XML-based open standard; adapter + agent architecture; good for
  modern CNC machines (Mazak, Okuma, Haas with MTConnect option)
- **OPC UA**: rich information model; supports pub/sub and client/server; preferred
  for new industrial deployments; use open62541 or Python opcua library
- **Modbus TCP/RTU**: legacy but ubiquitous; simple register-based; use for PLCs,
  drives, sensors; poll interval typically 500ms–5s
- **Vendor APIs**: FANUC FOCAS2 (C library), Siemens S7 (snap7), Haas NGC (THINC API),
  Mitsubishi CNC (MX Component) — each requires vendor SDK and often NDA
- **Serial/PLC gateway**: RS-232/RS-485 to Ethernet bridge for legacy machines;
  use industrial protocol converters (Moxa, Advantech, Red Lion)

### Edge Architecture
- **Edge device selection**:
  - Raspberry Pi CM4 / industrial SBC: low cost, adequate for monitoring
  - NVIDIA Jetson: GPU-accelerated edge inference for vision or ML workloads
  - Ruggedised IPC: Beckhoff, Siemens IPC, Advantech — for harsh environments
  - Fanless design: mandatory for dusty/vibration-heavy environments
- **Offline-first data buffering**:
  - Store-and-forward: buffer to local SQLite / InfluxDB / flat files when offline
  - Sync on reconnect: MQTT QoS 1/2, or custom sync with conflict resolution
  - Buffer sizing: calculate max offline duration × data rate × message size
- **Edge processing**:
  - Filter and aggregate at edge: send summaries, not raw samples, to cloud
  - Anomaly detection at edge: run lightweight ML model locally (TensorFlow Lite,
    ONNX Runtime) for real-time alerting without cloud round-trip
  - Downsampling: reduce telemetry volume for non-critical signals

### OT/IT Security
- **Network segmentation**: OT network isolated from IT and internet; use DMZ
  with firewall between zones; never put edge devices directly on corporate LAN
- **Unidirectional gateways**: for high-security OT environments — data diode pattern
- **Device identity**: unique certificate per device; PKI-based mutual TLS
- **IEC 62443**: industrial cybersecurity standard — apply Zone and Conduit model
- **Firmware security**: secure boot, signed firmware images, encrypted storage
- **No default credentials**: enforce strong credential policy from factory provisioning

### Fleet Provisioning & OTA Updates
- **Zero-touch provisioning**: device boots, contacts provisioning server, receives
  config and certificates automatically — no manual setup on shop floor
- **OTA update strategy**:
  - Staged rollout: update 1 device → validate → 10% fleet → validate → full fleet
  - Atomic updates: A/B partition scheme; rollback to previous partition on failure
  - Offline update: USB fallback for air-gapped sites
- **Fleet management platforms**: Balena, Mender, AWS IoT Greengrass, Azure IoT Edge

### Device Reliability
- **Watchdog timer**: hardware watchdog restarts device if firmware hangs
- **Power management**: graceful shutdown on power loss; UPS or supercapacitor buffer
  to complete write operations before power cut
- **Operating temperature**: validate thermal design for shop floor range
  (typically −10°C to +55°C ambient; higher near furnaces or foundries)
- **Ingress protection**: IP65 minimum for coolant splash; IP67 for washdown areas
- **MTBF target**: set mean time between failures target early; design to it

---

## Stage 6 — Market Testing (IIoT additions)
- **Pilot site selection**: choose 1 factory with cooperative OT team, accessible
  machines, and manageable network — not your most complex site first
- **Machine diversity test**: validate against at least 3 different machine models
  or vintages during pilot
- **Connectivity stability KPI**: target > 99% data completeness over pilot period
- **Operator adoption metric**: are technicians actually using the interface?
  Track daily active device sessions per shift
- **OT team sign-off**: get formal approval from plant OT/maintenance lead before
  scaling — they can block the rollout if trust is not established

---

## Stage 7 — Launch (IIoT additions)
- [ ] Site survey checklist completed for each factory (network, power, machine access)
- [ ] Installation SOP documented: step-by-step for field technicians
- [ ] Remote access to edge devices configured (VPN tunnel or secure remote access
      platform — e.g. Secomea, Tosibox, TeamViewer IoT)
- [ ] Escalation path defined: device issue → edge → cloud → OEM support
- [ ] Spare device inventory: keep 5–10% spare units per deployed fleet
- [ ] Customer OT team trained on device maintenance and basic troubleshooting

---

## Stage 8 — Post-Launch (IIoT additions)
- **Fleet health dashboard**: % devices online, firmware version distribution,
  connectivity uptime, data completeness per machine
- **OEE trend report**: monthly OEE delta vs. pre-deployment baseline
- **Predictive maintenance accuracy**: if applicable, track alert precision and recall
- **Firmware version drift**: what % of fleet is on the latest version?
  Set target: > 95% within 30 days of release
- **Protocol coverage expansion**: which new machine types or protocols are customers
  requesting? Use to prioritise v2 connectivity roadmap

---

## Key Standards & Certifications (IIoT)
- **IEC 62443**: Industrial cybersecurity — OT network security levels
- **MTConnect**: ANSI/MTC1.4 — open CNC data standard
- **OPC UA**: IEC 62541 — unified architecture for industrial interoperability
- **CE marking**: required for sale in EU — EMC and safety directives
- **UL listing**: required for North American market — electrical safety
- **IP rating**: IEC 60529 — ingress protection for dust and water
- **ATEX / IECEx**: required if deployed in explosive atmospheres (rare but critical)
