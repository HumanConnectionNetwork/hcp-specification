# HCP-0011

# Query Model

Version: 0.3 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Humanitarian Record
- HCP-0003 — Subject Model
- HCP-0004 — Correlation Model
- HCP-0006 — Observation Model
- HCP-0008 — Event Type Model
- HCP-0010 — Canonical JSON Specification

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Query Model of the Humanitarian Connection Protocol (HCP).

A Query is the standardized semantic representation of the humanitarian evidence known by the person initiating a search.

Rather than searching for identities or exact matches, an HCP Query describes available humanitarian evidence that may correspond to one or more independent Observations.

The purpose of a Query is to enable HCP Nodes to perform explainable correlation while preserving implementation independence and semantic interoperability.

Queries describe what is known.

Nodes correlate Observations.

People interpret the results.

---

# 1. Introduction

Humanitarian emergencies frequently involve incomplete, uncertain or fragmented information.

Families, volunteers, hospitals and emergency responders often know only part of what happened.

A Query allows that partial humanitarian evidence to be represented using a standardized semantic model.

The Query does not attempt to identify a person or animal directly.

Instead, it describes the available humanitarian evidence so that compatible HCP Nodes may correlate it with existing Humanitarian Records.

The result of a Query is never identity confirmation.

It is a collection of compatible humanitarian observations that may assist human interpretation and later verification.

---

# 2. Purpose

The purpose of the Query Model is to standardize how humanitarian evidence is described when searching for compatible observations.

Queries maximize the humanitarian evidence available for correlation.

Every Query may contain as much or as little information as the reporter knows.

Partial Queries are expected.

Unknown information does not invalidate a Query.

By standardizing the semantic representation of humanitarian evidence, HCP enables independent implementations to perform compatible searches while remaining free to innovate in their correlation algorithms.

---

# 3. Design Principles

Every HCP Query follows the fundamental architectural principles of HCP.

---

## Observation-Based

Queries describe humanitarian observations.

They do not describe identities.

---

## Evidence-Based

Every field contributes humanitarian evidence.

No individual field establishes identity.

---

## Partial Information

Incomplete Queries are expected.

Unknown information should simply be omitted whenever possible.

---

## Semantic

The Query Model standardizes humanitarian meaning.

It does not standardize search algorithms.

---

## Explainable

Queries should produce explainable correlation results whenever reasonably possible.

Returned candidates should include sufficient humanitarian evidence to support human interpretation.

---

## Implementation Independent

Every HCP implementation may use different search engines, databases or correlation strategies.

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

Nodes correlate Observations.
---

# 5. Canonical Query Structure

A Canonical Query follows the same semantic organization as the Canonical JSON Specification.

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

    "status": "missing",

    "reported_location": "Caracas"

  }
}
```

Unlike a Humanitarian Record, a Query contains only the humanitarian evidence currently known by the person initiating the search.

Unknown information should simply be omitted.

---

# 6. Subject Query

The Subject section describes the known humanitarian evidence concerning the observed living being.

Example:

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

Human-readable description provided by the person performing the search.

Examples:

```
Juan Pérez

Unknown child

White dog

Green parrot
```

The reported label contributes humanitarian evidence.

It is never interpreted as a permanent identifier.

---

## estimated_age

Approximate age when known.

Applicable only to human Subjects.

If unknown, this field should be omitted.

---

## recognition_features

Observable characteristics remembered by the person initiating the search.

Typical examples include:

Humans:

- clothing;
- glasses;
- scars;
- tattoos;
- backpack;
- hairstyle.

Animals:

- collar;
- coat color;
- distinctive markings;
- ear shape;
- visible injuries.

Recognition Features frequently provide some of the strongest humanitarian evidence available for correlation.

---

# 7. Observation Query

The Observation section describes the humanitarian event being searched.

Example:

```json
{
  "observation": {

    "event_type": "missing_report",

    "status": "missing",

    "reported_location": "Caracas"
  }
}
```

The Observation section answers questions such as:

- What humanitarian event is being searched?
- What humanitarian condition is known?
- Where was the observation reported?

---

## event_type

Describes the humanitarian event known by the person initiating the search.

Examples:

```
missing_report

hospital_admission

rescue

shelter_registration
```

This field contributes humanitarian evidence.

It never guarantees that matching observations represent the same Subject.

---

## status

Represents the humanitarian condition known at the time of the search.

Examples:

```
missing

stable

critical

safe
```

Status contributes humanitarian evidence.

It should not be interpreted as a mandatory filter.

Different implementations may use this information differently during correlation.

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

Reported Location contributes humanitarian context.

It is evaluated together with all other available evidence.

---

# 8. Humanitarian Evidence

Every field contained in a Query contributes humanitarian evidence.

Typical evidence includes:

- Subject Type;
- Reported Label;
- Estimated Age;
- Recognition Features;
- Event Type;
- Status;
- Reported Location;
- temporal proximity.

No single element is sufficient to identify a Subject.

Correlation emerges from the combined evaluation of multiple compatible pieces of humanitarian evidence.

Different HCP implementations may prioritize different evidence according to their humanitarian context while preserving semantic interoperability.
---

# 9. Correlation

A Query requests humanitarian correlation.

It does not request exact matching.

The HCP Node compares the humanitarian evidence contained in the Query with the humanitarian evidence contained in independent Humanitarian Records.

Correlation evaluates compatible observations.

It never evaluates identity.

Different HCP implementations may adopt different correlation strategies.

The protocol intentionally does not prescribe a mandatory algorithm.

Only the semantic meaning of the Query is standardized.

---

# 10. Correlation Results

The result of a Query is a collection of Correlation Candidates.

Each candidate represents an independent Humanitarian Record whose humanitarian evidence appears compatible with the submitted Query.

Typical response:

```json
{
  "results": [
    {
      "record_id": "d71b5f...",

      "score": 0.93,

      "event_type": "hospital_admission",

      "status": "stable"
    },
    {
      "record_id": "ab91de...",

      "score": 0.81,

      "event_type": "missing_report",

      "status": "missing"
    }
  ]
}
```

Returned candidates should be ordered according to the implementation's correlation strategy.

A higher Correlation Score indicates stronger humanitarian compatibility.

It does not confirm identity.

---

# 11. Explainability

Implementations are strongly encouraged to explain why a Correlation Candidate was returned.

Typical explanations include:

- compatible Reported Label;
- compatible Estimated Age;
- compatible Recognition Features;
- geographically compatible Reported Location;
- compatible Event Type;
- compatible Status;
- compatible temporal proximity.

Explainable correlation improves transparency and supports human interpretation.

Users should understand why a candidate was presented.

---

# 12. Incomplete Queries

Humanitarian emergencies frequently involve incomplete information.

A person searching may remember only:

- clothing;
- approximate age;
- hospital;
- municipality;
- animal color;
- collar;
- last known location.

All these Queries remain valid.

Unknown information should simply be omitted.

Partial humanitarian evidence frequently produces valuable humanitarian correlation.

Future Observations may strengthen or complement previous search results without modifying earlier Humanitarian Records.

---

# 13. Interoperability

Every compatible HCP implementation shall accept Queries following this semantic model.

Internal search engines, correlation algorithms, databases and optimization techniques remain implementation-specific.

The protocol standardizes only the semantic representation of humanitarian evidence.

This allows independent HCP implementations to exchange compatible Queries while preserving complete implementation independence.

---

# 14. Relationship with Other Specifications

The Query Model defines how humanitarian evidence is represented when requesting humanitarian correlation.

Complementary specifications define the remaining concepts involved in this process.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0004** defines the Correlation Model.
- **HCP-0006** defines the Observation Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0010** defines the Canonical JSON Specification.
- **HCP-0012** defines the Correlation Model.
- **HCP-0015** defines the Result Presentation Model.

Together, these specifications define how humanitarian evidence is represented, queried, correlated and presented while preserving semantic interoperability.

---

# 15. Summary

The Query Model defines the standardized semantic representation of humanitarian evidence used to request humanitarian correlation.

A Query does not describe an identity.

It describes what is currently known.

Queries represent humanitarian evidence.

Nodes correlate Observations.

Correlation produces Correlation Candidates.

People interpret the results.

People verify reality.

The Query Model intentionally separates humanitarian evidence from identity, allowing independent HCP implementations to assist humanitarian reunification without requiring centralized identity systems or exact matching.

Users search for people and animals.

Clients build Queries.

Nodes correlate Observations.

The Query Model embodies one of the central architectural principles of HCP:

**The protocol standardizes humanitarian semantics.**

**Queries standardize humanitarian evidence.**

**Nodes correlate observations.**

**People interpret results.**

**Reality is verified by humans.**
