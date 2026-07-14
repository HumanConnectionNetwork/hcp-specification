# HCP-0008

# Event Type Model

Version: 0.4 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Humanitarian Record
- HCP-0003 — Subject Model
- HCP-0006 — Observation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Event Type Model of the Humanitarian Connection Protocol (HCP).

An Event Type defines the humanitarian meaning of a Humanitarian Observation.

It answers one fundamental question:

> **What happened?**

Event Types are one of the core semantic concepts of HCP.

They provide the common humanitarian vocabulary that allows independent implementations to exchange Humanitarian Records while preserving semantic interoperability.

The protocol standardizes the humanitarian meaning associated with every Event Type.

Implementations remain free to define workflows, operational procedures and user experiences.

---

# 1. Introduction

Every Humanitarian Observation describes a humanitarian event.

That event is represented by an Event Type.

An Event Type defines the humanitarian meaning of the Observation.

Rather than describing identities, histories or operational procedures, Event Types provide a shared semantic vocabulary that allows independent organizations to interpret humanitarian observations consistently.

Humanitarian Records preserve observations.

Event Types define their humanitarian meaning.

Because every compatible implementation interprets Event Types consistently, Humanitarian Records remain semantically interoperable regardless of software architecture, programming language or communication technology.

---

# 2. Purpose

The purpose of the Event Type Model is to define the humanitarian semantics of Humanitarian Observations.

Rather than standardizing workflows or implementation behavior, HCP standardizes the meaning of humanitarian events.

This shared semantic model allows independent organizations to exchange Humanitarian Records while preserving:

- semantic interoperability;
- organizational autonomy;
- implementation independence;
- explainable correlation;
- long-term protocol stability.

The Event Type Model answers one simple question:

> **What happened?**

---

# 3. Design Principles

Every Event Type should preserve the following architectural principles.

## Semantic

Event Types define humanitarian meaning.

They do not define implementation behavior.

---

## Observation-Oriented

Every Event Type describes the humanitarian event represented by a Humanitarian Observation.

It does not describe identity, ownership or historical evolution.

---

## Subject-Aware

The humanitarian interpretation of an Event Type depends upon the Subject associated with the Observation.

The same Event Type may therefore be applied to different Subject Types while preserving its semantic meaning.

---

## Language Independent

Canonical Event Type values remain language-independent.

Clients may translate or localize Event Types without changing their humanitarian semantics.

---

## Semantic Stability

Event Types should evolve conservatively.

Once introduced, their humanitarian meaning should remain stable across protocol versions whenever reasonably possible.

This stability protects long-term interoperability between independent HCP implementations.

---

## Infrastructure Independent

The Event Type Model remains independent of programming languages, databases, communication technologies and deployment architectures.

Only humanitarian semantics are standardized.

---

# 4. Relationship with Subject

The humanitarian interpretation of an Event Type always depends upon the Subject referenced by the Observation.

For example:

```json
{
  "subject": "human",
  "event_type": "missing_report"
}
```

represents a report that a person has been reported missing.

Whereas:

```json
{
  "subject": "animal",
  "event_type": "missing_report"
}
```

represents a report that an animal has been reported missing.

The humanitarian meaning of **missing_report** remains identical.

Only the Subject changes.

This allows HCP to reuse a common semantic vocabulary across multiple Subject Types while preserving semantic consistency and interoperability.

---

# 5. Core Event Types

The current version of HCP defines a common humanitarian vocabulary shared across compatible implementations.

Detailed organization of Event Types into Event Families is defined by **HCP-0017 — Event Classification**.

The following Event Types constitute the recommended core vocabulary.

## Human Event Types

- Missing Report
- Hospital Admission
- Shelter Registration
- Rescue
- Medical Evaluation
- Transfer
- Family Reunification
- Public Emergency Report

## Animal Event Types

- Missing Report
- Found Animal
- Shelter Admission
- Veterinary Assistance
- Animal Transfer
- Animal Reunification

Future HCP specifications may extend this vocabulary while preserving semantic compatibility with previously defined Event Types.
---
# 6. Event Types and Correlation

Event Types contribute semantic meaning during humanitarian correlation.

Rather than determining identity, Event Types help implementations understand how different Humanitarian Observations may relate to one another.

Compatible Event Types generally strengthen humanitarian correlation.

For example:

```text
Missing Report

        │

        ▼

Rescue

        │

        ▼

Hospital Admission

        │

        ▼

Transfer

        │

        ▼

Family Reunification
```

Each Event Type contributes humanitarian context.

Correlation evaluates Event Types together with other humanitarian evidence, including:

- Reported Label;
- Recognition Features;
- observation timestamp;
- reported location;
- reporting source;
- protocol-defined metadata.

No Event Type alone is sufficient to establish identity or humanitarian certainty.

Correlation always evaluates the complete humanitarian context.

---

# 7. Semantic Interoperability

Semantic interoperability depends upon preserving the humanitarian meaning of every Event Type.

Different HCP implementations may internally organize, store or process Event Types differently.

However, they should preserve the same humanitarian semantics when exchanging Humanitarian Records.

Interoperability therefore depends on shared meaning rather than identical implementation.

Clients may:

- translate Event Types;
- display localized terminology;
- use icons;
- apply accessibility adaptations;
- organize user interfaces differently.

None of these presentation differences affect protocol interoperability.

The protocol standardizes humanitarian meaning.

Clients define user experience.

---

# 8. Relationship with Other Specifications

The Event Type Model defines the humanitarian meaning associated with Humanitarian Observations.

Complementary HCP specifications define how those observations are represented, exchanged, interpreted and presented.

```text
Reality
        │
        ▼
Humanitarian Observation
        │
        ▼
HCP-0006
Observation Model
        │
        ▼
HCP-0008
Event Type Model
        │
        ▼
HCP-0010
Canonical JSON
        │
        ▼
HCP-0012
Correlation Model
        │
        ▼
HCP-0015
Result Presentation
```

Each specification has a distinct responsibility.

- **HCP-0006** defines what a Humanitarian Observation is.
- **HCP-0008** defines the humanitarian meaning of that Observation.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0012** defines how Humanitarian Records are locally correlated.
- **HCP-0015** defines how correlated observations are presented to people.
- **HCP-0017** organizes Event Types into Event Families without changing their semantic meaning.

Together, these specifications separate humanitarian evidence, semantic meaning, protocol representation, local interpretation and presentation while preserving universal semantic interoperability.

---

# 9. Summary

The Event Type Model defines the humanitarian meaning of Humanitarian Observations within the Humanitarian Connection Protocol.

Every Humanitarian Observation is associated with one Event Type.

Every Event Type answers one fundamental question:

> **What happened?**

Event Types define humanitarian semantics.

They do not define workflows.

They do not define implementation behavior.

They do not determine identity.

Humanitarian Observations preserve humanitarian evidence.

Event Types define humanitarian meaning.

Correlation creates local understanding.

Humanitarian Cases communicate interpretation.

People verify reality.

By standardizing humanitarian semantics independently of software architecture, databases, programming languages and communication technologies, HCP enables autonomous implementations to exchange meaningful humanitarian information while preserving organizational autonomy and long-term interoperability.

The Event Type Model reinforces one of the central architectural principles of HCP:

**Humanitarian Observations preserve evidence.**

**Event Types define meaning.**

**Correlation creates understanding.**

**Humanitarian Cases communicate interpretation.**

**People verify reality.**
