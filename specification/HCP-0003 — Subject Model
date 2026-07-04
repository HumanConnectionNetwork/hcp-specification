# HCP-0003

# Humanitarian Connection Protocol
## Subject Model

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

---

# 1. Abstract

The Subject Model defines the humanitarian entities that may be described by a Humanitarian Record.

A Humanitarian Subject is the entity about which a humanitarian observation is made.

Subjects are intentionally independent from identity systems and legal definitions.

They provide a common abstraction that allows different humanitarian situations to be represented using the same protocol.

---

# 2. Purpose

The Subject Model enables HCP to represent humanitarian information beyond individual persons.

Humanitarian operations frequently involve families, communities, organizations, shelters, resources and locations.

The protocol therefore models the observed entity rather than assuming every observation refers to a person.

---

# 3. Design Principles

The Subject Model follows these principles:

- Identity independent
- Extensible
- Technology neutral
- Globally interoperable
- Privacy aware
- Observation centered
- Compatible with future subject types

---

# 4. Humanitarian Subject

A Humanitarian Subject is the primary entity described by a Humanitarian Record.

A Subject is never identified globally.

Instead, it is described through humanitarian observations.

Multiple Humanitarian Records may legitimately describe the same Subject.

Likewise, a single Humanitarian Record always refers to exactly one Subject.

---

# 5. Subject Types

The initial version of HCP defines the following Subject Types.

## Person

Represents an individual human being.

Examples:

- Missing person
- Injured person
- Survivor
- Patient
- Volunteer
- Donor
- Recipient

---

## Family

Represents a household or family group.

Examples:

- Family reunification
- Family displacement
- Family shelter request

---

## Group

Represents a temporary collection of individuals.

Examples:

- Evacuation group
- Rescue team
- Refugee convoy

---

## Community

Represents a neighborhood, village, municipality or population.

Examples:

- Flooded community
- Indigenous village
- Isolated town

---

## Organization

Represents an institution participating in humanitarian operations.

Examples:

- Hospital
- NGO
- Fire department
- Government agency
- Volunteer organization

---

## Facility

Represents a physical structure.

Examples:

- Hospital
- Shelter
- School
- Distribution center
- Warehouse

---

## Resource

Represents humanitarian assets.

Examples:

- Food
- Water
- Medicine
- Generator
- Vehicle
- Medical equipment

---

## Location

Represents a geographic place.

Examples:

- Refugee camp
- Flood zone
- Shelter area
- Landslide
- Evacuation point

---

# 6. Subject Independence

Subject Types are descriptive only.

They do not imply:

- ownership;
- legal identity;
- citizenship;
- government registration;
- database identifiers.

The protocol intentionally separates humanitarian observations from administrative systems.

---

# 7. Subject Identification

Subjects do not receive permanent identifiers from HCP.

Only Humanitarian Records receive UUIDs.

Applications may associate multiple records using probabilistic matching techniques.

This separation preserves decentralization while avoiding global identity management.

---

# 8. Subject Relationships

Subjects may be related through Humanitarian Records.

Examples include:

- parent of
- child of
- member of
- located at
- belongs to
- supplied by
- managed by
- treated at
- transferred to

Relationships describe humanitarian context rather than ownership.

---

# 9. Subject Evolution

A Subject evolves through observations.

Example:

A Person may initially appear as:

Missing Person

↓

Located

↓

Hospitalized

↓

Transferred

↓

Recovered

Each observation generates a new Humanitarian Record.

The Subject itself is never modified.

Instead, its humanitarian history grows over time.

---

# 10. Subject Correlation

Different Nodes may independently describe the same Subject.

Correlation occurs through similarities such as:

- names;
- approximate age;
- photographs;
- location;
- timestamps;
- relationships;
- evidence;
- organizational observations.

Correlation never guarantees identity.

Instead, it increases confidence that multiple observations describe the same Subject.

---

# 11. Privacy

The Subject Model intentionally minimizes identity assumptions.

Only the information required for humanitarian purposes should be exchanged.

Applications remain responsible for enforcing local privacy legislation.

---

# 12. Extensibility

Future versions of HCP may define additional Subject Types without affecting existing implementations.

Nodes shall ignore unknown Subject Types whenever possible while preserving interoperability.

---

# 13. Compliance

An implementation complies with the Subject Model when:

- every Humanitarian Record references exactly one Subject;
- Subject Types follow this specification;
- Subjects remain identity independent;
- relationships preserve protocol semantics.

---

# 14. Examples

Example 1

Subject Type:
Person

Observation:
Located alive at temporary shelter.

---

Example 2

Subject Type:
Facility

Observation:
Hospital operating at reduced capacity.

---

Example 3

Subject Type:
Resource

Observation:
Food supplies delivered.

---

Example 4

Subject Type:
Community

Observation:
Flood waters receding.

---

# 15. Summary

The Subject Model defines what a Humanitarian Record is about.

Rather than limiting humanitarian information to individuals, HCP introduces a generalized Humanitarian Subject capable of representing people, families, organizations, facilities, resources and locations.

This abstraction enables the protocol to support a broad range of humanitarian scenarios while remaining decentralized, extensible and interoperable.
