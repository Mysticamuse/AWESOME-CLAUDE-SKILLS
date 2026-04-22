# Capability Module: Fleet Operations

Load when the product involves managing a population of deployed field devices —
provisioning, monitoring, configuration, updates, and retirement.

---

## 1. Device Lifecycle States

```
MANUFACTURED → PROVISIONED → DEPLOYED → ACTIVE → DEGRADED →
MAINTENANCE → DECOMMISSIONED
```

Each state transition must be: triggerable (manually or automatically) ·
logged with timestamp and actor · reversible where appropriate

---

## 2. Zero-Touch Provisioning

### Provisioning Workflow
1. Device manufactured with unique identity (certificate or token) embedded
2. Device shipped to site; powered on; connects to provisioning endpoint
3. Provisioning service validates device identity
4. Device receives: site configuration · cloud endpoint · credentials · initial firmware
5. Device moves to DEPLOYED state; appears in fleet management dashboard
6. Site engineer verifies device on dashboard — no manual credential entry needed

### Provisioning Infrastructure Requirements
- Provisioning service: high availability (device may provision at any time)
- Device registry: single source of truth for all device metadata
- Configuration management: version-controlled config; per-device or group config
- Audit: every provisioning event logged with device ID, site, timestamp, operator

---

## 3. Fleet Observability

### Health Metrics Per Device
Track at minimum:
- Connectivity status: online / offline; time since last heartbeat
- Firmware version: current version; target version; update status
- Hardware health: battery level (if applicable); storage utilisation; memory usage;
  CPU temperature; uptime since last reset; reset reason
- Data quality: completeness % (received events / expected events); error rate
- Application metrics: relevant to product function (e.g. connection success rate)

### Fleet Dashboard Requirements
- Real-time status: % fleet online; alert on fleet-wide outage patterns
- Version distribution: % on each firmware version; track rollout progress
- Health heatmap: visualise device health by site and asset group
- Alert management: deduplicated alerts; escalation; snooze with expiry

---

## 4. OTA Rollout Governance

### Rollout Stages
1. **Canary**: 1–2 devices; monitor 24–48 hours before proceeding
2. **Early adopter**: 5–10% of fleet; monitor 1 week
3. **General availability**: 50% of fleet; monitor 48 hours
4. **Full rollout**: 100%

### Automated Halt Criteria
Pause rollout automatically if within 24 hours of a stage start:
- Device error rate increases > 5% vs. baseline
- Device offline rate increases > 3% vs. baseline
- Any critical crash report from updated devices

### Rollback Procedure
- Automatic rollback: device health check fails post-update → revert to previous partition
- Manual rollback: operator triggers rollback to previous version via fleet dashboard
- Rollback audit: log rollback event, reason, and outcome per device

---

## 5. Decommissioning

- Data export: export all device data before decommissioning
- Credential revocation: revoke device certificate immediately on decommission
- Remote wipe: trigger secure erase of device storage
- Registry update: mark device as DECOMMISSIONED; retain record for audit
- Hardware return: define RMA process for failed or end-of-life devices

---

## Key Standards
- NISTIR 8259: IoT device cybersecurity capability core baseline
- FIDO Device Onboard (FDO): open standard for zero-touch provisioning
- SUIT (IETF): software updates for IoT — secure OTA framework


---
