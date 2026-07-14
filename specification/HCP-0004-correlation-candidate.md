# HCP-0004

# Correlation Candidate Model

Version: 0.3 (Draft)

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
- HCP-0012 — Correlation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Correlation Candidate Model of the Humanitarian Connection Protocol (HCP).

A Correlation Candidate is a temporary implementation object generated locally by an HCP Node after evaluating humanitarian evidence contained within independent Humanitarian Records.

A Correlation Candidate represents one possible interpretation of compatible humanitarian evidence.

It is not a protocol object.

It is never synchronized.

It is never exchanged between Nodes.

Instead, it assists local humanitarian interpretation by organizing related observations before they are presented to users.

The protocol standardizes the semantic role of Correlation Candidates.

It does not standardize how implementations generate them.

---

# 1. Introduction

Humanitarian emergencies frequently generate multiple independent Humanitarian Records that may describe the same observed Subject.

After evaluating the available humanitarian evidence, an HCP Node may determine that some Humanitarian Records appear sufficiently compatible to justify further interpretation.

Rather than modifying those Humanitarian Records, the Node may generate a Correlation Candidate.

A Correlation Candidate represents the Node's current interpretation of compatible humanitarian evidence.

It exists only inside the implementation that generated it.

The protocol never exchanges Correlation Candidates.

Only Humanitarian Records are exchanged.

Different HCP Nodes may generate different Correlation Candidates from exactly the same Humanitarian Records.

This behavior is expected because interpretation always remains local.

---

# 2. Purpose

The purpose of the Correlation Candidate Model is to define the semantic role of Correlation Candidates within HCP.

Correlation Candidates allow implementations to:

- organize compatible Humanitarian Records;
- summarize humanitarian evidence;
- support explainable correlation;
- reconstruct humanitarian timelines;
- prepare information for local presentation.

Correlation Candidates never replace Humanitarian Records.

They simply represent one possible local interpretation of compatible humanitarian evidence.

Humanitarian evidence is exchanged.

Correlation Candidates organize that evidence.

Humanitarian Cases communicate the resulting interpretation.

---

# 3. Design Principles

Every Correlation Candidate follows the architectural principles of HCP.

## Temporary

Correlation Candidates exist only while humanitarian evidence is being evaluated or presented.

They are reconstructed whenever humanitarian evidence changes.

They are never synchronized between Nodes.

---

## Evidence-Oriented

Correlation Candidates organize humanitarian evidence.

They do not replace or modify Humanitarian Records.

---

## Explainable

Every Correlation Candidate should be explainable whenever reasonably possible.

Supporting and conflicting humanitarian evidence should remain available for human interpretation.

---

## Dynamic

Correlation Candidates reflect the current interpretation of available humanitarian evidence.

Different Nodes may continuously reconstruct them as new Humanitarian Records become available.

---

## Implementation Independent

The protocol does not prescribe how Correlation Candidates are internally represented.

Every implementation remains free to choose its own internal data structures and algorithms.

Only their semantic role is standardized.

---

# 4. Correlation Candidate Philosophy

A Correlation Candidate is not a humanitarian fact.

It is not a verified identity.

It is not a Humanitarian Case.

It is a temporary humanitarian hypothesis generated from compatible Humanitarian Records.

Its purpose is to assist humanitarian reasoning by reducing the amount of evidence requiring manual evaluation.

Correlation Candidates support people.

They never replace people.

Their existence reflects one of the fundamental architectural principles of HCP:

**Humanitarian Records preserve observations.**

**Correlation Candidates organize humanitarian evidence.**

**Humanitarian Cases communicate local interpretation.**

**Human verification determines reality.**

---

# 5. Relationship with Humanitarian Cases

Correlation Candidates and Humanitarian Cases have different responsibilities.

A Correlation Candidate is an internal implementation object.

A Humanitarian Case is a presentation object intended for human interpretation.

One or more Correlation Candidates may contribute to a Humanitarian Case depending on implementation design.

The protocol intentionally leaves this relationship implementation-specific.

Correlation Candidates belong to local processing.

Humanitarian Cases belong to local presentation.

Neither object is exchanged between HCP Nodes.
---
# 6. Correlation Candidate Structure

The internal structure of a Correlation Candidate is entirely implementation-specific.

The protocol does not prescribe any data structure, class hierarchy or storage model.

Conceptually, however, a Correlation Candidate is expected to organize humanitarian evidence such as:

- associated Humanitarian Records;
- Correlation Score;
- Supporting Evidence;
- Conflicting Evidence;
- optional Humanitarian Timeline.

Illustrative representation:

```text
Correlation Candidate

├── Humanitarian Records
├── Correlation Score
├── Supporting Evidence
├── Conflicting Evidence
└── Humanitarian Timeline
```

Implementations remain free to organize this information using any internal representation.

The protocol standardizes only the semantic purpose of each element.

---

# 7. Associated Humanitarian Records

Every Correlation Candidate references one or more independent Humanitarian Records.

Those Humanitarian Records remain immutable.

Correlation never modifies them.

Instead, the Correlation Candidate organizes existing humanitarian evidence for local interpretation.

Illustrative example:

```text
Correlation Candidate

├── Humanitarian Record A
├── Humanitarian Record B
└── Humanitarian Record C
```

Each Humanitarian Record preserves its original humanitarian observation exactly as reported.

The Correlation Candidate simply evaluates their semantic compatibility.

---

# 8. Correlation Score

A Correlation Candidate may include a Correlation Score representing the implementation's estimation of humanitarian compatibility.

The Correlation Score is entirely implementation-specific.

The protocol does not prescribe scoring algorithms, numerical ranges or weighting strategies.

Its purpose is to assist:

- result ranking;
- humanitarian interpretation;
- explainable correlation.

A Correlation Score does not:

- establish identity;
- guarantee correctness;
- replace human verification.

Different implementations may use completely different scoring models while remaining semantically interoperable.

---

# 9. Supporting Evidence

Supporting Evidence represents the humanitarian observations that increase confidence in a Correlation Candidate.

Typical examples include:

- compatible Reported Labels;
- compatible estimated ages;
- compatible Recognition Features;
- compatible reported locations;
- compatible Event Types;
- compatible reporting sources;
- compatible chronology.

Supporting Evidence improves explainability.

It helps people understand why Humanitarian Records appear related.

---

# 10. Conflicting Evidence

Conflicting Evidence represents humanitarian observations that reduce confidence in a Correlation Candidate.

Examples include:

- incompatible chronology;
- conflicting Recognition Features;
- geographically incompatible observations;
- incompatible Event Types;
- contradictory humanitarian status.

Conflicting Evidence should not automatically invalidate a Correlation Candidate.

Instead, it provides additional context supporting transparent human interpretation.

Explainable correlation should expose both Supporting Evidence and Conflicting Evidence whenever reasonably possible.

---

# 11. Humanitarian Timeline

A Correlation Candidate may organize its associated Humanitarian Records into a Humanitarian Timeline.

The timeline is reconstructed dynamically by arranging observations according to their chronological relationship.

Illustrative example:

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

Family Reunification
```

Humanitarian Timelines are implementation objects.

They are reconstructed whenever humanitarian evidence changes.

They are never synchronized between Nodes.

Presentation of Humanitarian Timelines belongs to **HCP-0015 — Result Presentation**.

---

# 12. Privacy

Correlation Candidates should contain only the humanitarian information necessary to support local interpretation.

They should never become permanent identity profiles.

Whenever equivalent humanitarian value can be achieved through humanitarian observations, implementations should prioritize humanitarian evidence over personally identifiable information.

Any personal information contained within Humanitarian Records remains humanitarian evidence.

It never becomes protocol identity.

Additional privacy guidance is defined in:

- **HCP-0021 — Privacy and Data Minimization**

---

# 13. Relationship with Other Specifications

This document defines the semantic role of Correlation Candidates.

Complementary specifications define the remaining stages of humanitarian interoperability.

```text
HCP-0001
Humanitarian Record
        │
        ▼
HCP-0012
Correlation Model
        │
        ▼
HCP-0004
Correlation Candidate
        │
        ▼
HCP-0015
Result Presentation
        │
        ▼
Humanitarian Case
```

Each specification has a distinct responsibility.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0012** defines the correlation process.
- **HCP-0004** defines the Correlation Candidate.
- **HCP-0014** defines explainable correlation.
- **HCP-0015** defines the presentation of Humanitarian Cases.

Together, these specifications separate humanitarian evidence from local interpretation while preserving semantic interoperability.

---

# 14. Summary

The Correlation Candidate Model defines the semantic role of Correlation Candidates within the Humanitarian Connection Protocol.

Correlation Candidates are temporary implementation objects.

They are generated locally by HCP Nodes.

They organize compatible humanitarian evidence.

They assist explainable correlation.

They are never synchronized.

They are never exchanged between Nodes.

Humanitarian Records preserve observations.

Correlation Candidates organize humanitarian evidence.

Humanitarian Cases communicate local interpretation.

People verify reality.

By separating humanitarian evidence from local interpretation, HCP enables independent implementations to continuously improve correlation quality without modifying exchanged Humanitarian Records or compromising semantic interoperability.
