# HCP-0017

# Event Classification Model

Version: 0.3 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0006 — Observation Model
- HCP-0008 — Event Type Model
- HCP-0010 — Canonical JSON Specification
- HCP-0016 — Humanitarian Record Lifecycle Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Event Classification Model of the Humanitarian Connection Protocol (HCP).

The Event Classification Model organizes Event Types into semantic Event Families to improve conceptual organization, documentation and long-term protocol evolution.

Event Families do not define humanitarian meaning.

Humanitarian meaning is defined exclusively by the Event Types specified in **HCP-0008 — Event Type Model**.

Instead, Event Families provide a recommended conceptual organization that simplifies documentation, implementation guidance and future protocol expansion.

The protocol standardizes conceptual organization.

It does not standardize implementation hierarchy.

---

# 1. Introduction

Humanitarian emergencies generate many different kinds of humanitarian observations.

Hospitals report admissions.

Volunteers report missing persons.

Shelters report registrations.

Emergency responders report rescues.

Environmental agencies report disasters.

Although these observations belong to different humanitarian contexts, they often share conceptual similarities.

The Event Classification Model groups related Event Types into Event Families.

Different HCP implementations may internally organize Event Types in completely different ways.

Event Families provide one recommended conceptual organization.

This organization improves readability, documentation and future protocol evolution without modifying the semantic meaning of any individual Event Type.

---

# 2. Purpose

The purpose of the Event Classification Model is to define the conceptual organization of Event Types within HCP.

This specification enables implementations to:

- organize related Event Types;
- improve documentation;
- simplify protocol understanding;
- facilitate future protocol evolution;
- preserve conceptual consistency.

This specification defines conceptual organization.

It does not define humanitarian meaning.

Semantic meaning always belongs to the Event Type Model.

The Event Classification Model answers one fundamental question:

> **How are Event Types conceptually organized?**

---

# 3. Design Principles

Every Event Classification Model follows the architectural principles of HCP.

---

## Semantic

Event Families organize humanitarian meaning.

They never redefine Event Types.

---

## Conceptual

Event Families exist only as conceptual groupings.

They are not protocol objects.

---

## Non-Normative

Event Families improve documentation and protocol understanding.

They are never required for protocol interoperability.

---

## Extensible

New Event Families may be introduced as humanitarian practice evolves.

Extensions should preserve compatibility with existing Event Types.

---

## Language Independent

Event Families represent humanitarian concepts.

Human-readable labels remain entirely the responsibility of HCP Clients.

---

## Stable

The conceptual purpose of an Event Family should remain stable across protocol versions.

---

## Implementation Independent

Implementations remain completely free to organize Event Types internally using any suitable data structures.

Only conceptual organization is standardized.

---

# 4. Classification Philosophy

The Humanitarian Connection Protocol intentionally separates humanitarian meaning from conceptual organization.

Event Types define humanitarian meaning.

Event Families organize humanitarian meaning.

Canonical JSON exchanges Event Types.

HCP Nodes never exchange Event Families.

This separation allows Event Types to remain stable while Event Families continue evolving as humanitarian practice expands.

The fundamental philosophy of Event Classification is:

**Event Types define humanitarian meaning.**

**Event Families organize humanitarian meaning.**

**Canonical JSON exchanges Event Types.**

**Implementations remain free to organize both internally.**

---

# 5. Classification Boundaries

The Event Classification Model intentionally defines strict architectural boundaries.

Event Families never:

- appear in the Canonical JSON;
- participate in humanitarian correlation;
- participate in synchronization;
- determine semantic interoperability;
- modify the meaning of Event Types.

Their purpose is exclusively conceptual.

They organize humanitarian concepts.

Nothing more.

---

# 6. Event Families

An Event Family groups together Event Types that share a common humanitarian context.

Event Families improve organization and documentation.

They never modify or redefine the semantic meaning of individual Event Types.

An Event Family is a conceptual grouping.

It is not part of the Canonical JSON.

It is not exchanged between HCP Nodes.

It is never part of protocol interoperability.

Implementations remain completely free to:

- use Event Families internally;
- extend Event Families;
- ignore Event Families entirely.

Semantic interoperability remains unaffected.

---

# 7. Standard Event Families

HCP recommends a common set of Event Families to improve documentation and conceptual consistency across implementations.

Illustrative Event Families include:

---

## Human Observation

Typical Event Types include:

- missing_report
- located
- safe
- family_reunification
- public_emergency

---

## Medical Observation

Typical Event Types include:

- hospital_admission
- medical_evaluation
- transfer
- discharge

---

## Rescue Observation

Typical Event Types include:

- rescue
- evacuation
- extraction

---

## Shelter Observation

Typical Event Types include:

- shelter_registration
- shelter_transfer
- shelter_departure

---

## Humanitarian Aid Observation

Typical Event Types include:

- food_distribution
- water_distribution
- medical_supply_distribution
- hygiene_kit_distribution
- clothing_distribution

---

## Infrastructure Observation

Typical Event Types include:

- building_collapse
- bridge_damage
- road_blocked
- utility_failure
- fire_damage

---

## Environmental Observation

Typical Event Types include:

- flood
- landslide
- earthquake
- wildfire
- storm

---

## Logistics Observation

Typical Event Types include:

- resource_deployment
- supply_arrival
- transportation_available
- access_route_open
- access_route_closed

---

## Veterinary Observation

Typical Event Types include:

- animal_missing
- animal_found
- veterinary_care
- animal_transfer
- animal_reunification

These Event Families are recommendations.

They are not mandatory.

Future protocol versions may introduce additional Event Families while preserving semantic compatibility.
---
# 8. Language Independence

Event Families represent humanitarian concepts rather than natural language.

Different HCP Clients may present the same Event Family using different languages.

Illustrative examples:

English

```
Medical Observation
```

Spanish

```
Observación Médica
```

Portuguese

```
Observação Médica
```

Although labels differ, the underlying humanitarian concept remains identical.

Localization belongs entirely to HCP Clients.

---

# 9. Extensions

Organizations remain free to define additional Event Families whenever necessary.

Illustrative examples include:

- Veterinary Disaster Response;
- Maritime Rescue;
- Cultural Heritage Protection;
- Hazardous Materials Response;
- Humanitarian Logistics Support.

Custom Event Families should complement the recommended conceptual organization.

They should never redefine existing Event Types.

Future versions of HCP may incorporate widely adopted Event Families without affecting semantic interoperability.

---

# 10. Optional Use During Correlation

Although Event Families are never exchanged between HCP Nodes, implementations may optionally use them internally.

Possible uses include:

- organizing related Event Types;
- simplifying internal correlation rules;
- improving explainability;
- generating humanitarian statistics;
- supporting internal analytics.

The Correlation Model always evaluates Event Types.

Event Families provide only conceptual context.

They never replace Event Types during semantic evaluation.

---

# 11. Humanitarian Record Lifecycle

Every Humanitarian Record preserves exactly one Event Type representing one humanitarian observation.

Future observations generate new Humanitarian Records containing their own Event Types.

Event Families simply organize those Event Types conceptually throughout the Humanitarian Record Lifecycle.

They never modify:

- Humanitarian Records;
- Event Types;
- humanitarian evidence.

Historical humanitarian evidence remains immutable.

---

# 12. Version Evolution

Future protocol versions may introduce:

- additional Event Families;
- reorganized conceptual groupings;
- improved documentation;
- additional illustrative examples.

Whenever possible, conceptual evolution should preserve compatibility with previously defined Event Types.

Changes to Event Families should never modify the semantic meaning of existing Event Types.

---

# 13. Implementation Guidelines

Implementations are encouraged to:

- recognize the recommended Event Families;
- preserve unknown Event Types;
- allow custom Event Families;
- support future Event Family extensions.

Implementations should never:

- reject a Humanitarian Record because an Event Family is unknown;
- reject a Humanitarian Record because an Event Family is absent;
- require Event Families for protocol interoperability.

Only Event Types participate directly in semantic interoperability.

---

# 14. Relationship with Other Specifications

The Event Classification Model defines the conceptual organization of Event Types within HCP.

Complementary specifications define how humanitarian observations are represented, preserved and interpreted.

```text
Observation

        │

        ▼

Event Type

        │

        ▼

Event Family

        │

        ▼

Documentation
```

Each specification has a distinct responsibility.

- **HCP-0006** defines the Observation Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0012** defines humanitarian correlation.
- **HCP-0016** defines the Humanitarian Record Lifecycle.

Together, these specifications define how humanitarian observations acquire meaning, are conceptually organized and remain semantically interoperable across independent HCP implementations.

---

# 15. Summary

The Event Classification Model defines the conceptual organization of Event Types within the Humanitarian Connection Protocol.

Event Types define humanitarian meaning.

Event Families organize humanitarian meaning.

Canonical JSON exchanges Event Types.

Event Families are never exchanged.

They are not protocol objects.

They do not participate in synchronization.

They do not participate in humanitarian correlation.

They do not determine semantic interoperability.

Instead, they improve:

- conceptual organization;
- documentation;
- protocol learning;
- future extensibility.

By separating semantic meaning from conceptual organization, HCP preserves stable interoperability while allowing humanitarian concepts to evolve over time.

The Event Classification Model reinforces one of the central architectural principles of HCP:

**Event Types define humanitarian meaning.**

**Canonical JSON exchanges Event Types.**

**Event Families organize humanitarian meaning.**

**Implementations remain completely free to organize them internally.**
