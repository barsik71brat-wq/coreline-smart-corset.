# CORELINE Mobile App

## Overview

The CORELINE Mobile App is a **future companion application concept** for sensor-enabled versions of the CORELINE platform.

The application is intended to provide a user interface for viewing measurements collected by compatible CORELINE sensor modules, managing device configuration, and presenting useful summaries of wear and movement data.

> **Development status**
>
> The mobile application is currently a concept / R&D component of the CORELINE architecture.
> Features described in this document represent planned or candidate functionality and should not be interpreted as currently available product capabilities.
>
> The application is not intended to provide medical diagnosis, treatment recommendations, or clinical interpretation unless such functionality is separately developed, validated, and approved for the applicable intended use.

---

## Design Principles

The application architecture should prioritize:

- clear and understandable presentation of sensor data;
- minimal user interaction during normal wear;
- privacy by design;
- local processing where practical;
- explicit user control over data sharing;
- reliable operation when an internet connection is unavailable;
- compatibility with modular CORELINE hardware;
- separation between raw measurements and interpreted metrics;
- transparent indication of sensor quality and connection status; and
- accessibility across supported mobile platforms.

The application should remain useful without requiring unnecessary collection of personal data.

---

# Planned Architecture

A future CORELINE mobile system may consist of:

1. a sensor-enabled CORELINE wearable;
2. a removable electronics module;
3. a wireless communication interface;
4. the CORELINE mobile application; and
5. optional user-controlled data export or synchronization services.

The mechanical support system should remain operational independently of the mobile application.

Loss of phone connectivity must therefore not prevent the baseline wearable from performing its mechanical function.

---

# Candidate Features

## 1. Device Connection

The application may provide:

- discovery of compatible CORELINE devices;
- secure device pairing;
- connection-status monitoring;
- battery-status reporting;
- sensor-module identification;
- hardware and firmware version information; and
- controlled device removal / unpairing.

Bluetooth Low Energy (BLE) is a candidate communication technology for future prototypes.

The final communication protocol will depend on hardware architecture, power requirements, security evaluation, and prototype testing.

---

## 2. Live Sensor Visualization

Sensor-enabled versions may provide real-time or near-real-time visualization of selected measurements.

Potential measurements include:

- torso orientation;
- motion data;
- relative posture changes;
- pressure or force distribution;
- device wear state;
- temperature; and
- humidity.

The exact measurements available will depend on the installed sensor module.

### Visualization principle

The application should clearly distinguish between:

- **raw sensor measurements**;
- **processed measurements**;
- **derived metrics**; and
- **user-facing interpretations**.

Derived values should not be presented as clinically meaningful measurements unless their accuracy and intended use have been independently validated.

---

## 3. Movement & Posture Trends

The application may calculate summaries from compatible motion sensors.

Candidate outputs include:

- time spent in selected orientation ranges;
- movement frequency;
- changes in torso orientation over time;
- wear duration;
- activity periods; and
- user-defined posture or movement events.

Rather than presenting an unexplained universal "posture score," the application should favor transparent metrics that users can understand.

If a composite score is introduced, its calculation method, limitations, and validation status should be documented.

---

## 4. Pressure Visualization

Future prototypes equipped with pressure or force sensors may provide a simplified visualization of interface loading.

Potential functions include:

- relative pressure mapping;
- left/right loading comparison;
- identification of unusually concentrated loads;
- fit-assessment support during prototype testing; and
- historical comparison between sessions.

Pressure measurements should not be interpreted as medical diagnostic information without appropriate validation.

Sensor calibration, drift, hysteresis, placement, temperature sensitivity, and textile deformation must be considered when interpreting these measurements.

---

## 5. Wear-Time Tracking

Where supported by hardware, the application may estimate:

- session start and end;
- total wear duration;
- interruptions in wear;
- daily or weekly usage patterns; and
- sensor operating time.

Wear detection should preferably use device measurements rather than assuming that a connected device is necessarily being worn.

---

# Calibration

Some future sensor configurations may require calibration.

The application may guide the user through procedures such as:

1. device connection;
2. sensor readiness check;
3. neutral reference position;
4. calibration measurement;
5. quality verification; and
6. calibration storage.

Calibration requirements should be specific to the installed sensor type.

The application should never hide calibration failure or poor measurement quality from the user.

---

# Personalized Thresholds

The system may allow users to configure non-clinical thresholds for selected measurements.

Examples could include:

- orientation ranges;
- inactivity duration;
- wear-time targets; and
- user-defined movement reminders.

Default thresholds should not be represented as medically optimal values unless supported by appropriate evidence and validation.

Personalization should therefore be presented as configuration rather than diagnosis or treatment.

---

# Notifications

Optional notifications may include:

- device disconnected;
- low battery;
- calibration required;
- firmware update available;
- user-defined wear-time reminder; and
- user-defined movement reminder.

Notifications should be configurable and should avoid unnecessary interruption.

The application should not use alarm-like language for measurements that have not been validated as safety-critical.

---

# Historical Data

The application may provide session and trend views such as:

- daily summaries;
- weekly summaries;
- wear-time history;
- movement trends;
- user-selected sensor metrics; and
- device status history.

Historical information should clearly indicate missing or incomplete data.

The interface should avoid presenting gaps in sensor recording as valid zero values.

---

# Data Model

A future implementation should maintain separation between several classes of data.

| Data class | Examples |
|---|---|
| Device metadata | Hardware revision, firmware version, device identifier |
| Raw measurements | Accelerometer, gyroscope, pressure, temperature |
| Processed measurements | Orientation, filtered pressure values |
| Derived metrics | Wear duration, movement statistics |
| User configuration | Thresholds, notification preferences |
| System events | Connection, calibration, firmware events |

Each derived metric should be traceable to its source measurements and processing version where practical.

---

# Offline Operation

Core application functionality should be designed to work without continuous internet access.

Candidate offline capabilities include:

- device connection;
- live visualization;
- calibration;
- local session recording;
- local historical summaries; and
- configuration.

Cloud connectivity should not be required merely to operate a locally connected CORELINE device unless a future feature has a specific technical reason for doing so.

---

# Data Storage & Privacy

CORELINE should follow a **privacy-by-design** approach.

Design principles include:

- collect only data required for defined functionality;
- prefer local storage where practical;
- avoid unnecessary personal identifiers;
- provide clear data-retention behavior;
- allow users to delete locally stored data;
- require explicit user action before optional data sharing;
- protect stored data using platform security mechanisms; and
- protect data in transit using appropriate authenticated encryption.

The application should clearly document what information is collected, where it is stored, and whether it leaves the user's device.

---

# Data Export

Future versions may allow users to export their own measurements.

Potential formats include:

- CSV for tabular measurements;
- JSON for structured datasets; and
- summarized reports for selected sessions.

Exported datasets should include sufficient metadata to interpret the measurements, such as:

- timestamp;
- sensor type;
- units;
- sampling information where applicable;
- firmware version;
- processing version; and
- calibration status where relevant.

Any export functionality should remain consistent with the project's data and privacy policy.

---

# Security

A production implementation should include a documented security model covering:

- secure pairing;
- device authentication;
- communication encryption;
- firmware authenticity;
- protection against unauthorized configuration changes;
- secure local storage;
- dependency management;
- vulnerability handling; and
- software update lifecycle.

Security requirements should be defined before production deployment rather than added after hardware and application development are complete.

---

# Firmware Updates

The application may eventually provide a firmware update interface for compatible electronics modules.

A production update mechanism should support:

- firmware version verification;
- integrity checking;
- authenticated firmware packages;
- interrupted-update recovery;
- compatibility checks; and
- clear reporting of update status.

Firmware updates should not modify the fundamental mechanical operation of the wearable.

---

# Platform Strategy

Potential mobile targets include:

- Android; and
- iOS.

The implementation strategy may use native or cross-platform development depending on:

- Bluetooth requirements;
- background-operation requirements;
- sensor data throughput;
- maintainability;
- testing requirements; and
- available development resources.

No specific mobile framework is considered mandatory at the concept stage.

---

# Accessibility & UX

The application should aim for:

- readable typography;
- high-contrast interfaces;
- understandable units and terminology;
- color-independent status indicators;
- clear error messages;
- minimal setup complexity;
- support for common device accessibility settings; and
- visualization that does not require specialist knowledge to interpret.

Technical sensor information may be exposed through optional advanced views without making the primary interface unnecessarily complex.

---

# Validation Strategy

Application validation should occur progressively.

## Functional testing

Examples include:

- pairing and reconnection;
- sensor data acquisition;
- calibration workflows;
- local storage;
- data export;
- notification behavior; and
- firmware update recovery.

## Measurement validation

For each displayed sensor-derived metric, testing should address:

- accuracy;
- precision;
- repeatability;
- latency;
- drift;
- missing-data behavior; and
- sensitivity to device placement.

## Usability testing

Representative users should be evaluated for their ability to:

- connect the device;
- understand connection status;
- complete calibration;
- interpret displayed measurements;
- configure relevant settings; and
- identify measurement or connection errors.

---

# Relationship to the CORELINE Hardware

The mobile application should be treated as an optional layer above the mechanical platform:

```text
┌───────────────────────────────────────┐
│          CORELINE Mobile App          │
│ Visualization · History · Settings    │
└───────────────────┬───────────────────┘
                    │
              Wireless link
                    │
┌───────────────────▼───────────────────┐
│       Removable Electronics Module    │
│ MCU · Power · Communications          │
└───────────────────┬───────────────────┘
                    │
┌───────────────────▼───────────────────┐
│             Sensor Layer              │
│ IMU · Pressure · Environmental        │
└───────────────────┬───────────────────┘
                    │
┌───────────────────▼───────────────────┐
│       Mechanical CORELINE System      │
│ Support · Compression · Comfort       │
└───────────────────────────────────────┘
