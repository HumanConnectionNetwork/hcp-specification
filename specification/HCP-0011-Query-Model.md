# HCP-0011
# Query Model

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0010 Canonical JSON Specification

---

# 1. Introduction

This document defines the Query Model used by the Humanitarian Connection Protocol (HCP).

A Query allows an HCP Node to search for Humanitarian Records that may describe the same humanitarian event.

Unlike traditional search systems, an HCP Query is not intended to perform exact matching.

Instead, it provides a collection of correlation variables that enable implementations to estimate the probability that multiple observations refer to the same real-world event.

---

# 2. Purpose

The purpose of an HCP Query is to maximize humanitarian correlation.

A query should contain as many meaningful correlation variables as are available.

Incomplete queries are expected and fully supported.

The protocol is designed to operate effectively even when only partial information is known.

---

# 3. Design Principles

Every HCP Query follows these principles.

## Correlation-Oriented

A query represents a collection of correlation variables rather than an exact search.

---

## Partial Information

Every field is optional.

Nodes SHOULD submit whatever information is available.

Unknown information MUST NOT prevent a query from being executed.

---

## Humanitarian

Queries exist to locate humanitarian observations.

They are not intended for identity verification or personal identification.

---

## Decentralized

Any HCP Node may create and submit queries.

No central authority is required.

---

# 4. Canonical Query Structure

A canonical query SHOULD follow the structure below.

```json
{
  "subject": "person",

  "event_type": "missing",

  "reported_name": "Juan Pérez",

  "estimated_age": 42,

  "recognition_features": "Blue jacket, black backpack, glasses",

  "reported_location": "Caracas",

  "status": "reported"
}
```

---

# 5. Query Variables

Every field acts as a potential correlation variable.

## subject

Defines the type of subject.

Examples:

```
person
animal
```

---

## event_type

Defines the humanitarian event being searched.

Examples:

```
missing
hospitalized
sheltered
located
```

---

## reported_name

Reported name.

Names are treated as reported observations.

They MUST NOT be interpreted as unique identifiers.

---

## estimated_age

Approximate age.

This field may be omitted if unknown.

---

## recognition_features

Observable characteristics that improve correlation.

Examples for persons:

- blue jacket
- black backpack
- glasses
- tattoo
- scar
- beard

Examples for animals:

- red collar
- white chest
- brown coat
- missing ear
- limp

This field SHOULD contain concise observable characteristics instead of narratives.

---

## reported_location

Approximate location where the observation occurred.

Examples:

- Hospital Central
- Shelter A
- Plaza Bolívar
- Highway KM 18

---

## status

Optional filter.

Implementations MAY use this field to narrow search results.

---

# 6. Correlation Model

An HCP Query does not request exact matches.

Instead, it requests probable correlations.

Implementations SHOULD evaluate the similarity between the submitted correlation variables and existing Humanitarian Records.

Correlation algorithms are implementation-specific.

The protocol intentionally does not prescribe a mandatory algorithm.

---

# 7. Correlation Variables

Typical variables include:

- reported_name
- estimated_age
- recognition_features
- reported_location
- event_type
- subject
- status
- temporal proximity

Implementations MAY consider additional variables.

---

# 8. Query Results

The protocol does not require exact matches.

Instead, implementations SHOULD return one or more Correlation Candidates.

Each candidate represents an independent Humanitarian Record that may correspond to the queried event.

Candidates SHOULD be ordered according to the implementation's confidence or probability score.

---

# 9. Confidence Scores

Implementations MAY assign a confidence score to every returned candidate.

Typical representation:

```json
{
  "probability": 0.91
}
```

The meaning of the score is implementation-specific.

The protocol only requires that higher values indicate stronger correlation.

---

# 10. Explainability

Implementations are encouraged to explain why a candidate was returned.

Examples:

- Similar reported name
- Similar estimated age
- Matching recognition features
- Nearby reported location
- Close reporting time

Providing explainable correlation improves transparency and helps users evaluate search results.

---

# 11. Incomplete Queries

Humanitarian emergencies frequently involve incomplete information.

Examples:

A family member may remember:

- only the clothing

Another may remember:

- only the hospital

Another may remember:

- only the approximate age

All these queries remain valid.

Implementations SHOULD attempt correlation using every available variable.

---

# 12. Interoperability

Every compliant HCP implementation MUST accept canonical HCP Queries.

Internal search engines may differ.

However, the semantic meaning of every query variable MUST remain consistent across all implementations.

This guarantees interoperability between independent HCP Nodes.
