# HCP-0008

# Event Type Model

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

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Event Type Model of the Humanitarian Connection Protocol (HCP).

An Event Type classifies the humanitarian event that generated an Observation.

It answers one fundamental question:

> **What happened?**

Event Types classify humanitarian observations.

They do not describe humanitarian condition.

Humanitarian condition is represented independently by the Status Model.

This separation allows HCP to distinguish the event being reported from the condition observed, improving semantic clarity, interoperability and long-term protocol evolution.

---

# 1. Introduction

Every Humanitarian Observation is created because something happened.

That humanitarian occurrence is represented by an Event Type.

An Event Type classifies the humanitarian event that generated an Observation.

It does not describe the current condition of the observed Subject.

For example:

A person may be admitted to a hospital.

The Event Type is:

```text
Hospital Admission
```

The observed Status may be:

```text
Stable
```

These represent different semantic concepts.

Separating Event Type from Status allows HCP to represent humanitarian evidence with greater precision while preserving semantic interoperability.

---

# 2. Purpose

The purpose of the Event Type Model is to standardize how humanitarian events are classified.

Rather than defining operational workflows or implementation behavior, Event Types provide a common semantic vocabulary describing what humanitarian event generated an Observation.

Event Types classify humanitarian observations.

Status describes observed humanitarian condition.

Together they provide the semantic context necessary for humanitarian interoperability, explainable correlation and Humanitarian Timeline reconstruction.

---

# 3. Design Principles

Every Event Type should preserve the following principles.

## Event-Oriented

An Event Type describes what humanitarian event occurred.

It does not describe humanitarian condition.

---

## Semantic

Event Types define humanitarian meaning.

They do not define workflows, operational procedures or implementation behavior.

---

## Subject-Aware

An Event Type should be compatible with the reported Subject Type.

Not every Event Type applies to every Subject.

---

## Language Independent

Canonical Event Type values remain language-independent.

HCP Clients may present localized translations without changing semantic meaning.

---

## Infrastructure Independent

The Event Type Model remains independent of programming languages, databases, communication technologies and software architectures.

Only semantic meaning is standardized.

---

## Extensible

Future HCP specifications may introduce additional Event Types while preserving semantic compatibility whenever reasonably possible.

---

# 4. Relationship with Subject

The interpretation of an Event Type depends on the observed Subject.

For example:

```json
{
  "subject": "human",
  "event_type": "missing_report"
}
```

represents a report that a person has been reported missing.

Whereas:

```json
{
  "subject": "animal",
  "event_type": "missing_report"
}
```

represents a report that an animal has been reported missing.

The Event Type remains semantically identical.

Only its humanitarian interpretation changes according to the Subject.

This allows HCP to reuse a common semantic vocabulary across different Subject Types while preserving interoperability.
---

# 5. Human Event Types

Human Event Types classify humanitarian events concerning individual human beings.

The following Event Types represent the core vocabulary recommended by HCP.

---

## Missing Report

A person has been reported as missing.

Typical situations include:

- family reports a disappearance;
- emergency responders receive a missing person report;
- humanitarian organizations register a missing individual.

---

## Hospital Admission

A person has been admitted to a medical facility.

This Event Type describes the admission event itself.

The observed humanitarian condition is represented separately through Status.

---

## Shelter Registration

A person has been registered at a temporary shelter or humanitarian refuge.

The Event Type represents the registration event.

Status describes the observed humanitarian condition.

---

## Rescue

A person has been rescued or recovered during a humanitarian emergency.

Examples include:

- fire department rescue;
- flood rescue;
- earthquake rescue;
- maritime rescue.

---

## Medical Evaluation

A medical assessment has been performed.

The Event Type represents the evaluation itself.

Observed medical condition belongs to Status.

---

## Transfer

A person has been transferred between humanitarian locations.

Examples include:

- hospital transfer;
- shelter transfer;
- evacuation transfer.

---

## Family Reunification

A person has been reunited with relatives or responsible caregivers.

This Event Type represents the reunification event itself.

---

## Public Emergency Report

A humanitarian observation has been reported directly by the public without belonging to another predefined Event Type.

This Event Type provides flexibility while preserving semantic interoperability.

---

# 6. Animal Event Types

Animal Event Types classify humanitarian events concerning individual animals.

Typical Event Types include:

---

## Missing Report

An animal has been reported as missing.

---

## Found Animal

An unidentified or missing animal has been found.

---

## Shelter Admission

An animal has been admitted to a temporary shelter or rescue organization.

---

## Veterinary Assistance

An animal has received veterinary evaluation or treatment.

---

## Animal Transfer

An animal has been transferred between humanitarian facilities or responsible caregivers.

---

## Animal Reunification

An animal has been reunited with its responsible family or caretaker.

Future HCP specifications may extend these vocabularies while remaining fully compatible with this semantic model.

---

# 7. Event Type and Status

Although closely related, Event Type and Status describe different aspects of an Observation.

Event Type answers:

> **What happened?**

Status answers:

> **What was the observed condition?**

Example:

```json
{
  "subject": "human",
  "event_type": "hospital_admission",
  "status": "stable"
}
```

This means:

The humanitarian event was:

```text
Hospital Admission
```

The observed humanitarian condition was:

```text
Stable
```

Another example:

```json
{
  "subject": "human",
  "event_type": "missing_report",
  "status": "missing"
}
```

The humanitarian event was:

```text
Missing Report
```

The observed humanitarian condition was:

```text
Missing
```

Keeping these concepts separate allows HCP to represent humanitarian evidence with greater semantic precision.

---

# 8. Correlation

Event Types contribute valuable humanitarian evidence during correlation.

Compatible Event Types generally increase correlation confidence.

However, correlation is not restricted to identical Event Types.

For example:

```text
Missing Report
```

may reasonably correlate with:

```text
Hospital Admission
```

or

```text
Rescue
```

when other humanitarian evidence strongly suggests that the Observations describe the same Subject.

Correlation evaluates the complete humanitarian context.

Event Type is one source of humanitarian evidence.

It is never sufficient by itself to establish identity.

The detailed Correlation Model is defined in **HCP-0004**.
---

# 9. Interoperability

Every compliant HCP Node shall exchange canonical Event Type values defined by the protocol.

User interfaces may translate Event Types into local languages or adapt their presentation without changing their semantic meaning.

Internal implementations may organize Event Types differently according to their own software architecture.

However, their humanitarian semantics shall remain consistent across all compatible HCP implementations.

The protocol standardizes humanitarian semantics.

Implementations remain free to define behavior.

Clients remain free to define presentation.

---

# 10. Relationship with Other Specifications

This document defines the semantic model used to classify humanitarian events.

Complementary specifications define other aspects of humanitarian observations.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0003** defines the Subject Model.
- **HCP-0004** defines the Correlation Model.
- **HCP-0006** defines the Observation Model.
- **HCP-0007** defines the Status Model.
- **HCP-0010** defines the Canonical HCP JSON Representation.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.

Together, these specifications define how humanitarian observations are represented, exchanged, interpreted and correlated while preserving semantic interoperability across independent HCP implementations.

---

# 11. Summary

The Event Type Model defines how humanitarian events are classified within the Humanitarian Connection Protocol.

An Event Type answers one question:

> **What happened?**

Status answers a different question:

> **What was the observed condition?**

This separation allows humanitarian observations to describe both the event that generated the Observation and the condition observed at that moment without confusing the two concepts.

Event Types classify humanitarian observations.

Status contributes humanitarian evidence.

Observations preserve humanitarian evidence.

Correlation relates compatible observations.

Humanitarian Timelines emerge from correlated observations.

People interpret the results.

People verify reality.

By separating semantic meaning from implementation behavior and human interpretation, HCP enables organizations to exchange meaningful humanitarian information without requiring centralized databases, global identity systems or shared software infrastructure.

The Event Type Model reinforces one of the fundamental principles of HCP:

**The protocol standardizes semantics.**

**Nodes correlate observations.**

**People interpret results.**

**Reality is verified by humans.**
