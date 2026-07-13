# HCP-0001

# Humanitarian Record

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the **Humanitarian Record**, the fundamental semantic unit of the Humanitarian Connection Protocol (HCP).

A Humanitarian Record represents an independent humanitarian observation describing a living being involved in a humanitarian event.

It is designed to be portable, interoperable and implementation-independent, allowing compatible systems to exchange humanitarian observations without requiring centralized identity management.

This document establishes the conceptual model upon which Canonical HCP JSON representations, queries, correlation and synchronization are built.

---

# 1. Introduction

The Humanitarian Record is the fundamental semantic unit of the Humanitarian Connection Protocol.

It represents an independent humanitarian observation recorded by a person, institution or system during a humanitarian event.

A Humanitarian Record is intentionally simple.

It is designed to be exchanged, understood and correlated across independent HCP implementations.

A Humanitarian Record is **not**:

- a digital identity
- a personal profile
- a medical record
- a government registry
- a permanent history of an individual

Instead, it records what was observed at a specific moment in time using the common language defined by HCP.

Multiple Humanitarian Records may describe the same humanitarian reality from different perspectives.

Those observations remain independent until correlation suggests they may refer to the same humanitarian case.

---

# 2. Purpose

The purpose of a Humanitarian Record is to enable humanitarian interoperability.

Rather than requiring organizations to exchange databases or adopt common software, HCP enables them to exchange structured humanitarian observations through a shared semantic model.

A Humanitarian Record allows independent systems to describe the same humanitarian reality using a common language.

Because every implementation represents observations consistently, records created by different organizations can later be queried, exchanged and correlated while preserving organizational autonomy and technological independence.

The Humanitarian Record therefore becomes the fundamental building block of humanitarian interoperability.

---

# 3. Design Principles

Every Humanitarian Record should preserve the following principles.

## Observation-Based

A Humanitarian Record describes an observation rather than a verified fact.

It records what is known at the time of reporting.

Future observations may confirm, refine or contradict previous observations.

The protocol intentionally preserves independent observations rather than replacing them.

---

## Correlation-Oriented

Humanitarian Records are designed to maximize the quality of future correlation.

Correlation evaluates the consistency of multiple independent observations rather than relying on permanent identifiers.

Each observation contributes evidence that may increase or decrease the probability that two records describe the same humanitarian case.

No individual field should be interpreted as definitive proof of identity.

---

## Independent

Every Humanitarian Record exists independently.

Independent observations should never overwrite one another.

As humanitarian situations evolve, new observations may complement previous ones according to the lifecycle defined by HCP.

Preserving observation history improves transparency and explainability.

---

## Infrastructure Independent

Humanitarian Records are implementation-independent.

Any compatible HCP Node may create, store and exchange Humanitarian Records using its own programming languages, databases and infrastructure.

Interoperability is achieved through the shared protocol specification rather than through shared software.

---

## Minimal

Humanitarian Records should contain only the information necessary to improve humanitarian coordination and future correlation.

Implementations should avoid collecting unnecessary personal information whenever possible.

Data minimization improves both privacy and interoperability.
---

# 4. Humanitarian Observation

Every Humanitarian Record represents a single humanitarian observation.

An observation records that a person, institution or system witnessed, received or documented information about a humanitarian event at a particular point in time.

Examples include:

- A volunteer reports seeing a missing child.
- A hospital admits an unidentified patient.
- A shelter reports a family arriving safely.
- A firefighter reports rescuing an injured person.
- A citizen reports finding a lost dog.

Each observation generates its own Humanitarian Record.

Independent organizations may observe the same humanitarian event without communicating with one another.

Rather than attempting to eliminate these independent observations, HCP preserves them and allows compatible implementations to correlate them later.

This approach improves transparency, explainability and resilience during humanitarian emergencies.

---

# 5. Correlation Evidence

The primary purpose of a Humanitarian Record is to provide evidence that may contribute to future humanitarian correlation.

Instead of relying on a single identifier, HCP evaluates the consistency of multiple independent observations.

Typical correlation evidence may include:

- reported name
- estimated age
- reported location
- observation time
- humanitarian status
- event type
- reporting source
- recognition features
- protocol-defined metadata

No individual attribute should be interpreted as definitive proof of identity.

Correlation emerges from the combined consistency of multiple pieces of evidence.

Different HCP implementations may apply different correlation strategies or weighting algorithms while remaining fully interoperable.

---

# 6. Recognition Features

One of the most valuable forms of correlation evidence is the set of observable characteristics recorded in the field:

```text
recognition_features
```

Recognition Features describe characteristics that may assist future humanitarian correlation.

They describe observable evidence rather than inferred attributes.

Examples for persons include:

- clothing
- colors
- tattoos
- scars
- glasses
- backpacks
- hairstyle
- beard
- mobility aids
- visible injuries

Examples for animals include:

- collar
- harness
- coat color
- visible markings
- scars
- injuries
- tail characteristics
- ear shape
- distinctive physical features

Recognition Features should remain concise and objective.

Implementations should avoid subjective opinions or speculative descriptions whenever possible.

---

# 7. Humanitarian Record Lifecycle

A Humanitarian Record evolves as additional humanitarian observations become available.

Rather than modifying the historical meaning of previous observations, new information should complement the existing humanitarian record according to the lifecycle defined by the protocol.

A typical lifecycle may include:

```text
Reported

        │

        ▼

Correlated

        │

        ▼

Validated

        │

        ▼

Updated

        │

        ▼

Closed
```

The detailed lifecycle model is defined in **HCP-0016 — Humanitarian Record Lifecycle Model**.

Maintaining independent observations throughout this lifecycle improves explainability, transparency and long-term interoperability.
---

# 8. Identity

Humanitarian Records intentionally separate humanitarian observations from permanent identity.

Identity may eventually be confirmed through human verification performed by families, hospitals, emergency responders or other responsible institutions.

The protocol itself does not attempt to establish identity as a technical certainty.

Instead, it provides a structured representation of humanitarian observations that may later contribute to that verification process.

Reported names, estimated ages and similar attributes are treated as reported information rather than unique identifiers.

This approach allows HCP to remain effective even when official identification is unavailable, incomplete or uncertain.

By separating observations from identity, the protocol improves interoperability while minimizing unnecessary dependence on centralized identity systems.

---

# 9. Interoperability

Every compliant HCP implementation exchanges Humanitarian Records using the Canonical HCP JSON Representation defined in **HCP-0010**.

Implementations remain free to use:

- any programming language
- any database technology
- any deployment architecture
- any communication infrastructure

The protocol standardizes the semantic meaning of Humanitarian Records rather than their internal implementation.

Shared meaning replaces shared infrastructure.

This allows independent HCP Nodes to exchange and interpret humanitarian observations while preserving technological independence.

---

# 10. Security and Privacy

Humanitarian Records should contain only the information necessary to support humanitarian coordination and explainable correlation.

Implementations should minimize the collection and exchange of personally identifiable information whenever possible.

Whenever equivalent humanitarian value can be achieved through observable characteristics, implementations should prefer observation-based evidence over permanent identifiers.

Privacy protection should never unnecessarily reduce humanitarian interoperability.

Likewise, interoperability should never require excessive exposure of personal information.

The protocol seeks to balance humanitarian usefulness, privacy protection and long-term interoperability.

Additional security and privacy requirements are defined in:

- **HCP-0020 — Security Model**
- **HCP-0021 — Privacy and Data Minimization**

---

# 11. Relationship with Other Specifications

This document defines the conceptual model of the Humanitarian Record.

Additional HCP specifications define complementary aspects of that model.

- **HCP-0006** defines the Observation Model.
- **HCP-0007** defines the Status Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0009** defines Node APIs for exchanging Humanitarian Records.
- **HCP-0010** defines the Canonical HCP JSON Representation.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0014** defines Explainable Correlation.
- **HCP-0016** defines the Humanitarian Record Lifecycle.

Together, these specifications establish a common semantic model that allows independent systems to create, exchange, query, correlate and understand Humanitarian Records while preserving organizational autonomy and technological independence.

---

# 12. Summary

The Humanitarian Record is the fundamental semantic unit of the Humanitarian Connection Protocol.

It represents an independent humanitarian observation rather than a permanent identity.

Its purpose is to enable humanitarian interoperability by providing a common language through which independent systems can describe the same humanitarian reality.

Humanitarian Records preserve observations.

Correlation relates observations.

Human verification confirms identities.

Together, these principles allow HCP to improve humanitarian collaboration without requiring centralized databases or centralized identity management.

The Humanitarian Record is not simply a data structure.

It is the shared semantic foundation upon which the entire Humanitarian Connection Protocol is built.
