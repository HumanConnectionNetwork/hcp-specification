# HCP-0007

# Status Model

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Humanitarian Record
- HCP-0002 — HCP Node
- HCP-0003 — Subject Model
- HCP-0004 — Correlation Model
- HCP-0005 — Node Communication Protocol
- HCP-0006 — Observation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Status Model of the Humanitarian Connection Protocol (HCP).

A Status represents the observed humanitarian condition of a Subject at a specific moment in time.

Status describes observed humanitarian condition.

It does not represent permanent reality.

Every Observation contains exactly one Status, contributing humanitarian evidence that may later participate in explainable correlation and Humanitarian Timeline reconstruction.

This document establishes the semantic role of Status within the protocol while intentionally separating the Status Model from subject-specific vocabularies.

---

# 1. Introduction

Every Humanitarian Observation reports the humanitarian condition of one observed Subject.

That condition is represented by a Status.

A Status describes only what was observed at the moment the Observation was made.

It should never be interpreted as a permanent attribute of the Subject.

As humanitarian situations evolve, new Observations report new Status values.

Previous Status values remain preserved as part of their original Observations.

This approach preserves historical integrity while allowing Humanitarian Timelines to emerge dynamically through correlation.

---

# 2. Purpose

The purpose of the Status Model is to standardize how observed humanitarian conditions are represented.

Rather than defining permanent states, HCP represents humanitarian evidence through immutable Observations.

Status contributes semantic meaning to an Observation.

It does not define identity, ownership or long-term humanitarian history.

By standardizing the semantic role of Status, HCP enables independent implementations to exchange compatible humanitarian evidence while preserving organizational autonomy and long-term interoperability.

---

# 3. Fundamental Principles

The Status Model follows these principles.

## Observation-Based

A Status always describes an observed humanitarian condition.

It never represents permanent reality.

---

## Observation Ownership

Every Observation contains exactly one Status.

A Status belongs to an Observation.

It never belongs directly to a Subject.

---

## Humanitarian Evidence

Status contributes humanitarian evidence.

It does not establish identity.

---

## Immutable

Once an Observation has been created, its Status should never be modified.

Changes in humanitarian condition are represented by new Observations containing new Status values.

---

## Historical Preservation

Historical Status values remain preserved exactly as originally observed.

Humanitarian Timelines emerge through correlation rather than by modifying previous Status values.

---

## Infrastructure Independent

The semantic meaning of Status remains independent of databases, programming languages, communication technologies and software architectures.

Every compatible HCP implementation interprets Status according to the same semantic model.

---

# 4. Relationship Between Observation and Status

Every Observation reports the humanitarian condition observed for one Subject at a specific moment in time.

Conceptually:

```text
Humanitarian Record
        │
        ▼
     Subject
        │
        ▼
   Observation
        │
        ▼
      Status
```

Status has meaning only within the Observation that reports it.

Different Observations concerning the same Subject may legitimately report different Status values.

Those differences represent humanitarian evolution rather than inconsistency.

Status is evidence, not history.
---

# 5. Semantic Status Model

The HCP Core defines the semantic role of Status.

It intentionally does not define exhaustive Status vocabularies.

Status vocabularies may evolve independently while preserving the semantic model established by this specification.

This separation allows HCP to remain stable while supporting increasingly diverse humanitarian scenarios.

The protocol standardizes semantics.

Future specifications define vocabularies.

---

# 6. Subject-Specific Status Vocabularies

Different Subject Types require different humanitarian Status vocabularies.

The following examples illustrate typical Status values.

They are informative rather than exhaustive.

---

## Human

Typical human Status values include:

- Missing
- Located
- Hospitalized
- Sheltered
- Receiving Assistance
- Stable
- Critical
- Safe
- Reunified
- Deceased

These values describe humanitarian conditions observed for individual human beings.

---

## Animal

Typical animal Status values include:

- Missing
- Found
- Sheltered
- Receiving Care
- Stable
- Critical
- Safe
- Reunited

These values describe humanitarian conditions observed for individual animals.

Future specifications may extend these vocabularies while remaining fully compatible with the Status Model.

---

# 7. Status Evolution

Status evolves through successive independent Observations.

Each Observation contributes a new Status describing the humanitarian condition observed at that moment.

Example:

```text
Observation 1

Status

Missing

        │

        ▼

Observation 2

Status

Located

        │

        ▼

Observation 3

Status

Hospitalized

        │

        ▼

Observation 4

Status

Sheltered

        │

        ▼

Observation 5

Status

Reunified
```

Each Observation preserves its own Status permanently.

Humanitarian evolution emerges from multiple Observations.

Previous Status values are never modified.

---

# 8. Last Known Status

The Last Known Status is reconstructed dynamically through the Correlation Model.

It represents the most recent compatible Status available for a correlated humanitarian case.

The Last Known Status is never stored as an independent protocol object.

Different HCP implementations may reconstruct different Last Known Status values depending on:

- available Humanitarian Records;
- locally implemented correlation strategies;
- synchronization state;
- observation availability.

This flexibility preserves implementation independence while maintaining semantic interoperability.

---

# 9. Unknown Status Values

HCP implementations should preserve unknown Status values whenever reasonably possible.

Unknown values should not invalidate Humanitarian Records.

Instead, they should remain available for future interpretation by newer protocol versions or extended subject-specific vocabularies.

This approach improves:

- forward compatibility;
- interoperability;
- protocol evolution;
- long-term preservation of humanitarian information.

Implementations should avoid discarding humanitarian evidence simply because a Status value is not yet recognized.
---

# 10. Presentation

Status values are protocol semantics.

Their visual representation, translation and user experience belong entirely to HCP Clients.

Different Clients may present the same Status using:

- different languages;
- different icons;
- different colors;
- different terminology;
- different accessibility adaptations.

These presentation differences do not affect protocol interoperability.

The protocol standardizes semantic meaning.

Clients standardize user experience.

---

# 11. Extensibility

The Status Model is intentionally extensible.

Future HCP specifications may define additional subject-specific Status vocabularies without modifying the semantic model defined by this specification.

Examples include:

- Human Status Vocabulary
- Animal Status Vocabulary
- Wildlife Status Vocabulary
- Marine Animal Status Vocabulary
- Future humanitarian subject vocabularies

All future vocabularies should remain semantically compatible with the Status Model defined by HCP Core.

The protocol standardizes semantics.

Future specifications define vocabularies.

---

# 12. Compliance

A compliant implementation should:

- associate exactly one Status with every Observation;
- preserve Status immutability;
- preserve Observation independence;
- preserve historical Status values;
- preserve unknown Status values whenever reasonably possible;
- reconstruct Last Known Status dynamically through correlation;
- interpret Status according to HCP semantic definitions.

Compliance concerns semantic protocol behavior.

It does not prescribe internal software architecture or implementation techniques.

---

# 13. Relationship with Other Specifications

This document defines the semantic role of Status within the Humanitarian Connection Protocol.

Complementary specifications define related aspects of humanitarian information.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0003** defines the Subject Model.
- **HCP-0004** defines the Correlation Model.
- **HCP-0006** defines the Observation Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0010** defines the Canonical HCP JSON Representation.
- **HCP-0012** defines the Correlation Model.
- **HCP-0016** defines the Humanitarian Record Lifecycle.

Together, these specifications define how humanitarian conditions are represented, preserved and interpreted while maintaining semantic interoperability across independent HCP implementations.

---

# 14. Summary

The Status Model defines the semantic representation of observed humanitarian conditions within HCP.

A Status belongs to an Observation.

It does not belong directly to a Subject.

Status contributes humanitarian evidence.

Observations preserve Status.

Correlation reconstructs Humanitarian Timelines.

People verify identities.

By separating semantic meaning from subject-specific vocabularies, HCP allows the protocol to remain stable while enabling future humanitarian extensions without sacrificing interoperability.

The Status Model demonstrates one of the fundamental principles of the Humanitarian Connection Protocol:

**The protocol standardizes semantics.**

**Implementations define behavior.**

**Clients define presentation.**
