# HCP Specification Index

This directory contains the **normative specification documents** of the Humanitarian Connection Protocol (HCP).

Each document defines one aspect of the protocol and should be interpreted together with the remaining specifications.

Unless explicitly stated otherwise, all published HCP documents are currently considered **Draft**.

---

# Purpose

The Humanitarian Connection Protocol is divided into multiple independent specifications rather than a single monolithic document.

This organization allows different areas of the protocol to evolve independently while preserving interoperability between compatible implementations.

Each document focuses on a specific responsibility, such as:

* Humanitarian Records
* Node behavior
* Canonical JSON
* Query semantics
* Correlation
* Synchronization
* Federation
* Security
* Privacy
* Interoperability

---

# Recommended Reading Order

Developers implementing HCP for the first time should read the specifications in the following order:

1. **HCP-0000** — Architecture and Overview
2. **HCP-0001** — Humanitarian Record
3. **HCP-0002** — HCP Node
4. **HCP-0010** — Canonical JSON Specification
5. **HCP-0011** — Query Model
6. **HCP-0012** — Correlation Model
7. **HCP-0014** — Explainable Correlation Model
8. **HCP-0009** — Node API

The remaining documents extend specific areas of the protocol and may be consulted as required by each implementation.

---

# Specification Organization

The specification is organized into five major areas.

## Core Architecture

Defines the conceptual foundations of HCP.

| Document | Title                     | Status |
| -------- | ------------------------- | ------ |
| HCP-0000 | Architecture and Overview | Draft  |
| HCP-0001 | Humanitarian Record       | Draft  |
| HCP-0002 | HCP Node                  | Draft  |
| HCP-0003 | Subject Model             | Draft  |
| HCP-0004 | Correlation Candidate     | Draft  |

---

## Communication and Record Model

Defines how Humanitarian Records are represented and exchanged.

| Document | Title                        | Status |
| -------- | ---------------------------- | ------ |
| HCP-0005 | Node Communication Protocol  | Draft  |
| HCP-0006 | Observation Model            | Draft  |
| HCP-0007 | Status Model                 | Draft  |
| HCP-0008 | Event Type Model             | Draft  |
| HCP-0009 | Node API                     | Draft  |
| HCP-0010 | Canonical JSON Specification | Draft  |

---

## Search and Correlation

Defines how Humanitarian Records are queried, correlated and presented.

| Document | Title                         | Status |
| -------- | ----------------------------- | ------ |
| HCP-0011 | Query Model                   | Draft  |
| HCP-0012 | Correlation Model             | Draft  |
| HCP-0014 | Explainable Correlation Model | Draft  |
| HCP-0015 | Result Presentation Model     | Draft  |
| HCP-0018 | Search and Query Protocol     | Draft  |

---

## Lifecycle, Synchronization and Federation

Defines how records evolve and how HCP Nodes exchange information.

| Document | Title                               | Status |
| -------- | ----------------------------------- | ------ |
| HCP-0013 | Synchronization Model               | Draft  |
| HCP-0016 | Humanitarian Record Lifecycle Model | Draft  |
| HCP-0017 | Event Classification Model          | Draft  |
| HCP-0019 | Federation and Node Discovery Model | Draft  |

---

## Security, Privacy and Interoperability

Defines operational requirements for compatible implementations.

| Document | Title                         | Status |
| -------- | ----------------------------- | ------ |
| HCP-0020 | Security Model                | Draft  |
| HCP-0021 | Privacy and Data Minimization | Draft  |
| HCP-0022 | Interoperability Requirements | Draft  |

---

# Document Status

The following status values may be used throughout the HCP specification.

| Status           | Description                                                                          |
| ---------------- | ------------------------------------------------------------------------------------ |
| **Draft**        | Under active development and subject to change.                                      |
| **Review**       | Considered technically complete and open for community review.                       |
| **Experimental** | Available for implementation and interoperability testing.                           |
| **Stable**       | Recommended for production-compatible implementations.                               |
| **Deprecated**   | Retained for historical reference but no longer recommended for new implementations. |

Unless explicitly stated otherwise, all current HCP specifications should be considered **Draft**.

---

# Normative Language

HCP documents may use the following requirement keywords:

* **MUST**
* **MUST NOT**
* **SHOULD**
* **SHOULD NOT**
* **MAY**

These terms indicate requirement levels for interoperable implementations and should be interpreted according to the normative language defined by the specification.

Future conformance documents will define the minimum requirements necessary for an implementation to claim compatibility with HCP.

---

# Scope

The specification defines:

* protocol concepts
* Humanitarian Records
* Canonical JSON
* Node behavior
* query semantics
* correlation semantics
* explainable correlation
* synchronization
* federation
* privacy requirements
* security requirements
* interoperability requirements

The specification does **not** prescribe:

* programming languages
* frameworks
* database technologies
* deployment architectures
* cloud providers
* user interfaces

Implementers remain free to choose the technologies most appropriate for their own environment.

---

# Relationship with Implementations

The specification is implementation-independent.

Reference Nodes, clients, SDKs and applications are maintained in separate repositories.

A software implementation may claim HCP compatibility only by following the normative requirements defined in these specification documents.

---

# Contributing

Changes to HCP should be proposed through GitHub Issues or Pull Requests.

New protocol behavior should first be discussed, reviewed and documented within the specification before becoming part of compatible implementations.

The protocol evolves through open technical discussion and community consensus.
