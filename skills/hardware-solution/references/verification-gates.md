# Verification Gates

Apply gates only to stages and deliverables in scope. For a focused task or existing-design review, use the relevant checks without forcing unrelated stages. Record excluded checks as not applicable and unresolved checks as open; never claim a gate passed when it was not performed.

## Gate 1: After Requirements Freeze

- [ ] Relevant constraints (scenario, power, communication, environment, cost/volume, certification) are recorded as known, explicitly assumed, or open; no missing value is presented as confirmed.
- [ ] For a new design with a material unresolved trade-off, the user was offered 2–4 relevant decision options; omit when the user already specified the direction or it is a focused task/review.
- [ ] Decision-critical open items were handled according to mode; remaining non-critical open items have an owner and target date or are explicitly blocked.
- [ ] Requirements and assumptions were confirmed or the user authorized provisional, assumption-based progress.

## Gate 2: After Architecture Selection

- [ ] For a new design without a specified platform or regional restriction, applicable architecture archetypes (China-first, Europe/Americas ecosystem, and hybrid) were compared; regional sourcing groups are not counted as separate architecture archetypes.
- [ ] For critical modules, at least two credible regional sourcing groups were compared when available; include China, Europe, and Americas for a global comparison unless the user excludes one or it is inapplicable.
- [ ] User-specified platforms, excluded regions, and lack of credible alternatives are documented; no unsuitable candidate was added only to meet a count.
- [ ] Each candidate has clear advantages, disadvantages, and applicable conditions.
- [ ] Each candidate covers device ranges for main controller, power, communication interface, and sensor/analog front-end.
- [ ] The recommendation rationale is based on constraint matching, not “commonly used” or “familiar”.
- [ ] User has confirmed the architecture direction.
- [ ] Selection stage may only begin after the user confirms the architecture direction; do not proceed by default.

## Gate 3: After Component Selection

- [ ] Key devices (MCU, PMIC, wireless, connectors) all have alternatives.
- [ ] Each key module compares candidates from at least two of the three regions (China, Europe, Americas), or explains why one category is not applicable.
- [ ] When domestic substitution or China-market mass production is involved, `domestic-sources.md` has been consulted to cover mainstream domestic chips, components, modules, and solution platforms.
- [ ] Technical specifications are supported by current manufacturer documentation; authorized-distributor documents may corroborate, while aggregators are treated only as leads and cross-verified.
- [ ] Availability, price, lifecycle, and certification claims use sources suitable for those claims and include verification dates; unavailable verification is explicitly disclosed.
- [ ] Evidence identifies exact part number/package, source URL, and datasheet revision or verification date where applicable.
- [ ] If solution teardowns or reference-design platforms were referenced, reusable points and non-reusable points are clearly stated, and they are traced back to manufacturer documentation for verification.
- [ ] Supply-chain risks have been verified online where current status matters: lifecycle, inventory, lead time, and certification.
- [ ] Risk table is non-empty; each risk has an ID, impact, probability, verification action, owner, and due date. High risks have linked validation tests or a dated verification action.
- [ ] Device parameters come from datasheets or distributor pages, not memory.
- [ ] Each recommended key IC and functional-module device has a purchase reference link (domestic e-commerce / distributor page) or is marked “requires online verification”.
- [ ] Each recommended key IC and functional-module device has datasheet download and footprint download links, or is marked “requires online verification”.
- [ ] Passive components (resistors, capacitors, inductors) are not required to have links or document downloads.

## Gate 4: After Proposal Output

- [ ] Output contains system block diagram, interface matrix, power tree, PCB constraints, and validation plan.
- [ ] Risk list is non-empty; every risk has impact, probability, and verification action.
- [ ] Determined items contain no unresolved placeholder text; open items are permitted only in the clearly labeled open-items section and have an owner and target date or blocked status.
- [ ] Each material risk maps to one or more validation test IDs, or the proposal explains why a test is not currently feasible.
- [ ] Determined decisions, assumptions, open items, and high risks are clearly separated at the end.

## Gate 5: After Review

- [ ] Independent review completed using the `hardware-reviewer` agent.
- [ ] CONCERN and FAIL findings from the review have been addressed or explicitly retained as open risks with owners and due dates.
- [ ] The proposal is ready for the next agreed engineering step; claim schematic-capture readiness only when sufficient pin, interface, power, and component detail is present.
- [ ] Schematic fragments are checked only when requested or required by the agreed handoff scope; their absence alone does not fail proposal review.

## Gate 6: After Module Schematic Output

- [ ] This gate is performed only when module schematic output is in scope; otherwise mark it not applicable.
- [ ] User confirmed that module schematic output is needed before producing optional schematic deliverables.
- [ ] User has chosen a display method (structured connection table / ASCII diagram / D2 diagram / KiCad schematic file / LCSC EDA JSON).
- [ ] If the user chose KiCad or LCSC EDA format, the corresponding MCP Server availability was confirmed; if unavailable, the user was prompted and fallback to structured connection table was performed.
- [ ] Schematic fragments were output according to the user-specified module scope and display method.
- [ ] Each module is annotated with device model, pin connections, and key parameter values.
- [ ] Power rails are annotated with voltage and current budget.
- [ ] Schematic fragments can be handed directly to a hardware engineer for EDA capture.
