# HCP-0007

# Humanitarian Connection Protocol
## Status Model

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-04

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Fundamental Principles
- HCP-0002 — Humanitarian Record
- HCP-0003 — Subject Model
- HCP-0004 — Person Correlation Model
- HCP-0005 — Node Architecture
- HCP-0006 — Observation Model

---

# 1. Abstract

The Status Model defines how the condition of a Subject is represented within a Humanitarian Observation.

A Status describes the condition observed at a specific moment in time.

Status is always temporal.

It never represents a permanent truth.

Every Observation reports exactly one Status.

Future Observations may report a different Status for the same Subject.

---

# 2. Purpose

The purpose of the Status Model is to establish a common semantic structure for representing humanitarian conditions while preserving interoperability between all HCP implementations.

The HCP Core defines the Status Model.

Subject-specific Status vocabularies are defined in independent specifications.

---

# 3. Fundamental Principles

The Status Model follows these principles:

- A Status describes an observed condition.
- Every Observation contains exactly one Status.
- Statuses are immutable once published.
- New Observations generate new Statuses.
- Historical Statuses are never modified.
- Statuses belong to Observations, not to Subjects.

---

# 4. Relationship Between Observation and Status

Every Observation reports the condition of a Subject at the moment it was observed.

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

The Status has meaning only within the Observation that reports it.

---

# 5. Core Status Model

The HCP Core defines only the semantic model of Status.

It intentionally avoids defining exhaustive status lists for every Subject Type.

This allows the protocol to evolve without modifying its core architecture.

---

# 6. Core Status Vocabulary

The following Status values are recommended as a minimal common vocabulary across all HCP implementations.

- Unknown
- Pending
- Active
- Completed
- Cancelled

These values are intentionally generic.

Applications and future specifications may define more specialized vocabularies.

---

# 7. Subject-Specific Status Vocabularies

Different Subject Types require different humanitarian Status values.

Examples include:

Person

- Missing
- Located
- Hospitalized
- Sheltered
- Reunified
- Deceased

Facility

- Operational
- Damaged
- Closed
- Over Capacity

Resource

- Available
- Reserved
- Delivered
- Consumed

Community

- Accessible
- Isolated
- Evacuated
- Recovered

These vocabularies are outside the HCP Core and shall be defined by future specifications.

---

# 8. Status Evolution

Status evolves through new Observations.

Example:

```text
Observation 1

Status
Missing

↓

Observation 2

Status
Located

↓

Observation 3

Status
Hospitalized

↓

Observation 4

Status
Sheltered

↓

Observation 5

Status
Reunified
```

Each Observation creates a new historical Status.

Previous Statuses remain unchanged.

---

# 9. Last Known Status

The Last Known Status is determined during the Person Correlation process.

It corresponds to the Status reported by the most recent correlated Observation.

The Last Known Status is never stored as an independent object.

It is calculated dynamically.

---

# 10. Unknown Status Values

Nodes shall preserve unknown Status values whenever possible.

Unknown values shall not invalidate Humanitarian Records.

This guarantees forward compatibility as the protocol evolves.

---

# 11. Presentation

Status values are protocol semantics.

Their visual representation, translation and user interface are the responsibility of Clients.

Different Clients may present identical Status values differently while preserving their meaning.

---

# 12. Extensibility

Future HCP specifications may define:

- Person Status Vocabulary
- Facility Status Vocabulary
- Resource Status Vocabulary
- Community Status Vocabulary
- Organization Status Vocabulary

These extensions shall remain fully compatible with the Status Model defined by this specification.

---

# 13. Compliance

A compliant implementation shall:

- associate exactly one Status with every Observation;
- preserve historical Statuses;
- avoid modifying previous Observations;
- preserve unknown Status values whenever possible;
- expose the Last Known Status when presenting correlated humanitarian cases.

---

# 14. Summary

The Status Model defines the semantic framework used to represent humanitarian conditions within HCP.

Rather than defining exhaustive lists of humanitarian states, the HCP Core establishes a simple, extensible and interoperable model that allows future specifications to introduce specialized vocabularies for different Subject Types.

This approach keeps the protocol stable while allowing it to evolve to support increasingly diverse humanitarian scenarios.
