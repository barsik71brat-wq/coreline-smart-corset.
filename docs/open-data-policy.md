# Open Data & Documentation Policy

## Overview

CORELINE is being developed with an **open research and documentation approach**.

The project aims to make technical information, design decisions, experimental methods, and selected research outputs publicly accessible whenever doing so is compatible with:

- participant privacy;
- informed consent;
- intellectual-property obligations;
- third-party licensing restrictions;
- security considerations;
- applicable law; and
- responsible research practice.

Open publication does **not** mean that all project data can or should be released without restriction.

---

## Objectives

The CORELINE open-data and documentation policy is intended to:

- improve transparency and reproducibility;
- allow independent review of technical decisions;
- document both successful and unsuccessful experiments;
- support collaboration with researchers and developers;
- preserve traceability as the project evolves;
- encourage responsible reuse of non-sensitive project outputs; and
- distinguish clearly between measured results, engineering assumptions, and future concepts.

---

# Documentation

CORELINE intends to maintain public technical documentation covering major aspects of the project.

Documentation may include:

- product architecture;
- biomechanical design principles;
- materials and component selection;
- sensor architecture;
- electronics and firmware design;
- software architecture;
- prototype development history;
- test procedures;
- experimental results;
- known limitations; and
- development roadmap.

Documentation should be updated progressively as prototypes and test results become available.

Where an earlier assumption is shown to be incorrect, the preferred approach is to document the change rather than silently remove the historical engineering context.

---

# Research Data

## Data That May Be Published

Where appropriate, CORELINE may publish research datasets generated during development.

Examples may include:

- anonymized sensor measurements;
- IMU recordings;
- pressure-distribution measurements;
- mechanical test results;
- material test results;
- environmental measurements;
- calibration datasets;
- prototype performance measurements; and
- aggregated usability or wear-test results.

Published datasets should contain sufficient metadata to allow meaningful interpretation.

---

## Required Dataset Metadata

Where applicable, released datasets should document:

- dataset version;
- collection date or collection period;
- measurement purpose;
- hardware revision;
- sensor model;
- firmware version;
- sampling rate;
- measurement units;
- calibration procedure;
- test configuration;
- processing steps;
- known measurement limitations;
- missing-data conventions; and
- applicable license or usage terms.

Processed datasets should, where practical, identify the processing method or software version used to produce them.

---

# Raw vs. Processed Data

CORELINE should distinguish between:

### Raw data

Measurements obtained directly from sensors or test equipment with minimal transformation.

Examples:

- accelerometer samples;
- gyroscope samples;
- pressure-sensor readings;
- force measurements; and
- temperature measurements.

### Processed data

Measurements modified through filtering, calibration, synchronization, normalization, or other processing.

### Derived metrics

Values calculated from raw or processed measurements.

Examples may include:

- estimated orientation;
- wear duration;
- movement statistics;
- pressure-distribution metrics; and
- other experimental indicators.

Derived metrics should not be represented as direct measurements.

Where practical, published datasets should provide enough information to reproduce the derivation process.

---

# Human Participant Data

Data involving human participants requires additional safeguards.

CORELINE should not publicly release information that directly identifies individual participants.

Potential identifiers include:

- names;
- email addresses;
- phone numbers;
- account identifiers;
- precise home or work locations;
- photographs containing identifiable individuals;
- unrestricted timestamps when they create identification risk; and
- other information that could reasonably identify a participant.

Human-subject datasets should be reviewed before publication.

---

# Anonymization & De-identification

Removing a participant's name alone does not necessarily make a dataset anonymous.

Sensor and wearable datasets may contain behavioral patterns that can create re-identification risk.

Before public release, datasets should therefore be evaluated for:

- direct identifiers;
- indirect identifiers;
- precise timestamps;
- location information;
- rare behavioral patterns;
- small participant groups; and
- combinations of variables that may enable re-identification.

Depending on the dataset, appropriate measures may include:

- removal of identifiers;
- pseudonymization;
- timestamp reduction or shifting;
- aggregation;
- removal of unnecessary metadata;
- suppression of high-risk variables; or
- publication of summary statistics instead of participant-level records.

No anonymization method should be described as providing absolute protection against re-identification.

---

# Consent

Where data is collected from human participants, the intended use of the data should be communicated before collection.

Where applicable, participants should be informed about:

- what information will be collected;
- why it is being collected;
- how it will be stored;
- whether it may be processed or analyzed;
- whether anonymized or aggregated results may be published;
- whether data may be shared with third parties;
- applicable retention periods; and
- available withdrawal or deletion procedures.

Public release of participant-level research data should occur only when consistent with the applicable consent process and legal requirements.

---

# Data Minimization

CORELINE should collect only information reasonably necessary for a defined development, research, or product function.

For example, a posture or movement experiment should not collect unrelated personal information merely because the software is technically capable of doing so.

Data minimization reduces:

- privacy risk;
- security exposure;
- storage requirements;
- regulatory complexity; and
- unnecessary research noise.

---

# Data Quality

Public datasets should not imply a level of accuracy greater than the measurement system supports.

Where relevant, releases should document known issues such as:

- sensor drift;
- calibration uncertainty;
- sampling irregularities;
- sensor saturation;
- packet loss;
- placement variability;
- textile deformation;
- environmental sensitivity;
- missing samples; and
- prototype hardware limitations.

Experimental data should be clearly identified as experimental.

---

# Negative & Inconclusive Results

CORELINE supports publication of technically useful negative or inconclusive results.

Examples include:

- materials that did not meet durability requirements;
- sensor configurations with unacceptable drift;
- unsuccessful mechanical geometries;
- algorithms that failed validation;
- communication approaches with excessive power consumption; and
- prototype designs rejected after testing.

Publishing such information can reduce duplicated work and provide important context for later design decisions.

---

# Reproducibility

Where practical, experimental publications should include enough information for another researcher or engineer to understand or reproduce the test.

This may include:

- test objective;
- equipment;
- hardware configuration;
- software version;
- firmware version;
- calibration procedure;
- protocol;
- environmental conditions;
- processing methodology;
- results; and
- limitations.

Reproducibility does not require publication of sensitive, proprietary, licensed, or security-critical information.

---

# Software

Source code released by the CORELINE project may be distributed under the license specified in the repository's [`LICENSE`](../LICENSE) file or in the relevant software component.

A software license applies to software covered by that license.

It should **not automatically be assumed to define the licensing terms for datasets, photographs, research publications, hardware designs, or third-party materials**.

Individual components may therefore specify separate licensing terms where necessary.

---

# Hardware & Design Files

Future hardware design files may include:

- schematics;
- PCB layouts;
- mechanical drawings;
- CAD models;
- connector definitions;
- enclosure designs;
- manufacturing notes; and
- prototype assembly information.

Publication of these materials will depend on:

- development maturity;
- third-party intellectual-property restrictions;
- safety considerations;
- manufacturing readiness; and
- the license selected for the relevant hardware documentation.

The applicable license should be stated explicitly when hardware design files are released.

---

# Dataset Licensing

Datasets should include explicit usage terms rather than relying implicitly on the software license.

Depending on the nature and origin of a dataset, release options may include:

- an appropriate open-data license;
- a Creative Commons license where suitable;
- dataset-specific terms; or
- restricted access where open publication would create unacceptable privacy, legal, or ethical risk.

The exact license should be included with each released dataset.

---

# Third-Party Materials

CORELINE may use components, software libraries, datasets, publications, images, or other resources created by third parties.

Such materials remain subject to their respective licenses and terms.

Their presence in the repository does not imply that CORELINE can relicense them.

Where third-party content is included, attribution and licensing requirements should be preserved.

---

# Security-Sensitive Information

Transparency does not require publication of information that would create an unreasonable security risk.

Examples may include:

- private cryptographic keys;
- credentials;
- authentication secrets;
- signing infrastructure;
- exploitable vulnerabilities before responsible remediation;
- personal access tokens; and
- private participant information.

Security-sensitive information should never be committed to the public repository merely to satisfy an open-development objective.

---

# Data Repository Structure

As the project grows, public research outputs may use a structure similar to:

```text
research/
├── datasets/
│   ├── README.md
│   └── <dataset-name>/
│       ├── README.md
│       ├── metadata.json
│       └── data/
│
├── protocols/
│   └── <test-protocol>.md
│
├── reports/
│   └── <test-report>.md
│
└── analysis/
    └── <analysis-name>/
