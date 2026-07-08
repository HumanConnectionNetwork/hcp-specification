# HCP-0008
# Event Type Model

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0003 Subject Model
- HCP-0006 Observation Model
- HCP-0007 Status Model

---

# 1. Introduction

This document defines the Event Type Model used by the Humanitarian Connection Protocol (HCP).

An Event Type describes the humanitarian situation being observed.

It answers the question:

> **What humanitarian event is being reported?**

Event Types are independent of both the subject being reported and the current status of the observation.

---

# 2. Purpose

The Event Type Model provides a standardized vocabulary that allows independent HCP Nodes to describe humanitarian events consistently.

Using common Event Types improves:

- interoperability
- search
- correlation
- synchronization
- statistical analysis

Different implementations may present localized labels to users while preserving the same canonical values internally.

---

# 3. Design Principles

Every Event Type follows these principles.

## Standardized

Each humanitarian event has a canonical identifier.

---

## Subject-Aware

An Event Type must be compatible with the reported subject.

Not every Event Type applies to every Subject.

---

## Language Independent

Canonical values remain in English.

User interfaces may display localized translations.

---

## Extensible

Future specifications may introduce new Event Types without breaking compatibility.

---

# 4. Relationship with Subject

The meaning of an Event Type depends on the Subject Model.

For example:

```json
{
  "subject": "person",
  "event_type": "missing"
}
```

represents a missing person.

Whereas:

```json
{
  "subject": "animal",
  "event_type": "missing"
}
```

represents a missing animal.

The canonical Event Type remains the same while its interpretation depends on the subject.

---

# 5. Person Event Types

Recommended Event Types for persons include:

| Canonical Value | Description |
|-----------------|-------------|
| missing | Person whose location is unknown |
| hospitalized | Person receiving medical care |
| sheltered | Person staying in a temporary shelter |
| located | Person confirmed safe or located |

Implementations may present localized names such as:

Spanish:

- Persona desaparecida
- Persona hospitalizada
- Persona refugiada
- Persona localizada

Portuguese:

- Pessoa desaparecida
- Pessoa hospitalizada
- Pessoa abrigada
- Pessoa localizada

---

# 6. Animal Event Types

Recommended Event Types for animals include:

| Canonical Value | Description |
|-----------------|-------------|
| missing | Animal whose location is unknown |
| treated | Animal receiving veterinary care |
| sheltered | Animal under temporary protection |
| located | Animal confirmed safe or located |

Localized names may vary while preserving canonical values.

---

# 7. Future Subjects

Future HCP versions may introduce additional Subject Types.

Each new Subject Type may define its own compatible Event Types.

Examples include:

- infrastructure
- vehicle
- supply
- resource
- hazard

The protocol intentionally allows controlled expansion.

---

# 8. Event Type vs Status

Event Type and Status represent different concepts.

Example:

```json
{
  "subject": "person",
  "event_type": "hospitalized",
  "status": "reported"
}
```

This means:

The humanitarian event is hospitalization.

The observation itself has been reported.

Later:

```json
{
  "status": "confirmed"
}
```

The Event Type remains:

```
hospitalized
```

Only the confidence or lifecycle of the observation changes.

---

# 9. Correlation

Event Types are important correlation variables.

Implementations SHOULD prioritize candidates sharing the same Event Type.

However, correlation is not restricted to identical Event Types.

Example:

A query searching for:

```
missing
```

may reasonably correlate with:

```
hospitalized
```

or

```
located
```

when other correlation variables strongly suggest they describe the same humanitarian event.

Correlation behavior is defined in HCP-0012.

---

# 10. Interoperability

Every compliant HCP Node MUST exchange canonical Event Type values.

User interfaces may translate these values into local languages.

Internal implementations may organize them differently.

However, their semantic meaning MUST remain consistent across all HCP Nodes.

---

# 11. Relationship with Other Specifications

This document defines the humanitarian event taxonomy.

Related specifications include:

- HCP-0003 Subject Model
- HCP-0006 Observation Model
- HCP-0007 Status Model
- HCP-0010 Canonical JSON Specification
- HCP-0011 Query Model
- HCP-0012 Correlation Model

Together these documents define how humanitarian observations are described, exchanged and correlated throughout the HCP ecosystem.
