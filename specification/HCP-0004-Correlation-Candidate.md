# HCP-0004

# Correlation Model

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0000 Overview
- HCP-0001 Humanitarian Record
- HCP-0002 HCP Node

---

# 1. Abstract

The Correlation Model defines how HCP Nodes estimate whether multiple Humanitarian Records may describe the same humanitarian subject.

A humanitarian subject is any living being observed during a humanitarian situation.

Supported subject types include:

- Human
- Animal

Correlation transforms multiple independent observations into explainable humanitarian hypotheses.

It never creates or assigns a global identity.

---

# 2. Purpose

Humanitarian emergencies generate fragmented observations.

A living being may be observed by:

- Family
- Hospital
- Fire Department
- Police
- Volunteers
- Community members

Each observation becomes an independent Humanitarian Record.

The purpose of correlation is to estimate which observations are likely to describe the same humanitarian subject.

---

# 3. Fundamental Principle

HCP stores observations.

HCP does not store identities.

A Humanitarian Record represents one observation.

A humanitarian subject is inferred through the correlation of multiple observations.

Therefore:

- Humanitarian Records are exchanged.
- Correlation Candidates are generated locally.
- Humanitarian Cases are presented to users.

Identity verification always remains a human responsibility.

---

# 4. Correlation Philosophy

Correlation is probabilistic.

It never represents certainty.

The objective is not to answer:

"Who is this?"

The objective is to answer:

"Which observations are likely describing the same humanitarian event involving the same living being?"

Different Nodes may produce different results while remaining fully compliant with HCP.

---

# 5. Correlation Signals

Correlation should evaluate multiple compatible observations.

Recommended signals include:

- Temporal proximity
- Geographic proximity
- Subject type
- Event evolution
- Reported name similarity
- Estimated age
- Source
- Description
- Observable characteristics
- Humanitarian status

Future versions may introduce additional correlation signals while preserving interoperability.

---

# 6. Correlation Priority

Not every signal has the same importance.

Recommended evaluation order:

## 1. Time

Observations occurring within compatible time windows receive higher correlation.

Impossible chronological sequences reduce confidence.

---

## 2. Geographic Proximity

Nearby observations receive higher correlation.

Observations separated by impossible travel distances within short time intervals should significantly reduce confidence.

---

## 3. Subject Type

Only compatible subject types should be correlated.

Examples:

Human ↔ Human

Animal ↔ Animal

Human ↔ Animal should never correlate.

---

## 4. Reported Name

Reported names increase confidence but never determine identity.

Nodes should tolerate:

- spelling variations
- accent differences
- abbreviations
- unknown names

Large name differences reduce confidence.

---

## 5. Estimated Age

Estimated age should be evaluated using compatible ranges.

Small differences are acceptable.

Large differences reduce confidence.

---

## 6. Event Evolution

Compatible humanitarian transitions increase confidence.

Examples:

Missing

↓

Hospitalized

↓

Safe

or

Missing Animal

↓

Sheltered Animal

↓

Reunited

---

## 7. Source

Institutional observations may contribute additional confidence.

Examples:

Hospital

Fire Department

Police

Family

Volunteer

Friend

Unknown

---

## 8. Description

Descriptions may contain observable characteristics useful for correlation.

Examples:

Humans

- clothing
- shoes
- backpack
- glasses
- injuries

Animals

- species
- estimated breed
- estimated size
- collar
- harness
- fur color

Descriptions should complement structured information.

---

# 7. Excluded Signals

Core HCP intentionally excludes:

- biometric identifiers
- fingerprints
- facial recognition
- DNA
- government identifiers
- centralized identity databases

Applications remain free to use additional local information, but protocol interoperability must never depend on these resources.

---

# 8. Correlation Candidate

The output of the correlation process is a Correlation Candidate.

A Correlation Candidate:

- is temporary;
- exists only inside a Node;
- is never synchronized;
- is never globally unique;
- is never part of the HCP protocol.

It represents a humanitarian hypothesis generated from compatible observations.

---

# 9. Humanitarian Timeline

When multiple compatible observations are correlated, Nodes may reconstruct a Humanitarian Timeline.

Example:

```text
12 Aug

Missing

↓

13 Aug

Hospitalized

↓

15 Aug

Transferred

↓

18 Aug

Safe
```

Timelines are generated dynamically.

They are never synchronized between Nodes.

---

# 10. Confidence

Confidence expresses compatibility.

It does not express certainty.

Confidence may increase when:

- compatible observations accumulate;
- temporal consistency exists;
- geographic consistency exists;
- event evolution is coherent;
- institutional observations exist.

Confidence may decrease when observations conflict.

---

# 11. Explainability

Every Correlation Candidate should be explainable.

Clients should expose why a candidate was suggested.

Example:

✓ Compatible reporting time

✓ Same geographic area

✓ Similar reported name

✓ Compatible estimated age

✓ Compatible event evolution

✗ Different source

Explainability improves trust and transparency.

---

# 12. Conflicting Observations

Conflicting observations do not invalidate Humanitarian Records.

Every observation should remain preserved.

The correlation engine evaluates conflicts without modifying the original observations.

Historical uncertainty is expected during humanitarian emergencies.

---

# 13. Local Intelligence

Correlation belongs exclusively to the Node.

Each implementation may improve its own correlation engine using:

- probabilistic models
- artificial intelligence
- statistical inference
- machine learning
- custom heuristics

These implementation details never affect HCP interoperability.

---

# 14. Privacy

Correlation should use only the minimum humanitarian information necessary.

Its purpose is humanitarian assistance.

It must never become a centralized identity system.

The protocol prioritizes observations over identities.

---

# 15. Compliance

A compliant implementation shall:

- preserve Humanitarian Records unchanged;
- treat correlation as probabilistic;
- generate Correlation Candidates dynamically;
- expose explainable results;
- preserve observation history;
- avoid global subject identifiers.

---

# 16. Summary

The Correlation Model enables HCP Nodes to transform independent Humanitarian Records into explainable Correlation Candidates.

Correlation does not identify living beings.

It estimates compatible humanitarian observations.

Humanitarian Records remain immutable.

Correlation Candidates remain local.

Humanitarian Cases remain human-readable.

This separation preserves decentralization while allowing increasingly intelligent humanitarian search across independent HCP implementations.
