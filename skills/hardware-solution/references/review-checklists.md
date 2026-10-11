# Hardware Review Checklists

Use these lists when reviewing a hardware design, schematic, PCB constraint set, BOM, or design proposal.

## Schematic Review

- Main-controller boot configuration, reset, clock, and download/debug interfaces are complete.
- Every power pin has appropriate decoupling; power-domain naming is clear.
- Power-IC feedback, inductor, capacitors, compensation, enable, PG, and soft-start match the datasheet.
- Input ports have reverse-polarity, over-voltage, surge, ESD, and short-circuit protection.
- External interface voltage levels match; isolation or level shifting is provided where needed.
- Pull-ups, termination, voltage levels, and address conflicts for I2C/SPI/UART/CAN/RS485 buses are explicit.
- Analog front-end has input protection, filtering, reference source, ground partitioning, and calibration path.
- USB/Ethernet/RF/high-speed interfaces retain impedance, ESD, common-mode chokes, and connector constraints according to reference designs.
- Battery and charging path cover temperature sensing, protection, shipping mode, and certification requirements.
- Test points cover power rails, key buses, reset, boot mode, programming, and production calibration.

## PCB Review

- High-current power paths are short and wide; return paths are continuous.
- DCDC thermal loop, switch node, and feedback path follow datasheet layout guidance.
- Analog, digital, RF, and power regions have clear boundaries to avoid critical noise coupling.
- High-speed differential pairs meet length matching, impedance, reference-plane, and via-count requirements.
- Crystal is close to the chip; load capacitors, ground guard ring, and distance from noise sources are appropriate.
- Antenna keep-out, matching network, grounding vias, and distance from metal structures follow RF recommendations.
- Connector mechanical stress, ESD discharge path, mounting-hole grounding, and edge clearance are reasonable.
- Test points are accessible, not obstructed by mechanics, and satisfy fixture orientation and bed-of-nails spacing.
- Heat sources have copper pours, vias, thermal paths, and a temperature-rise verification plan.

## BOM Review

- Key chips have lifecycle status, lead time, second source, or alternative strategy.
- Resistor/capacitor/inductor packages are not excessively miniaturized relative to manufacturing capability and yield targets.
- High-precision, low-noise, high-voltage, and high-current devices have adequate parameter margin.
- Long-lead-time items (connectors, harnesses, batteries, displays) have been locked early.
- Parts with licensing issues, EOL status, exclusive agents, regional restrictions, or unclear certification are marked as risks.
- Component grade matches environmental requirements: industrial, automotive, medical, or consumer boundaries are explicit.

## Design Proposal Review

- Explains “why this architecture” rather than only “which parts were used”.
- Trade-offs among cost, power, reliability, and software complexity are acceptable.
- TBD items are listed with owners responsible for confirmation.
- Risks of single-supplier, single-toolchain, or single-certification-path dependence are identified.
- A closed validation loop from EVT to PVT exists.
