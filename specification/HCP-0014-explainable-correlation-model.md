# HCP-0014

# Explainable Correlation Model

Version: 0.4 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0004 — Correlation Candidate Model
- HCP-0008 — Event Type Model
- HCP-0010 — Canonical JSON Specification
- HCP-0011 — Query Model
- HCP-0012 — Correlation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Explainable Correlation Model of the Humanitarian Connection Protocol (HCP).

The Explainable Correlation Model describes how HCP Nodes communicate humanitarian reasoning derived from humanitarian evidence.

Rather than exposing algorithms, implementation details or mathematical calculations, HCP explains the humanitarian evidence that contributed to a correlation result.

Explainability transforms humanitarian evidence into understandable humanitarian reasoning.

The protocol standardizes the semantic meaning of explanations.

It does not standardize explanation formats, user interfaces or correlation algorithms.

---

# 1. Introduction

Correlation assists humanitarian decision-making by identifying compatible humanitarian evidence.

However, a Correlation Score alone is frequently insufficient for people to understand why humanitarian evidence appears related.

The Explainable Correlation Model enables HCP Nodes to communicate humanitarian reasoning in a transparent and understandable manner.

Explainability improves:

- transparency;
- trust;
- human verification;
- humanitarian decision-making.

Its objective is not to reveal implementation techniques.

Its objective is to explain the humanitarian reasoning derived from humanitarian evidence.

---

# 2. Purpose

The purpose of the Explainable Correlation Model is to define the semantic principles governing humanitarian explanations.

Explainability enables HCP implementations to communicate:

- why humanitarian evidence appears related;
- which humanitarian evidence supports correlation;
- which humanitarian evidence reduces confidence;
- how people may better interpret humanitarian understanding.

The protocol intentionally avoids prescribing explanation formats or user interface designs.

Only the semantic meaning of humanitarian explanations is standardized.

The Explainable Correlation Model answers one fundamental question:

> **Why does this humanitarian interpretation appear reasonable?**

---

# 3. Design Principles

Every Explainable Correlation Model follows the architectural principles of HCP.

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

They never describe implementation algorithms.

---

## Transparent

Supporting and conflicting humanitarian evidence should be communicated whenever reasonably possible.

Transparency strengthens human verification.

---

## Neutral

Explanations should communicate humanitarian reasoning without suggesting certainty or verified identity.

They support interpretation.

They never replace human judgment.

---

## Implementation Independent

Different HCP Nodes may generate different explanations while preserving identical humanitarian semantics.

The protocol standardizes humanitarian evidence.

Implementations define explanations.

---

## Optional

Explainability is strongly encouraged.

Implementations operating under constrained computational environments may provide simplified explanations whenever necessary.

---

# 4. Explainability Philosophy

Explainability exists to support people.

It does not exist to justify algorithms.

The protocol intentionally separates humanitarian evidence from implementation techniques.

Different HCP Nodes may generate Correlation Candidates using completely different algorithms while communicating similar humanitarian reasoning.

The fundamental philosophy of explainability is:

**Humanitarian evidence supports reasoning.**

**Explainability communicates reasoning.**

**People interpret the evidence.**

**Reality is verified by humans.**

---

# 5. Explainability Boundaries

Explainability intentionally defines strict architectural boundaries.

Explainability never communicates:

- internal algorithms;
- probability formulas;
- implementation details;
- machine learning models;
- artificial intelligence internals;
- optimization strategies.

Explainability communicates only humanitarian reasoning derived from humanitarian evidence.

This separation preserves implementation independence while maintaining transparency.

---

# 6. Humanitarian Evidence

Explainability is constructed from the humanitarian evidence evaluated during correlation.

Rather than exposing mathematical calculations, HCP communicates the humanitarian evidence that contributed to humanitarian reasoning.

Typical humanitarian evidence includes:

- Subject Type;
- Reported Label;
- Estimated Age;
- Recognition Features;
- Event Type;
- Reported Location;
- Reporting Source;
- Temporal Proximity.

Future protocol versions may introduce additional forms of humanitarian evidence while preserving semantic interoperability.
---
# 7. Supporting Evidence

Supporting Evidence describes the humanitarian evidence that increases confidence in a humanitarian interpretation.

Supporting Evidence does not establish identity.

It explains why humanitarian evidence appears compatible.

Typical examples include:

- compatible Reported Labels;
- compatible Estimated Ages;
- compatible Recognition Features;
- geographically compatible Reported Locations;
- compatible Event Types;
- compatible Reporting Sources;
- compatible Temporal Proximity.

Supporting Evidence assists people in understanding why a humanitarian interpretation appears plausible.

---

# 8. Conflicting Evidence

Conflicting Evidence describes humanitarian evidence that reduces confidence without necessarily invalidating humanitarian compatibility.

Typical examples include:

- incompatible Estimated Ages;
- conflicting Recognition Features;
- geographically distant observations;
- incompatible Event Types;
- inconsistent Reporting Sources;
- unexpected temporal sequence.

Conflicting Evidence contributes additional humanitarian context.

Presenting both Supporting Evidence and Conflicting Evidence improves transparency and strengthens human interpretation.

---

# 9. Humanitarian Reasoning

Humanitarian reasoning emerges from the relationship between:

- Supporting Evidence;
- Conflicting Evidence;
- Correlation Score.

Conceptually:

```text
Supporting Evidence

        +

Conflicting Evidence

        +

Correlation Score

        │

        ▼

Humanitarian Reasoning

        │

        ▼

Human Understanding
```

The protocol standardizes the humanitarian meaning of this reasoning.

Implementations remain free to communicate it using different formats.

---

# 10. Correlation Score and Explanation

The Correlation Score and the Explanation represent different concepts.

The Correlation Score estimates humanitarian compatibility.

The Explanation communicates the humanitarian reasoning supporting that estimation.

Neither element should replace the other.

A Correlation Score without humanitarian reasoning provides limited transparency.

Likewise, humanitarian reasoning without a Correlation Score may reduce prioritization efficiency.

Together they provide:

- quantitative estimation;
- qualitative explanation.

The protocol standardizes explanation semantics.

It does not standardize scoring methodologies.

---

# 11. Illustrative Example

Instead of returning only a Correlation Score:

```json
{
  "score": 0.91
}
```

An HCP Node is encouraged to communicate humanitarian reasoning together with the score.

Illustrative example:

```json
{
  "score": 0.91,

  "reasoning": {

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

Applications remain free to present this humanitarian reasoning using different user experiences.

The protocol standardizes only its semantic meaning.

---

# 12. Human-Friendly Presentation

Presentation of humanitarian reasoning remains entirely implementation-specific.

Different HCP Clients may communicate identical humanitarian reasoning using different user experiences.

Illustrative example:

```text
Why was this humanitarian case suggested?

✓ Similar Reported Label

✓ Compatible Recognition Features

✓ Nearby Reported Location

✓ Compatible Event Type

⚠ Estimated Age differs slightly
```

Other implementations may present the same humanitarian reasoning using:

- icons;
- colors;
- timelines;
- accessibility adaptations;
- voice interfaces.

The protocol standardizes humanitarian meaning.

It does not standardize presentation.

Presentation is defined by **HCP-0015 — Result Presentation**.

---

# 13. Algorithm Independence

The Explainable Correlation Model remains completely independent of the correlation algorithm.

Compatible implementations may generate humanitarian reasoning using:

- deterministic rules;
- weighted scoring;
- statistical models;
- machine learning;
- artificial intelligence;
- graph analysis;
- hybrid techniques;
- future approaches.

Regardless of implementation strategy, humanitarian explanations should communicate humanitarian reasoning rather than implementation techniques.

This separation enables continuous innovation while preserving transparency.

---

# 14. Privacy

Humanitarian explanations should expose only the humanitarian evidence necessary to justify a humanitarian interpretation.

Implementations should avoid unnecessarily revealing personally identifiable information.

Whenever equivalent humanitarian value can be achieved through humanitarian observations, implementations should prioritize humanitarian evidence.

Additional privacy guidance is defined in:

- **HCP-0021 — Privacy and Data Minimization**

---

# 15. Interoperability

Explainability forms part of the semantic interoperability provided by HCP.

Although different HCP Nodes may generate different Correlation Candidates and Humanitarian Cases, compatible implementations should communicate humanitarian reasoning using the semantic principles defined by this specification.

Applications remain free to present humanitarian reasoning differently while preserving identical humanitarian meaning.

Interoperability depends upon shared humanitarian semantics rather than identical user interfaces.

---

# 16. Relationship with Other Specifications

The Explainable Correlation Model defines how humanitarian reasoning derived from humanitarian evidence is communicated.

Complementary specifications define the remaining stages of humanitarian interoperability.

```text
Query

        │

        ▼

Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Correlation Candidates

        │

        ▼

Humanitarian Reasoning

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

- **HCP-0004** defines the Correlation Candidate Model.
- **HCP-0008** defines Event Types.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines humanitarian correlation.
- **HCP-0014** defines humanitarian reasoning and explainability.
- **HCP-0015** defines Humanitarian Case presentation.

Together, these specifications define how humanitarian evidence is represented, evaluated, explained and communicated while preserving semantic interoperability and implementation independence.

---

# 17. Summary

The Explainable Correlation Model defines the semantic principles governing humanitarian explanations within HCP.

Explainability communicates humanitarian reasoning.

It never communicates algorithms.

Supporting Evidence explains why humanitarian compatibility increases.

Conflicting Evidence explains why uncertainty remains.

Together with the Correlation Score, humanitarian reasoning enables people to better understand, evaluate and verify humanitarian interpretations.

By separating humanitarian reasoning from implementation techniques, HCP enables Nodes to continuously improve their correlation algorithms while maintaining transparency, explainability and user trust.

The Explainable Correlation Model reinforces one of the central architectural principles of HCP:

**Humanitarian evidence supports reasoning.**

**Explainability communicates reasoning.**

**Humanitarian Cases communicate interpretation.**

**People verify reality.**
