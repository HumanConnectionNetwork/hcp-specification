# HCP-0004

# Correlation Model

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
- HCP-0003 — Subject Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Correlation Model of the Humanitarian Connection Protocol (HCP).

The Correlation Model specifies how HCP Nodes evaluate independent Humanitarian Records to estimate whether they describe the same observed Subject.

Correlation is based on humanitarian evidence rather than permanent identifiers.

Its purpose is to assist humanitarian search, reunification and coordination while preserving observation independence, explainability and organizational autonomy.

The protocol does not establish identity.

It enables compatible implementations to generate explainable humanitarian hypotheses from independent observations.

---

# 1. Introduction

Humanitarian emergencies generate many independent observations concerning the same living being.

Different people and organizations may report compatible information without communicating with one another.

Examples include:

- families reporting missing relatives;
- hospitals admitting unidentified patients;
- firefighters documenting rescues;
- volunteers reporting sightings;
- citizens reporting found animals.

Each observation becomes an independent Humanitarian Record.

The role of correlation is to evaluate those observations and estimate whether they are likely to describe the same observed Subject.

Correlation therefore improves humanitarian interoperability without requiring centralized identity systems.

---

# 2. Purpose

The purpose of the Correlation Model is to support humanitarian decision-making by relating compatible observations while preserving their independence.

Correlation allows HCP implementations to:

- estimate compatible observations;
- generate Correlation Candidates;
- reconstruct humanitarian timelines;
- improve humanitarian search;
- assist family reunification;
- support explainable humanitarian decisions.

Correlation never modifies Humanitarian Records.

It only evaluates relationships between them.

---

# 3. Fundamental Principle

The Correlation Model follows one fundamental principle:

**Observations are exchanged.**

**Correlations are generated locally.**

**Identities are verified by people.**

Every Humanitarian Record represents an independent humanitarian observation.

Correlation evaluates compatibility between observations.

Human verification confirms identity whenever sufficient humanitarian evidence exists.

This separation preserves transparency, explainability and long-term interoperability.

---

# 4. Correlation Philosophy

Correlation is probabilistic.

It never represents certainty.

Its objective is not to answer:

> "Who is this?"

Its objective is to answer:

> "Which independent observations are most likely describing the same observed Subject?"

Different HCP Nodes may legitimately produce different Correlation Candidates from the same Humanitarian Records.

This variation does not reduce interoperability.

The protocol standardizes the semantic information used during correlation.

It does not prescribe a single correlation algorithm or implementation strategy.
---

# 5. Correlation Evidence

Correlation evaluates the consistency of multiple independent humanitarian observations.

Rather than relying on a single identifier, HCP combines multiple pieces of humanitarian evidence to estimate whether two or more Humanitarian Records describe the same observed Subject.

Correlation evidence may include:

- temporal proximity
- geographic proximity
- Subject Type
- humanitarian status
- event evolution
- reported name similarity
- estimated age
- reporting source
- Recognition Features
- protocol-defined metadata

No individual piece of evidence should be interpreted as proof of identity.

Correlation emerges from the combined consistency of multiple observations.

Future versions of HCP may introduce additional forms of correlation evidence while preserving interoperability.

---

# 6. Recommended Evaluation Order

The protocol does not prescribe a correlation algorithm.

However, compatible implementations are encouraged to evaluate correlation evidence using a logical progression that improves explainability.

A recommended evaluation order is:

## 1. Subject Type

Only compatible Subject Types should be correlated.

Examples:

Human ↔ Human

Animal ↔ Animal

Human ↔ Animal should never correlate.

---

## 2. Temporal Proximity

Observations occurring within compatible time windows increase confidence.

Chronologically impossible sequences should significantly reduce confidence.

---

## 3. Geographic Proximity

Observations located within compatible geographic areas increase confidence.

Observations requiring impossible travel distances within incompatible time intervals should reduce confidence.

---

## 4. Event Evolution

Compatible humanitarian transitions strengthen correlation.

Examples:

Missing

↓

Hospitalized

↓

Safe

or

Missing Animal

↓

Sheltered

↓

Reunited

---

## 5. Reported Name

Reported names may increase confidence but should never establish identity.

Implementations should tolerate:

- spelling variations
- abbreviations
- accent differences
- unknown names

Large inconsistencies should reduce confidence.

---

## 6. Estimated Age

Estimated ages should be evaluated using compatible ranges rather than exact values.

Minor estimation differences are expected during humanitarian emergencies.

---

## 7. Recognition Features

Recognition Features provide valuable observable evidence.

Examples include:

For Humans:

- clothing
- glasses
- tattoos
- scars
- backpacks
- hairstyle
- visible injuries

For Animals:

- species
- estimated breed
- estimated size
- collar
- harness
- coat color
- visible markings

Recognition Features should complement structured humanitarian information rather than replace it.

---

## 8. Reporting Source

Reporting source contributes additional confidence.

Examples include:

- Hospital
- Fire Department
- Police
- Family
- Volunteer
- Friend
- Unknown

Reporting source contributes confidence.

It never determines identity.

---

# 7. Excluded Evidence

Core HCP intentionally excludes dependence on:

- biometric identifiers
- fingerprints
- facial recognition
- DNA
- government identity systems
- centralized identity databases
- proprietary identity services

Implementations may use additional local information when permitted by applicable legislation and organizational policy.

However, HCP interoperability must never depend on those resources.

---

# 8. Correlation Candidate

The result of the correlation process is a **Correlation Candidate**.

A Correlation Candidate represents an implementation-generated humanitarian hypothesis suggesting that multiple Humanitarian Records may describe the same observed Subject.

A Correlation Candidate:

- is temporary;
- exists only inside an HCP Node;
- is generated dynamically;
- is never synchronized;
- is never assigned a protocol identifier;
- is not a protocol object.

A Correlation Candidate is an implementation artifact.

It exists to assist humanitarian decision-making.

It is never exchanged as part of HCP itself.

---

# 9. Humanitarian Timeline

When compatible observations are correlated, an HCP Node may reconstruct a Humanitarian Timeline.

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

The timeline is reconstructed from correlated Humanitarian Records.

It is not stored as a protocol object.

Different implementations may reconstruct different timelines from the same observations while remaining fully interoperable.

---

# 10. Confidence

Confidence represents compatibility between humanitarian observations.

It does not represent certainty.

Confidence may increase when:

- compatible observations accumulate;
- temporal consistency exists;
- geographic consistency exists;
- humanitarian evolution is coherent;
- Recognition Features are compatible;
- multiple independent sources provide consistent observations.

Confidence may decrease when:

- observations conflict;
- chronology is incompatible;
- locations become implausible;
- humanitarian evolution becomes inconsistent.

Confidence assists humanitarian reasoning.

It never replaces human judgment.
---

# 11. Explainability

Every Correlation Candidate should be explainable.

HCP implementations should provide users with understandable evidence supporting each suggested correlation whenever reasonably possible.

Explainability should include both:

- supporting evidence
- conflicting evidence

Typical supporting evidence may include:

- compatible observation times;
- compatible geographic locations;
- similar reported names;
- compatible estimated ages;
- compatible humanitarian status;
- matching Recognition Features;
- consistent event evolution.

Typical conflicting evidence may include:

- incompatible chronology;
- conflicting Recognition Features;
- incompatible locations;
- contradictory humanitarian status.

Explainability supports humanitarian decision-making.

It does not replace human judgment.

Transparent reasoning increases trust, facilitates verification and reduces misinformation during humanitarian emergencies.

The detailed Explainable Correlation Model is defined in **HCP-0014**.

---

# 12. Conflicting Observations

Conflicting observations do not invalidate Humanitarian Records.

Every Humanitarian Record should remain preserved exactly as originally reported.

Correlation evaluates relationships between observations.

It never modifies or replaces the original observations.

Conflicting information is expected during humanitarian emergencies.

Preserving those observations improves transparency and allows future humanitarian evidence to clarify uncertainty.

Observation independence remains one of the core principles of HCP.

---

# 13. Local Correlation Implementation

Correlation belongs entirely to the HCP Node.

The protocol intentionally avoids prescribing a specific correlation implementation.

Compatible HCP Nodes may implement correlation using techniques such as:

- heuristic rules;
- probabilistic models;
- statistical inference;
- machine learning;
- artificial intelligence;
- expert systems;
- future compatible methods.

These implementation details remain local.

They do not affect protocol interoperability.

HCP standardizes the humanitarian evidence exchanged between implementations.

It does not standardize how that evidence is evaluated.

---

# 14. Privacy

Correlation should evaluate only the humanitarian information necessary to support humanitarian assistance.

Whenever possible, implementations should prioritize observation-based evidence over permanent personal identifiers.

The objective of correlation is humanitarian coordination.

It must never become a centralized identity system.

The protocol preserves humanitarian usefulness while minimizing unnecessary exposure of personal information.

Additional privacy requirements are defined in:

- **HCP-0021 — Privacy and Data Minimization**

---

# 15. Compliance

A compliant implementation should:

- preserve Humanitarian Records unchanged;
- preserve observation independence;
- treat correlation as probabilistic;
- generate Correlation Candidates dynamically;
- expose explainable correlation whenever reasonably possible;
- preserve historical observations;
- avoid permanent subject identifiers;
- avoid dependence on centralized identity systems.

Compliance concerns protocol behavior.

It does not prescribe implementation techniques.

---

# 16. Summary

The Correlation Model enables HCP Nodes to transform independent Humanitarian Records into explainable humanitarian hypotheses.

Humanitarian Records preserve observations.

Correlation Candidates estimate relationships between observations.

Human verification confirms identity.

This separation allows independent organizations to cooperate without requiring centralized databases, shared infrastructure or global identity systems.

By standardizing humanitarian evidence rather than correlation algorithms, HCP enables increasingly intelligent implementations while preserving long-term interoperability.

The Correlation Model is the semantic bridge that transforms independent humanitarian observations into meaningful humanitarian understanding.
