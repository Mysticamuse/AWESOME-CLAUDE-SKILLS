# Capability Module: Industrial Connectivity

Load when the product must connect to machines, PLCs, sensors, SCADA systems,
or any industrial equipment. Covers protocol selection, device discovery, tag
mapping, data normalisation, and integration architecture.

---

## 1. Protocol Landscape

### Protocol Decision Matrix

| Protocol | Topology | Transport | Best For | Limitations |
|---|---|---|---|---|
| OPC UA | Client/Server + Pub/Sub | TCP (4840), HTTPS (443) | Modern machines; rich information model; secure | Requires OPC UA server on machine or gateway |
| Modbus TCP | Client/Server | TCP (502) | Legacy PLCs, drives, sensors; ubiquitous | No security; no data model; polling only |
| Modbus RTU | Master/Slave | RS-485 / RS-232 | Serial field devices; lowest cost | Half-duplex; slow; no error recovery |
| MTConnect | Agent/Adapter | HTTP (5000) | CNC machines with MTConnect option | Read-only; XML verbose; requires adapter |
| MQTT | Pub/Sub | TCP (1883), TLS (8883) | Cloud ingestion; async telemetry; IoT gateways | Not a machine protocol; needs adapter |
| EtherNet/IP | Client/Server | TCP/UDP | Rockwell / Allen-Bradley PLCs | Rockwell ecosystem; licensing implications |
| PROFINET | Controller/Device | Ethernet | Siemens ecosystems; real-time control | Real-time requires managed switch |
| BACnet/IP | Client/Server | UDP (47808) | Building automation; HVAC; access control | Not common in manufacturing |
| DNP3 | Master/Outstation | TCP / Serial | Utilities; SCADA; substations | Primarily utility sector |

### Protocol Selection Process
For any new integration, answer these questions in order:
1. What protocol does the target equipment natively support?
2. Does the equipment vendor provide an API or SDK?
3. Is there a gateway/adapter that can bridge to a preferred protocol?
4. What is the required data freshness? (real-time < 100ms → OPC UA pub/sub;
   monitoring 1s–60s → Modbus polling or OPC UA; reporting > 1min → MQTT)

> For a structured decision tree, see `decision-frameworks/protocol-selection.md`

---

## 2. Device Discovery and Connection Management

### Site Discovery Workflow
Before any integration work:
1. **Network scan**: identify all IP-addressable devices on OT subnet
   (use passive scan only in production — never active nmap against live OT)
2. **Machine inventory**: document make · model · controller type · firmware version ·
   native protocol · available data points · current network address
3. **OT topology map**: document network architecture — zones · firewalls ·
   switches · VLANs · air gaps
4. **Data access audit**: which tags / registers / nodes are accessible without
   modification to the machine? Which require OEM permission or configuration change?

### Connection Resilience
- Reconnection: exponential back-off with cap; log every reconnection event
- Connection pooling: maintain persistent connections to avoid repeated handshake overhead
- Health monitoring: poll connection health; alert on extended disconnection
- Graceful degradation: if machine connection lost, cache last known values with
  UNCERTAIN quality flag; do not silently serve stale data as good

---

## 3. Tag Mapping and Data Normalisation

### Tag Mapping Process
1. Obtain tag list from machine OEM or site engineer
2. Map each raw tag to a canonical data model (see `capabilities/telemetry-data-contracts.md`)
3. Apply unit conversion: document source unit and target unit for every numeric tag
4. Apply scaling: raw register value → engineering unit (e.g. 0–4095 ADC → 0–100 bar)
5. Apply data quality logic: define what constitutes a bad value for each tag
6. Validate: compare normalised values against machine HMI display during commissioning

### Canonical Machine State Taxonomy
Normalise machine states across all vendor-specific representations:

| Canonical state | Meaning | Typical raw values |
|---|---|---|
| ACTIVE | Machine producing | "RUNNING", "AUTOMATIC", mode=1 |
| IDLE | Powered, not producing | "READY", "STANDBY", mode=2 |
| FAULT | Machine in alarm/error | "ALARM", "ERROR", "FAULT", mode=4 |
| SETUP | Operator setup or toolchange | "SETUP", "MANUAL", mode=3 |
| OFFLINE | No data / connection lost | Timeout, no heartbeat |

---

## 4. Time Synchronisation

Time synchronisation is critical for industrial data. Without it, correlating events
across machines or with cloud data is unreliable.

- NTP synchronisation: all edge devices and gateways must sync to NTP;
  use local NTP server on OT network (not internet NTP from air-gapped networks)
- PTP (IEEE 1588): sub-microsecond precision for high-speed processes;
  requires PTP-capable switches
- Timestamp at source: apply timestamp at acquisition — not at gateway or cloud
- Time zone handling: always store UTC internally; apply local timezone only for display
- Clock drift monitoring: log and alert on drift > defined threshold
- Monotonic clock: use monotonic clock for interval measurements;
  use wall clock for timestamps only

---

## 5. Gateway Architecture

When direct protocol access to machines is not possible or practical:

### Gateway Roles
- **Protocol translation**: convert Modbus / proprietary → MQTT / OPC UA / REST
- **Data buffering**: store-and-forward when cloud connectivity is unavailable
- **Edge processing**: filter, aggregate, and downsample before cloud transmission
- **Security boundary**: terminate OT-side connections; present only normalised
  data to IT-side; never route arbitrary traffic across OT/IT boundary

### Gateway Selection Criteria
- Protocol support: covers all required source protocols
- Processing capability: adequate for edge compute requirements
- Reliability: fanless design; wide temperature range; watchdog
- Management: supports remote configuration and firmware update
- Security: certificate-based identity; encrypted storage; network segmentation support

---

## Key Standards
- OPC UA: IEC 62541 series
- MTConnect: ANSI/MTC1.4
- Modbus: modbus.org specification (de facto standard)
- MQTT: ISO/IEC 20922
- DNP3: IEEE 1815
- IEC 61158: industrial fieldbus standards family
