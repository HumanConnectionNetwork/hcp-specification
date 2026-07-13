# HCP-0017

# Event Classification Model

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0006 — Observation Model
- HCP-0008 — Event Type Model
- HCP-0016 — Humanitarian Record Lifecycle Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Event Classification Model of the Humanitarian Connection Protocol (HCP).

The Event Classification Model organizes Event Types into semantic Event Families to improve consistency, documentation and interoperability across independent HCP implementations.

Event Families do not define humanitarian meaning.

Humanitarian meaning is defined by the Event Types specified in **HCP-0008**.

Instead, Event Families provide a conceptual organization that simplifies understanding, implementation and future protocol evolution.

The protocol standardizes semantic organization.

It does not impose implementation hierarchy.

---

# 1. Introduction

Humanitarian emergencies involve a wide variety of humanitarian observations.

Hospitals report admissions.

Volunteers report missing persons.

Shelters report registrations.

Emergency responders report rescues.

Although these observations belong to different humanitarian contexts, they often share common semantic characteristics.

The Event Classification Model organizes related Event Types into Event Families.

This organization improves readability, documentation and interoperability without changing the semantic meaning of individual Event Types.

Event Families exist to organize humanitarian concepts.

They do not replace Event Types.

---

# 2. Purpose

The purpose of the Event Classification Model is to provide a consistent conceptual organization for Event Types defined within HCP.

This model enables implementations to:

- organize related Event Types;
- improve documentation;
- simplify protocol understanding;
- facilitate future protocol extensions;
- preserve semantic consistency across implementations.

The Event Classification Model intentionally avoids prescribing implementation-specific hierarchies or database structures.

Only conceptual organization is standardized.

---

# 3. Design Principles

Every Event Classification Model follows the fundamental architectural principles of HCP.

---

## Semantic

Event Families organize humanitarian meaning.

They never redefine Event Types.

---

## Conceptual

Event Families provide conceptual organization.

They are not implementation objects.

---

## Extensible

New Event Families may be introduced as humanitarian needs evolve.

Extensions should preserve compatibility with existing Event Types.

---

## Language Independent

Event Families represent humanitarian concepts.

Human-readable labels remain the responsibility of HCP Clients.

---

## Stable

The semantic purpose of an Event Family should remain stable across protocol versions.

This improves long-term interoperability.

---

## Implementation Independent

Implementations remain free to organize Event Types internally using any suitable data structures.

The protocol standardizes only their conceptual organization.

---

# 4. Classification Philosophy

Event Types define humanitarian meaning.

Event Families organize humanitarian meaning.

The protocol intentionally separates semantic definition from conceptual organization.

This distinction allows Event Types to remain stable while Event Families continue evolving as humanitarian practice expands.

The fundamental philosophy of Event Classification is:

**Event Types define humanitarian meaning.**

**Event Families organize humanitarian meaning.**

**Implementations remain free to organize both internally.**
---

# 5. Event Families

An Event Family groups together Event Types that share a common humanitarian context.

Event Families improve organization and documentation.

They do not modify or redefine the semantic meaning of individual Event Types.

An Event Family is a conceptual grouping.

It is not part of the Canonical JSON.

It is not exchanged between HCP Nodes.

Implementations remain free to use Event Families internally or ignore them entirely.

---

# 6. Standard Event Families

HCP recommends a set of standard Event Families to promote consistent documentation and understanding across implementations.

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

---

Additional Event Families may be introduced as humanitarian practice evolves.

The recommended Event Families are intended to improve semantic organization.

They are not mandatory.

---

# 7. Language Independence

Event Families represent humanitarian concepts rather than natural language.

Different HCP Clients may present the same Event Family using different languages.

Examples:

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

The underlying humanitarian concept remains identical.

Localization belongs entirely to HCP Clients.

---

# 8. Extensions

Organizations remain free to define additional Event Families whenever necessary.

Examples include:

- Veterinary Disaster Response;
- Maritime Rescue;
- Cultural Heritage Protection;
- Hazardous Materials Response.

Custom Event Families should complement the standard organization rather than redefine existing humanitarian concepts.

Future HCP versions may incorporate widely adopted Event Families into the core specification without affecting existing semantic interoperability.
---

# 9. Correlation

Although Event Families are not exchanged between HCP Nodes, they may assist implementations during humanitarian correlation.

Implementations may use Event Families to:

- organize compatible Event Types;
- simplify internal correlation logic;
- improve explainability;
- support humanitarian analytics.

The Correlation Model always evaluates Event Types.

Event Families provide conceptual context.

They never replace Event Types during semantic evaluation.

---

# 10. Humanitarian Record Lifecycle

Each Humanitarian Record preserves the Event Type observed at the moment the humanitarian snapshot was created.

Subsequent observations generate new Humanitarian Records with their own Event Types.

Event Families help organize those observations conceptually throughout the Humanitarian Record Lifecycle.

They never modify previously recorded humanitarian observations.

---

# 11. Versioning

Future versions of HCP may introduce:

- additional Event Families;
- reorganized conceptual groupings;
- improved documentation;
- new illustrative examples.

Changes to Event Families should preserve the semantic meaning of existing Event Types.

Whenever possible, backward compatibility should be maintained.

---

# 12. Implementation Guidelines

Implementations are encouraged to:

- recognize the standard Event Families;
- preserve unknown Event Types;
- allow custom Event Families;
- avoid rejecting valid Humanitarian Records because an Event Family is unknown.

Unknown Event Families do not affect protocol interoperability.

Only Event Types participate directly in semantic interoperability.

---

# 13. Relationship with Other Specifications

The Event Classification Model defines the conceptual organization of Event Types within HCP.

Complementary specifications define the remaining semantic components of humanitarian observations.

- **HCP-0006** defines the Observation Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0016** defines the Humanitarian Record Lifecycle Model.

Together, these specifications define how humanitarian observations are classified, preserved and interpreted while maintaining semantic interoperability across independent HCP implementations.

---

# 14. Summary

The Event Classification Model defines the conceptual organization of Event Types within the Humanitarian Connection Protocol.

Event Types define humanitarian meaning.

Event Families organize humanitarian meaning.

The protocol intentionally separates semantic definition from conceptual organization.

This separation allows Event Types to remain stable while Event Families continue evolving as humanitarian practice expands.

Event Families improve documentation, understanding and future extensibility.

They do not impose implementation hierarchy.

They are not exchanged between HCP Nodes.

By organizing humanitarian concepts without constraining implementation, HCP preserves both semantic consistency and implementation independence.

The Event Classification Model reinforces one of the central architectural principles of HCP:

**Event Types define humanitarian meaning.**

**Event Families organize humanitarian meaning.**

**Implementations remain free to organize both internally.**
