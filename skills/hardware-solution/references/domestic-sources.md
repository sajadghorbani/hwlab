# Domestic Sources For Hardware Solutions

Use this when a design needs Chinese MCU, SoC, analog, power, interface, wireless module, component supply, or reference-solution coverage. These sources are starting points for discovery and cross-checking, not final proof by themselves.

## Verification Principles

- Parameters must be based on manufacturer datasheets, application notes, reference designs, and errata.
- Inventory, price, MOQ, and lead time must be based on distributor or authorized-agent pages.
- Solution platforms, community articles, and teardown articles may only be used to discover leads; they cannot serve as final parameter evidence.
- Domestic candidates and overseas candidates must be comparable in the same table: parameters, ecosystem, supply, certification, and alternative cost.
- Datasheet verification priority: manufacturer official documentation download page > authorized-distributor specification attachments > domestic component-platform specification attachments > datasheet aggregators > community/article leads.

## MCU / SoC / Security Chips

| Type | Manufacturer / Platform | What to look up |
|------|-------------------------|-----------------|
| MCU / Flash | GigaDevice | GD32 MCU, SPI NOR Flash, documentation and selection tables |
| MCU / USB / BLE | WCH (QinHeng) | CH32 MCU, USB, Ethernet, BLE, low-cost interface solutions |
| MCU | HK32 (HangShun) | ARM Cortex-M MCU, domestic-alternative selection |
| MCU | MindMotion | MM32 MCU, industrial control, low-power MCU |
| MCU / Security | NATIONSTECH | Security MCU, general MCU, national-cryptography related needs |
| MCU / Security | Fudan Micro (FM) | Security chips, MCU, smart-card related devices |
| MCU / Analog | Chipsea | Low-power MCU, sensing measurement, ADC-related solutions |
| MCU | APM32 (Geehy) | General MCU, industrial and consumer control |
| MCU / Meter | HDSC (HuaDa) | MCU, electricity meters, low-power and industrial applications |

## Power / Analog / Interface / Isolation

| Type | Manufacturer / Platform | What to look up |
|------|-------------------------|-----------------|
| Analog / Power | SG Micro (ShengBang) | Op-amps, comparators, LDO, DCDC, analog switches |
| Analog / Signal chain | 3PEAK | Op-amps, ADC, interfaces, isolation, industrial signal chain |
| Isolation / Sensing / Interface | NOVOSENSE | Isolators, isolated power, sensors, automotive and industrial interfaces |
| Power | Silergy | DCDC, PMIC, power management |
| Power | JoulWatt | DCDC, LDO, battery management, LED drivers |
| Power | Chipown | AC/DC, DC/DC, power management |
| Interface / Isolation | Chipanalog | RS485, CAN, isolation, interface protection |
| Interface / Protection | Belling (Shanghai) | Power, interfaces, EEPROM, analog devices |

## Wireless / Communication / Modules

| Type | Manufacturer / Platform | What to look up |
|------|-------------------------|-----------------|
| Wi-Fi / BLE SoC | Espressif | ESP32 series, certified modules, low-power networking solutions |
| Cellular modules | Quectel | 4G/5G/NB-IoT/GNSS modules, certification and hardware design guides |
| Cellular modules | Fibocom | Cellular communication modules, certification, reference designs |
| Cellular / Cat.1 / NB | AirM2M (Hezhou) | Low-cost cellular modules, development materials and solutions |
| Wi-Fi / BLE modules | Ai-Thinker | ESP-series modules, LoRa/Wi-Fi/BLE modules |
| IoT modules | OneMO (China Mobile IoT) | Cellular modules, IoT platform adaptation |

## Component and Inventory/Price Platforms

| Platform | What to look up | Notes |
|----------|-----------------|-------|
| LCSC | Domestic and general components, inventory, tiered pricing, packages | Check whether in stock and whether supply is sustainable |
| Huaqiu Mall | Component procurement, PCB/SMT support | Suitable for mass-production and prototype supply-chain checks |
| Yunhan Core City | Component inventory, alternatives, inquiry | Suitable for lead-time and price cross-verification |
| Digi-Key China | Overseas devices for domestic purchase, inventory and parameters | Prices better for sample/small-volume reference |
| Mouser China | Overseas devices for domestic purchase, documents and inventory | Suitable for new devices and authorized-channel confirmation |
| Lixiang (Hunt Chip) | Inquiry, inventory, alternative discovery | Requires secondary confirmation of authorization and source |
| Hard City | Component supply and BOM services | Suitable for initial BOM risk screening |
| IC ChaCha (Core Check) | Model search, parameters, supplier leads | Leads only; not final evidence |

## Datasheet / Specification Search Platforms

| Platform | What to look up | Usage boundary |
|----------|-----------------|----------------|
| Manufacturer Chinese official documentation download page | Latest datasheets, application notes, reference designs, errata | Highest priority; use first |
| LCSC specification attachments | Common domestic and general-device datasheets, packages, inventory | Confirm attachment version matches manufacturer |
| Huaqiu Mall specification attachments | Mass-production common-device documents, parameters, inventory | Must cross-check with manufacturer or authorized channel |
| Yunhan Core City specification attachments | Model datasheets, alternative leads, inventory | Supplementary source |
| Digi-Key China / Mouser China document pages | Overseas-device datasheets, application notes, CAD models | Authoritative cross-verification for overseas devices |
| IC ChaCha | Model search, parameter summaries, datasheet leads | Aggregated information is leads only; not final evidence |
| icspec | Model search, PDF datasheet leads | Confirm manufacturer, version, and release date |
| datasheet5 | PDF datasheet search | Supplementary lead only; must cross-verify |
| Datasheet Archive / AllDatasheet | Overseas aggregator datasheet search | Historical or supplementary lead only |

## Solution Teardown / Reference Design Platforms

| Platform | What to look up | Usage boundary |
|----------|-----------------|----------------|
| eWiseTech | Phone, IoT, smart-hardware teardowns, device combinations and structural stacking | Useful for understanding mature product architectures; cannot be parameter evidence |
| 52Audio | TWS, speakers, microphones, audio SoC, power and battery solution teardowns | Suitable for audio and low-power consumer product reference |
| ChargeHead | Charger, power-bank, energy-storage, power-chip, protocol-chip teardowns | Suitable for power, fast-charge, protection, and thermal design reference |
| EEFocus | Solution analysis, development boards, manufacturer solutions, application cases | Suitable as solution leads |
| Elecfans Solution Center | Industry solutions, reference designs, manufacturer promotional solutions | Must return to manufacturer and actual BOM for verification |
| Digi-Key Reference Design | Overseas reference designs, application circuits, material leads | Suitable for overseas-device solution verification |
| Mouser Technical Resources / Reference Designs | New-product solutions, application notes, design resources | Suitable for overseas-device ecosystem verification |
| TI Reference Designs | Power, analog, interface, sensing reference designs | Suitable as baseline for power and analog solutions |
| ADI Reference Designs | Precision analog, isolation, power, data-acquisition | Suitable for high-precision acquisition and industrial signal chain |
| ST Design Resources | STM32, sensing, power, motor-control reference designs | Suitable for STM32 ecosystem solutions |
| Microchip Application Notes | Low-power MCU, analog, communication, storage application notes | Suitable for low-power and industrial control |
| NXP Designs | Industrial, automotive, edge computing, connectivity reference designs | Suitable for high-performance MCU/MPU solutions |

When using teardown websites, the output must include:

- Reusable points: architecture, device combination, power path, interface protection, structure/thermal.
- Non-reusable points: unknown parameters, unknown firmware strategy, unknown certification boundaries, designs that may be affected by patents or copyright.
- Trace-back verification: corresponding manufacturer datasheet, reference design, application note, or distributor documentation.

## Solution / Open-Source Hardware / Community Leads

| Platform | What to look up | Usage boundary |
|----------|-----------------|----------------|
| JLC EDA Open Source Square | Reference schematics, PCBs, domestic-device implementation cases | Must return to manufacturer datasheets for verification |
| LCSC Open Source Hardware Platform | Module solutions, engineering files, BOM leads | Do not copy directly; re-review required |
| Elecfans | Solution articles, manufacturer news, application cases | Leads and background only |
| 21ic | MCU experience, domestic-alternative discussions, troubleshooting | Experience reference only |
| EEWorld | Engineering experience, reviews, development-board materials | Experience reference only |

## Output Requirements

When domestic sources are used, append to the proposal:

| Module | Domestic candidate | Information source | Credibility | Still requires verification |
|--------|--------------------|--------------------|-------------|-----------------------------|
| Main controller |  | Manufacturer / distributor / community lead | High / Medium / Low | Datasheet / inventory / lead time / certification |
