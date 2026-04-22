# Decision Framework: Protocol Selection

Use this framework to select the right industrial protocol for any integration.
Answer each question in sequence — the first match wins.

---

## Step 1 — What does the target machine natively support?

Check machine documentation and OEM support:
- If machine has OPC UA server → **use OPC UA** (richest information model, secure)
- If machine has MTConnect adapter → **use MTConnect** (read-only, good for CNC)
- If machine has Modbus TCP registers documented → **use Modbus TCP**
- If machine only has serial RS-232/RS-485 → **use Modbus RTU** via serial gateway
- If machine has vendor-specific API (FANUC FOCAS, Siemens S7, Haas NGC) →
  **use vendor API** via SDK; wrap in abstraction layer

## Step 2 — What is the required data freshness?

- < 100ms (real-time control, safety interlock) → **OPC UA pub/sub or PROFINET**;
  never use cloud round-trip for this latency class
- 100ms – 1s (process monitoring, fast anomaly detection) → **OPC UA client/server**
  or **Modbus TCP** at high poll rate
- 1s – 60s (operational monitoring, OEE calculation) → **Modbus polling** or
  **MTConnect streaming** or **OPC UA at low rate**
- > 60s (reporting, analytics, dashboards) → **MQTT to cloud** after local aggregation

## Step 3 — What is the security requirement?

- High security (plant IT policy, OT/IT crossing) → **OPC UA with Sign+Encrypt**;
  never use plain Modbus across security zones
- Medium (internal OT zone only) → Modbus TCP with network segmentation is acceptable
- Low (development/lab) → any protocol; use this phase to document final protocol choice

## Step 4 — What is the integration volume?

- 1–5 machine types → direct protocol implementation per machine type
- 6–20 machine types → consider a protocol normalisation layer / gateway
  (Kepware, Ignition, Node-RED industrial) to avoid n×m integration complexity
- 20+ machine types → industrial IoT platform with pre-built driver library is justified

## Protocol Comparison Summary

| Criterion | OPC UA | Modbus TCP | MTConnect | MQTT | Vendor API |
|---|---|---|---|---|---|
| Security built-in | ✅ | ❌ | ❌ | ✅ (TLS) | Varies |
| Information model | Rich | Register map | XML schema | None | Vendor-defined |
| Bidirectional | ✅ | ✅ | Read-only | ✅ | Varies |
| Real-time capable | ✅ | ✅ | No | No | Varies |
| Ecosystem support | Growing | Universal | CNC-specific | IoT/Cloud | Machine-specific |
| Implementation complexity | High | Low | Medium | Low | High |
