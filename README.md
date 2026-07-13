# Humanitarian Connection Protocol (HCP)

> **Interoperability begins when independent systems describe reality using the same language.**

The **Humanitarian Connection Protocol (HCP)** is an open semantic interoperability standard for humanitarian observations.

HCP enables independent organizations, governments, hospitals, NGOs, volunteers and digital platforms to exchange humanitarian information using a common language, while preserving their own systems, infrastructure and governance.

It does not define how organizations build their software.

It defines how humanitarian observations can be understood everywhere.

---

# Why HCP?

Every humanitarian emergency generates thousands of independent observations.

Hospitals register patients.

Families report missing relatives.

Shelters receive displaced people.

Volunteers document urgent needs.

Emergency teams report rescues.

Governments maintain official records.

Most of these observations describe the same reality.

Yet very few of the systems collecting them can understand one another.

The problem is rarely the lack of information.

The problem is the lack of interoperability.

---

# Our Vision

Humanitarian interoperability should depend on shared meaning, not shared infrastructure.

Organizations should not be required to replace their existing software in order to collaborate.

Instead, they should be able to exchange structured humanitarian observations through an open protocol.

Just as HTTP standardized communication between web servers without requiring the same operating system, HCP seeks to standardize humanitarian observations without requiring the same database, application or infrastructure.

The protocol connects understanding—not databases.

---

# What is HCP?

HCP is an open specification that defines:

* how humanitarian observations are represented
* how they are exchanged
* how they are queried
* how they are correlated
* how implementations can explain correlation results
* how independent systems remain interoperable

HCP is:

* Open
* Infrastructure-agnostic
* Vendor-neutral
* Human-readable
* Machine-readable
* Explainable
* Extensible
* Open Source

---

# Shared Meaning, Not Shared Databases

HCP does not require organizations to share databases.

It does not prescribe storage technologies.

It does not prescribe programming languages.

It does not prescribe cloud providers.

Every organization remains free to use its own architecture.

The protocol only standardizes the meaning of humanitarian observations.

Different databases.

Different applications.

Different institutions.

One shared language.

---

# Humanitarian Records

The core object of HCP is the **Humanitarian Record**.

A Humanitarian Record represents an independent humanitarian observation.

Examples include:

* Missing Person
* Hospitalized Person
* Sheltered Person
* Located Person
* Public Emergency
* Missing Animal
* Found Animal

Humanitarian Records describe observations.

They are not digital identity records.

---

# Correlation Instead of Identification

Traditional systems often begin by identifying a person.

HCP follows a different approach.

Independent observations can be correlated before identity is confirmed.

Correlation estimates whether multiple observations may describe the same humanitarian case.

Implementations are encouraged to use factors such as:

* approximate location
* estimated time
* humanitarian status
* observable characteristics
* event context
* protocol-defined metadata

HCP does not require centralized identity.

It does not require government identifiers.

It does not require phone numbers.

It does not require passport numbers.

The protocol correlates humanitarian observations—not personal identities.

---

# Explainable Correlation

Correlation should never be a black box.

Implementations should be able to explain why two Humanitarian Records appear related.

Explainability helps humanitarian workers, institutions and families evaluate possible matches using transparent criteria.

Human judgment remains essential.

---

# Design Principles

## Shared Meaning over Shared Infrastructure

Humanitarian interoperability should depend on shared meaning, not shared infrastructure.

## Observations over Identities

Humanitarian information begins as observations, not centralized identities.

## Correlation over Identification

Independent observations can be correlated before identity is confirmed.

## Federation over Centralization

Organizations collaborate without surrendering ownership of their own systems.

## Explainability over Black Boxes

Every correlation should be understandable by humans.

---

# What HCP Does Not Do

HCP is not:

* a humanitarian platform
* a centralized database
* a donation platform
* a messaging application
* a blockchain
* a global identity registry
* a replacement for existing information systems

Those solutions can implement HCP.

HCP defines the common language they use to communicate.

---

# Repository Structure

```
hcp-specification/

├── README.md
├── specification/
├── schema/
├── examples/
└── archive/
```

---

# Specification Index

| HCP      | Title                               | Status |
| -------- | ----------------------------------- | ------ |
| HCP-0000 | Architecture and Overview           | Draft  |
| HCP-0001 | Humanitarian Record                 | Draft  |
| HCP-0002 | HCP Node                            | Draft  |
| HCP-0003 | Subject Model                       | Draft  |
| HCP-0004 | Correlation Candidate               | Draft  |
| HCP-0005 | Node Communication Protocol         | Draft  |
| HCP-0006 | Observation Model                   | Draft  |
| HCP-0007 | Status Model                        | Draft  |
| HCP-0008 | Event Type Model                    | Draft  |
| HCP-0009 | Node API                            | Draft  |
| HCP-0010 | Canonical JSON Specification        | Draft  |
| HCP-0011 | Query Model                         | Draft  |
| HCP-0012 | Correlation Model                   | Draft  |
| HCP-0013 | Synchronization Model               | Draft  |
| HCP-0014 | Explainable Correlation Model       | Draft  |
| HCP-0015 | Result Presentation Model           | Draft  |
| HCP-0016 | Humanitarian Record Lifecycle Model | Draft  |
| HCP-0017 | Event Classification Model          | Draft  |
| HCP-0018 | Search and Query Protocol           | Draft  |
| HCP-0019 | Federation and Node Discovery Model | Draft  |
| HCP-0020 | Security Model                      | Draft  |
| HCP-0021 | Privacy and Data Minimization       | Draft  |
| HCP-0022 | Interoperability Requirements       | Draft  |

---

# Design Goals

The protocol is designed to be:

* Human-readable
* Machine-readable
* Explainable
* Privacy-aware
* Infrastructure-agnostic
* Offline-friendly
* Extensible
* Easy to implement

---

# Ecosystem

The Humanitarian Connection Protocol is part of the Human Connection Network ecosystem.

| Repository                   | Purpose                           |
| ---------------------------- | --------------------------------- |
| **human-connection-network** | Project overview                  |
| **hcp-specification**        | Official protocol specification   |
| **hcp-reference**            | Reference HCP Node implementation |
| **hcp-client-telegram**      | First official HCP Client         |
| **hcp-node-web**             | Future web implementation         |

---

# Contributing

Contributions are welcome from:

* Software Engineers
* Humanitarian Organizations
* Emergency Response Teams
* NGOs
* Governments
* Universities
* Researchers
* Open Source Contributors

Please read the contribution guidelines before submitting proposals or pull requests.

---

# License

Released under the Apache License 2.0.

---

> **HCP is not designed to know who people are.**
>
> **It is designed to help independent systems understand the same humanitarian reality.**

