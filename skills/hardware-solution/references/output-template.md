# Hardware Solution Output Template

Use this structure for a full formal design proposal. Scale detail to the request; for a scoped answer or existing-design review, use only relevant sections rather than filling every heading.

## 1. Proposal Summary

- Product goal:
- Recommended architecture:
- Recommendation rationale:
- Main risks:
- Next actions:

## 2. Requirements and Assumptions

| Item | Content | Status | Owner / due date (open items only) |
|------|---------|--------|-----------------------------------|
| Use case |  | Known / Assumption / Open |  |
| Power |  | Known / Assumption / Open |  |
| Communication |  | Known / Assumption / Open |  |
| Environment |  | Known / Assumption / Open |  |
| Cost / volume |  | Known / Assumption / Open |  |
| Certification / target market |  | Known / Assumption / Open |  |
| Supply-chain preference | China / Europe / Americas / Hybrid / No preference | Known / Assumption / Open |  |

## 3. User Decision Options

For a new design with a material unresolved trade-off, give 2–4 relevant choices before detailed selection. Omit this section for a focused request, user-directed architecture, or existing-design review.

| Option | Core orientation | Applicable conditions | Cost / Risk |
|--------|------------------|-----------------------|-------------|
| A |  |  |  |
| B |  |  |  |
| C |  |  |  |

## 4. Architecture Comparison

| Option | Architecture / sourcing direction | Regional candidates compared | Main trade-offs | Applicable conditions | Conclusion |
|--------|------------------------------------|------------------------------|-----------------|-----------------------|------------|
| A | China-first | China; compare relevant other regions |  |  | Recommended / Alternative / Not applicable |
| B | Europe/Americas ecosystem | Compare Europe and/or Americas as relevant, plus credible alternatives |  |  | Recommended / Alternative / Not applicable |
| C | Hybrid | Regions selected by subsystem |  |  | Recommended / Alternative / Not applicable |

## 5. Recommended System Block Diagram

**Required for new designs. ASCII only, high quality.**

- Use ASCII boxes (`+`, `-`, `|`), arrows (`-->`, `v`), and consistent alignment in a monospaced code block.
- Minimum content: power path, main controller, major interfaces, sensing/actuation, debug/production test.
- Annotate key rails and interfaces.
- Readable in plain text (aim for ≤100 columns).

Example:

```
+-------------+     +--------------+     +------------------+
| Power Input |---->| Protection   |---->| PMIC / Regulators|
| (USB/Battery)|    | (TVS, fuse)  |     | 3V3 / 1V8        |
+-------------+     +--------------+     +--------+---------+
                                                  |
                                         +--------v--------+
                                         |    MCU / SoC    |
                                         +--+-----+-----+--+
                                            |     |     |
                               +------------+     |     +------------+
                               v                  v                  v
                        +-------------+   +-------------+   +-------------+
                        | Interfaces  |   | Sensors/AFE |   | Debug/Test  |
                        +-------------+   +-------------+   +-------------+
```

## 6. Key Component Recommendations

| Module | Recommended part / package | Regional alternatives | Key parameters / authoritative evidence (revision, date) | Purchase / availability source | Footprint source | Trade-off / risk |
|--------|------------------------------|-----------------------|----------------------------------------------------------|-------------------------------|-----------------|------------------|
| Main controller |  |  |  |  |  |  |
| Power |  |  |  |  |  |  |
| Communication |  |  |  |  |  |  |
| Storage |  |  |  |  |  |  |
| Protection |  |  |  |  |  |  |

Use links where they can be verified. State the verification date for time-sensitive claims; identify aggregator results as leads, not final technical evidence.

## 7. Interface and Signal Planning

| Interface | Signal | Direction | Voltage level | Rate / Current | Protection / Constraints |
|-----------|--------|-----------|---------------|----------------|--------------------------|
|  |  |  |  |  |  |

## 8. Power Tree and Power Budget

| Rail | Source | Load | Estimated current | Control method | Notes |
|------|--------|------|-------------------|----------------|-------|
|  |  |  |  |  |  |

## 9. PCB and Mechanical Constraints

- Recommended layer count:
- Partitioning recommendations:
- High-speed / RF / analog constraints:
- Thermal constraints:
- Connector and mounting constraints:
- Test points and fixture constraints:

## 10. Firmware and Debug Impact

- Boot and update:
- Logging and debug interfaces:
- Low-power strategy:
- Calibration and production test:
- Interface agreements with the firmware team:

## 11. Risk List

| Risk ID | Risk | Impact | Probability | Verification action / linked test ID | Owner | Due |
|---------|------|--------|-------------|-------------------------------------|-------|-----|
| R-01 |  | Cost / schedule / reliability / certification | High / Medium / Low |  |  |  |

## 12. Validation Plan

| Test ID | Phase | Linked risk ID(s) | Test item / method | Measurable pass criteria | Owner / due |
|---------|-------|-------------------|--------------------|--------------------------|-------------|
| V-01 | EVT | R-01 |  |  |  |
| V-02 | DVT |  |  |  |  |
| V-03 | PVT |  |  |  |  |

## 13. Module Schematics

Include schematic-level fragments only when requested or required by the agreed handoff scope. Annotate device models, pin connections, power rails, and key parameter values.

### 13.1 Power Module

- Input protection and power path:
- DCDC/LDO topology and devices:
- Rail voltage/current budget:
- Key component values and pin connections:

### 13.2 Main-Controller Minimum System

- MCU/SoC model and package:
- Crystal / clock configuration:
- Reset and boot circuitry:
- Decoupling and power-pin connections:

### 13.3 Communication Interfaces

- Interface type and transceiver:
- Level shifting and protection:
- Termination and impedance matching:
- Connector pin definitions:

### 13.4 Sensing / Actuation Front-End

- Sensor / actuator model:
- Analog front-end and signal conditioning:
- Protection and isolation:
- Key parameter values and pin connections:

## 14. Decisions and Handoff

### Determined

List decisions supported by the available evidence and ready for the agreed next engineering step.

### Assumptions

| Assumption | Why it is needed | Impact if wrong | Owner / review date |
|------------|------------------|-----------------|--------------------|
|  |  |  |  |

### Open Items

| Item | Decision needed | Owner | Due date | Blocked progress? |
|------|-----------------|-------|----------|-------------------|
|  |  |  |  | Yes / No |

### High Risks

List risk IDs and linked verification test IDs. Do not duplicate the complete risk table here.
