# Capability Module: Telemetry & Data Contracts

Load when the product generates, transmits, stores, or processes time-series data,
sensor readings, events, or machine telemetry.

---

## 1. Data Contract Principles

A data contract is the formal agreement between producers and consumers about the
structure, semantics, quality, and delivery guarantees of data.

Without data contracts:
- Downstream analytics break silently when upstream changes
- Units and timestamps are interpreted inconsistently
- Data quality issues are discovered in production, not at source

Every telemetry stream must define:
- **Schema**: field names, types, units, ranges, nullability
- **Semantics**: what each field means; what causes it to change
- **Quality**: how to interpret each value (GOOD / UNCERTAIN / BAD)
- **Delivery**: frequency, latency guarantee, ordering guarantee, deduplication

---

## 2. Canonical Event Schema

### Base Event Structure
Every telemetry event must include these mandatory fields:

```json
{
  "schema_version": "1.0",
  "event_id": "uuid-v4",
  "asset_id": "globally-unique-asset-identifier",
  "asset_type": "machine-type-enum",
  "site_id": "site-identifier",
  "event_type": "telemetry | state_change | alarm | heartbeat",
  "timestamp_utc": "ISO-8601 with milliseconds",
  "sequence_number": 12345,
  "source_timestamp_utc": "timestamp at acquisition point",
  "quality": "GOOD | UNCERTAIN | BAD | MISSING",
  "payload": { }
}
```

### Asset Identification
- Asset ID must be globally unique, permanent, and human-readable
- Recommended format: `{site_code}-{asset_type}-{serial_number}`
- Example: `PUNE01-LATHE-SN4823`
- Never use auto-increment IDs as asset identifiers — they break across systems

### Timestamp Rules
- Always UTC — no local time in stored events
- Millisecond precision minimum; microsecond for high-speed processes
- Source timestamp: when the reading was taken at the machine
- Ingestion timestamp: when the event arrived at the platform
- Always store both; never overwrite source with ingestion time
- ISO 8601 format: `2025-04-20T09:30:00.123Z`

### Quality Flags
- GOOD: value within range, fresh, validated
- UNCERTAIN: communication timeout < threshold; value may be stale
- BAD: out-of-range, sensor fault, comms timeout exceeded threshold
- MISSING: expected value not received; gap in time-series
- Propagate quality: if input is BAD, derived values must also be marked BAD or UNCERTAIN

---

## 3. Unit Normalisation

- Store all values in SI units internally: metres (not inches), °C (not °F),
  Pascal (not PSI), m/s (not RPM unless dimensionally meaningful)
- Apply unit conversion at ingestion — never downstream
- Document source unit and target unit in the tag mapping for every numeric field
- Include unit in field name for human-readable schemas: `spindle_speed_rpm`,
  `coolant_temp_celsius`, `feed_rate_mm_per_min`

---

## 4. Machine State Model

Define a formal state machine for each asset type. Minimum states:

```
OFFLINE → ONLINE → IDLE → ACTIVE → FAULT → SETUP
```

- Each state transition must produce a `state_change` event
- State duration must be computable from state change events
- OEE (Overall Equipment Effectiveness) is computed from state durations:
  - Availability = (ACTIVE + IDLE) / (ACTIVE + IDLE + FAULT + OFFLINE) × 100
  - Performance = actual output / theoretical output × 100
  - Quality = good output / total output × 100
  - OEE = Availability × Performance × Quality

---

## 5. Time-Series Storage Patterns

- Write path: buffer → validate → deduplicate → write to time-series DB
- Retention policy: hot (last 90 days, full resolution) → warm (90d–1yr, downsampled) →
  cold (archive, aggregated only)
- Downsampling: store raw + 1min aggregates + 1hr aggregates + 1day aggregates
- Aggregates: min, max, mean, stddev, count, first, last per interval
- Partitioning: partition by asset_id + time (monthly or weekly) for query performance
- Schema on read vs. write: prefer schema on write for operational data;
  schema on read only for exploratory analytics

---

## Key Standards
- ISO 8601: datetime representation
- OPC UA Part 8: data access (quality bits and timestamp patterns)
- Apache Avro / Protobuf / JSON Schema: schema definition formats
- OpenMetrics: metrics exposition standard (extends Prometheus format)
