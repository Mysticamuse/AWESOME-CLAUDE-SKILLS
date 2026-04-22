# Capability Module: Reliability & Validation

Load when the product must meet reliability targets, pass environmental qualification,
or go through structured field validation before commercial launch.

---

## 1. Reliability Engineering

### Reliability Targets
Define before hardware design begins:
- MTBF (Mean Time Between Failures): target based on product category and market expectation
- MTTR (Mean Time to Repair): target for field service; drives spare parts and support model
- Design life: intended operational life in years; drives component selection
- Warranty period: commercial commitment; must be backed by reliability data

### HALT / HASS Testing
- **HALT** (Highly Accelerated Life Testing): stress beyond spec limits to find failure modes;
  thermal cycling + vibration simultaneously; done during development
- **HASS** (Highly Accelerated Stress Screening): ongoing production screen;
  catch manufacturing defects before shipment; subset of HALT stresses
- Temperature cycling: ramp rate, dwell time, min/max temperatures
- Vibration: random vibration; six degrees of freedom simultaneously

---

## 2. Environmental Qualification

### Test Sequence (perform in this order to catch field failures early)
1. Visual inspection and baseline functional test
2. ESD (electrostatic discharge) per IEC 61000-4-2
3. EMC emissions and immunity per applicable standard
4. Temperature: operating range soak (high and low); thermal shock
5. Humidity: condensing and non-condensing
6. Vibration: sinusoidal and random per IEC 60068-2-6/64
7. Mechanical shock: half-sine pulse per IEC 60068-2-27
8. Drop test: onto concrete; defined height and number of drops
9. IP rating: dust and water ingress per IEC 60529
10. Final functional test: verify all functions after environmental stress

---

## 3. Field Validation

### Pilot Acceptance Criteria
Define quantitative pass/fail criteria before pilot starts:
- Data completeness: ≥ 99% of expected events received over pilot period
- Device uptime: ≥ 99.5% uptime over pilot period
- Connection stability: < 5 unexpected disconnections per device per week
- Data accuracy: ≤ 1% deviation vs. reference measurement for all numeric values
- User task completion: ≥ 95% of defined operator tasks completed without error or support

### Validation Matrix
Track validation status per requirement:

| Requirement | Test method | Pass criteria | Status | Evidence |
|---|---|---|---|---|
| IP65 ingress | IEC 60529 test | No ingress after 30min | PASS | Test report ref |
| Operating temp | IEC 60068-2-1/2 | Function at −10°C to +55°C | PASS | Test report ref |
| Drop 1.2m | IEC 60068-2-27 | No damage, functional after | IN PROGRESS | — |

> Use `templates/validation-matrix-template.md` for the full tracking template

---

## Key Standards
- IEC 60068: environmental testing series
- IEC 61000: electromagnetic compatibility
- MIL-STD-810H: environmental engineering considerations


---
