# HCP-0014

# Explainable Correlation Model

Version: 0.3 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0004 — Correlation Candidate Model
- HCP-0011 — Query Model
- HCP-0012 — Correlation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Explainable Correlation Model of the Humanitarian Connection Protocol (HCP).

The Explainable Correlation Model describes how HCP Nodes communicate the humanitarian evidence supporting a Correlation Candidate.

Rather than exposing internal algorithms or implementation details, HCP explains the humanitarian evidence that contributed to a correlation.

Explainability transforms probabilistic correlation into understandable humanitarian reasoning.

The protocol standardizes the semantic meaning of explanations.

It does not standardize correlation algorithms.

---

# 1. Introduction

Correlation assists humanitarian decision-making by identifying compatible observations.

However, a Correlation Score alone is often insufficient for people to understand why a Correlation Candidate was generated.

The Explainable Correlation Model enables HCP Nodes to communicate the humanitarian evidence supporting a candidate in a transparent and understandable manner.

Explainability improves:

- transparency;
- trust;
- human verification;
- humanitarian decision-making.

The objective of explainability is not to reveal implementation details.

Its objective is to explain the humanitarian evidence that contributed to a Correlation Candidate.

---

# 2. Purpose

The purpose of the Explainable Correlation Model is to define the semantic principles governing humanitarian explanations.

Explainability enables HCP implementations to communicate:

- why a Correlation Candidate was generated;
- which humanitarian evidence supported the correlation;
- which humanitarian evidence reduced confidence;
- how people may better interpret correlation results.

The protocol intentionally avoids prescribing explanation formats or user interface designs.

Only the semantic meaning of humanitarian explanations is standardized.

---

# 3. Design Principles

Every Explainable Correlation Model follows the fundamental architectural principles of HCP.

---

## Human Readable

Explanations should be understandable by non-technical users.

Humanitarian emergencies require explanations that people can interpret quickly.

---

## Machine Readable

Implementations are encouraged to expose structured explanation data suitable for software processing.

Different applications may present the same explanation differently.

---

## Evidence-Based

Explanations describe humanitarian evidence.

They never describe internal correlation algorithms.

---

## Transparent

Supporting and conflicting humanitarian evidence should be communicated whenever reasonably possible.

Transparent explanations improve trust and facilitate human verification.

---

## Implementation Independent

Different HCP Nodes may generate different explanations while preserving identical semantic meaning.

The protocol standardizes humanitarian evidence.

Implementations define how that evidence is explained.

---

## Optional

Explainability is strongly encouraged.

Implementations operating under constrained computational environments may provide simplified explanations whenever necessary.

---

# 4. Explainability Philosophy

Explainability exists to support people.

It does not exist to justify algorithms.

The protocol intentionally separates humanitarian evidence from implementation techniques.

Different HCP Nodes may generate Correlation Candidates using completely different algorithms while presenting similar humanitarian explanations.

The fundamental philosophy of explainability is:

**Correlation explains humanitarian evidence.**

**It does not explain algorithms.**

**People interpret the evidence.**

**Reality is verified by humans.**
---

# 5. Humanitarian Evidence

Explainability is built from the humanitarian evidence evaluated during correlation.

Rather than exposing mathematical calculations or algorithmic details, HCP communicates the humanitarian evidence that contributed to a Correlation Candidate.

Typical humanitarian evidence includes:

- Subject Type;
- Reported Label;
- Estimated Age;
- Recognition Features;
- Reported Location;
- Event Type;
- Status;
- Reported By;
- Temporal Proximity.

Future protocol versions may introduce additional forms of humanitarian evidence while preserving semantic interoperability.

---

# 6. Supporting Evidence

Supporting Evidence describes the humanitarian observations that increased the Correlation Score.

Typical examples include:

- compatible Reported Label;
- compatible Estimated Age;
- compatible Recognition Features;
- geographically compatible Reported Location;
- compatible Event Type;
- compatible Status;
- compatible reporting source;
- compatible temporal proximity.

Supporting Evidence explains why a Correlation Candidate appears plausible.

It assists people in understanding the humanitarian reasoning behind the candidate.

---

# 7. Conflicting Evidence

Conflicting Evidence describes humanitarian observations that reduce confidence without necessarily invalidating the Correlation Candidate.

Typical examples include:

- incompatible Estimated Age;
- conflicting Recognition Features;
- geographically distant observations;
- incompatible Event evolution;
- contradictory Status values;
- inconsistent temporal sequence.

Conflicting Evidence provides additional humanitarian context.

Presenting both supporting and conflicting evidence improves transparency and enables better human judgment.

---

# 8. Correlation Score and Explanation

The Correlation Score and the Explanation represent different concepts.

The Correlation Score estimates humanitarian compatibility.

The Explanation communicates the humanitarian evidence supporting that estimation.

A high Correlation Score without explanation provides limited value.

Likewise, an explanation without a Correlation Score may make prioritization more difficult.

Together, they provide both:

- quantitative estimation;
- qualitative justification.

The protocol intentionally standardizes explanation semantics rather than scoring methodologies.

---

# 9. Example

Instead of returning only a Correlation Score:

```json
{
  "score": 0.91
}
```

An HCP Node is encouraged to provide humanitarian explanations together with the score.

Illustrative example:

```json
{
  "score": 0.91,

  "explanation": {

    "supporting_evidence": [

      "Compatible Reported Label",

      "Compatible Recognition Features",

      "Compatible Reported Location",

      "Compatible Temporal Proximity"

    ],

    "conflicting_evidence": [

      "Estimated Age differs by approximately two years"

    ]
  }
}
```

Applications remain free to present this information using different user interface designs.

The protocol standardizes only the semantic meaning of the explanation.
---

# 10. Human-Friendly Presentation

The presentation of explanations remains entirely implementation-specific.

Different HCP Clients may present identical humanitarian explanations using different user experiences.

For example, an implementation may present:

```text
Why was this candidate suggested?

✓ Similar Reported Label

✓ Compatible Recognition Features

✓ Nearby Reported Location

✓ Compatible Event Type

⚠ Estimated Age differs slightly
```

Another implementation may visualize the same humanitarian evidence using icons, colors, timelines or other presentation techniques.

The protocol standardizes humanitarian meaning.

It does not standardize user interface design.

---

# 11. Artificial Intelligence Independence

The Explainable Correlation Model remains independent of the correlation algorithm used by the implementation.

Compatible HCP Nodes may generate Correlation Candidates using:

- deterministic rules;
- weighted scoring systems;
- statistical models;
- machine learning;
- artificial intelligence;
- graph-based correlation;
- hybrid approaches;
- future techniques.

Regardless of the implementation strategy, humanitarian explanations should describe the supporting humanitarian evidence rather than the internal algorithm.

This separation enables continuous innovation while preserving transparency.

---

# 12. Privacy

Humanitarian explanations should expose only the information necessary to justify a Correlation Candidate.

Implementations should avoid unnecessarily revealing sensitive personal information.

Whenever possible, explanations should prioritize humanitarian evidence over personally identifiable information.

If voluntarily disclosed personal information appears within a Humanitarian Record, implementations should reveal only the information genuinely required for humanitarian interpretation.

Additional privacy guidance is defined in:

- **HCP-0021 — Privacy and Data Minimization**

---

# 13. Interoperability

Explainability forms part of the semantic interoperability provided by HCP.

Although different HCP Nodes may generate different Correlation Candidates, every compatible implementation should communicate humanitarian explanations using the semantic principles defined by this specification.

Applications remain free to present explanations differently while preserving their humanitarian meaning.

Interoperability depends upon shared humanitarian semantics rather than identical user interfaces.

---

# 14. Relationship with Other Specifications

The Explainable Correlation Model defines how humanitarian evidence supporting a Correlation Candidate is communicated.

Complementary specifications define the remaining stages of humanitarian interoperability.

- **HCP-0004** defines the Correlation Candidate Model.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0015** defines the Result Presentation Model.

Together, these specifications define how humanitarian evidence is queried, correlated, explained and ultimately presented to people while preserving implementation independence.

---

# 15. Summary

The Explainable Correlation Model defines the semantic principles governing humanitarian explanations within HCP.

Explainability communicates humanitarian evidence.

It does not communicate correlation algorithms.

Supporting Evidence explains why a Correlation Candidate appears compatible.

Conflicting Evidence explains why uncertainty remains.

Together with the Correlation Score, humanitarian explanations enable people to better understand, evaluate and verify correlation results.

By separating humanitarian reasoning from implementation techniques, HCP allows Nodes to continuously improve their correlation algorithms while maintaining transparency and user trust.

The Explainable Correlation Model reinforces one of the central architectural principles of HCP:

**Correlation explains humanitarian evidence.**

**It does not explain algorithms.**

**People interpret the evidence.**

**Reality is verified by humans.**
