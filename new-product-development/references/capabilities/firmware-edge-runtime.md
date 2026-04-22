# Capability Module: Firmware & Edge Runtime

Load when the product includes embedded firmware, an edge runtime, local data processing,
offline operation, or OTA update capability.

---

## 1. Firmware Architecture

### OS / Runtime Selection
| Option | Use case | Trade-offs |
|---|---|---|
| Bare-metal (no OS) | Ultra-low-power sensors, deterministic timing | No multitasking; complex to maintain |
| FreeRTOS / Zephyr | MCU-based; real-time requirements | Good ecosystem; no MMU |
| Embedded Linux (Yocto, Buildroot) | Application processor; rich connectivity | Higher complexity; longer boot |
| Android (AOSP) | Consumer-style UI; app ecosystem | High resource requirement |
| NuttX | POSIX-compatible RTOS | Good for MCUs needing POSIX APIs |

### State Machine Design
- Define all device states explicitly: BOOT → INIT → CONNECTING → OPERATING →
  DEGRADED → ERROR → UPDATING → SHUTDOWN
- Every state transition must have: trigger condition · action on entry ·
  action on exit · timeout behaviour
- Degraded mode: device must operate with reduced capability when cloud is unavailable —
  define minimum viable local functionality
- Error recovery: classify errors as transient (retry) · recoverable (restart component) ·
  fatal (safe shutdown + report)

### Acquisition Loop
- Define sample rate per signal: align with Nyquist; balance with power budget
- Timestamping: apply hardware timestamp at point of acquisition — not at transmission;
  use hardware RTC with battery backup; sync to NTP when connected
- Data quality flags: GOOD · UNCERTAIN · BAD · MISSING — apply per reading;
  propagate quality through all downstream processing
- Ring buffer: circular buffer for acquisitions during offline periods;
  size = max offline duration × sample rate × bytes per sample × safety margin (2×)

---

## 2. Offline-First Design

### Store-and-Forward Pattern
- Local storage: SQLite for structured data; flat binary files for high-rate telemetry;
  RocksDB for high-throughput write-heavy workloads
- Write-ahead log (WAL): ensure no data loss on unexpected power loss —
  fsync after every critical write or batch
- Capacity management: define storage full behaviour —
  drop oldest · drop lowest priority · stop acquisition · alert operator
- Sync queue: ordered queue of unsynced records; dequeue on confirmed server receipt;
  exponential back-off on sync failure (1s → 2s → 4s → ... → 5min max)

### Sync Protocol Design
- Idempotency: every sync message must carry a unique ID; server deduplicates —
  safe to retry without double-counting
- Batch sync: bundle multiple records per HTTP/MQTT message; reduces connection overhead
- Delta sync: transmit only changes since last confirmed sync; reduces bandwidth
- Conflict resolution: define what happens when local and server have diverged;
  last-write-wins vs. server-authoritative vs. merge — document the policy

### Connectivity Management
- Connection lifecycle: DISCONNECTED → CONNECTING → CONNECTED → AUTHENTICATING →
  AUTHENTICATED → SYNCING → IDLE
- Reconnection strategy: exponential back-off with jitter; max interval cap
- Heartbeat: send keepalive on idle connection; detect silent disconnection
- Network selection priority: Ethernet > Wi-Fi > cellular (4G/LTE) > LoRaWAN/NB-IoT

---

## 3. OTA Update Architecture

### Update Strategy
| Approach | Description | When to use |
|---|---|---|
| A/B partition | Two full OS images; boot from known-good on failure | Most connected devices |
| Delta update | Send only changed binary sections | Bandwidth-constrained (cellular) |
| Component update | Update individual packages / containers | Container-based edge |
| Bootloader update | Update bootloader separately | Critical security patches |

### OTA Pipeline
1. Build system produces signed firmware artifact
2. Artifact uploaded to update server with version, target model, rollout group
3. Device polls for update (or receives push notification)
4. Device validates signature before applying
5. Update applied to inactive partition
6. Device reboots to new partition; runs health check
7. Health check passes → commit new partition as active
8. Health check fails → revert to previous partition; report failure

### OTA Security Requirements
- Code signing: firmware signed with vendor private key; device validates with
  embedded public key before applying any update
- Transport security: TLS 1.3 for all OTA download traffic
- Version downgrade protection: device rejects firmware older than minimum version
- Rollback capability: always maintain one known-good fallback image
- Staged rollout: 1% → 5% → 20% → 100% with automated halt on error spike

---

## 4. Watchdog and Reliability

- Hardware watchdog: independent hardware timer; firmware must kick it periodically;
  if firmware hangs, watchdog resets the device
- Software watchdog: application-level watchdog per critical thread / process
- Crash reporting: capture stack trace, register dump, and last-known state on crash;
  transmit on next connectivity window
- Uptime counter: track device uptime and reset count; use to detect instability patterns
- Memory management: no dynamic allocation in interrupt handlers; static allocation
  for time-critical paths; heap fragmentation monitoring in long-running deployments

---

## Key Standards
- IETF RFC 7252: CoAP (Constrained Application Protocol)
- MQTT v5.0: OASIS standard for IoT messaging
- SUIT (Software Updates for IoT): IETF standard for secure OTA
- Matter / Thread: smart device interoperability (consumer IoT)
