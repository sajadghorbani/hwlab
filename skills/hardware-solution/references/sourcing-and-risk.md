# Sourcing And Risk Guidance

Use this when a design depends on current chip availability, lifecycle status, certification, price, or regulatory constraints.

## Items That Must Be Verified

Verify online; do not answer from memory:

- Whether the chip is NRND, EOL, discontinued, out of stock, or restricted to specific regions.
- Whether the module has target-region certifications, e.g., SRRC, CE, FCC, IC, TELEC, KC.
- Whether wireless frequency bands, transmit power, and antenna restrictions suit the target market.
- Battery, charging, adapter, PoE, and safety-certification requirements.
- Unit price, inventory, lead time, MOQ, package availability.
- Manufacturer reference designs, layout guidelines, errata, and application-note versions.
- Technical claims and datasheet revisions: manufacturer datasheet/product page, errata, and application notes are authoritative. Use authorized-distributor documents as a cross-check; aggregators are discovery leads and must be verified against an authoritative source.
- Solution-teardown or reference-design sources: use only to discover mature architectures and device combinations; must be traced back to manufacturer documentation for verification.

## Evidence Hierarchy

Apply the source hierarchy according to the claim being supported; no single source type is best for every claim.

| Claim | Preferred evidence | Use of other sources |
|-------|--------------------|----------------------|
| Electrical limits, package, timing, layout, errata | Current manufacturer datasheet, product page, errata, and application notes | Authorized-distributor documents can corroborate; aggregators are leads only |
| Price, stock, MOQ, and lead time | Authorized distributor or manufacturer/authorized-agent quotation | Marketplace listings are leads unless seller authorization and stock are verified |
| Certification and regional approvals | Certification-body/regulator records and official module/manufacturer certificates | Distributor or aggregator summaries are leads only |
| Footprints and CAD models | Manufacturer CAD files or verified official/authorized EDA library entry | Third-party libraries require package/dimension cross-check against the mechanical drawing |

Record the exact part number and package, source URL, document/revision where applicable, and verification date. Distinguish a verified fact from a derived calculation, an assumption, or an unverified lead. If current online verification is not possible, state that limitation and do not imply the claim is current.

## Recommended Information Sources

- Manufacturer websites and datasheets.
- Manufacturer product-change notices, lifecycle pages, and errata.
- Digi-Key, Mouser, Arrow, Avnet, LCSC, and other distributor pages.
- Domestic (China) manufacturer websites, agent pages, LCSC, Huaqiu Mall, Yunhan Core City, Digi-Key China, Mouser China, and similar channels.
- Certification-body or regulatory-agency documents.
- Module-vendor official certification lists and hardware design guides.

Detailed lists of China chips, components, modules, datasheet search, solution teardowns, and reference-design platforms are in [domestic-sources.md](domestic-sources.md). Must be read when China-focused sourcing, China-market mass production, or regional alternatives are involved.

## Regional Sourcing Comparison (China / Europe / Americas)

Treat region as a sourcing dimension, not a requirement to invent a separate architecture for every geography. For new designs where sourcing region matters or is unspecified, compare relevant regional groups in a compact table. Cover at least two groups for critical modules; include China, Europe, and Americas when the user requests a global comparison or no region is excluded. State exclusions and why they do not apply. A hybrid option describes cross-region sourcing by subsystem; it is not an additional geography.

- **China-first**: China MCU/SoC (GigaDevice, WCH, Espressif, etc.), China power, interface, storage, and protection devices. Focus on cost, local supply autonomy, documentation completeness, ecosystem maturity, and mass-production cases.
- **Europe-first**: European manufacturers and ecosystems (ST, NXP, Infineon, Renesas Europe presence, etc.). Focus on industrial reliability, long-term availability, CE/UKCA certification readiness, and mature reference designs.
- **Americas-first**: North American manufacturers and ecosystems (TI, Microchip, ADI, Silicon Labs, Nordic where relevant, etc.). Focus on ecosystem tools, Digi-Key/Mouser availability, FCC certification readiness, and developer resources.
- **Hybrid**: Mix regions per subsystem (e.g., China main controller + Europe/Americas analog or RF) based on risk, cost, and certification. Explicitly note second-source and BOM complexity.

Explain why an applicable group was rejected or not selected. Do not add irrelevant candidates merely to satisfy a count; user-specified platforms, exclusions, safety constraints, or lack of a credible equivalent may narrow the comparison.

## Risk Grading

| Level | Criteria | Response |
|-------|----------|----------|
| High | Affects architecture, certification, mass production, or long-lead-time materials | Immediately provide alternatives and schedule sample verification |
| Medium | Affects cost, PCB, firmware complexity, or test coverage | Enter TBD list and set a verification milestone |
| Low | Can be mitigated by parameter adjustment, package substitution, or software | Mark as assumption and check during schematic review |

## Alternative-Part Strategy

- For key materials such as main controller, PMIC, wireless module, sensors, connectors, and batteries, consider at least one backup path.
- Alternatives must not be judged only by pin compatibility; also compare registers, package thermal resistance, supply range, certification, firmware drivers, and EMC performance.
- If the alternative affects the PCB, state whether compatible pads, 0R options, or a separate revision will be reserved.

## Output Format

Append at the end of a full proposal. Assign every risk an ID and record its owner, due date, and linked validation test where applicable:

| ID | Material / Module | Current selection | Evidence and verification date | Risk | Alternative | Verification action / linked test | Owner | Due |
|----|-------------------|------------------|---------------------------------|------|-------------|-------------------------------|-------|-----|
| R-01 |  |  | URL, document revision, date | High / Medium / Low |  | Test ID or next action |  |  |
