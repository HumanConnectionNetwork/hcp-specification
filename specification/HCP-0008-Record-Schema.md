# HCP-0008

# Humanitarian Connection Protocol
## Record Schema

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
- HCP-0006 — Observation Model
- HCP-0007 — Status Model

---

# 1. Abstract

This specification defines the canonical structure of a Humanitarian Record.

The Record Schema establishes the minimum information required for interoperability between HCP Nodes while remaining extensible for future protocol versions.

Every Humanitarian Record exchanged through HCP shall conform to this schema.

---

# 2. Purpose

The Record Schema provides a common structure for representing humanitarian observations.

It defines how information is organized, independent of programming language, database technology or serialization format.

---

# 3. Design Principles

The schema follows these principles:

- Human-readable
- Machine-readable
- Technology independent
- Extensible
- Immutable
- Backward compatible
- Forward compatible

---

# 4. Record Structure

Every Humanitarian Record consists of six logical sections.

```text
Humanitarian Record

├── Metadata
├── Subject
├── Observation
├── Context
├── Relationships
└── Extensions
```

Each section has a specific semantic purpose.

---

# 5. Metadata

Metadata identifies the record itself.

Mandatory fields include:

- Record UUID
- Protocol Version
- Schema Version
- Node Identifier
- Record Creation Timestamp

Metadata never describes the Subject.

It describes only the Humanitarian Record.

---

# 6. Subject

The Subject section identifies the humanitarian entity being observed.

Examples include:

- Person
- Family
- Community
- Facility
- Resource
- Organization

The Subject does not receive a global identifier.

---

# 7. Observation

The Observation section describes the humanitarian event.

Typical elements include:

- Observation Type
- Observation Timestamp
- Status
- Source

Every Humanitarian Record contains exactly one Observation.

---

# 8. Context

Context provides additional humanitarian information.

Examples include:

- geographic location;
- municipality;
- shelter;
- hospital;
- disaster event;
- operational notes.

Context helps interpret the Observation without modifying its meaning.

---

# 9. Relationships

Relationships connect the Humanitarian Record with other Humanitarian Records.

Examples include:

- previous observation;
- follow-up;
- duplicate report;
- family relationship;
- correction.

Relationships preserve humanitarian history while avoiding data duplication.

---

# 10. Extensions

Extensions allow implementations to include additional structured information.

Extensions shall never modify the semantics of the HCP Core.

Unknown extensions should be preserved whenever possible.

---

# 11. Canonical JSON Structure

The conceptual structure of a Humanitarian Record is:

```json
{
  "metadata": {},
  "subject": {},
  "observation": {},
  "context": {},
  "relationships": [],
  "extensions": {}
}
```

This structure is normative.

The internal content of each section is defined by the corresponding HCP specifications.

---

# 12. Required Sections

Every Humanitarian Record shall contain:

- metadata
- subject
- observation

The following sections are optional:

- context
- relationships
- extensions

---

# 13. Schema Evolution

Future protocol versions may:

- add optional sections;
- add optional fields;
- introduce new extension namespaces.

Existing mandatory fields shall remain compatible.

---

# 14. Serialization

The canonical data model is independent of serialization.

Implementations may use:

- JSON
- CBOR
- Protocol Buffers
- YAML

JSON is the reference serialization for HCP.

---

# 15. Validation

Nodes shall validate:

- mandatory sections;
- required fields;
- schema version;
- protocol version.

Invalid records shall not be accepted.

---

# 16. Compliance

A compliant Humanitarian Record shall:

- implement the canonical schema;
- preserve immutable observations;
- preserve unknown extensions;
- satisfy required sections.

---

# 17. Summary

The Record Schema defines the canonical organization of every Humanitarian Record exchanged through HCP.

By separating Metadata, Subject, Observation, Context, Relationships and Extensions, HCP provides a stable semantic foundation capable of evolving without breaking interoperability.
