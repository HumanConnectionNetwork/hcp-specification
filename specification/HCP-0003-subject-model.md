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

This document defines the Subject Model of the Humanitarian Connection Protocol (HCP).

A Subject is the living being to which a Humanitarian Observation refers.

The Subject Model intentionally separates the observed living being from concepts such as identity, ownership, legal status and administrative registration.

By providing a common semantic definition of the observed Subject, HCP enables independent implementations to exchange Humanitarian Records while preserving semantic interoperability, privacy and organizational autonomy.

This document defines what Humanitarian Records are about.

---

# 1. Introduction

Every Humanitarian Record refers to exactly one observed Subject.

Within HCP, a Subject is the living being that is the focus of a Humanitarian Observation.

A Subject is not created by the protocol.

A Subject exists independently of HCP.

The protocol simply provides a common semantic model for describing humanitarian observations concerning that living being.

The Subject Model intentionally distinguishes the observed Subject from concepts such as:

- identity;
- ownership;
- legal status;
- nationality;
- administrative registration;
- institutional records.

A Subject is therefore not a permanent identity.

It is the living being about which a Humanitarian Observation is made.

Multiple Humanitarian Records may independently refer to the same Subject.

Those observations remain independent.

Only local correlation may later suggest that they contribute to the same Humanitarian Case.

---

# 2. Purpose

The purpose of the Subject Model is to define what a Humanitarian Record refers to.

HCP intentionally focuses on living beings affected by humanitarian events.

The protocol does not describe institutions, facilities, inventories, infrastructure or administrative entities.

Instead, it provides a common semantic model for representing observations concerning living beings.

This design keeps HCP focused on humanitarian interoperability while preserving implementation independence and long-term semantic consistency.

The Subject Model answers one simple question:

> **Who or what is this Humanitarian Observation about?**

---

# 3. Subject vs Identity

The Subject Model intentionally separates the concept of a Subject from the concept of identity.

A Subject is the living being observed.

Identity is the human process of determining who that living being actually is.

HCP does not establish identity.

It represents humanitarian observations.

Identity may eventually be confirmed by families, hospitals, emergency responders or other responsible organizations through human verification.

The protocol itself remains independent of identity systems.

This distinction allows humanitarian information to be exchanged even when official identification is unavailable, incomplete or uncertain.

Subjects are observed.

Humanitarian Records represent observations.

People determine identity.

---

# 4. Design Principles

Every Subject represented within HCP should preserve the following architectural principles.

## Living Being

A Subject always represents a living being.

The current version of HCP supports observations concerning humans and animals.

---

## Observation-Oriented

Subjects are described through Humanitarian Observations.

The protocol never attempts to replace those observations with inferred conclusions.

---

## Identity Independent

Subjects remain independent from passports, medical record numbers, government identifiers or any other administrative identity systems.

Identity verification remains outside the scope of HCP.

---

## Correlation-Oriented

Subjects are designed to support explainable humanitarian correlation.

Independent Humanitarian Records may later contribute to the same Humanitarian Case without requiring centralized identity databases.

---

## Implementation Independent

The Subject Model is independent of programming languages, databases, software architectures and deployment environments.

Every compatible implementation represents Subjects using the same semantic definitions established by HCP.

---

## Minimal

The Subject Model intentionally defines only the semantic concept of the observed living being.

All additional interpretation belongs to other HCP specifications.
---
# 5. Supported Subject Types

The current version of HCP defines two Subject Types.

## Human Subject

Represents an individual human being observed during a humanitarian event.

Examples include:

- missing person;
- hospitalized person;
- sheltered person;
- located person;
- injured person;
- rescued person;
- unidentified person.

The Subject Model intentionally avoids administrative classifications such as nationality, legal status, ethnicity, religion or citizenship.

Those concepts remain outside the scope of HCP.

---

## Animal Subject

Represents an individual non-human animal observed during a humanitarian event.

Examples include:

- missing animal;
- found animal;
- rescued animal;
- displaced animal;
- injured animal;
- unidentified animal.

Animals are included because they frequently become part of humanitarian emergencies, evacuation processes and family reunification efforts.

The current version of HCP does not distinguish between companion animals, working animals or wildlife.

Those distinctions may be defined by future complementary specifications without changing the Subject Model.

---

# 6. Observation Independence

Subjects are described through independent Humanitarian Observations.

Every Humanitarian Record represents one observation concerning one Subject.

Different organizations may independently observe the same Subject.

Each observation remains valid independently of all others.

The protocol never merges observations.

Instead, independent implementations may later correlate Humanitarian Records when sufficient humanitarian evidence suggests they refer to the same Subject.

Observation independence improves:

- transparency;
- explainability;
- historical consistency;
- semantic interoperability.

---

# 7. Subject Identity

Subjects are not identified by the Humanitarian Connection Protocol.

Only Humanitarian Records receive protocol identifiers such as UUIDs.

Subjects themselves do not receive permanent protocol identifiers.

Reported Labels, estimated ages, Recognition Features and similar attributes represent humanitarian observations rather than identity.

Identity may eventually be confirmed through human verification performed by families, hospitals, emergency responders or other responsible organizations.

The protocol intentionally separates humanitarian observations from identity determination.

This separation allows humanitarian interoperability even when official identification is unavailable, incomplete or uncertain.

HCP minimizes identity.

HCP maximizes humanitarian evidence.

---

# 8. Subject Representation

Every Humanitarian Record refers to exactly one observed Subject.

The Subject represents the living being.

The Humanitarian Record represents the humanitarian observation concerning that living being.

Multiple Humanitarian Records may independently refer to the same Subject.

Those observations remain independent throughout their lifecycle.

Only local correlation may later suggest that multiple Humanitarian Records contribute to the same Humanitarian Case.

This separation between Subject, Humanitarian Record and Humanitarian Case is fundamental to the architecture of HCP.

---

# 9. Interoperability

The Subject Model provides a common semantic definition of the observed living being.

Every compatible implementation should interpret Subjects according to this specification regardless of its internal technologies or software architecture.

Implementations remain free to choose:

- programming languages;
- database technologies;
- deployment architectures;
- communication mechanisms;
- internal data structures.

HCP standardizes the semantic meaning of the Subject.

It does not standardize implementation details.

Shared meaning replaces shared infrastructure.

Semantic interoperability allows independent HCP Nodes to exchange Humanitarian Records while preserving complete technological independence.

---

# 10. Privacy

The Subject Model intentionally minimizes assumptions about identity.

Subjects should be described using only the information necessary to support humanitarian interoperability and explainable correlation.

Whenever equivalent humanitarian value can be achieved through humanitarian observations, implementations should prefer observation-based evidence over permanent identifiers.

The Subject Model separates the observed living being from administrative identity systems, reducing unnecessary exposure of sensitive information while preserving humanitarian usefulness.

Privacy is achieved primarily through protocol architecture rather than through infrastructure.

Additional privacy requirements are defined in:

- **HCP-0021 — Privacy and Data Minimization**
- ---
# 11. Relationship with Other Specifications

The Subject Model defines what a Humanitarian Record refers to.

It complements the remaining HCP Core specifications, each of which defines a different aspect of humanitarian interoperability.

```text
HCP-0000
Architecture and Overview
        │
        ▼
HCP-0001
Humanitarian Record
        │
        ▼
HCP-0003
Subject Model
        │
        ├───────────────┐
        ▼               ▼
HCP-0006          HCP-0008
Observation       Event Type
Model             Model
        │               │
        └───────┬───────┘
                ▼
          HCP-0010
      Canonical JSON
                │
        ┌───────┼────────┐
        ▼       ▼        ▼
   HCP-0011 HCP-0012 HCP-0013
     Query  Correlation Synchronization
                │
                ▼
          HCP-0015
    Result Presentation
```

Each specification has a distinct responsibility.

- **HCP-0000** defines the architectural principles of HCP.
- **HCP-0001** defines the Humanitarian Record.
- **HCP-0003** defines the Subject of a Humanitarian Observation.
- **HCP-0006** defines the Observation Model.
- **HCP-0008** defines the semantic meaning of observations through Event Types.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines how Humanitarian Records are queried.
- **HCP-0012** defines how Humanitarian Records are correlated.
- **HCP-0013** defines synchronization between autonomous Nodes.
- **HCP-0015** defines the local presentation of Humanitarian Cases.

Together, these specifications establish a complete semantic model while maintaining a clear separation between the observed Subject, the Humanitarian Record and the resulting Humanitarian Case.

---

# 12. Summary

The Subject Model defines the living being to which a Humanitarian Observation refers.

A Subject is not an identity.

A Subject is not an administrative entity.

A Subject is not a protocol object.

It is the living being observed during a humanitarian event.

Humanitarian Records describe observations concerning a Subject.

Humanitarian Cases are local interpretations created from one or more Humanitarian Records.

By intentionally separating Subjects, observations and identity, HCP enables independent organizations to exchange humanitarian evidence while preserving privacy, organizational autonomy and semantic interoperability.

Subjects represent living beings.

Humanitarian Records preserve observations.

Correlation creates understanding.

Human verification determines identity.

This separation enables humanitarian collaboration without requiring centralized identity systems, centralized databases or shared software platforms.
