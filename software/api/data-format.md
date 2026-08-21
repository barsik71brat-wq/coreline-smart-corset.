# Sensor Data Format

## Status

**Provisional specification — subject to change during sensor-module development.**

This document describes the proposed data structure for the optional
CORELINE sensor module.

The mechanical CORELINE prototype does not require electronics or this
data format for its core biomechanical function.

---

## Overview

The future sensor module may collect:

- inertial measurement unit (IMU) data;
- pressure measurements;
- battery status;
- device status information.

Data may be transmitted to a companion application using Bluetooth Low
Energy (BLE).

JSON is currently proposed as a human-readable representation for
development and testing.

---

## Example Payload

```json
{
  "schema_version": "0.1",
  "timestamp": "2026-08-21T12:30:45.250Z",
  "device_id": "coreline-dev-001",
  "imu": {
    "accel": {
      "x": 0.02,
      "y": -0.11,
      "z": 9.79
    },
    "gyro": {
      "x": 0.4,
      "y": -0.2,
      "z": 0.1
    }
  },
  "pressure": [
    12.4,
    18.1,
    16.7,
    10.9
  ],
  "battery": {
    "level_percent": 82
  }
}
