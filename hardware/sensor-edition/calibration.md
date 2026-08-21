# Sensor Calibration

## CORELINE Sensor Edition

This document describes the proposed calibration framework for sensors used in the optional CORELINE Sensor Edition.

The calibration process is intended to improve measurement consistency and establish reference conditions for motion, orientation, pressure, and load-related measurements.

It is **not yet a final production calibration procedure**. Sensor selection, calibration algorithms, acceptance limits, reference equipment, and production procedures remain subject to prototype testing and validation.

> **Development status:** Sensor prototype / calibration architecture  
> Calibration methods described here represent the current engineering direction and may change as sensor hardware and firmware are developed.

---

## Purpose

Calibration is intended to reduce measurement errors caused by factors such as:

- sensor manufacturing tolerances;
- installation orientation;
- mechanical integration;
- zero-offset variation;
- temperature effects;
- sensor drift;
- pressure-sensor variation;
- material deformation; and
- differences between individual sensor modules.

Calibration does not convert the system into a medical diagnostic device.

The objective at the current development stage is repeatable engineering measurement suitable for prototype evaluation.

---

## Sensor Categories

The Sensor Edition may include several sensor types.

### Inertial Measurement Unit (IMU)

A future IMU may provide:

- acceleration;
- angular velocity;
- orientation-related data; and
- motion information.

Depending on the selected hardware, additional sensing capabilities may be available.

### Pressure / Load Sensors

Pressure or force-sensitive elements may be used to estimate:

- local loading;
- relative pressure distribution;
- changes in support loading;
- contact patterns; and
- changes associated with posture or movement.

The final sensor technology and placement have not yet been finalized.

---

## Calibration Architecture

Calibration may be divided into several levels:

1. **sensor-level calibration** — compensation for individual sensor characteristics;
2. **module-level calibration** — calibration after sensors are integrated into the electronics module;
3. **installation calibration** — compensation for sensor orientation and mechanical placement;
4. **user reference calibration** — establishing a reference condition after fitting; and
5. **verification** — checking whether calibration remains within acceptable limits.

Not every level will necessarily be required in the final implementation.

---

## Calibration Data

A calibration record may eventually contain information such as:

| Field | Purpose |
|---|---|
| Hardware revision | Identifies sensor-module configuration |
| Sensor identifier | Identifies sensor or sensor group |
| Firmware version | Records firmware used during calibration |
| Calibration version | Identifies calibration method |
| Timestamp | Records calibration time |
| Offset values | Zero/bias compensation |
| Scale factors | Sensitivity compensation |
| Orientation parameters | Sensor alignment correction |
| Pressure coefficients | Pressure/load correction where required |
| Temperature reference | Reference temperature if applicable |
| Validation status | Result of calibration verification |

The final calibration data structure has not yet been defined.

---

## IMU Calibration

### Accelerometer

Accelerometer calibration may compensate for:

- zero-g offset;
- axis-dependent sensitivity;
- axis misalignment; and
- other systematic measurement errors.

A prototype calibration procedure may use known stationary orientations to establish reference measurements.

For example, gravity can provide a useful reference during stationary testing.

The final method will depend on the selected IMU and required measurement accuracy.

---

## Gyroscope Calibration

Gyroscope calibration may include estimation of zero-rate bias.

A basic prototype procedure may:

1. place the module in a stationary condition;
2. collect gyroscope samples for a defined period;
3. estimate average zero-rate output;
4. store calculated bias values; and
5. subtract those values during subsequent measurements.

The required sample duration and acceptance criteria will be determined experimentally.

---

## Orientation Alignment

Even a correctly calibrated IMU may produce misleading orientation data if its physical coordinate system does not match the coordinate system of the wearable structure.

Installation calibration may therefore define the relationship between:

- sensor axes;
- electronics-module orientation;
- mechanical support structure; and
- body-relative reference directions.

A transformation may then be applied in firmware or software.

The final coordinate convention should be documented once sensor placement is fixed.

---

## Stationary Reference

Some calibration operations require the sensor module to remain stationary.

The software should verify, where practical, that movement remains below an acceptable threshold before accepting a stationary reference.

If excessive movement is detected, calibration should be rejected or restarted rather than silently storing an unreliable reference.

---

## Pressure / Load Sensor Calibration

Pressure or force-sensitive sensors may require calibration because their output can vary between individual elements.

Potential sources of variation include:

- manufacturing tolerance;
- sensor geometry;
- mounting pressure;
- textile compression;
- mechanical preload;
- temperature;
- hysteresis;
- repeated loading; and
- material aging.

The final calibration method will depend strongly on the selected sensor technology.

---

## Zero-Load Calibration

A pressure-sensor array may require a zero or baseline measurement.

A conceptual procedure may include:

1. place the system in the defined unloaded reference condition;
2. verify that no unintended external load is present;
3. collect multiple samples;
4. calculate baseline values for each sensing element;
5. reject unstable measurements; and
6. store the accepted baseline.

This baseline can later be removed from raw measurements.

---

## Loaded Reference Calibration

Where quantitative load estimation is required, calibration may use one or more known reference loads.

Prototype testing may compare sensor output against controlled reference conditions to evaluate:

- sensitivity;
- linearity;
- repeatability;
- hysteresis;
- sensor-to-sensor variation; and
- long-term stability.

The project should not claim absolute force or pressure accuracy until it has been experimentally established.

---

## Relative vs. Absolute Measurements

During early development, relative pressure distribution may be more reliable than absolute pressure measurement.

For example, the system may initially evaluate:

- whether loading increases or decreases;
- how load is distributed across sensing regions;
- changes from a personal baseline; and
- differences between postures or movements.

Absolute physical units should only be reported when the measurement chain has been appropriately calibrated and validated.

---

## User Reference Calibration

A future application may allow the user to establish a personal reference condition.

A possible workflow is:

1. correctly fit the CORELINE system;
2. connect the sensor module;
3. confirm sensor communication;
4. assume the required reference posture or condition;
5. remain stationary for the required period;
6. collect baseline sensor measurements;
7. verify measurement stability; and
8. store the accepted reference.

The exact user procedure has not yet been finalized.

---

## Calibration Quality Checks

Calibration should not automatically be considered valid merely because a procedure completed.

Possible quality checks include:

- measurement stability;
- sensor availability;
- communication integrity;
- expected measurement range;
- excessive noise detection;
- movement detection;
- comparison with previous calibration;
- missing sensor channels; and
- physically implausible values.

Failed checks should produce a clear calibration error rather than storing questionable calibration data.

---

## Calibration States

The firmware or application may distinguish between states such as:

- not calibrated;
- calibration in progress;
- calibration valid;
- calibration failed;
- calibration data unavailable;
- calibration outdated; and
- recalibration recommended.

The exact state model will be defined together with firmware and application development.

---

## Recalibration

Recalibration may be required after events such as:

- sensor replacement;
- electronics-module replacement;
- firmware changes affecting sensor processing;
- mechanical reassembly;
- significant change in sensor placement;
- detected calibration drift;
- failed verification; or
- extended prototype testing.

The final product may also implement periodic calibration verification.

---

## Calibration Storage

Calibration coefficients may be stored:

- in non-volatile memory within the sensor module;
- in the mobile application;
- or through a combination of both.

Storing essential sensor-specific calibration data on the module may help preserve consistency when the module connects to a different compatible device.

The final storage architecture has not yet been selected.

---

## Calibration Versioning

Calibration data should include a version identifier.

This helps prevent incompatible firmware or software from applying calibration coefficients using the wrong interpretation.

A future system may separately track:

- hardware revision;
- sensor configuration;
- firmware version;
- calibration algorithm version; and
- calibration-data version.

---

## Raw and Calibrated Data

During engineering development, it may be useful to distinguish between:

**Raw data**  
Direct or minimally processed sensor output.

**Calibrated data**  
Sensor output after applying validated calibration parameters.

**Derived data**  
Higher-level values calculated from calibrated measurements.

Keeping these categories distinct can simplify debugging and validation.

---

## Calibration Pipeline

A conceptual processing sequence may be:

`Raw Sensor Data → Offset Correction → Scale Correction → Alignment Correction → Filtering → Calibrated Data → Derived Metrics`

The exact sequence may differ depending on sensor type.

Filtering and calibration should be treated as separate processing functions where practical.

---

## Temperature Effects

Some sensors may exhibit temperature-dependent behavior.

Prototype testing should determine whether temperature significantly affects:

- IMU bias;
- pressure-sensor baseline;
- sensitivity;
- drift; or
- measurement stability.

Temperature compensation should only be introduced if testing demonstrates that it is necessary and provides measurable improvement.

---

## Mechanical Effects

Calibration should be evaluated with sensors installed in the actual wearable structure.

Bench calibration alone may not capture effects caused by:

- textile tension;
- foam compression;
- structural reinforcement;
- sensor curvature;
- mounting method;
- body contact; and
- repeated flexing.

For this reason, module-level and installed-system testing are important parts of the development process.

---

## Verification Testing

Calibration verification may include repeated measurements under known conditions.

Testing should evaluate:

- repeatability;
- short-term stability;
- drift;
- sensor-to-sensor consistency;
- behavior after power cycling;
- behavior after reconnection;
- mechanical repositioning effects; and
- long-duration operation.

Results should be recorded rather than relying only on visual inspection.

---

## Prototype Test Record

A calibration test record may use a structure such as:

| Field | Record |
|---|---|
| Date | |
| Prototype revision | |
| Hardware revision | |
| Firmware revision | |
| Sensor type | |
| Sensor identifier | |
| Calibration method | |
| Reference equipment | |
| Environmental conditions | |
| Initial values | |
| Calibration coefficients | |
| Verification result | |
| Observed drift | |
| Notes | |

This structure may evolve as testing becomes more formal.

---

## Reference Equipment

Calibration and verification may require external reference equipment.

Depending on the sensor being tested, this could include:

- stable mechanical fixtures;
- known reference masses or forces;
- orientation fixtures;
- calibrated measurement equipment; and
- controlled test surfaces.

The required equipment will be selected after sensor architecture is defined.

Reference equipment accuracy should be appropriate for the measurement being evaluated.

---

## Error Handling

Calibration software should distinguish between errors such as:

- sensor unavailable;
- unstable reference condition;
- excessive movement;
- measurement outside expected range;
- communication failure;
- invalid calibration data;
- incompatible calibration version;
- storage failure; and
- verification failure.

Clear error reporting is important for both development testing and future user-facing workflows.

---

## Safety Considerations

Sensor calibration should not alter the mechanical support structure in a way that creates unsafe loading or excessive compression.

Calibration procedures should avoid requiring users to:

- intentionally assume painful positions;
- apply uncontrolled external loads;
- exceed normal adjustment ranges; or
- treat sensor output as medical diagnosis.

Prototype calibration should be performed under controlled conditions appropriate to the test being conducted.

---

## Relationship to Bluetooth

Calibration commands and calibration status may be exchanged through BLE.

Possible operations include:

- request calibration;
- start calibration;
- cancel calibration;
- retrieve calibration status;
- read calibration version; and
- report calibration errors.

The proposed wireless architecture is documented in:

[`bluetooth-connection.md`](bluetooth-connection.md)

---

## Relationship to Electronics

Calibration requirements depend directly on the selected:

- sensors;
- microcontroller;
- analog front-end;
- ADC configuration;
- power architecture; and
- physical sensor installation.

Electronics development is documented in:

[`electronics.md`](electronics.md)

---

## Relationship to Software

The mobile application may eventually provide:

- calibration guidance;
- progress indication;
- calibration validation feedback;
- error messages;
- recalibration prompts; and
- engineering diagnostics.

Application behavior remains under development.

See:

[`../../docs/mobile-app.md`](../../docs/mobile-app.md)

---

## Development Priorities

Before calibration can be treated as a stable specification, development should establish:

1. final prototype sensor types;
2. sensor placement;
3. electronics architecture;
4. raw measurement characteristics;
5. repeatability;
6. drift behavior;
7. appropriate reference procedures;
8. calibration algorithms;
9. acceptance criteria; and
10. verification procedures.

Measured prototype data should drive these decisions.

---

## Current Status

The calibration architecture remains under development.

The following items are **not yet finalized**:

- IMU model;
- pressure/load sensor technology;
- sensor count;
- sensor placement;
- calibration coefficients;
- reference loads;
- calibration duration;
- acceptance tolerances;
- recalibration interval;
- temperature compensation;
- calibration storage format; and
- production calibration equipment.

No specific accuracy claim should be inferred from this document.

---

## Disclaimer

This document describes an **experimental engineering calibration framework** for the CORELINE Sensor Edition.

It is not a validated medical calibration protocol, production quality-control specification, clinical measurement procedure, or certification document.

Final procedures and performance claims will require physical prototype testing, documented verification, and appropriate regulatory assessment where applicable.
