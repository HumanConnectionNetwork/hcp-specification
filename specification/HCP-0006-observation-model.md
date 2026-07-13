# HCP-0006

# Observation Model

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
- HCP-0004 — Correlation Model
- HCP-0005 — Node Communication Protocol

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Observation Model of the Humanitarian Connection Protocol (HCP).

An Observation represents structured humanitarian evidence describing what was observed about a Subject at a specific moment in time.

Observations describe what was observed.

They do not describe permanent truth.

Each Observation becomes an independent Humanitarian Record that may later be exchanged, correlated and incorporated into a reconstructed Humanitarian Timeline.

This document establishes the semantic model upon which humanitarian evidence is represented throughout the protocol.

---

# 1. Introduction

Every Humanitarian Record represents exactly one humanitarian observation.

An Observation records humanitarian evidence concerning one observed Subject at a particular moment in time.

Rather than describing permanent states, observations preserve what was known when the observation was made.

As humanitarian situations evolve, additional observations may complement previous ones without modifying or replacing them.

Independent observations remain preserved throughout the protocol.

Compatible HCP implementations may later correlate those observations to reconstruct an increasingly complete Humanitarian Timeline.

---

# 2. Purpose

The purpose of the Observation Model is to standardize how humanitarian evidence is represented.

Instead of exchanging permanent states or centralized identity records, HCP exchanges independent observations.

This approach allows multiple organizations to describe the same humanitarian reality while preserving observation independence, explainability and long-term interoperability.

Humanitarian Timelines emerge dynamically through correlation rather than through modification of previous observations.

---

# 3. Fundamental Principle

The Observation Model follows one fundamental principle.

Every Humanitarian Record represents one Observation.

One Observation describes one Subject.

One Subject may be represented by many independent Observations.

Observations preserve humanitarian evidence.

Correlation reconstructs Humanitarian Timelines.

People verify identities.

This separation preserves transparency, explainability and organizational autonomy throughout the protocol.

---

# 4. Observation

An Observation is structured humanitarian evidence describing something witnessed, reported or documented concerning an observed Subject.

Every Observation represents information available at a specific moment in time.

An Observation should include:

- one Subject;
- one observation timestamp;
- one observation type;
- one reported status.

Observations are immutable.

Once recorded, they should never be modified.

If humanitarian circumstances evolve, a new Observation should be created instead.

This approach preserves historical integrity while allowing progressively richer humanitarian understanding through explainable correlation.
---

# 5. Observation Types

An Observation Type describes the humanitarian situation being reported.

Observation Types provide semantic meaning to humanitarian evidence.

They classify what was observed.

They do not prescribe humanitarian workflows or operational procedures.

Future HCP versions may introduce additional Observation Types while preserving backward compatibility whenever reasonably possible.

The current core specification defines Observation Types for the following Subject Types.

---

## Human

Typical human observations include:

- Missing Reported
- Located
- Hospitalized
- Sheltered
- Transferred
- Medical Assistance
- Emergency Assistance
- Safe
- Reunified

These Observation Types describe humanitarian situations concerning individual human beings.

---

## Animal

Typical animal observations include:

- Missing Reported
- Found
- Sheltered
- Veterinary Assistance
- Safe
- Reunited

These Observation Types describe humanitarian situations concerning individual animals affected by humanitarian emergencies.

Future protocol versions may define additional subject-specific observation vocabularies while remaining fully compatible with this model.

---

# 6. Observation Timestamp

Every Observation shall contain the date and time when the observed situation occurred.

The Observation Timestamp represents when the humanitarian evidence was observed.

It does not necessarily represent when the Humanitarian Record was created.

Example:

Observation occurred:

```text
10:15
```

Humanitarian Record created:

```text
10:42
```

Both timestamps are valid.

Maintaining this distinction preserves historical accuracy and improves future correlation.

---

# 7. Reported Status

Every Observation reports the humanitarian status observed at that specific moment.

Examples include:

- Missing
- Located
- Hospitalized
- Sheltered
- Stable
- Critical
- Safe
- Reunified

For animals:

- Missing
- Found
- Sheltered
- Receiving Care
- Reunited

Reported Status reflects only the observed moment.

It never represents the complete Humanitarian Timeline.

Future Observations may legitimately report different statuses for the same Subject.

---

# 8. Observation Context

Observations may include contextual humanitarian information that improves interpretation without changing the Observation itself.

Typical contextual information includes:

- hospital
- temporary shelter
- municipality
- disaster area
- evacuation route
- emergency zone
- geographic reference

Observation Context contributes humanitarian understanding.

It is not part of the Subject.

It does not establish identity.

---

# 9. Observation Source

Every Observation originates from a reporting source.

Examples include:

- Family
- Friend
- Volunteer
- Hospital
- Fire Department
- Police
- Humanitarian Organization
- Government Agency
- Verified HCP Node

Observation Source describes where humanitarian evidence originated.

It contributes humanitarian context and confidence.

It does not determine whether the Observation is true.

---

# 10. Independent Observations

Different organizations may independently report compatible humanitarian evidence concerning the same Subject.

Example:

Hospital reports:

```text
Person admitted.
```

Fire Department reports:

```text
Person rescued.
```

Family reports:

```text
Person located.
```

Each Observation remains independently valid.

The protocol never merges Observations.

Compatible HCP implementations may later correlate them to reconstruct a more complete Humanitarian Timeline.

Observation independence remains one of the fundamental principles of HCP.
---

# 11. Observation Evolution

Humanitarian situations evolve through successive independent Observations.

Each new Observation contributes additional humanitarian evidence.

Previous Observations remain unchanged.

Example:

```text
Missing Reported

        │

        ▼

Located

        │

        ▼

Hospitalized

        │

        ▼

Stable

        │

        ▼

Sheltered

        │

        ▼

Reunified
```

Each step represents a new Humanitarian Record.

The protocol preserves every Observation exactly as originally reported.

Humanitarian evolution emerges from the relationship between multiple Observations rather than from modifying previous ones.

---

# 12. Observation Integrity

Observations are immutable.

Once a Humanitarian Record has been created, its Observation should never be modified.

If new humanitarian evidence becomes available, a new Humanitarian Record should be created instead.

This principle preserves:

- historical integrity;
- auditability;
- explainability;
- observation independence;
- long-term interoperability.

Immutable observations provide a trustworthy historical foundation for humanitarian decision-making.

---

# 13. Observation Relationships

An Observation may reference one or more related Humanitarian Records.

These relationships improve humanitarian understanding without altering the original observations.

Typical relationships include:

- follow-up observation;
- status update;
- continuation;
- duplicate report;
- correction.

Observation relationships provide contextual continuity.

They never replace or merge Humanitarian Records.

Every Observation remains independently valid.

---

# 14. Humanitarian Timeline

HCP does not explicitly store Humanitarian Timelines.

Timelines are reconstructed dynamically by correlating compatible Observations referring to the same Subject.

Example:

```text
12 Aug

Missing Reported

        │

        ▼

13 Aug

Hospitalized

        │

        ▼

15 Aug

Transferred

        │

        ▼

18 Aug

Safe
```

Different HCP Nodes may reconstruct different Humanitarian Timelines from the same Humanitarian Records depending on their locally implemented correlation strategies.

This flexibility preserves implementation independence while maintaining semantic interoperability.

---

# 15. Compliance

A compliant implementation should:

- represent exactly one Observation per Humanitarian Record;
- preserve Observation immutability;
- preserve Observation independence;
- preserve Observation Timestamps;
- represent Observation Types according to HCP semantics;
- preserve Reported Status exactly as observed;
- reconstruct Humanitarian Timelines without modifying previous Observations.

Compliance concerns semantic protocol behavior.

It does not prescribe implementation techniques or internal software architecture.

---

# 16. Summary

The Observation Model defines how humanitarian evidence is represented throughout the Humanitarian Connection Protocol.

An Observation is structured humanitarian evidence concerning one observed Subject at a specific moment in time.

Observations preserve humanitarian evidence.

Correlation reconstructs Humanitarian Timelines.

People verify identities.

This separation allows independent organizations to exchange humanitarian information while preserving historical integrity, explainability and organizational autonomy.

Rather than storing permanent states or centralized identities, HCP preserves immutable humanitarian observations that become increasingly valuable as compatible implementations reconstruct meaningful Humanitarian Timelines.

The Observation Model provides the semantic foundation upon which Humanitarian Records, correlation and humanitarian interoperability are built.
