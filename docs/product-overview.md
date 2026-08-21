# Product Overview

## CORELINE Smart Corset

CORELINE is an experimental **wearable spinal-support platform** designed to explore a lightweight, adaptive alternative to conventional rigid support systems.

The project combines:

- biomechanical support structures;
- adjustable textile compression;
- breathable wearable materials;
- modular mechanical components; and
- a future-ready architecture for optional sensing and digital features.

The current development focus is the **passive mechanical and textile system**. Sensor electronics, posture analytics, and mobile software are planned as separate future capabilities.

> **Development status:** CORELINE is an R&D-stage project. Performance, comfort, durability, and biomechanical effects require validation through structured testing.

---

## Product Concept

Traditional spinal-support products span a wide range of designs, from lightweight posture-oriented wearables to rigid orthopedic braces intended for specific clinical applications.

CORELINE explores a different engineering approach:

**provide configurable mechanical support while preserving practical freedom of movement and everyday wearability.**

Rather than treating maximum rigidity as the primary design objective, the system is being developed around controlled support, progressive resistance, distributed compression, and modular adjustment.

The intended result is a wearable platform that can be tuned for different activities, body geometries, and future sensing configurations.

---

## Design Objectives

The CORELINE architecture is being developed around five primary objectives:

1. **Load Distribution**  
   Distribute mechanical forces across a larger area of the torso rather than concentrating pressure at isolated contact points.

2. **Controlled Mechanical Support**  
   Provide configurable support to the lumbar and thoracic regions while avoiding unnecessary rigid immobilization.

3. **Movement Compatibility**  
   Allow normal functional movement within the intended operating range of the wearable system.

4. **Long-Wear Comfort**  
   Reduce heat accumulation, moisture retention, bulk, and localized pressure through material and ventilation design.

5. **Platform Modularity**  
   Support future integration of sensing, electronics, and software without requiring a complete redesign of the mechanical product.

These are **engineering objectives**, not validated medical or clinical claims.

---

# System Architecture

CORELINE uses a layered architecture in which different components perform different mechanical or comfort functions.

## 1. External Load-Distribution Layer

The external structure is intended to:

- maintain the overall geometry of the wearable;
- distribute tensile forces;
- reduce localized loading;
- provide attachment points for adjustment mechanisms; and
- protect internal structural components.

Candidate materials include high-tenacity woven textiles and abrasion-resistant technical fabrics.

---

## 2. Biomechanical Support Framework

The internal support structure is intended to provide controlled resistance along selected regions of the torso.

Candidate technologies include:

- flexible polymer support stays;
- selectively reinforced composite elements;
- spring-like structural elements; and
- interchangeable support geometries.

The design principle is **progressive mechanical resistance rather than complete rigidity**.

Different geometries and stiffness profiles will require physical validation.

---

## 3. Adaptive Compression System

Adjustable compression is intended to help:

- stabilize the wearable on the body;
- control the interaction between structural elements and the torso;
- accommodate different body geometries; and
- allow the user to adjust support within the permitted operating range.

Candidate mechanisms include:

- elastic technical textiles;
- zonal stretch structures;
- mechanical tensioning straps;
- low-profile hook-and-loop systems; and
- future dial or micro-ratchet mechanisms.

Compression limits and adjustment procedures must be established through prototype testing.

---

## 4. Comfort & Ventilation Layer

The skin-contact system is being designed around:

- breathability;
- moisture management;
- reduced friction;
- pressure distribution;
- thermal comfort; and
- extended wearability.

Candidate materials include:

- 3D spacer mesh;
- technical microfiber;
- selected cellulose-based textile blends; and
- other breathable liner materials.

Ventilation concepts include airflow channels and strategically placed mesh zones.

---

## 5. Optional Future Sensor Layer

Active electronics are **not required for the fundamental mechanical operation of the initial CORELINE concept**.

Future versions may incorporate:

- inertial measurement units (IMUs);
- pressure sensors;
- temperature or environmental sensors;
- wear-time monitoring; and
- other experimental sensing technologies.

Sensor-derived metrics would require independent validation before being represented as clinically meaningful measurements.

See [`sensor-module.md`](sensor-module.md) for the planned sensor architecture.

---

# How the System Is Intended to Work

At a high level:

1. The user positions and secures the wearable around the torso.
2. Adjustable textile structures establish the required fit and baseline compression.
3. External layers distribute mechanical tension across the garment.
4. Internal support elements provide resistance in selected regions.
5. Flexible structures allow movement while changing resistance according to geometry and deformation.
6. Breathable inner materials manage skin contact, heat, and moisture.
7. Future sensor-enabled versions may record movement or pressure data for experimental analysis.

The mechanical system is intended to remain functional independently of the future electronics subsystem.

---

# Intended Use During R&D

The initial CORELINE platform is being developed for **research, prototyping, engineering evaluation, and non-medical wellness exploration**.

Potential evaluation scenarios include:

- prolonged seated work;
- standing activities;
- commuting;
- selected everyday activities;
- light to moderate physical activity; and
- controlled movement and wearability testing.

These scenarios describe intended development and testing contexts. They do not establish clinical effectiveness.

---

# Target Evaluation Groups

Future prototype evaluations may involve consenting adult participants representing use cases such as:

- office and remote workers;
- people interested in ergonomic wearables;
- physically active users;
- participants evaluating long-duration wearable comfort; and
- users participating in controlled posture or movement studies.

Any research involving human participants should follow appropriate consent, privacy, data-protection, and safety procedures.

See [`open-data-policy.md`](open-data-policy.md) for project data principles.

---

# What CORELINE Is Not

The current CORELINE project should not be represented as:

- a clinically validated treatment;
- a substitute for professional medical assessment;
- a device proven to correct spinal deformity;
- a proven method for preventing back pain;
- a rehabilitation protocol;
- a diagnostic system; or
- a certified medical device.

The project is currently an **experimental wearable engineering platform**.

---

# Performance Validation

The following characteristics require measurement rather than assumption:

| Area | Example Evaluation |
|---|---|
| Mechanical support | Force-displacement and stiffness testing |
| Pressure distribution | Multi-point pressure measurements |
| Mobility | Range-of-motion comparison |
| Fit stability | Displacement during standardized movement |
| Thermal comfort | Temperature and humidity measurements |
| Material durability | Repeated loading and abrasion testing |
| Compression | Circumferential force / pressure characterization |
| Wearability | Structured participant feedback |
| Sensor performance | Calibration and reference-system comparison |

Test methods and acceptance criteria should be documented before strong performance claims are made.

---

# Development Principles

## Evidence Before Claims

CORELINE documentation should distinguish clearly between:

- **design intent** — what the system is intended to do;
- **prototype observation** — what has been observed during development;
- **measured result** — what controlled testing has demonstrated; and
- **validated claim** — what sufficient evidence supports.

This distinction is especially important for statements concerning posture, pain, spinal loading, injury prevention, or medical benefit.

---

## Mechanical Function First

The initial product architecture prioritizes the passive wearable system.

This allows mechanical performance to be evaluated independently from:

- sensor accuracy;
- firmware;
- wireless connectivity;
- mobile applications; and
- analytics algorithms.

Electronics should extend the platform rather than compensate for inadequate mechanical design.

---

## Modular Development

Where practical, components should be replaceable or configurable independently.

Examples include:

- support elements;
- textile panels;
- tensioning mechanisms;
- sensor modules;
- electronics compartments; and
- software components.

This approach supports faster iteration and clearer experimental comparison between design revisions.

---

# Future Digital Platform

If the mechanical platform is successfully validated, future development may add a digital layer consisting of:

```text
Wearable Structure
        │
        ▼
Optional Sensors
        │
        ▼
Embedded Electronics
        │
        ▼
Firmware
        │
        ▼
Mobile Application
        │
        ▼
Data Visualization / Analysis
