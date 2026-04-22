# Decision Framework: Edge vs. Cloud Partitioning

Use this framework to decide what logic runs locally on the device/gateway
versus centrally in the cloud.

---

## Partitioning Principles

Run at the **edge** when:
- Latency requirement < 100ms (cloud round-trip cannot meet this)
- Connectivity is unreliable or intermittent (must work offline)
- Bandwidth is constrained (transmitting raw high-rate data is too expensive)
- Data privacy or regulatory requirement prohibits cloud transmission
- Safety or control action must not depend on external availability

Run in the **cloud** when:
- Requires data from multiple assets or sites for correlation
- Requires historical data for trend analysis or ML training
- Storage requirement exceeds edge capacity
- Elastic compute is needed (ML inference at scale, batch analytics)
- Multi-user access or cross-organisation sharing is needed

---

## Partitioning Decision Matrix

| Function | Edge | Cloud | Notes |
|---|---|---|---|
| Data acquisition | ✅ Always | ❌ | Must happen locally |
| Timestamping | ✅ Always | ❌ | Apply at source |
| Validation / quality flagging | ✅ | | Catches bad data early |
| Filtering (remove noise) | ✅ | | Reduce transmission volume |
| Aggregation (min/max/mean) | ✅ | | Downsample before cloud |
| Alerting on local threshold | ✅ | Optional | Edge alert for low-latency response |
| Offline buffering | ✅ Always | N/A | Required for connectivity resilience |
| Cross-asset correlation | ❌ | ✅ | Requires data from multiple sources |
| Historical trend analysis | ❌ | ✅ | Requires long time-series |
| ML model training | ❌ | ✅ | Requires large compute + labelled data |
| Lightweight ML inference | Optional | ✅ | Edge only if latency or privacy requires |
| Multi-user dashboards | ❌ | ✅ | Cloud-hosted |
| Configuration management | Optional | ✅ | Source of truth in cloud |
| OTA update orchestration | ❌ | ✅ | Managed centrally |

---

## Bandwidth Estimation Guide

Before deciding what to stream vs. aggregate:
- Calculate raw data rate: fields per message × bytes per field × messages per second
- Calculate aggregated data rate: fields per aggregate × bytes per field × aggregates per minute
- Calculate cost at scale: data rate × number of devices × cloud ingestion cost per GB
- If raw streaming cost > aggregation cost by > 3×, aggregate at edge

---
