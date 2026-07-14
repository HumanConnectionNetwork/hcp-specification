# HCP-0011

# Query Model

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
- HCP-0008 — Event Type Model
- HCP-0010 — Canonical JSON Specification
- HCP-0012 — Correlation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Query Model of the Humanitarian Connection Protocol (HCP).

A Query is the standardized semantic representation of the humanitarian evidence currently known by the person initiating a search.

Rather than searching for identities or exact matches, an HCP Query represents the available humanitarian evidence that may correspond to one or more independent Humanitarian Records.

The purpose of a Query is to enable compatible HCP Nodes to perform explainable humanitarian correlation while preserving semantic interoperability and implementation independence.

Queries describe what is known.

Nodes evaluate Humanitarian Records.

Correlation creates Humanitarian Cases.

People verify reality.

---

# 1. Introduction

Humanitarian emergencies frequently involve incomplete, uncertain or fragmented information.

Families, volunteers, hospitals and emergency responders often know only part of what happened.

An HCP Query provides a standardized semantic representation of that partial humanitarian evidence.

The Query does not attempt to identify a person or animal directly.

Instead, it represents the humanitarian evidence currently known by the person initiating the search.

Compatible HCP Nodes evaluate that evidence against locally available Humanitarian Records.

The result of a Query is never identity confirmation.

It is a locally generated humanitarian interpretation that assists people in evaluating possible relationships between independent Humanitarian Records.

---

# 2. Purpose

The purpose of the Query Model is to standardize how humanitarian evidence is represented when requesting humanitarian correlation.

Queries maximize the humanitarian evidence available for local evaluation.

Every Query may contain as much or as little information as the person initiating the search currently knows.

Partial Queries are expected.

Unknown information does not invalidate a Query.

By standardizing the semantic representation of humanitarian evidence, HCP enables independent implementations to perform compatible humanitarian searches while remaining completely free to innovate in their correlation algorithms.

The Query Model answers one fundamental question:

> **What is currently known?**

---

# 3. Design Principles

Every HCP Query follows the architectural principles of HCP.

## Evidence-Based

Queries represent humanitarian evidence.

They never represent verified identity.

---

## Observation-Oriented

Queries describe humanitarian observations remembered, reported or known by the person performing the search.

They do not describe complete humanitarian histories.

---

## Partial Information

Incomplete Queries are expected.

Unknown information should simply be omitted whenever reasonably possible.

Partial humanitarian evidence frequently produces valuable humanitarian correlation.

---

## Semantic

The Query Model standardizes humanitarian meaning.

It does not standardize search engines, databases or correlation algorithms.

---

## Explainable

Queries should enable explainable humanitarian correlation.

Returned Humanitarian Cases should provide sufficient humanitarian evidence to support human interpretation.

---

## Implementation Independent

Compatible implementations remain free to choose:

- search engines;
- databases;
- indexing strategies;
- optimization techniques;
- correlation algorithms.

Only the semantic meaning of the Query is standardized.

---

# 4. Relationship with HCP Clients

The Query Model defines the semantic structure exchanged between HCP Clients and HCP Nodes.

It does not prescribe user interface design.

For example, an HCP Client may present the following workflow:

```text
🔍 Search

      │

      ├── 👤 Person

      │        │

      │        └── Search Flow

      │

      └── 🐾 Animal

               │

               └── Search Flow
```

Internally, the Client transforms the information provided by the user into a canonical HCP Query.

This separation preserves a simple user experience while maintaining semantic interoperability.

Users search for people or animals.

Clients build Queries.

Nodes evaluate Humanitarian Records.

Correlation creates Humanitarian Cases.

People verify reality.

---

# 5. Canonical Query Structure

The Canonical Query follows the same semantic organization used by the Canonical JSON Specification.

This consistency allows implementations to compare humanitarian evidence without requiring structural transformations.

A Query contains two conceptual sections:

- Subject
- Observation

Illustrative structure:

```json
{
  "subject": {

    "type": "human",

    "reported_label": "Juan Pérez",

    "estimated_age": 42,

    "recognition_features": "Blue jacket, black backpack"

  },

  "observation": {

    "event_type": "missing_report",

    "reported_location": "Caracas"

  }
}
```

Unlike a Humanitarian Record, a Query contains only the humanitarian evidence currently known by the person initiating the search.

Unknown information should simply be omitted.

---

# 6. Subject Query

The Subject section represents the humanitarian evidence currently known about the observed Subject.

Illustrative example:

```json
{
  "subject": {

    "type": "human",

    "reported_label": "Juan Pérez",

    "estimated_age": 42,

    "recognition_features": "Blue jacket, glasses"

  }
}
```

The Subject Query follows the semantic definitions established by **HCP-0003 — Subject Model**.

---

## type

Defines the Subject Type being searched.

Examples:

```
human

animal
```

---

## reported_label

Human-readable label provided by the person initiating the search.

Examples:

```
Juan Pérez

Unknown child

White dog

Green parrot
```

Reported Labels contribute humanitarian evidence.

They never establish identity.

---

## estimated_age

Approximate age when known.

Applicable only to human Subjects.

If unknown, this field should be omitted.

Estimated Age contributes humanitarian evidence.

It never establishes identity.

---

## recognition_features

Observable characteristics remembered by the person initiating the search.

Typical examples for humans include:

- clothing;
- glasses;
- scars;
- tattoos;
- hairstyle;
- backpacks.

Typical examples for animals include:

- collar;
- coat color;
- distinctive markings;
- ear shape;
- visible injuries.

Recognition Features frequently provide some of the strongest humanitarian evidence available for explainable correlation.
---
# 7. Observation Query

The Observation section represents the humanitarian evidence associated with the event being searched.

Illustrative example:

```json
{
  "observation": {

    "event_type": "missing_report",

    "reported_location": "Caracas"

  }
}
```

The Observation Query answers questions such as:

- What happened?
- Where was it observed?

The Observation Query follows the semantic definitions established by **HCP-0006 — Observation Model**.

---

## event_type

Defines the humanitarian event known by the person initiating the search.

Examples:

```
missing_report

hospital_admission

rescue

shelter_registration

family_reunification

veterinary_assistance
```

Event Types contribute humanitarian meaning.

They never establish identity.

The complete semantic model is defined by **HCP-0008 — Event Type Model**.

---

## reported_location

Free-text description of the location associated with the humanitarian observation.

Examples:

```
Hospital Central

Shelter A

Near Plaza Bolívar

Highway KM 18
```

Reported Location contributes humanitarian evidence.

It is evaluated together with all other available humanitarian evidence.

---

# 8. Humanitarian Evidence

Every field contained within a Query contributes humanitarian evidence.

Typical humanitarian evidence includes:

- Subject Type;
- Reported Label;
- Estimated Age;
- Recognition Features;
- Event Type;
- Reported Location;
- temporal proximity.

No individual element is sufficient to establish identity.

Correlation evaluates the complete humanitarian context represented by the Query together with the humanitarian evidence contained within independent Humanitarian Records.

Different HCP implementations may assign different importance to different evidence while preserving semantic interoperability.

The protocol standardizes humanitarian evidence.

Implementations define correlation.

---

# 9. Humanitarian Correlation

A Query requests humanitarian correlation.

It never requests identity confirmation.

The HCP Node evaluates the humanitarian evidence contained within the Query against locally available Humanitarian Records.

Correlation remains entirely implementation-specific.

Different HCP implementations may adopt completely different correlation strategies while preserving semantic interoperability.

Only the semantic representation of humanitarian evidence is standardized.

The correlation process itself is defined by **HCP-0012 — Correlation Model**.

---

# 10. Humanitarian Results

The result of a Query is a collection of Humanitarian Cases generated locally by the HCP Node.

Each Humanitarian Case represents one possible humanitarian interpretation of compatible Humanitarian Records.

Illustrative response:

```json
{
  "results": [
    {
      "case_id": "case-001",

      "score": 0.93,

      "supporting_evidence": [

        "Reported Labels are compatible",

        "Recognition Features are compatible",

        "Reported Locations are compatible"

      ],

      "conflicting_evidence": [

        "Estimated Age differs by approximately five years"

      ]
    }
  ]
}
```

Returned Humanitarian Cases should be ordered according to the implementation's correlation strategy.

A higher Correlation Score indicates stronger humanitarian compatibility.

It never confirms identity.

Presentation of Humanitarian Cases is defined by **HCP-0015 — Result Presentation**.

---

# 11. Explainability

Implementations are strongly encouraged to explain why a Humanitarian Case was presented.

Typical explanations include:

- compatible Reported Labels;
- compatible Estimated Age;
- compatible Recognition Features;
- geographically compatible Reported Locations;
- compatible Event Types;
- compatible temporal proximity.

Explainable correlation improves transparency.

People should understand why humanitarian evidence appears related.

The explainability model is defined by **HCP-0014 — Explainable Correlation**.

---

# 12. Incomplete Queries

Humanitarian emergencies frequently involve incomplete information.

A person initiating a search may remember only:

- clothing;
- approximate age;
- municipality;
- hospital;
- animal color;
- collar;
- last known location.

All these Queries remain valid.

Unknown information should simply be omitted.

Partial humanitarian evidence frequently produces valuable humanitarian correlation.

Future Humanitarian Observations may strengthen previous search results without modifying earlier Humanitarian Records.

---

# 13. Interoperability

Every compatible HCP implementation shall accept Queries following the semantic model defined by this specification.

Internal implementation details remain entirely independent.

Implementations remain free to choose:

- databases;
- search engines;
- indexing strategies;
- optimization techniques;
- correlation algorithms.

Only the semantic representation of humanitarian evidence is standardized.

Shared semantics enable universal interoperability.

---

# 14. Relationship with Other Specifications

The Query Model defines how humanitarian evidence is represented when requesting humanitarian correlation.

Complementary specifications define the remaining stages of the humanitarian search process.

```text
User

        │

        ▼

Query

        │

        ▼

Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Humanitarian Cases

        │

        ▼

Presentation

        │

        ▼

Human Verification
```

Each specification has a distinct responsibility.

- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines humanitarian correlation.
- **HCP-0014** defines explainable correlation.
- **HCP-0015** defines Humanitarian Case presentation.

Together, these specifications define how humanitarian evidence is represented, evaluated, interpreted and presented while preserving semantic interoperability.

---

# 15. Summary

The Query Model defines the standardized semantic representation of humanitarian evidence used to request humanitarian correlation.

A Query does not represent identity.

It represents what is currently known.

Queries describe humanitarian evidence.

Humanitarian Records preserve observations.

Correlation creates local understanding.

Humanitarian Cases communicate interpretation.

People verify reality.

By separating humanitarian evidence from identity, HCP enables independent implementations to assist humanitarian reunification without requiring centralized identity systems or exact matching.

The Query Model embodies one of the central architectural principles of HCP:

**Queries describe known humanitarian evidence.**

**Humanitarian Records preserve observations.**

**Correlation creates local understanding.**

**Humanitarian Cases communicate interpretation.**

**People verify reality.**
