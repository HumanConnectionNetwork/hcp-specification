# HCP-0003

# Subject Model

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

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the **Subject Model** of the Humanitarian Connection Protocol (HCP).

A Humanitarian Subject is the living being about which a Humanitarian Record is created.

The Subject Model intentionally separates the observed subject from identity, administrative records and institutional information.

By defining a common semantic representation of the observed living being, HCP enables independent implementations to exchange and correlate humanitarian observations while preserving interoperability, privacy and organizational autonomy.

---

# 1. Introduction

Every Humanitarian Record describes exactly one observed subject.

Within HCP, a **Subject** is the living being that is the focus of a humanitarian observation.

The protocol intentionally distinguishes the observed subject from concepts such as identity, ownership, legal status or administrative registration.

A Subject is therefore not a permanent identity.

It is the living being described by an independent humanitarian observation.

Multiple Humanitarian Records may independently describe the same Subject.

Those observations remain independent until compatible HCP implementations determine that they may represent the same humanitarian case through explainable correlation.

---

# 2. Purpose

The purpose of the Subject Model is to define what a Humanitarian Record is about.

Rather than describing institutions, facilities, inventories or administrative entities, HCP intentionally focuses on living beings affected by humanitarian events.

This design keeps the protocol simple, implementation-independent and focused on humanitarian interoperability.

The Subject Model enables independent systems to describe the same living being using a common semantic model while preserving observation independence and avoiding centralized identity management.

---

# 3. Design Principles

Every Humanitarian Subject should preserve the following principles.

## Living Being

A Subject always represents a living being.

The protocol currently supports observations concerning humans and animals.

---

## Observation-Based

Subjects are described through humanitarian observations.

The protocol does not attempt to define permanent identities.

---

## Identity Independent

Subjects remain independent from government identifiers, passports, medical record numbers or other administrative identity systems.

Identity verification remains outside the scope of HCP.

---

## Correlation-Oriented

Subjects are designed to support explainable humanitarian correlation.

Independent observations may later be related through compatible correlation implementations without requiring centralized identity databases.

---

## Infrastructure Independent

The Subject Model is independent of programming languages, databases, software architectures and deployment environments.

Every compatible implementation represents Subjects using the common semantic definitions established by HCP.

---

## Extensible

Future versions of HCP may introduce additional subject classifications while preserving backward compatibility whenever reasonably possible.
---

# 4. Supported Subject Types

The current version of HCP defines two Subject Types.

## Human

Represents an individual human being observed during a humanitarian event.

Examples include:

- missing person
- hospitalized person
- sheltered person
- located person
- injured person
- rescued person
- unidentified person

The protocol does not distinguish subjects by nationality, legal status, gender, ethnicity or other administrative classifications.

Those attributes remain outside the scope of the Subject Model.

---

## Animal

Represents an individual non-human animal observed during a humanitarian event.

Examples include:

- missing pet
- found pet
- rescued animal
- displaced animal
- injured animal
- unidentified animal

The protocol intentionally treats animals as humanitarian subjects because they frequently become part of humanitarian emergencies and family reunification efforts.

Future specifications may extend animal classifications while preserving interoperability.

---

# 5. Observation Independence

Subjects are described through independent humanitarian observations.

Each Humanitarian Record represents one observation concerning one Subject.

Different organizations may independently observe the same Subject.

Each observation remains valid on its own.

The protocol does not merge observations.

Instead, compatible HCP implementations may later determine that multiple observations probably describe the same Subject through explainable correlation.

This approach preserves transparency, explainability and historical consistency.

---

# 6. Subject Identification

Subjects do not receive permanent identifiers from HCP.

Only Humanitarian Records receive protocol identifiers such as UUIDs.

Reported names, estimated ages and similar information are treated as observation evidence rather than permanent identity.

Identity may eventually be confirmed by people or responsible institutions.

The protocol itself remains focused on describing observations rather than establishing identity.

This distinction enables humanitarian interoperability even when official identification is unavailable or uncertain.

---

# 7. Subject Representation

Every Humanitarian Record references exactly one Subject.

The Subject represents the living being observed.

The Humanitarian Record represents the humanitarian observation describing that Subject.

This distinction is fundamental to the HCP semantic model.

A Subject may be represented by multiple independent Humanitarian Records created by different HCP Nodes.

Likewise, every Humanitarian Record always refers to one and only one observed Subject.

This model allows observations to remain independent while enabling future correlation between compatible implementations.
---

# 8. Interoperability

The Subject Model provides a common semantic definition of the observed living being.

Every compatible HCP implementation should represent Subjects according to this specification regardless of its internal technologies or data models.

Implementations remain free to choose:

- programming languages
- database technologies
- deployment architectures
- communication mechanisms
- internal data structures

The protocol standardizes the semantic meaning of the Subject.

It does not standardize software implementation.

Shared meaning replaces shared infrastructure.

This enables independent HCP Nodes to exchange humanitarian observations while preserving technological independence.

---

# 9. Privacy

The Subject Model intentionally minimizes identity assumptions.

Subjects should be described using only the information necessary to support humanitarian coordination and explainable correlation.

Whenever possible, implementations should prioritize observable characteristics over permanent personal identifiers.

The Subject Model separates the observed living being from administrative identity systems, reducing unnecessary exposure of sensitive information while preserving humanitarian usefulness.

Additional privacy requirements are defined in:

- **HCP-0021 — Privacy and Data Minimization**

---

# 10. Relationship with Other Specifications

This document defines what a Humanitarian Subject is.

Other HCP specifications define complementary aspects of the protocol.

- **HCP-0000** defines the overall architecture and philosophy of HCP.
- **HCP-0001** defines the Humanitarian Record.
- **HCP-0002** defines the HCP Node.
- **HCP-0006** defines the Observation Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0010** defines the Canonical HCP JSON Representation.
- **HCP-0012** defines the Correlation Model.
- **HCP-0016** defines the Humanitarian Record Lifecycle.

Together, these specifications establish a common semantic model for representing, exchanging and correlating humanitarian observations concerning living beings.

---

# 11. Summary

The Subject Model defines the living being described by a Humanitarian Record.

Within HCP, a Subject is not an identity, a database entity or an administrative record.

It is the living being observed during a humanitarian event.

Humanitarian Records describe observations.

Subjects represent the living beings to which those observations refer.

This distinction allows independent organizations to exchange meaningful humanitarian information while preserving observation independence, organizational autonomy and technological independence.

By limiting the Subject Model to humans and animals, HCP remains focused on its primary mission: enabling humanitarian interoperability for living beings affected by humanitarian events.

The Subject Model provides the semantic foundation upon which Humanitarian Records, correlation and humanitarian interoperability are built.
