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

The Status Model defines the humanitarian condition observed and reported within an Observation.

A Status describes the condition of a Subject at the exact moment an Observation is made.

Status is never permanent.

It represents only the condition observed at a specific point in time.

Future observations may report different statuses.

---

# 2. Purpose

The purpose of the Status Model is to provide a common vocabulary that allows humanitarian organizations to describe situations consistently while preserving interoperability.

Status values are intended to be simple, unambiguous and internationally understandable.

---

# 3. Fundamental Principle

Status describes the observed condition.

It does not describe the person.

It does not replace previous statuses.

Each Observation reports exactly one Status.

---

# 4. Status Lifecycle

Status exists only within an Observation.

Example:

```text
Observation
    Person Located

Status
    Alive
```

A new Observation generates a new Status.

Historical statuses remain unchanged.

---

# 5. Recommended Status Values

The following statuses are recommended for HCP Core.

## Unknown

The current humanitarian condition cannot yet be determined.

---

## Missing

The person's whereabouts are unknown.

---

## Located

The person's location has been confirmed.

---

## Safe

The person is confirmed to be safe.

---

## Injured

The person has sustained injuries.

---

## Critical

The person's condition is critical.

---

## Hospitalized

The person has been admitted to a medical facility.

---

## Sheltered

The person is currently located in a shelter.

---

## Evacuated

The person has been successfully evacuated.

---

## Reunified

The person has been reunited with family or caregivers.

---

## Deceased

The person's death has been confirmed.

---

## Assistance Requested

The person requires humanitarian assistance.

---

## Assistance Delivered

Humanitarian assistance has been delivered.

---

# 6. Status Progression

Status values should not be interpreted as a predefined workflow.

Example:

```text
Missing

↓

Located

↓

Hospitalized

↓

Sheltered

↓

Reunified
```

This sequence represents one possible humanitarian history.

Other situations may follow different paths.

---

# 7. Status Independence

Status values are independent of Subject Type.

Different Subjects may share similar statuses.

Examples:

Person

Status:
Evacuated

Facility

Status:
Operational

Resource

Status:
Delivered

Community

Status:
Isolated

Each Subject Type may define its own recommended Status vocabulary.

---

# 8. Status Consistency

Nodes should preserve received Status values exactly as transmitted.

Nodes should not reinterpret or automatically translate Status values.

Presentation to end users is the responsibility of Clients.

---

# 9. Unknown Status

Implementations shall preserve unknown Status values whenever possible.

Unknown values should not invalidate a Humanitarian Record.

This allows future protocol versions to introduce additional standardized statuses while maintaining backward compatibility.

---

# 10. Last Known Status

Person Candidates should expose the Status reported by the most recent correlated Observation.

The Last Known Status represents the best available humanitarian information at the time of the query.

---

# 11. Humanitarian Timeline

As new Observations are created, Status values evolve.

Example:

```text
12 Aug

Status
Missing

↓

13 Aug

Status
Located

↓

15 Aug

Status
Hospitalized

↓

18 Aug

Status
Sheltered

↓

20 Aug

Status
Reunified
```

The timeline is reconstructed dynamically.

It is never stored as a permanent object.

---

# 12. Extensibility

Future HCP specifications may define additional Status values.

Nodes shall preserve unknown Status values whenever possible.

Implementations should avoid rejecting records solely because they contain newer Status definitions.

---

# 13. Compliance

A compliant implementation shall:

- assign exactly one Status to every Observation;
- preserve historical Status values;
- avoid modifying previous Observations;
- preserve unknown Status values whenever possible;
- expose the Last Known Status during correlation.

---

# 14. Summary

The Status Model defines the humanitarian condition reported by each Observation.

Status represents only the observed condition at a specific moment.

Historical Status values are never modified or replaced.

Through multiple Observations, Nodes reconstruct humanitarian histories and expose the most recent Status as the Last Known Status, providing meaningful and up-to-date information while preserving the complete historical record.
