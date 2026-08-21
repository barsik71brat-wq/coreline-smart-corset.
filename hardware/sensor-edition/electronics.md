# Sensor Electronics

## CORELINE Sensor Edition

This document describes the proposed electronics architecture for the optional CORELINE Sensor Edition.

The electronic subsystem is intended to support motion sensing, pressure/load sensing, local data processing, wireless communication, power management, and future sensor-related functionality.

It is **not a final production schematic or bill of materials (BOM)**. Component selection, electrical specifications, PCB design, battery configuration, sensor interfaces, and manufacturing details remain subject to prototype development and validation.

> **Development status:** Sensor electronics architecture / component evaluation  
> The architecture described here represents the current engineering direction and may change as physical prototypes are developed and tested.

---

## Design Objectives

The Sensor Edition electronics should be designed around the following priorities:

- low power consumption;
- compact physical size;
- low mass;
- reliable sensor acquisition;
- stable wireless communication;
- modular integration;
- removable electronics where practical;
- safe battery operation;
- serviceability during prototyping;
- manufacturability;
- firmware upgrade capability; and
- compatibility with the mechanical CORELINE platform.

The electronics are intended to remain optional and should not be required for the basic biomechanical function of the mechanical prototype.

---

## High-Level Architecture

A conceptual system architecture is:

`Sensors → Signal Acquisition → Microcontroller → Data Processing → BLE → Mobile Device`

Supporting subsystems may include:

`Battery → Protection → Power Regulation → Electronics`

and:

`USB / Charging Interface → Battery Charging → Power Management`

The exact architecture will depend on component selection and prototype measurements.

---

## Functional Blocks

The electronic subsystem may contain the following functional blocks:

1. microcontroller;
2. Bluetooth Low Energy interface;
3. inertial measurement unit;
4. pressure/load sensor interfaces;
5. power-management circuitry;
6. rechargeable battery;
7. charging interface;
8. voltage regulation;
9. non-volatile storage where required;
10. programming/debug interface; and
11. status indication.

Some functions may be integrated into a single component.

---

## Microcontroller

The main controller should provide sufficient resources for:

- sensor acquisition;
- BLE communication;
- calibration processing;
- data buffering;
- basic filtering;
- device configuration;
- power management;
- diagnostics; and
- future firmware updates.

Selection criteria may include:

- low-power operating modes;
- integrated BLE capability;
- processor performance;
- RAM;
- flash memory;
- ADC capability;
- I²C/SPI interfaces;
- GPIO availability;
- package size;
- development-tool support;
- component availability; and
- long-term sourcing considerations.

No production microcontroller has yet been selected.

---

## Bluetooth Low Energy

Bluetooth Low Energy (BLE) is the current proposed wireless technology.

The BLE subsystem may be integrated into the main microcontroller or implemented using a separate radio device.

The design should consider:

- smartphone compatibility;
- power consumption;
- antenna requirements;
- data throughput;
- connection stability;
- security capabilities;
- firmware support; and
- certification implications.

The proposed communication architecture is documented in:

[`bluetooth-connection.md`](bluetooth-connection.md)

---

## Inertial Measurement Unit

An IMU may be used to measure motion and orientation-related information.

A candidate IMU may provide:

- three-axis acceleration;
- three-axis angular velocity; and
- optional additional sensing depending on the selected device.

Selection criteria should include:

- measurement range;
- noise;
- bias stability;
- power consumption;
- sampling capability;
- package size;
- digital interface;
- interrupt support;
- availability; and
- software support.

The final IMU model has not yet been selected.

---

## Pressure / Load Sensors

The Sensor Edition may include pressure-sensitive or force-sensitive elements integrated into selected areas of the wearable structure.

Potential sensor technologies may include:

- resistive force-sensitive elements;
- capacitive pressure sensors;
- piezoresistive sensors;
- textile pressure sensors; or
- other flexible sensing technologies.

Selection should be based on physical testing rather than nominal datasheet characteristics alone.

Important evaluation criteria include:

- flexibility;
- thickness;
- measurement repeatability;
- hysteresis;
- drift;
- sensitivity;
- durability;
- integration with textile layers;
- response to bending;
- temperature behavior; and
- manufacturing feasibility.

---

## Sensor Interface

Sensor interfaces will depend on the selected technology.

Digital sensors may use interfaces such as:

- I²C;
- SPI; or
- other supported digital buses.

Analog sensors may require:

- analog-to-digital conversion;
- biasing circuitry;
- multiplexing;
- filtering;
- amplification; and
- reference-voltage management.

The final interface topology will be established after sensor selection.

---

## Pressure Sensor Array

If multiple pressure sensors are used, the electronics may require a multiplexed acquisition architecture.

A conceptual path may be:

`Pressure Sensors → Multiplexer / Analog Front End → ADC → Microcontroller`

The design should consider:

- channel count;
- acquisition speed;
- cross-channel interference;
- ADC resolution;
- reference stability;
- wiring complexity;
- connector reliability; and
- power consumption.

The number and placement of sensing channels remain under development.

---

## Sampling Architecture

Different sensors may operate at different sampling rates.

The firmware may therefore independently configure:

- IMU sampling;
- pressure/load sampling;
- battery monitoring;
- diagnostic measurements; and
- BLE transmission intervals.

Sensor sampling frequency should not automatically be assumed to equal wireless transmission frequency.

Data may be buffered or grouped before transmission to reduce communication overhead.

---

## Signal Conditioning

Analog sensing elements may require signal conditioning before conversion.

Depending on the selected sensor, this may include:

- voltage division;
- current limiting;
- amplification;
- low-pass filtering;
- offset adjustment;
- impedance matching; and
- input protection.

Circuit values should be determined from measured sensor behavior.

Final resistor, capacitor, amplifier, and reference values are intentionally not specified at the current development stage.

---

## Power Architecture

A conceptual power path may be:

`Rechargeable Battery → Protection → Regulation → MCU / Sensors / BLE`

The power system should provide stable operation across expected battery voltage and operating conditions.

Separate power domains may be considered if they provide measurable benefits for:

- sensor noise;
- standby power;
- radio operation;
- analog acquisition; or
- subsystem shutdown.

The final topology remains to be determined.

---

## Battery

A compact rechargeable battery is currently considered appropriate for the optional sensor module.

Battery selection should consider:

- capacity;
- dimensions;
- mass;
- discharge capability;
- cycle life;
- charging requirements;
- protection requirements;
- operating temperature;
- mechanical protection;
- supplier documentation; and
- applicable transport and safety requirements.

No final battery capacity or cell model has been selected.

---

## Battery Safety

Battery integration should include appropriate protection against foreseeable electrical faults.

Depending on the selected architecture, protection may address:

- overcharge;
- over-discharge;
- overcurrent;
- short circuit;
- reverse connection where applicable; and
- abnormal temperature conditions.

Mechanical integration should also minimize the risk of:

- crushing;
- puncture;
- excessive bending;
- cable damage; and
- direct exposure to moisture.

Battery safety requirements must be validated before any production design is finalized.

---

## Charging

The sensor module may use a rechargeable architecture.

Potential charging approaches may include:

- USB-based charging;
- removable module charging; or
- another appropriately protected low-voltage charging interface.

The final connector and charging method have not yet been selected.

Charging circuitry should provide controlled charging appropriate to the selected battery chemistry.

---

## Operation During Charging

Whether the sensor module may operate while charging remains a design decision.

This behavior should be evaluated with respect to:

- electrical safety;
- thermal behavior;
- measurement noise;
- charging time;
- firmware complexity; and
- intended user workflow.

The final implementation should define this behavior explicitly.

---

## Battery Monitoring

The electronics may monitor battery state using:

- supply-voltage measurement;
- dedicated battery-management circuitry; or
- a fuel-gauge device.

The mobile application may eventually display an estimated battery level.

Battery percentage should not be presented as highly precise unless the estimation method has been validated against actual discharge behavior.

---

## Power Consumption

Power consumption should be measured for individual operating states.

Potential states include:

| Operating State | Description |
|---|---|
| Off / shipping | Minimum possible consumption |
| Sleep | Electronics inactive except required wake functions |
| Advertising | BLE discoverable |
| Connected idle | BLE connected with limited sensor activity |
| Active sensing | Sensors operating |
| Active streaming | Sensors operating with BLE transmission |
| Calibration | Calibration-related acquisition |
| Charging | Battery charging state |

Measured values should replace theoretical estimates as prototype hardware becomes available.

---

## Power Budget

The total power budget may include:

`MCU + BLE + IMU + Pressure Sensors + Analog Front End + Regulators + Indicators + Other Losses`

Battery runtime should be estimated only after measuring realistic operating modes.

Datasheet minimum-current values should not be treated as representative of complete system consumption.

---

## Low-Power Strategy

Potential power-saving techniques include:

- MCU sleep modes;
- sensor standby modes;
- reduced sampling rates;
- duty-cycled acquisition;
- buffered BLE transmission;
- reduced advertising activity;
- disabling unused analog circuitry;
- automatic inactivity timeout; and
- user-controlled power states.

Power optimization should not compromise required measurement integrity.

---

## Data Storage

The sensor module may require temporary local storage.

Potential uses include:

- configuration;
- calibration coefficients;
- device identifiers;
- firmware metadata;
- diagnostic information; and
- temporary sensor buffering.

Storage may use internal microcontroller flash or another non-volatile memory technology if required.

Raw sensor data should not be retained indefinitely without a defined purpose.

---

## Calibration Data

The electronics should support storage or retrieval of calibration information required by the selected sensors.

Calibration architecture is documented in:

[`calibration.md`](calibration.md)

Calibration data may include:

- offsets;
- scale factors;
- orientation parameters;
- pressure/load coefficients;
- calibration version; and
- validation status.

The final storage format remains under development.

---

## Firmware Interface

Firmware will be responsible for coordinating:

- sensor initialization;
- data acquisition;
- calibration;
- filtering;
- buffering;
- BLE communication;
- power management;
- diagnostics; and
- device state.

Hardware and firmware should therefore be developed together rather than treated as independent systems.

---

## Programming and Debugging

Prototype electronics should provide a practical programming and debugging interface.

Development access may be required for:

- initial programming;
- firmware debugging;
- logging;
- sensor characterization;
- power profiling;
- fault investigation; and
- firmware recovery.

The production design may remove or restrict externally accessible debug functionality where appropriate.

---

## Firmware Updates

Future versions may support firmware updates.

Possible approaches include:

- wired programming;
- service-mode updates; or
- secure over-the-air updates.

A production firmware-update mechanism should include appropriate integrity and security controls.

No final update architecture has yet been selected.

---

## Connectors

Prototype hardware may use connectors for:

- battery;
- sensor arrays;
- programming;
- charging;
- debugging; and
- modular replacement.

Connector selection should consider:

- size;
- insertion cycles;
- locking behavior;
- strain relief;
- current rating;
- contact resistance;
- assembly complexity; and
- resistance to movement during wear.

Production connectors may differ from development-board connectors.

---

## Flexible Interconnects

Because the electronics are intended for integration with a wearable structure, conventional rigid wiring may not always be appropriate.

Possible interconnect approaches may include:

- flexible wires;
- flexible printed circuits;
- conductive textile structures;
- compact board-to-wire connectors; or
- modular sensor harnesses.

The final approach should be selected based on durability and manufacturability testing.

---

## PCB Architecture

Early prototypes may use development boards or modular electronics.

Later prototypes may require a custom PCB to improve:

- dimensions;
- mass;
- power consumption;
- connector placement;
- mechanical integration;
- reliability; and
- manufacturability.

A custom production PCB should not be designed until the main sensor and interface requirements are sufficiently stable.

---

## PCB Design Considerations

Future PCB development should consider:

- power distribution;
- grounding;
- analog/digital separation where required;
- BLE RF layout;
- antenna keep-out;
- decoupling;
- ESD protection;
- programming access;
- test points;
- connector strain;
- component availability; and
- assembly constraints.

RF layout should follow the selected radio manufacturer's design recommendations.

---

## Antenna Integration

Antenna performance is particularly important because the module is intended to operate close to the human body.

Antenna placement should consider:

- body absorption;
- battery position;
- conductive materials;
- structural components;
- enclosure geometry;
- PCB ground plane;
- sensor wiring; and
- textile layers.

RF performance should be tested with the electronics installed in a representative wearable configuration.

---

## Mechanical Integration

Electronics should be integrated without compromising the mechanical purpose of the CORELINE system.

The module should avoid creating:

- uncomfortable pressure points;
- sharp edges;
- excessive local stiffness;
- excessive mass concentration;
- restricted movement; or
- interference with adjustment mechanisms.

A removable module architecture may simplify:

- charging;
- servicing;
- washing of textile components;
- firmware development; and
- electronics replacement.

---

## Enclosure

The sensor electronics may require a protective enclosure.

The enclosure should be evaluated for:

- impact protection;
- comfort;
- weight;
- ventilation;
- cable strain relief;
- accessibility;
- manufacturability; and
- resistance to expected environmental exposure.

Environmental protection requirements have not yet been finalized.

No ingress-protection rating should be claimed until formally tested.

---

## Thermal Considerations

Electronics worn close to the body should avoid uncomfortable surface temperatures.

Thermal testing should evaluate:

- normal sensing;
- continuous BLE transmission;
- charging;
- battery operation;
- fault conditions; and
- high ambient temperature.

Component temperature ratings alone are not sufficient to determine user comfort.

---

## Environmental Considerations

Prototype electronics should eventually be evaluated under conditions representative of intended use.

These may include:

- body heat;
- perspiration;
- humidity;
- repeated movement;
- vibration;
- bending;
- transportation;
- storage; and
- repeated connection/disconnection.

Environmental test requirements will become more specific as the product architecture matures.

---

## Electrical Protection

Depending on the final architecture, protection may be required for:

- USB or charging input;
- external sensor connections;
- programming interfaces;
- battery connections; and
- exposed user-accessible contacts.

Protection strategies may include:

- ESD protection;
- current limiting;
- reverse-polarity protection;
- transient protection; and
- appropriately rated battery protection.

Specific protection components will be selected during circuit development.

---

## Failure Behavior

The electronics should be designed so that electronic failure does not create uncontrolled mechanical loading.

Possible electronic faults include:

- sensor failure;
- MCU reset;
- firmware crash;
- BLE disconnection;
- low battery;
- battery shutdown;
- corrupted calibration data; and
- communication failure.

The mechanical support system should remain fundamentally independent of sensor availability.

---

## Prototype BOM Strategy

A detailed bill of materials should be created only after candidate components have been selected.

The prototype BOM may eventually include categories such as:

| Category | Status |
|---|---|
| BLE-capable MCU | To be selected |
| IMU | To be selected |
| Pressure/load sensors | Under evaluation |
| Analog front end | Architecture dependent |
| Power regulator | To be selected |
| Battery | To be selected |
| Charging controller | To be selected |
| Protection circuitry | To be selected |
| PCB | Future custom design |
| Connectors | Under evaluation |
| Enclosure | Prototype development |

This table is a development framework, not a purchasing BOM.

---

## Component Selection

Components should not be selected solely on headline specifications.

Evaluation should consider:

- measured performance;
- electrical compatibility;
- physical dimensions;
- power consumption;
- documentation quality;
- development support;
- supply availability;
- lifecycle status;
- cost at relevant quantities;
- manufacturing requirements; and
- regulatory implications.

Where possible, alternative components should be identified for supply-chain resilience.

---

## Prototype Stages

Electronics development may progress through stages such as:

### Stage 1 — Bench Prototype

Purpose:

- verify sensor communication;
- characterize sensors;
- test firmware concepts;
- measure basic power consumption; and
- validate BLE communication.

### Stage 2 — Wearable Electronics Prototype

Purpose:

- integrate electronics with the mechanical prototype;
- evaluate cable routing;
- evaluate antenna behavior;
- measure movement-related artifacts;
- test battery operation; and
- assess comfort.

### Stage 3 — Integrated Prototype

Purpose:

- reduce size;
- improve reliability;
- refine power management;
- validate sensor placement;
- improve enclosure design; and
- prepare for extended testing.

### Stage 4 — Pre-Production Electronics

Purpose:

- custom PCB development;
- design-for-manufacturing review;
- formal verification;
- component sourcing;
- safety assessment; and
- compliance preparation.

These stages may change as development progresses.

---

## Verification

Electronics verification should eventually include:

- supply-voltage testing;
- current-consumption measurement;
- sensor communication testing;
- BLE reliability;
- battery runtime;
- charging behavior;
- thermal behavior;
- reset/recovery behavior;
- sensor fault handling;
- calibration retention;
- firmware update behavior;
- mechanical integration; and
- long-duration operation.

Results should be documented with hardware and firmware revision identifiers.

---

## Electronics Test Record

Prototype tests may use a record such as:

| Field | Record |
|---|---|
| Date | |
| PCB / hardware revision | |
| Firmware revision | |
| MCU | |
| Sensor configuration | |
| Battery | |
| Supply voltage | |
| Operating mode | |
| Current consumption | |
| BLE status | |
| Test duration | |
| Temperature observations | |
| Faults observed | |
| Notes | |

This format can evolve as hardware testing becomes more formal.

---

## Security Considerations

The electronics architecture should support appropriate security controls for wireless and firmware functionality.

Potential requirements include:

- protected BLE communication;
- authenticated configuration where appropriate;
- firmware integrity verification;
- restricted debug access in production;
- secure device identity handling; and
- protection against unauthorized firmware modification.

Security requirements will be refined together with the BLE and software architecture.

---

## Privacy by Design

The electronics should collect only data required for intended functionality.

Hardware design should support:

- local processing where practical;
- user-controlled data transmission;
- minimal persistent identifiers;
- controlled data retention; and
- clear separation between sensor measurements and personal identity.

Wireless transmission does not imply mandatory cloud storage.

---

## Manufacturing Considerations

As development progresses, electronics should be reviewed for manufacturability.

Topics include:

- PCB assembly;
- component availability;
- automated assembly compatibility;
- test-point access;
- programming workflow;
- calibration workflow;
- connector assembly;
- enclosure assembly;
- final electrical testing; and
- traceability.

Production processes are not yet defined.

---

## Regulatory Considerations

A future wireless electronic product may require assessment against applicable requirements for:

- radio equipment;
- electromagnetic compatibility;
- electrical safety;
- battery safety;
- environmental compliance; and
- product-specific regulations.

Applicable requirements will depend on final product classification, markets, architecture, and intended claims.

No certification status is claimed by this document.

---

## Relationship to Other Documentation

This document should be read together with:

- [`bluetooth-connection.md`](bluetooth-connection.md) — proposed BLE architecture;
- [`calibration.md`](calibration.md) — sensor calibration framework;
- [`../../docs/sensor-module.md`](../../docs/sensor-module.md) — sensor-module overview;
- [`../../docs/mobile-app.md`](../../docs/mobile-app.md) — mobile application concept;
- [`../../docs/roadmap.md`](../../docs/roadmap.md) — project development roadmap; and
- [`../../docs/open-data-policy.md`](../../docs/open-data-policy.md) — data and documentation principles.

---

## Current Status

The electronics architecture remains under development.

The following items are **not yet finalized**:

- microcontroller;
- BLE radio implementation;
- IMU;
- pressure/load sensor technology;
- sensor count;
- analog front end;
- battery chemistry and capacity;
- charging architecture;
- voltage regulators;
- connectors;
- PCB dimensions;
- antenna design;
- enclosure;
- firmware architecture;
- production BOM; and
- compliance strategy.

Component-level specifications should therefore not be interpreted as finalized until supported by prototype testing and documented design decisions.

---

## Disclaimer

This document describes an **experimental electronics architecture** for the CORELINE Sensor Edition.

It is not a final schematic, production BOM, certified radio design, validated battery system, manufacturing specification, or medical-device electronics specification.

Final hardware will require electrical design review, physical prototype testing, safety evaluation, firmware validation, wireless testing, and applicable regulatory assessment.
