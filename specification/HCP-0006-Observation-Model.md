# HCP-0006

# Humanitarian Connection Protocol
## Observation Model

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-04

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Fundamental Principles
- HCP-0002 — Humanitarian Record
- HCP-0003 — Subject Model
- HCP-0004 — Person Correlation Model
- HCP-0005 — Node Architecture

---

# 1. Abstract

The Observation Model defines the humanitarian information represented by every Humanitarian Record.

Within HCP, every Humanitarian Record represents exactly one humanitarian observation.

Observations describe what was observed about a Subject at a specific moment in time.

They never represent permanent truth.

Instead, they preserve historical humanitarian facts that may later be complemented by new observations.

---

# 2. Purpose

The purpose of the Observation Model is to standardize how humanitarian situations are described.

By representing observations instead of permanent states, HCP allows multiple organizations to report independent facts without overwriting previous information.

This preserves historical integrity while enabling the reconstruction of humanitarian histories.

---

# 3. Fundamental Principle

A Humanitarian Record represents one observation.

One observation describes one Subject.

One Subject may have many observations.

Humanitarian history is reconstructed by correlating these observations.

---

# 4. Observation

An Observation is a structured description of something witnessed, reported or verified about a Subject.

Observations are always associated with:

- one Subject;
- one observation timestamp;
- one observation type;
- one reported status.

Observations never replace previous observations.

---

# 5. Observation Types

The protocol defines Observation Types as the category of humanitarian event being reported.

Examples include:

### Person

- Missing reported
- Person located
- Medical evaluation
- Hospital admission
- Shelter registration
- Family reunification
- Assistance requested
- Assistance delivered
- Transfer completed

### Facility

- Facility opened
- Facility closed
- Capacity updated
- Damage reported
- Operations resumed

### Resource

- Resource requested
- Resource delivered
- Resource depleted
- Resource replenished

### Community

- Flood reported
- Evacuation completed
- Access restored
- Communications restored

Future HCP versions may define additional Observation Types.

---

# 6. Observation Timestamp

Every Observation shall contain the date and time when the observed situation occurred.

This timestamp represents the observation itself.

It does not necessarily represent when the Humanitarian Record was created.

Example:

- Observation occurred at 10:15.
- Record created at 10:42.

Both timestamps may legitimately differ.

---

# 7. Reported Status

Every Observation reports the current humanitarian status observed at that moment.

Examples include:

- Missing
- Located
- Stable
- Critical
- Hospitalized
- Sheltered
- Evacuated
- Reunified
- Deceased

Status always reflects the observation at a specific point in time.

Future observations may report different statuses.

---

# 8. Observation Context

Observations may include contextual humanitarian information.

Examples:

- shelter;
- hospital;
- evacuation route;
- disaster area;
- municipality;
- medical unit;
- distribution center.

Context improves humanitarian understanding without changing the observation itself.

---

# 9. Observation Source

Every Observation originates from a source.

Examples include:

- Volunteer
- Family member
- Hospital
- Shelter
- Fire department
- Police
- Humanitarian organization
- Government agency
- Verified Node

The Observation Source describes who reported or generated the observation.

It does not determine whether the observation is true.

---

# 10. Independent Observations

Different organizations may independently report the same humanitarian situation.

Example:

Hospital reports:

"Person admitted."

Fire department reports:

"Person rescued."

Family reports:

"Person located."

These observations coexist.

They complement each other.

They are never merged into a single Humanitarian Record.

---

# 11. Observation Evolution

Humanitarian situations evolve through observations.

Example:

```text
Missing Reported

↓

Located

↓

Hospitalized

↓

Stable

↓

Sheltered

↓

Family Reunified
```

Each step represents a new Observation.

No previous Observation is modified.

---

# 12. Observation Integrity

Observations are immutable.

If an observation becomes outdated or incomplete, a new Humanitarian Record shall be created.

Historical observations remain available for auditing and humanitarian analysis.

---

# 13. Observation Relationships

Observations may reference previous Humanitarian Records.

Examples:

- status update;
- correction;
- follow-up;
- continuation;
- duplicate report.

Relationships preserve the continuity of humanitarian history.

---

# 14. Humanitarian History

HCP does not explicitly store humanitarian histories.

Histories emerge dynamically by correlating multiple observations referring to the same Subject.

This approach preserves decentralization while allowing increasingly complete humanitarian information.

---

# 15. Compliance

A compliant implementation shall ensure that:

- every Humanitarian Record represents exactly one Observation;
- observations remain immutable;
- observation timestamps are preserved;
- observation types follow HCP semantics;
- reported status reflects only the observed moment.

---

# 16. Summary

The Observation Model defines the semantic foundation of the Humanitarian Connection Protocol.

Rather than storing permanent states or identities, HCP stores immutable humanitarian observations.

These observations become progressively more valuable as Nodes correlate them into coherent humanitarian histories.

This model enables decentralized organizations to collaborate without losing historical integrity, while providing users with meaningful and continuously evolving humanitarian information.
