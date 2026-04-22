# Capability Module: OT/IT Security

Load when the product operates across operational technology (OT) and information
technology (IT) boundaries, or when security of field-deployed devices is a concern.

---

## 1. Network Architecture

### Zone and Conduit Model (IEC 62443)
Segment networks into security zones based on trust level and function:

```
Zone 0: Safety systems (SIS) — completely isolated
Zone 1: Control systems (PLCs, DCS) — no external access
Zone 2: Supervisory systems (SCADA, HMI, Historians)
Zone 3: Operations network (Edge devices, gateways, local servers)
DMZ:    Data exchange zone — controlled conduit between OT and IT
Zone 4: Enterprise IT network
Zone 5: External / Internet
```

- Conduits connect zones: each conduit must be documented, justified, and minimised
- Unidirectional gateways (data diodes): for Zone 1/2 — data can only flow outward
- Firewall rules: whitelist only; deny all by default; review quarterly

### Network Segmentation Principles
- Separate OT devices from IT devices at Layer 2 (VLANs) and Layer 3 (firewall)
- No direct internet access from OT zone — all cloud communication via DMZ proxy
- Remote access: encrypted VPN with MFA; time-limited sessions; full audit log;
  never leave permanent remote access open
- Wireless: dedicated SSID for OT devices; WPA3; isolated from corporate Wi-Fi

---

## 2. Device Identity and Credentials

### Identity Model
- Each device has a unique, cryptographically verifiable identity
- Use X.509 certificates issued by an internal CA or cloud PKI
  (AWS IoT Core, Azure IoT Hub, GCP IoT Core all provide certificate management)
- Certificate lifecycle: issue → deploy → monitor expiry → rotate before expiry → revoke
- Certificate rotation: automated; minimum annually; immediately on compromise

### Credential Management
- No default or shared credentials across devices
- No hardcoded credentials in firmware or configuration files
- Credentials stored in hardware secure element (TPM, ATECC608, SE050) where possible
- Provisioning: zero-touch provisioning — device receives credentials from
  provisioning service on first boot; no manual credential entry on shop floor

### Authentication Patterns
- Device-to-cloud: mutual TLS (mTLS) — both device and server authenticate
- Operator UI: username/password + MFA; RBAC for role-appropriate access
- API access: short-lived JWT tokens; OAuth 2.0 client credentials for service accounts
- Physical access: PIN or NFC badge for device unlock in sensitive environments

---

## 3. Secure Communication

- All data in transit: TLS 1.3 minimum; disable TLS 1.0/1.1/SSL
- Certificate validation: never disable certificate verification; pin certificates
  for high-security device-to-cloud connections
- MQTT: use TLS (port 8883); never plain MQTT (port 1883) in production
- OPC UA: enable security mode Sign and Encrypt; disable None mode in production
- Message integrity: HMAC or digital signatures for high-integrity command channels

---

## 4. Audit, Monitoring, and Incident Response

### Audit Trail Requirements
- Log every: authentication attempt (success and failure) · configuration change ·
  firmware update · remote access session · credential operation
- Log format: structured JSON; include: timestamp · actor identity · action ·
  result · source IP · target asset
- Log retention: minimum 1 year; 3 years for regulated environments; immutable log

### Security Monitoring
- Anomaly detection: alert on: unusual data volumes · unexpected connection sources ·
  repeated authentication failures · unexpected protocol traffic
- Vulnerability management: scan firmware and software dependencies monthly;
  patch critical CVEs within 14 days
- Penetration testing: annual minimum; after significant architecture changes

---

## Key Standards
- IEC 62443: industrial cybersecurity — series of standards for OT security
- NIST SP 800-82: guide to industrial control systems security
- OWASP IoT Top 10: common IoT security weaknesses
- NERC CIP: critical infrastructure protection (North America, energy sector)


---
