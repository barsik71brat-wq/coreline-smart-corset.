# Bluetooth Connection

## CORELINE Sensor Edition

This document describes the proposed Bluetooth Low Energy (BLE) communication architecture for the optional CORELINE Sensor Edition.

The wireless interface is intended to transfer posture, motion, load, device-status, and related sensor information between the removable sensor module and compatible software.

It is **not yet a final production communication specification**. Service definitions, characteristics, UUIDs, packet structures, security configuration, and hardware implementation remain subject to prototype testing.

> **Development status:** Sensor prototype / communication architecture  
> The BLE implementation described here represents the current engineering direction and may change as electronics and software development progresses.

---

## Purpose

Bluetooth connectivity is intended to provide a low-power wireless link between the CORELINE sensor module and a compatible mobile device.

The connection may support:

- sensor data streaming;
- device status reporting;
- battery-level monitoring;
- configuration;
- calibration-related commands;
- synchronization;
- connection diagnostics; and
- future firmware-management functions.

The mechanical CORELINE prototype does not depend on Bluetooth connectivity for its basic structural function.

---

## Communication Technology

The current architecture assumes the use of:

**Bluetooth Low Energy (BLE)**

BLE is being considered because it provides:

- low-power wireless communication;
- broad smartphone compatibility;
- standardized discovery and connection mechanisms;
- support for custom application data;
- established security mechanisms; and
- suitable bandwidth for the expected sensor data rates.

The final Bluetooth version and radio hardware have not yet been selected.

---

## System Architecture

A typical communication path is expected to be:

`Sensors → Embedded Controller → BLE Interface → Mobile Device → CORELINE Application`

The embedded electronics may collect data from:

- inertial sensors;
- pressure or force sensors;
- battery monitoring circuitry; and
- other future optional sensors.

The controller processes or packages the measurements before transmission over BLE.

---

## Device Roles

In the proposed architecture:

### Sensor Module

The CORELINE sensor module normally acts as the BLE peripheral.

Its responsibilities may include:

- advertising;
- accepting authorized connections;
- exposing sensor characteristics;
- transmitting measurement data;
- receiving configuration commands; and
- reporting device status.

### Mobile Device

The mobile device normally acts as the BLE central.

Its responsibilities may include:

- discovering the sensor module;
- initiating a connection;
- performing pairing where required;
- subscribing to data characteristics;
- sending configuration commands;
- displaying device status; and
- storing or processing authorized data.

---

## Device Discovery

When wireless communication is enabled, the sensor module may advertise a recognizable CORELINE device identifier.

The final advertising format has not yet been defined.

Advertising data may eventually contain limited information such as:

- device family;
- protocol version;
- connection availability; and
- basic capability indicators.

Personally identifiable information should not be included unnecessarily in BLE advertising packets.

---

## Pairing and Connection

The proposed connection sequence is:

1. sensor module enters advertising mode;
2. mobile application scans for compatible CORELINE devices;
3. the user selects or confirms the intended device;
4. the mobile device establishes a BLE connection;
5. supported services and characteristics are discovered;
6. security or pairing procedures are completed where required;
7. the application subscribes to required data channels; and
8. sensor communication begins.

The exact user interaction and authentication method remain under development.

---

## BLE Services

The prototype architecture may use one or more custom BLE services.

Potential service groups include:

### Sensor Data Service

May provide:

- motion data;
- orientation data;
- acceleration;
- angular velocity;
- pressure/load measurements; and
- derived posture metrics.

### Device Status Service

May provide:

- battery level;
- operating state;
- sensor status;
- error indicators;
- firmware version; and
- hardware revision.

### Configuration Service

May support:

- sampling-rate configuration;
- sensor enable/disable controls;
- calibration commands;
- operating-mode selection; and
- other prototype configuration parameters.

Final service definitions have not yet been established.

---

## Characteristics

BLE characteristics may use standard operations such as:

- **Read** — retrieve a current value;
- **Write** — send configuration or commands;
- **Notify** — stream updated values without repeated polling; and
- **Indicate** — transmit values requiring acknowledgement where appropriate.

High-frequency sensor measurements would normally be candidates for notifications.

Configuration values may use read/write characteristics.

The final characteristic structure will depend on measured bandwidth, power consumption, reliability, and software requirements.

---

## Provisional Data Categories

The sensor module may transmit data including:

- timestamp;
- accelerometer measurements;
- gyroscope measurements;
- orientation representation;
- pressure or load measurements;
- battery level;
- sensor status; and
- diagnostic flags.

This corresponds to the provisional sensor-data architecture documented elsewhere in the repository.

The exact binary representation remains under development.

---

## Example Logical Packet

A future sensor packet could conceptually contain:

| Field | Purpose |
|---|---|
| Protocol version | Identifies packet interpretation |
| Sequence number | Detects missing or reordered data |
| Timestamp | Associates measurements with time |
| Sensor flags | Identifies included measurements |
| Motion data | IMU measurements |
| Load data | Pressure/load measurements |
| Battery/status | Device state |
| Integrity field | Optional validation information |

This table describes a possible logical structure only.

It is **not a finalized wire protocol**.

---

## Sampling and Transmission

Sensor sampling frequency and BLE transmission frequency do not necessarily need to be identical.

For example, the embedded system may:

1. sample sensors internally;
2. temporarily buffer measurements;
3. perform basic preprocessing;
4. group measurements into packets; and
5. transmit them at an appropriate BLE interval.

This approach may improve power efficiency and reduce wireless overhead.

Actual sampling and transmission rates will be determined through prototype testing.

---

## Bandwidth Considerations

BLE bandwidth requirements depend on:

- number of active sensors;
- sampling frequency;
- measurement resolution;
- packet overhead;
- connection interval;
- notification frequency; and
- retransmission behavior.

The communication architecture should therefore be validated using real prototype measurements rather than theoretical maximum BLE throughput.

---

## Power Management

Wireless communication can represent a significant part of sensor-module power consumption.

Potential power-management strategies include:

- reduced advertising frequency when appropriate;
- automatic sleep states;
- configurable sampling rates;
- buffered transmission;
- disabling unused sensors;
- connection timeout behavior; and
- adaptive transmission frequency.

Power behavior will be evaluated together with battery capacity and electronics design.

---

## Connection Loss

Temporary Bluetooth disconnection should not create unsafe behavior in the mechanical device.

Possible software behavior after connection loss may include:

1. stop live transmission;
2. preserve essential local device state;
3. attempt controlled reconnection;
4. notify the user through the application; and
5. resume communication when the connection is restored.

Whether sensor measurements are buffered during disconnection remains an implementation decision.

---

## Reconnection

The system should be designed to recover from common interruptions such as:

- temporary radio interference;
- mobile application restart;
- smartphone Bluetooth restart;
- sensor-module sleep;
- movement outside wireless range; and
- temporary power interruption.

Reconnection behavior should be predictable and should avoid accidental connection to an unintended device.

---

## Security

BLE communication should use appropriate platform-supported security mechanisms.

The final implementation may include:

- authenticated pairing where appropriate;
- encrypted BLE links;
- controlled access to configuration characteristics;
- protection against unauthorized command execution;
- device identity validation; and
- secure handling of stored pairing information.

Security requirements will be refined as the electronics and application architecture mature.

---

## Privacy

The wireless architecture should minimize unnecessary exposure of user-related information.

Design principles include:

- transmitting only data required for intended functionality;
- avoiding personal information in advertising packets;
- limiting persistent identifiers where practical;
- encrypting communication where appropriate;
- allowing user control over cloud synchronization; and
- separating device telemetry from user identity where possible.

Raw sensor data should remain under user-controlled data policies described elsewhere in the repository.

---

## Data Storage

Bluetooth transmission does not inherently require cloud storage.

The proposed architecture allows sensor data to be:

- processed locally;
- stored temporarily on the mobile device;
- retained on the sensor module where supported; or
- shared with remote services only when explicitly enabled by the applicable software architecture.

Final storage behavior will be documented separately from the BLE transport protocol.

---

## Calibration Communication

BLE may also be used during sensor calibration.

Potential calibration operations include:

- start calibration;
- stop calibration;
- request current calibration state;
- transmit reference measurements;
- store calibration coefficients; and
- report calibration errors.

Calibration procedures are documented separately in:

[`calibration.md`](calibration.md)

---

## Electronics Integration

The Bluetooth implementation depends on the final electronics architecture.

Relevant hardware considerations include:

- BLE-capable microcontroller or radio;
- antenna placement;
- enclosure materials;
- battery capacity;
- power regulation;
- sensor bus architecture;
- electromagnetic interference;
- firmware memory requirements; and
- physical separation from structural components.

Electronics development is documented in:

[`electronics.md`](electronics.md)

---

## Antenna Considerations

Because the sensor module is intended for use close to the human body, antenna performance should be evaluated in realistic conditions.

Testing should consider:

- body proximity;
- orientation;
- textile layers;
- structural materials;
- electronics enclosure;
- battery position; and
- normal movement.

Radio performance measured on an open workbench may not represent performance when the module is installed in the wearable system.

---

## Reliability Testing

BLE prototype testing should evaluate:

- discovery reliability;
- connection establishment time;
- connection stability;
- packet loss;
- reconnection behavior;
- effective operating range;
- latency;
- throughput;
- power consumption;
- smartphone compatibility; and
- behavior during normal body movement.

Testing should include more than one compatible mobile device where practical.

---

## Error Handling

The software architecture should distinguish between conditions such as:

- sensor unavailable;
- Bluetooth unavailable;
- device not found;
- pairing failure;
- connection timeout;
- unexpected disconnection;
- malformed packet;
- unsupported protocol version;
- sensor error; and
- low battery.

Clear error classification will simplify application behavior and prototype debugging.

---

## Protocol Versioning

The BLE data protocol should include a mechanism for version identification.

This allows firmware and software to evolve without silently misinterpreting incompatible packet formats.

A future implementation may maintain separate identifiers for:

- hardware revision;
- firmware version;
- BLE protocol version; and
- data-format version.

The exact versioning scheme remains to be defined.

---

## Development Logging

During prototype development, BLE testing should record:

| Field | Record |
|---|---|
| Hardware revision | |
| Firmware revision | |
| Protocol revision | |
| Mobile device | |
| Operating system | |
| Connection interval | |
| Sampling configuration | |
| Test duration | |
| Connection interruptions | |
| Packet errors | |
| Observed range | |
| Battery behavior | |
| Notes | |

This information can help distinguish software, radio, hardware, and environmental problems.

---

## Future Development

Potential future communication features may include:

- optimized binary sensor packets;
- synchronized multi-sensor measurements;
- local buffering;
- configurable streaming modes;
- diagnostic telemetry;
- secure firmware updates;
- improved reconnection logic;
- standardized device capability discovery; and
- additional optional sensor channels.

These features are not required for the basic mechanical CORELINE prototype.

---

## Relationship to Other Documentation

This document should be read together with:

- [`electronics.md`](electronics.md) — sensor electronics architecture;
- [`calibration.md`](calibration.md) — sensor calibration approach;
- [`../../docs/sensor-module.md`](../../docs/sensor-module.md) — sensor-module overview;
- [`../../docs/mobile-app.md`](../../docs/mobile-app.md) — mobile application concept;
- [`../../docs/open-data-policy.md`](../../docs/open-data-policy.md) — data and sharing principles; and
- [`../../docs/roadmap.md`](../../docs/roadmap.md) — project development roadmap.

---

## Current Status

The BLE architecture remains under development.

The following items are **not yet finalized**:

- BLE chipset or microcontroller;
- Bluetooth version;
- service UUIDs;
- characteristic UUIDs;
- packet format;
- sampling rates;
- connection parameters;
- pairing method;
- authentication model;
- firmware-update mechanism; and
- production security configuration.

These decisions should be based on hardware prototyping and measured system requirements rather than treated as fixed specifications at the current stage.

---

## Disclaimer

This document describes an **experimental sensor communication architecture**.

It is not a final wireless specification, certified radio implementation, production security specification, or validated medical-device communication protocol.

Final implementation will require hardware testing, software validation, security review, interoperability testing, and applicable regulatory assessment.
