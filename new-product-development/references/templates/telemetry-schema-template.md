# Template: Telemetry Schema

**Purpose**: Define the canonical data model for a product's telemetry streams.
Every field must be defined before implementation begins.

---

## Asset Profile
- Asset type:
- Asset manufacturer / model (example):
- Protocol(s):
- Sample rate (default):
- Offline buffer duration required:

## Event Schema: Telemetry (periodic readings)

| Field | Type | Unit | Range | Nullable | Quality flag | Description |
|---|---|---|---|---|---|---|
| schema_version | string | — | "1.0" | No | — | Schema version for migration |
| event_id | uuid | — | — | No | — | Unique per event |
| asset_id | string | — | — | No | — | Globally unique asset identifier |
| timestamp_utc | datetime | UTC ms | — | No | — | Timestamp at source acquisition |
| ingestion_timestamp_utc | datetime | UTC ms | — | No | — | Timestamp at platform receipt |
| quality | enum | — | GOOD/UNCERTAIN/BAD/MISSING | No | — | Overall event quality |
| [field_1_name] | [type] | [unit] | [min–max] | [Y/N] | [Y/N] | [description] |

## Event Schema: State Change

| Field | Type | Description |
|---|---|---|
| previous_state | enum | State before transition |
| current_state | enum | State after transition |
| transition_reason | string | Human-readable reason |
| operator_id | string | If manually triggered |

## Machine State Enum Values
| Value | Description | Maps from (vendor-specific) |
|---|---|---|
| ACTIVE | Producing | |
| IDLE | Powered, not producing | |
| FAULT | Alarm or error condition | |
| SETUP | Setup or toolchange | |
| OFFLINE | No connectivity / power | |

## Unit Register
| Field | Source unit | Target unit | Conversion formula |
|---|---|---|---|

## Change Log
| Version | Date | Author | Change |
|---|---|---|---|

---
