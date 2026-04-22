# Capability Module: Device Engineering

Cross-cutting guidance for any product that includes physical hardware —
handheld devices, embedded systems, sensors, edge nodes, or field-deployed equipment.
Load this module whenever the product has a physical form factor.

---

## 1. Requirements Definition

### Environmental Classification
Before selecting any hardware, classify the operating environment:

| Dimension | Range to define |
|---|---|
| Ambient temperature | Operating min/max °C; storage min/max °C |
| Humidity | % RH operating; condensing or non-condensing |
| Vibration | Frequency (Hz) and amplitude (g); continuous vs. shock |
| Ingress | Dust and water exposure class → IP rating target |
| Drop / impact | Drop height (m); surface hardness; drop count per device life |
| Chemical exposure | Oils, solvents, cleaning agents, UV — list all likely exposures |
| Altitude | Relevant for aviation, mountain, or pressurised environments |

### IP Rating Selection Guide
- IP54: dust partial protection + splash from any direction — minimum for field use
- IP65: dust-tight + low-pressure water jet — outdoor and light industrial
- IP67: dust-tight + immersion 1m/30min — washdown environments
- IP68: dust-tight + continuous immersion — defined by manufacturer
- IP69K: high-pressure, high-temperature washdown — food processing, heavy industrial

### User Ergonomics Requirements
- Grip and form factor: one-hand vs. two-hand operation; gloved use?
- Weight target: handheld devices should not exceed 400g for prolonged use
- Display: outdoor readability (nits), glove-compatible touch, sunlight contrast ratio
- Controls: button size and tactile feedback for gloved / noisy environments
- Carrying: lanyard, holster, belt clip, chest mount — define primary carry mode
- Accessibility: one-hand emergency stop; clear visual and tactile orientation cues

---

## 2. Hardware Architecture

### Processing Selection
- Application processor: ARM Cortex-A series for Linux / Android / rich OS
- Microcontroller: ARM Cortex-M series for bare-metal / RTOS real-time workloads
- FPGA: deterministic timing, custom IO, signal processing — use only when justified
- DSP / NPU: on-device ML inference acceleration (NVIDIA Jetson, NXP i.MX, STM32 with
  CubeAI, Qualcomm Hexagon)
- Selection criteria: compute need · power budget · thermals · supply chain risk ·
  development ecosystem maturity

### Memory and Storage
- RAM: define minimum for OS + application + buffers + safety margin (2×)
- Flash storage: calculate: OS + application + log buffer + offline data buffer +
  OTA update staging partition + headroom (20%)
- A/B partition scheme: mandatory for safe OTA — device can always roll back
- Wear levelling: use industrial-grade eMMC or industrial SD with wear levelling;
  avoid consumer-grade SD cards for write-intensive applications
- Encryption at rest: AES-256 for all stored data on field devices

### Power Architecture
- Battery chemistry selection:
  - Li-ion / Li-Po: high energy density, temperature-sensitive, requires BMS
  - LiFePO4: safer, better thermal stability, lower energy density
  - Primary (non-rechargeable): Lithium thionyl chloride for low-drain IoT sensors
- Battery sizing: (peak current × peak duration) + (idle current × idle duration) ×
  target runtime × temperature derating factor × end-of-life derating (80%)
- Charging: USB-C PD preferred; POGO pin for rugged dock charging;
  define charge rate and thermal limits
- Power states: define all states (active / low-power / sleep / deep-sleep / off)
  and transition logic; measure current in each state
- Hot-swap / UPS: supercapacitor or secondary cell to complete writes on power loss
- Battery management system (BMS): cell balancing, overcharge, over-discharge,
  short-circuit, temperature protection — never omit

### Thermal Design
- Calculate thermal dissipation: worst-case CPU load + radio TX power + display backlight
- Thermal budget: maintain junction temperature < rated max under worst-case ambient
- Cooling path: passive heatsink → thermal pad → enclosure wall (preferred for IP-rated);
  forced air only if enclosure allows
- Thermal testing: 24-hour soak at max operating temperature + max CPU load

---

## 3. Enclosure and Mechanical Design

### Enclosure Strategy Options
| Approach | Pros | Cons | When to use |
|---|---|---|---|
| Custom injection mould | Best fit, branding, IP | High NRE, long lead | Volume > 5K units |
| Modified COTS ruggedised | Fast, proven IP | Limited differentiation | Prototype / early pilot |
| Extruded aluminium | Good thermal, durable | Limited shape options | Industrial box products |
| 3D printed (SLS/MJF) | Fast iteration | Not production-grade | Prototype only |

### Key Mechanical Considerations
- PCB mounting: vibration-resistant standoffs; no cantilevered connectors
- Connector selection: IP-rated connectors (M8, M12 circular) for harsh environments;
  USB-C with retention for field use
- Cable strain relief: all cable exits require strain relief moulding or clamp
- Sealing: O-ring vs. gasket vs. overmoulding — define for each aperture
- Serviceability: can battery and main PCB be replaced in field? Define tool requirements
- Labelling: permanent marking (laser etching preferred); include serial number,
  model, regulatory marks, and safety symbols

---

## 4. Compliance and Certification

### Mandatory Certifications by Market
| Market | Certifications |
|---|---|
| India | BIS (Bureau of Indian Standards), WPC (wireless), BEE (energy) |
| EU | CE marking (RED + LVD + EMC directives), WEEE, RoHS |
| USA / Canada | FCC (Part 15/22/24), IC (Canada), UL/ETL listing |
| Australia | RCM mark |
| Global radio | IEEE 802.11 (Wi-Fi), Bluetooth SIG, LoRa Alliance certification |

### Certification Planning
- Budget 3–6 months for first-time certification; 4–8 weeks for subsequent similar products
- Use pre-certified radio modules to reduce RF testing scope significantly
- EMC pre-compliance testing in-house before formal testing reduces failure risk
- Maintain a compliance matrix: each certification · standard · test house · timeline · cost

---

## 5. Supply Chain and Manufacturing Readiness

### Component Sourcing
- Single-source risk: identify any single-source components; qualify alternates
- Lead time management: long-lead components (displays, custom ASICs) — order early
- Component obsolescence: check PCN (product change notices) before design lock
- BOM cost optimisation: target BOM cost for pricing model viability at volume

### Design for Manufacture (DFM)
- PCB design rules: minimum trace/space per fab capability; panelisation for assembly
- Component placement: test point access; no components under shields without reason
- Assembly: SMT preferred over through-hole; minimise hand-assembly steps
- Testing: in-circuit test (ICT) or flying probe; functional test fixture design

### Manufacturing Stages
- EVT (Engineering Validation Test): 10–20 units; validate design intent
- DVT (Design Validation Test): 50–100 units; validate against all specifications
- PVT (Production Validation Test): 200–500 units; validate manufacturing process
- MP (Mass Production): full rate; ongoing SPC and quality monitoring

---

## Key Standards
- IEC 60529: IP ratings
- IEC 62133: battery pack safety
- MIL-STD-810: environmental testing (defence / harsh industrial reference)
- IEC 61010: safety for electrical equipment for measurement and control
- ISO 9001: quality management system for manufacturing
