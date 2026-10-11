# Hardware Solution Design Workflow

> **File output rule:** Stages that produce tables must output Markdown files to the `docs/hardware/` directory. See “File Output Rules” in SKILL.md.

## 0. Choose the Applicable Route

Use the smallest route that satisfies the request:

- **Focused task** (one component, interface, calculation, or narrow question): answer directly. Ask only for missing information that materially changes the answer; apply relevant source and safety checks. Do not force a mode choice, full architecture comparison, project files, or unrelated gates.
- **Existing-design review**: review the provided scope directly, identify evidence gaps, and give prioritized, actionable findings. Do not restart requirements freeze or require new-design architecture options.
- **New design / full proposal**: use the staged workflow below. Choose **Quick mode** when the request implies speed or prototype exploration; use clearly labeled assumptions that the user may confirm or correct together. Use **Professional mode** when production, compliance, handoff, or strict requirements control is requested; confirm unresolved decision-critical items one question at a time. Ask the user to choose a mode only when it is not clear and the interaction choice would materially affect progress.

Record a mode only for a full design workflow. Do not ask again for information already provided.

## 1. Requirements Freeze

Organize relevant requirements into an engineering constraints table. Mark unknowns as open items; do not present assumptions as confirmed facts. A constraint is required only when relevant to the design scope.

- Scenario: installation location, user interaction, operating duration, maintenance method.
- Environment: temperature, humidity, vibration, ESD, EMI, outdoor/industrial/automotive/medical boundaries.
- Power: battery, USB, adapter, PoE, vehicle power, wide-voltage input, isolation needs.
- Function: sensing, control, display, audio, imaging, networking, storage, security.
- Production: target cost, annual volume, certifications, test fixtures, serviceability.
- Supply-chain preference: China-first, Europe-first, Americas-first, or hybrid, or no preference.

For a new design, present a concise requirements summary and 2–4 relevant priority choices before detailed component selection. Avoid generic choices that do not affect this design. Examples:

- Prioritize low power: accept some cost and development convenience trade-offs; suitable for long battery life.
- Prioritize low cost: choose domestic or high-value devices; suitable when production volume is clear.
- Prioritize fast implementation: choose devices with mature ecosystems and reference designs; suitable for prototypes or tight schedules.
- Prioritize China supply chain: cover China MCU, power, interface chips, and sensor alternatives; suitable when cost or China localization is required.

**Professional mode:** Ask one question at a time for unresolved, decision-critical constraints. The user may provide a value, authorize a stated assumption, or mark it blocked. Do not block progress on non-critical unknowns; record an owner and target date for them.

```
Question: [specific question]
A. [option 1]
B. [option 2]
C. [option 3]
D. Custom input: ___
```

**Quick mode:** Present the relevant requirements and assumptions together. Label each unprovided value as an assumption; allow batch confirmation or correction. Do not treat silence as confirmation; proceed after user authorization or keep the proposal explicitly provisional.

**Output file:** `docs/hardware/01-requirements.md`

## 2. Architecture Candidates

Compare applicable architecture directions; do not create a fixed count of regional architectures. For a new design with no specified supply-chain restriction, normally compare these three **architecture archetypes**:

- **China-first**: use when domestic localization, local support, cost, or China supply autonomy is important.
- **Europe/Americas ecosystem**: select relevant Europe and/or Americas candidates based on technical fit, ecosystem, lead time, and target-region constraints. Europe and Americas are sourcing groups to compare, not necessarily separate architecture options.
- **Hybrid**: assign subsystems to regions based on evidence, risk, cost, and second-source needs; explain BOM and qualification complexity.

Compare viable options on the trade-offs that matter for this product, such as BOM cost at a stated volume, schedule, supply risk, power, PCB difficulty, software, certification, and scalability. A modular approach may be included when it is a credible option, not as a mandatory regional category. If the user specifies a platform or excludes a region, respect it and explain only material consequences.

Do not treat regional preference as a slogan. For critical modules, compare at least two relevant regional sourcing groups when credible alternatives exist; include China, Europe, and Americas when the user requests a global comparison or no group is excluded. Identify the selection candidates, evidence, advantages, disadvantages, and why relevant alternatives were not selected. Do not invent an unsuitable candidate to satisfy a count.

**Output file:** `docs/hardware/02-architecture.md`

## 3. System Block Diagram (new designs)

After architecture direction is confirmed, generate a clear, high-quality ASCII system block diagram.

Requirements:
- Use ASCII characters only (`+`, `-`, `|`, `>`) in a monospaced text block. Do not substitute Mermaid, D2, or an image for this required diagram.
- Use clear boxes, arrows, and alignment.
- Minimum modules: Power input → Protection/Regulation → Main controller → Interfaces, Sensors/Actuation, Storage, Debug/Production test.
- Annotate key power rails and major interfaces briefly inside or beside the boxes.
- Keep it readable in a plain text editor (max ~80–100 columns recommended).
- Save to `docs/hardware/03-block-diagram.md`.

Example style (adapt to the actual design):

```
+-------------+     +--------------+     +-----------------+
| Power Input |---->| Protection   |---->| PMIC / Regulators|
| (USB/Battery)|    | (TVS, fuse)  |     | 3V3 / 1V8 / 5V  |
+-------------+     +--------------+     +--------+--------+
                                                  |
                                         +--------v--------+
                                         |    MCU / SoC    |
                                         |  (main control) |
                                         +--+-----+-----+--+
                                            |     |     |
                               +------------+     |     +------------+
                               v                  v                  v
                        +-------------+   +-------------+   +-------------+
                        | Interfaces  |   | Sensors/AFE |   | Debug/Test |
                        +-------------+   +-------------+   +-------------+
```

This step is mandatory for new designs.

Break the hardware into functional domains rather than a flat parts list.

- Main controller and storage: MCU/SoC, Flash, RAM, boot method, debug interface.
- Power tree: input protection, charging/power path, DCDC/LDO, load switches, sensing.
- Communication: USB, UART, CAN, RS485, Ethernet, Wi-Fi, BLE, LTE, LoRa.
- Sensing and actuation: analog front-end, ADC/DAC, isolation, protection, calibration.
- HMI: buttons, LEDs, buzzer, screen, touch, audio.
- Safety and reliability: watchdog, power-loss protection, ESD/surge, thermal design.
- Production test: test points, programming port, boundary scan, calibration fixtures, serial-number write.

## 4. Key Component Selection

For each key device provide “selection rationale + alternatives + risks”.

- MCU/SoC: resource margin at least covers current requirements; state GPIO, RAM, Flash, peripherals, package, power, and ecosystem.
- Power ICs: input range, efficiency, thermal dissipation, ripple, EMI, protection features, package solderability.
- Wireless devices: frequency band, antenna, certification, RF layout, throughput, power, supply region.
- Connectors: mating cycles, keying, locking, harness cost, field maintainability.
- Storage: endurance, power-loss consistency, file-system or wear-leveling needs.

The selection stage must explicitly compare China, Europe, and Americas candidates:

- Domestic candidate: explain domestic-substitution value, ecosystem maturity, documentation availability, agent/distributor channels, and long-term supply risk.
- Europe/Americas candidate: explain ecosystem advantages, reference designs, certification materials (CE/FCC), price, and lead-time risk.
- Hybrid candidate: explain which modules should stay in a preferred region and which can be sourced from China, Europe, or Americas, plus the cost of alternative verification.

For each recommended key IC and functional-module device, provide purchase, datasheet, and footprint references when relevant, using the claim-specific evidence hierarchy in [sourcing-and-risk.md](sourcing-and-risk.md). Manufacturer documentation is authoritative for technical specifications; authorized distributors or agents support purchase and availability; aggregators are leads only and must be cross-checked. Verify footprint dimensions against the manufacturer's package drawing. If unavailable or not verifiable, label it clearly and state the follow-up action.

Device tiers:
- Key ICs (links and documents required): MCU, PMIC, transceivers, sensors, ADC/DAC, and other core chips
- Functional-module devices (links and documents required): crystals, connectors, ESD/TVS, memory, load switches, LDOs, etc.
- Passive components: no links or document downloads required

After selection, proceed to document download (step 4.5).

**Output file:** `docs/hardware/04-components.md`

## 4.5 Document Download

After component selection is verified, ask whether the user wants local downloads and, if so, which EDA tool they use. Download only when requested:

- Datasheet PDFs for selected key ICs and functional-module devices → `docs/hardware/datasheets/`
- Footprint files in the format required by the user’s EDA:
  - KiCad → `.kicad_mod`
  - Altium Designer → `.PcbLib`
  - LCSC EDA → `.elib`
  - Other → user-specified format or generic (`.bxl`)
- Follow the claim-specific evidence hierarchy in `references/sourcing-and-risk.md` and consult `references/download-sources.md` for records. Prior records must be revalidated for exact device, package, revision, and format.
- Record the reason for any download failure and annotate the manual-download link in `04-components.md`.
- After download, output a checklist listing the file path and status (downloaded / failed / requires manual) for each device.

**Output directories:** `docs/hardware/datasheets/` and `docs/hardware/footprints/`

## 5. Constraint Output

The proposal must produce constraints that can guide schematic and PCB design.

- Interface matrix: signal name, direction, voltage level, current, rate, protection, connector pinout.
- Power tree: input, protection, rails, current budget, power-up sequencing, shutdown strategy.
- PCB constraints: recommended layer count, critical routing, impedance, return paths, analog/digital/RF partitioning.
- Mechanical constraints: board outline, mounting holes, connector orientation, thermal, antenna keep-out.
- DFM/DFT: test points, programming method, fixture locating, production calibration items.

**Output file:** `docs/hardware/05-constraints.md`

## 6. Validation Plan

Every risk must have a verification action.

- EVT: core functions, power stability, interface connectivity, basic environmental tests.
- DVT: boundary conditions, EMC pre-scan, temperature rise, ESD, long-term stability, abnormal power loss.
- PVT: production test coverage, fixture cycle time, failure localization, alternative-part verification.

**Output file:** `docs/hardware/06-validation.md`

## 7. Decision Gate

At the end of a full proposal, clearly separate determined decisions, assumptions, open items, and high risks.

- Determined: content that can proceed to schematic capture.
- Open items: information that requires input from the user, mechanical, procurement, certification, or software team. Assign an owner and target date, or mark it blocked.
- High risk: content that, if not verified, will affect cost, schedule, reliability, or mass production.

**Output file:** `docs/hardware/07-decisions.md`

## 8. Module Schematic Output

After review passes, ask whether module-level schematic output is needed. It is optional and does not block proposal review or delivery unless schematic-ready handoff is explicitly in scope. After confirmation, agree on module scope and offer display-format options:

- Structured netlist/connection table: net name, source device.pin, destination device.pin, parameters/notes. Precise and unambiguous; suitable for direct hand-off to an engineer. No extra tools required.
- ASCII block diagram: use text symbols to express circuit topology and power paths, annotate device models and key parameter values. Intuitive and readable; no tools required.
- D2 diagram (`.d2`): describe module hierarchy and connections with D2 syntax; supports nesting and edge labels; renders well to SVG/PNG. Requires the `d2` CLI.
- KiCad schematic file (`.kicad_sch`): **requires a KiCad MCP Server.** Call KiCad APIs via MCP tools to place components, wire nets, and annotate, generating a schematic file that opens directly in KiCad.
- LCSC EDA JSON: **requires a JLCEDA MCP Server.** Call LCSC EDA APIs via MCP tools to generate importable schematic data; suitable for domestic users and LCSC EDA workflows.

**MCP Server dependency notes:**

KiCad and LCSC EDA formats depend on the corresponding MCP Server being available in the current environment. The LLM does not directly generate raw `.kicad_sch` or JSON files (formats are complex, coordinate precision is high, and symbol-library dependencies are strong). Instead, it calls the EDA’s native API through MCP tools so the EDA itself handles coordinate alignment, symbol references, and file format.

Known available MCP Servers:
- KiCad: `kicad-mcp`, `kicad-mcp-pro`, `mcp-kicad-sch-api`
- LCSC EDA: `jlceda-mcp`

**Fallback rule:** If the user chooses KiCad or LCSC EDA format but the corresponding MCP Server is not available in the current environment, prompt the user to install the MCP Server and automatically fall back to structured connection-table output.

After the user selects the display method and the modules to cover, output according to the chosen method. Annotate each module with device model, pin connections, power rails, and key parameter values (resistor/capacitor values, voltages/currents). Deliver after Gate 6 passes.

**Output files:** `docs/hardware/08-schematics.md` (connection table / ASCII) or `docs/hardware/08-schematics.d2` (D2) or `docs/hardware/08-schematics.kicad_sch` (KiCad) or `docs/hardware/08-schematics.json` (LCSC EDA)

## 9. PDF Report Output

When the user requests a PDF, merge the applicable Markdown deliverables under `docs/hardware/` into a PDF report. Do not include temporary or unrelated Markdown files.

The script is located in this skill’s `scripts/md_to_pdf.py` directory (sibling to SKILL.md).

```bash
python3 <skill_root>/scripts/md_to_pdf.py --merge docs/hardware/ docs/hardware/hardware-solution.pdf --title "Project-Name-Hardware-Solution-Report" --theme green
```

Optional color themes (`--theme`):
- `green`: engineering emerald (default)
- `blue`: business navy
- `gray`: minimal graphite

Ask the user for the preferred color theme before generating.

Script dependencies: `pip install weasyprint markdown`

The PDF includes a cover (project name, date), automatic pagination, header/footer, and table styling. Use the stage identifiers in filename order; inspect the merge inputs so schematics and other optional artifacts are included only when relevant.

**Output file:** `docs/hardware/hardware-solution.pdf`
