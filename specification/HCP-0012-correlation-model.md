# HCP-0012

# Correlation Model

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
- HCP-0006 — Observation Model
- HCP-0007 — Status Model
- HCP-0008 — Event Type Model
- HCP-0010 — Canonical JSON Specification
- HCP-0011 — Query Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Correlation Model of the Humanitarian Connection Protocol (HCP).

The Correlation Model describes how HCP Nodes compare independent Humanitarian Records in order to identify compatible humanitarian observations.

Rather than attempting to identify people or animals directly, HCP correlates humanitarian evidence contained within independent Observations.

The result of correlation is a collection of Correlation Candidates representing probabilistic relationships between humanitarian observations.

The protocol standardizes semantic meaning.

It does not prescribe correlation algorithms.

---

# 1. Introduction

Humanitarian emergencies frequently generate multiple independent observations describing the same real-world situation.

Hospitals, volunteers, families, emergency responders and humanitarian organizations may report compatible observations without knowing they refer to the same Subject.

The Correlation Model enables HCP Nodes to evaluate those independent observations using standardized humanitarian semantics.

Correlation compares humanitarian evidence.

It never compares identities.

The purpose of correlation is to assist human interpretation.

Identity confirmation always remains a human responsibility.

---

# 2. Purpose

The purpose of the Correlation Model is to define the semantic principles governing humanitarian correlation.

The protocol intentionally avoids prescribing specific algorithms, mathematical models or implementation techniques.

Instead, it defines:

- what humanitarian evidence may be compared;
- what correlation attempts to produce;
- what correlation never guarantees;
- how correlation contributes to humanitarian interoperability.

Every compatible implementation remains free to innovate while preserving the semantic behavior defined by HCP.

---

# 3. Design Principles

Every HCP Correlation Model follows the fundamental architectural principles of HCP.

---

## Observation-Based

Correlation compares independent Observations.

It never correlates identities.

---

## Evidence-Based

Correlation evaluates multiple independent pieces of humanitarian evidence.

No individual field is sufficient to establish identity.

---

## Probabilistic

Correlation produces probabilistic compatibility.

It never produces certainty.

---

## Explainable

Correlation should be explainable whenever reasonably possible.

Users should understand why a Correlation Candidate was generated.

---

## Implementation Independent

Every HCP Node remains free to implement its own correlation strategy.

The protocol standardizes semantic meaning.

It does not standardize algorithms.

---

## Evolvable

Correlation strategies may improve continuously without requiring modifications to the protocol itself.

Future implementations may incorporate new statistical methods, artificial intelligence or other techniques while remaining semantically compatible.

---

# 4. Correlation Philosophy

The Humanitarian Connection Protocol intentionally separates humanitarian evidence from identity.

Independent observations represent humanitarian evidence.

Correlation evaluates compatibility between those observations.

The result is never identity confirmation.

Instead, correlation produces humanitarian hypotheses that assist people during humanitarian emergencies.

This distinction preserves implementation flexibility while reducing the risk of treating probabilistic relationships as verified facts.

The fundamental philosophy of HCP correlation is:

**Observations preserve humanitarian evidence.**

**Correlation relates compatible observations.**

**People interpret the results.**

**Reality is verified by humans.**
---

# 5. Humanitarian Evidence

Correlation evaluates humanitarian evidence contained within independent Humanitarian Records.

Typical evidence includes:

- Subject Type;
- Reported Label;
- Estimated Age;
- Recognition Features;
- Event Type;
- Status;
- Reported Location;
- Reported By;
- Temporal Proximity.

Different implementations may evaluate additional evidence provided that semantic compatibility is preserved.

No individual piece of humanitarian evidence is sufficient to establish identity.

Correlation emerges from the combined interpretation of multiple compatible observations.

---

# 6. Correlation Process

Although implementations remain free to define their own algorithms, the semantic correlation process follows the same conceptual stages.

```text
Humanitarian Records

        │

        ▼

Humanitarian Evidence

        │

        ▼

Compatibility Evaluation

        │

        ▼

Correlation Candidates

        │

        ▼

Humanitarian Timeline Reconstruction
```

The protocol standardizes this conceptual model.

Implementations remain free to optimize or replace every internal processing step.

---

# 7. Compatibility Evaluation

Compatibility Evaluation compares the humanitarian evidence contained within independent Humanitarian Records.

Typical comparisons include:

- similarity of Reported Labels;
- compatibility of Estimated Age;
- similarity of Recognition Features;
- geographic proximity of Reported Location;
- compatibility of Event Types;
- compatibility of Status values;
- similarity of Reported By;
- temporal proximity between Observations.

Different implementations may assign different weights to different pieces of humanitarian evidence.

The protocol intentionally leaves weighting strategies unspecified.

---

# 8. Correlation Candidates

The result of correlation is a collection of Correlation Candidates.

A Correlation Candidate represents a probabilistic relationship between independent Humanitarian Records.

A Correlation Candidate does not represent:

- identity;
- certainty;
- verification;
- ownership.

Instead, it represents humanitarian compatibility between independent observations.

Multiple Correlation Candidates may legitimately exist for the same Query.

Different implementations may return different candidates while remaining fully compliant with HCP.

---

# 9. Correlation Score

Implementations may assign a Correlation Score to every Correlation Candidate.

Example:

```json
{
  "score": 0.92
}
```

The Correlation Score represents the implementation's estimation of humanitarian compatibility.

The protocol intentionally does not define:

- mathematical formulas;
- probability models;
- machine learning techniques;
- statistical methods;
- score ranges.

Only one semantic rule is defined:

Higher Correlation Scores represent stronger humanitarian compatibility.

They never represent identity confirmation.

Correlation Scores assist human interpretation.

They never replace human verification.
---

# 10. Explainability

Correlation should be explainable whenever reasonably possible.

HCP encourages implementations to provide human-readable explanations describing why a Correlation Candidate was generated.

Typical explanations may include:

- compatible Reported Label;
- compatible Estimated Age;
- compatible Recognition Features;
- geographically compatible Reported Location;
- compatible Event Type;
- compatible Status;
- compatible reporting source;
- temporal proximity.

Explainability improves transparency and supports human interpretation.

The protocol encourages explanations without prescribing a mandatory explanation format.

---

# 11. Timeline Reconstruction

Correlation enables the dynamic reconstruction of Humanitarian Timelines.

A Humanitarian Timeline is not stored as a permanent protocol object.

Instead, it is reconstructed by organizing correlated Humanitarian Records according to their observed chronology.

Typical sequence:

```text
Missing Report

        │

        ▼

Rescue

        │

        ▼

Hospital Admission

        │

        ▼

Transfer

        │

        ▼

Shelter Registration

        │

        ▼

Family Reunification
```

The timeline represents one possible humanitarian evolution inferred from correlated observations.

It remains subject to human interpretation and verification.

Timeline presentation is defined by **HCP-0015 — Result Presentation Model**.

---

# 12. Implementation Independence

The Humanitarian Connection Protocol intentionally avoids prescribing correlation algorithms.

Compatible HCP Nodes may implement correlation using technologies such as:

- deterministic rules;
- weighted scoring systems;
- statistical models;
- machine learning;
- artificial intelligence;
- graph-based correlation;
- hybrid approaches;
- future techniques.

Regardless of implementation strategy, every compliant implementation shall preserve the semantic behavior defined by this specification.

The protocol standardizes humanitarian semantics.

Implementations standardize correlation behavior.

---

# 13. Relationship with Other Specifications

The Correlation Model defines how independent humanitarian observations are compared.

Complementary specifications define the remaining concepts involved in this process.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0004** defines the Explainable Correlation Model.
- **HCP-0006** defines the Observation Model.
- **HCP-0007** defines the Status Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0010** defines the Canonical JSON Specification.
- **HCP-0011** defines the Query Model.
- **HCP-0015** defines the Result Presentation Model.

Together, these specifications define how humanitarian evidence is represented, queried, correlated and ultimately presented to people while preserving semantic interoperability across independent HCP implementations.

---

# 14. Summary

The Correlation Model defines the semantic principles used by HCP Nodes to compare independent humanitarian observations.

Correlation compares humanitarian evidence.

It does not compare identities.

Independent Humanitarian Records remain immutable.

Correlation dynamically relates compatible observations.

The result is a collection of Correlation Candidates representing probabilistic relationships between humanitarian observations.

Correlation assists people.

It never replaces human judgment.

Humanitarian Timelines emerge from correlated observations.

People interpret the results.

People verify reality.

By separating semantic meaning from correlation algorithms, HCP enables continuous innovation without sacrificing interoperability.

The Correlation Model reinforces one of the central architectural principles of HCP:

**The protocol standardizes humanitarian semantics.**

**Correlation compares humanitarian evidence.**

**Nodes generate Correlation Candidates.**

**People interpret results.**

**Reality is verified by humans.**
