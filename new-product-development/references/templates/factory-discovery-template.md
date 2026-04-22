# Template: Factory / Site Discovery

**Purpose**: Capture the information needed to plan and scope an integration at a
new customer site. Complete before any technical work begins.

---

## 1. Site Information
- Site name and location:
- Contact: (name, role, phone, email)
- OT/IT contact: (name, role, contact)
- Site visit date:
- Conducted by:

## 2. Production Environment
- Number of production lines:
- Number of machines in scope:
- Operating shifts: (hours per day, days per week)
- Planned downtime windows available for installation:

## 3. Machine Inventory

| Asset ID | Make | Model | Controller type | Controller firmware | Native protocol | Location / line |
|---|---|---|---|---|---|---|

## 4. Network Topology
- OT network architecture: (VLAN structure, zones, firewalls)
- Can edge devices connect to OT network? (Y/N + conditions)
- Is there internet access from OT zone? (Y/N — if no, describe path to cloud)
- Wi-Fi available on shop floor? (Y/N, coverage quality)
- Cellular signal quality: (operator, signal strength in key locations)
- Remote access policy: (VPN available? Any restrictions?)

## 5. Data Access
- Is machine data accessible without OEM permission? (Y/N per machine)
- OEM restrictions or NDAs required? (list)
- Existing historian or SCADA? (system name, vendor, accessible?)
- IT/OT team approval required? (Y/N, approval owner)

## 6. Installation Constraints
- Can hardware be permanently mounted? (Y/N, mounting constraints)
- Power available near machines? (voltage, socket type)
- Cable routing: (conduit available? Wireless preferred?)
- Safety requirements for installation: (PPE, permits, escort needed?)

## 7. Risk Flags
| Risk | Severity | Notes |
|---|---|---|
| Air-gapped OT network | High | Need local sync solution |
| No machine connectivity option | Critical | Escalate before committing |
| OEM restricts data access | High | Legal / commercial path needed |

## 8. Scope Confirmation
Based on this discovery:
- Machines in scope: [count]
- Protocols required: [list]
- Estimated installation time: [days]
- Blockers to resolve before start: [list]
- Recommended pilot start date: [date]
