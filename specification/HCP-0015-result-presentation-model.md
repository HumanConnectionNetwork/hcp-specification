# HCP-0015

# Result Presentation Model

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0004 — Correlation Candidate Model
- HCP-0012 — Correlation Model
- HCP-0014 — Explainable Correlation Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Result Presentation Model of the Humanitarian Connection Protocol (HCP).

The Result Presentation Model describes how HCP Clients transform Correlation Candidates into Humanitarian Cases that people can understand and evaluate.

The protocol intentionally separates humanitarian interpretation from humanitarian presentation.

Correlation Candidates remain implementation objects.

Humanitarian Cases are the information presented to users.

The protocol standardizes the semantic principles governing humanitarian presentation.

It does not standardize user interface design.

---

# 1. Introduction

After an HCP Node completes correlation and explainability, the resulting humanitarian information must be communicated to people.

Families, hospitals, emergency responders and humanitarian organizations require information that is understandable, transparent and actionable.

The Result Presentation Model defines the semantic principles that guide this communication.

Rather than presenting protocol objects, implementations present Humanitarian Cases.

Each Humanitarian Case represents one implementation's interpretation of the available humanitarian evidence.

Presentation assists humanitarian understanding.

It never claims certainty.

---

# 2. Purpose

The purpose of the Result Presentation Model is to define how correlated humanitarian information should be presented to people.

Presentation transforms technical correlation results into humanitarian information suitable for human interpretation.

The Result Presentation Model enables implementations to:

- organize humanitarian evidence;
- summarize correlated observations;
- communicate uncertainty;
- explain supporting and conflicting evidence;
- facilitate humanitarian decision-making.

The protocol standardizes humanitarian meaning.

Clients remain free to define their own user experiences.

---

# 3. Design Principles

Every Result Presentation Model follows the fundamental architectural principles of HCP.

---

## Human-Centered

Presentation exists to assist people during humanitarian emergencies.

Information should remain understandable under stressful conditions.

---

## Transparent

Implementations should clearly communicate both certainty and uncertainty.

Humanitarian evidence should remain visible.

---

## Explainable

Presentation should include humanitarian explanations whenever available.

People should understand why a Humanitarian Case was generated.

---

## Non-Authoritative

A Humanitarian Case represents humanitarian interpretation.

It never represents identity verification.

---

## Implementation Independent

Different HCP Clients may present identical Humanitarian Cases using completely different user interfaces.

The protocol standardizes humanitarian meaning.

It does not standardize presentation techniques.

---

## Accessible

Presentation should remain understandable across different platforms, devices, languages and accessibility technologies whenever reasonably possible.

---

# 4. Presentation Philosophy

The Result Presentation Model exists to communicate humanitarian understanding.

It does not expose protocol internals.

Users should never need to understand Correlation Models, Canonical JSON structures or implementation details.

Instead, they should receive humanitarian information that supports informed human judgment.

The fundamental philosophy of presentation is:

**The protocol exchanges observations.**

**Nodes generate interpretations.**

**Clients present Humanitarian Cases.**

**People verify reality.**
---

# 5. Humanitarian Case

A Humanitarian Case is the human-readable representation of one Correlation Candidate.

It organizes humanitarian evidence in a form intended to assist human interpretation and decision-making.

A Humanitarian Case is not exchanged between HCP Nodes.

It is generated locally by an implementation after correlation and explainability have been completed.

Different implementations may generate different Humanitarian Cases from the same Correlation Candidate while preserving semantic interoperability.

---

# 6. Humanitarian Case Structure

The internal representation of a Humanitarian Case remains implementation-specific.

However, a Humanitarian Case should communicate, whenever reasonably available:

- Current humanitarian situation;
- Correlation Score;
- Supporting Evidence;
- Conflicting Evidence;
- Humanitarian Timeline;
- Public Contact (when permitted);
- Related Humanitarian Observations.

Illustrative representation:

```text
Humanitarian Case

├── Current Situation
├── Correlation Score
├── Supporting Evidence
├── Conflicting Evidence
├── Humanitarian Timeline
├── Public Contact
└── Related Observations
```

The protocol standardizes the humanitarian meaning of these elements.

Implementations remain free to organize and visualize them according to their users' needs.

---

# 7. Ranking

When multiple Humanitarian Cases are available, implementations should present the most relevant cases first.

Typical ranking factors include:

- Correlation Score;
- amount of Supporting Evidence;
- consistency between observations;
- temporal proximity;
- geographic proximity.

Ranking assists navigation.

It never establishes identity.

Different implementations may prioritize different humanitarian criteria while preserving semantic interoperability.

---

# 8. Humanitarian Evidence Levels

Implementations are encouraged to communicate the strength of humanitarian evidence using human-readable descriptions.

Illustrative categories include:

- Very Strong Evidence;
- Strong Evidence;
- Moderate Evidence;
- Limited Evidence;
- Insufficient Evidence.

These categories assist interpretation.

They do not represent certainty or identity verification.

Different implementations may define their own presentation terminology while preserving the underlying humanitarian meaning.

---

# 9. Multiple Humanitarian Cases

A single Query may legitimately produce multiple Humanitarian Cases.

Each Humanitarian Case represents one possible interpretation of the available humanitarian evidence.

Implementations should avoid hiding uncertainty by presenting only one candidate when multiple plausible interpretations exist.

Humanitarian emergencies frequently involve incomplete or contradictory information.

Presenting multiple Humanitarian Cases allows people to evaluate alternative humanitarian hypotheses.

---

# 10. Humanitarian Timeline

Whenever reasonably possible, a Humanitarian Case should present correlated observations in chronological order.

Illustrative example:

```text
08:20

Missing Report

        │

        ▼

10:15

Rescue

        │

        ▼

11:40

Hospital Admission

        │

        ▼

18:10

Family Reunification
```

The Humanitarian Timeline represents correlated humanitarian observations.

It does not represent verified historical fact.

Its purpose is to assist humanitarian understanding by organizing available evidence into a coherent chronological sequence.
---

# 11. Source Transparency

Whenever reasonably possible, Humanitarian Cases should identify the origin of the humanitarian observations they summarize.

Examples include:

- Hospital;
- Fire Department;
- Civil Defense;
- Humanitarian Organization;
- Volunteer;
- Family;
- Government Agency.

Source transparency improves credibility and supports human verification.

The protocol encourages transparency without prescribing presentation formats.

---

# 12. Contradictory Information

Humanitarian emergencies frequently generate contradictory observations.

Contradictory information should remain visible whenever reasonably possible.

Examples include:

- different Reported Labels;
- conflicting Status values;
- incompatible Reported Locations;
- inconsistent Recognition Features.

Presenting contradictory information enables people to better evaluate humanitarian uncertainty.

Contradictions should not be hidden simply to produce cleaner user interfaces.

---

# 13. Human Readability

Humanitarian Cases should prioritize clarity over technical completeness.

People operating during emergencies should quickly understand:

- what is currently known;
- what remains uncertain;
- why the case was presented;
- which observations contributed to the result.

Human-centered communication remains one of the primary objectives of HCP presentation.

---

# 14. Machine Readability

Although Humanitarian Cases are intended for people, implementations are encouraged to preserve machine-readable representations whenever appropriate.

Machine-readable Humanitarian Cases facilitate:

- APIs;
- SDKs;
- humanitarian dashboards;
- reporting systems;
- future interoperable clients.

Presentation formats may differ while preserving identical humanitarian meaning.

---

# 15. Accessibility

Humanitarian Cases should remain accessible across different operational environments.

Implementations are encouraged to support:

- mobile devices;
- low-bandwidth environments;
- multilingual interfaces;
- screen readers;
- printable reports;
- future accessibility technologies.

Accessibility improves humanitarian response.

It should never compromise semantic interoperability.

---

# 16. Privacy

Nodes remain responsible for determining which humanitarian information may be presented.

Implementations may omit, redact or restrict information according to:

- local legislation;
- organizational policies;
- humanitarian context;
- user permissions.

Public Contact should only be presented when:

- voluntarily provided;
- permitted by local policy;
- considered appropriate for humanitarian purposes.

Additional privacy guidance is defined in:

- **HCP-0021 — Privacy and Data Minimization**

---

# 17. Relationship with Other Specifications

The Result Presentation Model defines how humanitarian interpretations are communicated to people.

Complementary specifications define the preceding stages of humanitarian interoperability.

- **HCP-0004** defines the Correlation Candidate Model.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.
- **HCP-0014** defines the Explainable Correlation Model.

Together, these specifications define how humanitarian evidence is queried, correlated, explained and ultimately presented as Humanitarian Cases while preserving semantic interoperability and implementation independence.

---

# 18. Summary

The Result Presentation Model defines the semantic principles governing how humanitarian interpretations are presented to people.

Humanitarian Cases organize humanitarian evidence into information that supports human understanding.

Presentation communicates humanitarian meaning.

It does not expose protocol internals.

Different HCP Clients may present Humanitarian Cases using completely different user experiences while preserving the same humanitarian semantics.

The protocol exchanges Humanitarian Records.

Nodes generate humanitarian interpretations.

Clients present Humanitarian Cases.

People interpret the information.

People verify reality.

The Result Presentation Model reinforces one of the central architectural principles of HCP:

**The protocol exchanges observations.**

**Nodes generate interpretations.**

**Clients present Humanitarian Cases.**

**People verify reality.**
