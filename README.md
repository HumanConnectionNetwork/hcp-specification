# Humanitarian Connection Protocol Specification

> **Humanitarian interoperability should depend on shared meaning, not shared infrastructure.**

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
![Status](https://img.shields.io/badge/status-Draft-orange)
![Version](https://img.shields.io/badge/HCP-v0.1-lightgrey)

The **Humanitarian Connection Protocol (HCP)** is an open semantic interoperability standard for representing, exchanging, querying and correlating humanitarian observations.

This repository contains the official technical specifications of HCP.

It defines the protocol.

It does not contain a production application, a centralized database or a mandatory server implementation.

---

## Why HCP Exists

Humanitarian emergencies generate large volumes of information.

Hospitals register patients.

Families report missing relatives.

Shelters receive displaced people.

Rescue teams document incidents.

Volunteers report urgent needs.

Organizations create their own applications and databases.

Although these systems may describe the same humanitarian reality, they often represent information differently and cannot understand one another.

The problem is not always the absence of data.

The problem is the absence of a shared language.

HCP addresses that problem by defining common semantics for humanitarian observations.

---

## Core Idea

HCP does not require organizations to share a database.

It does not require them to use the same software.

It does not prescribe a programming language, cloud provider or storage technology.

Each implementation may preserve its own:

* infrastructure
* database
* internal processes
* security policies
* governance
* operational autonomy

HCP only defines how humanitarian observations are structured and interpreted when independent systems choose to exchange them.

Different systems.

Different infrastructures.

One shared humanitarian language.

---

## What HCP Standardizes

HCP defines:

* Humanitarian Records
* subjects and event types
* humanitarian observations
* record status and lifecycle
* Canonical JSON representation
* query structures
* correlation rules
* explainable correlation results
* node communication
* synchronization
* federation
* privacy requirements
* security requirements
* interoperability requirements

---

## What HCP Does Not Standardize

HCP does not prescribe:

* how organizations store their internal data
* which database technology must be used
* which programming language must be used
* which user interface must be provided
* which cloud or hosting provider must be used
* how an institution organizes its internal operations
* how governments or organizations govern their systems

HCP is a protocol specification, not an application architecture mandate.

---

## Humanitarian Records

The fundamental object of HCP is the **Humanitarian Record**.

A Humanitarian Record represents an independent observation associated with a humanitarian event.

Examples include:

* a missing person observation
* a hospitalized person observation
* a sheltered person observation
* a located person observation
* a public emergency observation
* a missing animal observation
* a found animal observation

A Humanitarian Record is not intended to become a permanent global identity profile.

It describes an event or observation.

It does not claim to define who a person is.

---

## Observations, Not Identities

HCP separates humanitarian observations from centralized identity.

The protocol does not require:

* national identification numbers
* passport numbers
* centralized identity accounts
* phone numbers as identity keys
* universal personal identifiers
* a global registry of people

A record may contain reported descriptive information when relevant to a humanitarian observation, but HCP does not treat names or contact information as proof of identity.

The protocol is designed to work even when identity is incomplete, uncertain, misspelled or unknown.

---

## Correlation Instead of Automatic Identification

HCP does not automatically declare that two records belong to the same person or animal.

It creates **Correlation Candidates**.

A Correlation Candidate represents the possibility that two or more independent observations describe the same humanitarian case.

Correlation may consider protocol-defined factors such as:

* approximate time
* geographical proximity
* event context
* estimated age range
* observable characteristics
* humanitarian status
* reporting context
* animal species, size or breed
* supporting confirmations

Reported names may assist discovery, but they must not be treated as definitive identity evidence.

Sex, contact information and government identifiers are not intended to determine correlation confidence.

Correlation produces a probability or confidence assessment.

Human confirmation remains necessary.

---

## Explainable Correlation

HCP requires correlation to be understandable.

An implementation should not return only a percentage or opaque score.

It should explain which observations increased or decreased the probability of a relationship.

For example:

* locations were geographically close
* observation times were compatible
* estimated ages were similar
* visible characteristics were consistent
* event contexts matched
* some reported details were contradictory

Explainability allows families, humanitarian workers and institutions to evaluate possible relationships using transparent evidence.

---

## Design Principles

### Shared Meaning over Shared Infrastructure

Humanitarian interoperability should depend on shared meaning, not shared infrastructure.

### Observations over Identities

Humanitarian information begins as observations, not permanent identity profiles.

### Correlation over Automatic Identification

The protocol estimates relationships between observations without claiming identity as a technical certainty.

### Explainability over Black Boxes

Correlation results should explain why records may be related.

### Interoperability over Platform Dependency

No organization should need to adopt a specific application to participate.

### Data Minimization over Unnecessary Collection

Implementations should collect only the information necessary for the humanitarian purpose.

### Autonomy over Infrastructure Mandates

Every organization remains responsible for its own systems, governance and security.

---

## Protocol Architecture

A typical HCP interaction may follow this sequence:

```text
Human Observation
        │
        ▼
HCP Client
        │
        ▼
Canonical Humanitarian Record
        │
        ▼
HCP Node
        │
        ├── Create
        ├── Validate
        ├── Query
        ├── Correlate
        └── Exchange
        │
        ▼
Independent HCP Implementations
```

The specification defines the language and expected behavior.

Each implementation decides how that behavior is built internally.

---

## Repository Scope

This repository contains only the normative and supporting documentation of HCP.

Reference software implementations are maintained separately.

```text
hcp-specification/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
│
├── specification/
│   ├── README.md
│   ├── TEMPLATE.md
│   ├── HCP-0000-architecture-and-overview.md
│   ├── HCP-0001-humanitarian-record.md
│   ├── HCP-0002-hcp-node.md
│   └── ...
│
├── schema/
│   └── Humanitarian Record schemas
│
├── examples/
│   └── Canonical HCP Record examples
│
└── archive/
    └── Deprecated or historical documents
```

---

## Specification Index

### Core Architecture

| Document | Title                     | Status |
| -------- | ------------------------- | ------ |
| HCP-0000 | Architecture and Overview | Draft  |
| HCP-0001 | Humanitarian Record       | Draft  |
| HCP-0002 | HCP Node                  | Draft  |
| HCP-0003 | Subject Model             | Draft  |
| HCP-0004 | Correlation Candidate     | Draft  |

### Communication and Data Model

| Document | Title                        | Status |
| -------- | ---------------------------- | ------ |
| HCP-0005 | Node Communication Protocol  | Draft  |
| HCP-0006 | Observation Model            | Draft  |
| HCP-0007 | Status Model                 | Draft  |
| HCP-0008 | Event Type Model             | Draft  |
| HCP-0009 | Node API                     | Draft  |
| HCP-0010 | Canonical JSON Specification | Draft  |

### Search and Correlation

| Document | Title                         | Status |
| -------- | ----------------------------- | ------ |
| HCP-0011 | Query Model                   | Draft  |
| HCP-0012 | Correlation Model             | Draft  |
| HCP-0014 | Explainable Correlation Model | Draft  |
| HCP-0015 | Result Presentation Model     | Draft  |
| HCP-0018 | Search and Query Protocol     | Draft  |

### Lifecycle, Synchronization and Federation

| Document | Title                               | Status |
| -------- | ----------------------------------- | ------ |
| HCP-0013 | Synchronization Model               | Draft  |
| HCP-0016 | Humanitarian Record Lifecycle Model | Draft  |
| HCP-0017 | Event Classification Model          | Draft  |
| HCP-0019 | Federation and Node Discovery Model | Draft  |

### Security and Interoperability

| Document | Title                         | Status |
| -------- | ----------------------------- | ------ |
| HCP-0020 | Security Model                | Draft  |
| HCP-0021 | Privacy and Data Minimization | Draft  |
| HCP-0022 | Interoperability Requirements | Draft  |

---

## Document Status

HCP documents may use the following status values:

| Status       | Meaning                                                       |
| ------------ | ------------------------------------------------------------- |
| Draft        | Under active design and subject to change                     |
| Review       | Ready for community and technical review                      |
| Experimental | Available for implementation testing                          |
| Stable       | Considered sufficiently mature for compatible implementations |
| Deprecated   | Retained for historical reference but no longer recommended   |

Unless explicitly stated otherwise, current HCP documents are drafts.

---

## Normative Language

HCP documents may use the terms:

* **MUST**
* **MUST NOT**
* **SHOULD**
* **SHOULD NOT**
* **MAY**

These terms indicate requirement levels for compatible implementations.

A future conformance document will define the exact requirements an implementation must satisfy to claim HCP compatibility.

---

## Implementations

The specification is implementation-independent.

Current ecosystem repositories include:

| Repository                 | Purpose                                         |
| -------------------------- | ----------------------------------------------- |
| `human-connection-network` | Institutional overview of the HCN ecosystem     |
| `hcp-specification`        | Official HCP specifications                     |
| `hcp-reference`            | Minimal reference implementation of an HCP Node |
| `hcp-client-telegram`      | First operational HCP Client                    |
| `hcp-node-web`             | Planned web-oriented HCP implementation         |

An implementation does not need to use the same source code as the reference implementation.

It only needs to follow the protocol requirements.

---

## Current Status

HCP is currently under active development.

Current protocol version:

```text
HCP v0.1 — Draft
```

The current work focuses on:

* stabilizing the Humanitarian Record model
* defining Canonical JSON
* formalizing query semantics
* formalizing explainable correlation
* defining node communication
* preparing conformance requirements
* validating the protocol through real implementations

The Telegram Client serves as the first operational demonstration of the protocol concepts.

The reference implementation provides a minimal technical example of an HCP Node.

---

## Contributing

Contributions are welcome from:

* software engineers
* protocol designers
* humanitarian organizations
* emergency response teams
* hospitals
* NGOs
* governments
* universities
* privacy and security specialists
* open-source contributors

Contributions may include:

* specification corrections
* implementation feedback
* interoperability proposals
* JSON Schema improvements
* security reviews
* privacy reviews
* examples
* translations
* conformance tests

Please read `CONTRIBUTING.md` and `CODE_OF_CONDUCT.md` before submitting an Issue or Pull Request.

---

## Governance

HCP is developed openly through GitHub.

Protocol changes should be proposed, discussed and reviewed publicly.

No implementation automatically becomes part of the protocol merely because it introduces a new feature.

Normative behavior must be documented and accepted in the specification.

---

## License

The Humanitarian Connection Protocol specification is released under the Apache License 2.0.

---

> **HCP does not require humanitarian systems to share the same infrastructure.**
>
> **It allows them to understand the same humanitarian reality.**
