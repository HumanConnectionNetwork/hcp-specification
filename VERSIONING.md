# HCP Versioning

Version: 0.1 (Draft)

Status: Informational

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-14

---

# Introduction

This document describes the versioning strategy used by the Humanitarian Connection Protocol (HCP).

Its purpose is to define how the protocol evolves while preserving interoperability between independent implementations.

Unlike the HCP Specifications, this document is informational.

It explains how protocol versions are managed.

It does not define protocol behavior.

---

# Versioning Philosophy

HCP is designed as a long-lived interoperability standard.

Protocol evolution should favor stability over frequent change.

Whenever reasonably possible:

* existing implementations should continue working;
* protocol semantics should remain stable;
* backward compatibility should be preserved;
* unnecessary breaking changes should be avoided.

Protocol evolution should improve interoperability rather than disrupt it.

---

# Independent Versioning

Different parts of HCP may evolve independently.

Illustrative examples include:

* HCP Specification;
* Canonical JSON;
* JSON Schemas;
* Reference Documentation;
* Examples;
* Reference Implementations.

These components may have different release cycles.

They remain coordinated through documented compatibility.

---

# Specification Version

The HCP Specification represents the normative definition of the protocol.

Illustrative versions:

```text
0.1 Draft

0.2 Draft

0.5 Candidate

1.0 Stable
```

Specification versions describe the evolution of protocol semantics.

---

# Canonical JSON Version

The Canonical JSON Specification evolves independently from the overall protocol.

Illustrative versions:

```text
0.5

0.6

1.0
```

Humanitarian Records declare the Canonical JSON version using:

```json
{
  "schema_version": "0.5"
}
```

Implementations should validate records using the corresponding schema version.

---

# JSON Schema Version

Each Canonical JSON version has matching JSON Schemas.

Illustrative mapping:

| Canonical JSON | JSON Schema            |
| -------------- | ---------------------- |
| 0.5            | hcp-record.schema.json |
| 0.6            | hcp-record.schema.json |
| 1.0            | hcp-record.schema.json |

Schema versions follow Canonical JSON.

They do not redefine protocol semantics.

---

# Reference Documentation

Reference documentation evolves independently.

Updates may include:

* clearer explanations;
* additional examples;
* editorial improvements;
* implementation guidance.

Editorial changes do not modify protocol behavior.

---

# Examples

Examples may evolve independently.

New examples may be added without modifying the protocol.

Existing examples may be improved for clarity while preserving their humanitarian meaning.

Examples are informative.

They are not normative.

---

# Reference Implementations

Reference implementations evolve independently from the protocol.

Examples include:

* hcp-reference;
* hcp-client-telegram;
* hcp-node-web.

Reference implementations demonstrate HCP.

They do not define HCP.

---

# Backward Compatibility

Backward compatibility is a primary design objective.

Whenever reasonably possible:

* existing Humanitarian Records should remain valid;
* previous Canonical JSON versions should remain understandable;
* older implementations should continue exchanging humanitarian observations.

Breaking compatibility should occur only when absolutely necessary.

---

# Forward Compatibility

HCP encourages forward compatibility.

Illustrative examples include:

* preserving unknown optional fields;
* accepting unknown Event Types when structurally valid;
* ignoring unsupported optional extensions;
* preserving semantic meaning whenever technically possible.

Forward compatibility reduces fragmentation.

---

# Breaking Changes

A breaking change is one that prevents previously conformant implementations from remaining interoperable.

Illustrative examples include:

* changing required field names;
* changing field semantics;
* changing identifier meaning;
* removing mandatory protocol behavior.

Breaking changes should be extremely rare.

Whenever possible, migration paths should be documented before adoption.

---

# Non-Breaking Changes

Illustrative non-breaking changes include:

* editorial improvements;
* documentation clarification;
* additional examples;
* new optional properties;
* new optional Event Types;
* additional reference implementations.

These changes preserve interoperability.

---

# Deprecation

Deprecated protocol elements should remain documented whenever reasonably possible.

Deprecation should include:

* reason;
* replacement;
* migration guidance;
* expected removal timeline when applicable.

Deprecated elements should not disappear without notice.

---

# Migration

When migration becomes necessary, implementations should receive clear guidance.

Migration documentation should explain:

* what changed;
* why it changed;
* compatibility implications;
* recommended migration strategy.

Migration should preserve humanitarian information whenever technically possible.

---

# Version Identification

Implementations should clearly identify the protocol versions they support.

Illustrative example:

```text
Supported HCP Specification:

0.1 Draft

Supported Canonical JSON:

0.5

Supported Schemas:

hcp-record.schema.json
query.schema.json
humanitarian-case.schema.json
```

Version transparency improves interoperability.

---

# Semantic Stability

The humanitarian meaning of standardized concepts should remain stable.

Illustrative concepts include:

* Humanitarian Record;
* Humanitarian Observation;
* Query;
* Correlation;
* Humanitarian Case;
* Synchronization;
* Human Verification.

Terminology should not change without compelling humanitarian justification.

---

# Release Stages

Illustrative protocol maturity stages include:

| Stage      | Meaning                           |
| ---------- | --------------------------------- |
| Draft      | Active development                |
| Candidate  | Feature-complete, awaiting review |
| Stable     | Recommended for production use    |
| Deprecated | Scheduled for replacement         |
| Archived   | No longer maintained              |

These stages communicate protocol maturity.

---

# Community Review

Major protocol versions should be reviewed through the open HCP community.

Illustrative review sources include:

* implementation feedback;
* interoperability testing;
* specification review;
* humanitarian organizations;
* technical contributors.

Protocol evolution should prioritize practical interoperability.

---

# Relationship with Conformance

Conformance is always evaluated against a specific protocol version.

Illustrative relationship:

```text
Specification Version

        │

        ▼

Canonical JSON Version

        │

        ▼

JSON Schema Version

        │

        ▼

Conformance Evaluation
```

Implementations should clearly identify the versions against which they claim compatibility.

---

# Relationship with the Roadmap

The roadmap describes future protocol evolution.

Versioning describes how that evolution is managed.

```text
Roadmap

        │

        ▼

Development

        │

        ▼

Versioning

        │

        ▼

Stable Releases
```

The roadmap is directional.

Versioning is procedural.

---

# Related Documents

This document complements:

* ROADMAP.md
* ARCHITECTURE.md
* HCP-0010 — Canonical JSON Specification
* HCP-0022 — Conformance Requirements

---

# Summary

The HCP Versioning strategy is designed to preserve long-term interoperability while allowing the protocol to evolve.

Different HCP components may evolve independently.

Protocol semantics should remain stable.

Backward compatibility should be preserved whenever reasonably possible.

Version transparency enables reliable interoperability between independent implementations.

Stable evolution preserves humanitarian cooperation.
