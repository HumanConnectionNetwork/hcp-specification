# Canonical JSON Style Guide

Version: 0.3 (Draft)

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

---

# Introduction

This document defines editorial guidelines for writing Canonical JSON examples used throughout the Humanitarian Connection Protocol (HCP) documentation.

These guidelines apply only to examples.

They are **not normative**.

The normative definition of the Canonical JSON format is provided by:

- HCP-0010 — Canonical JSON Specification

The purpose of this guide is to ensure that all examples remain consistent, readable and easy to understand.

---

# Design Principles

Every Canonical JSON example should be:

- simple;
- realistic;
- consistent;
- human-readable;
- implementation independent.

Examples exist to explain the protocol.

They should never introduce new protocol behavior.

---

# One Observation

Every example shall represent exactly one Humanitarian Observation.

A Canonical JSON example should never combine multiple observations into the same Humanitarian Record.

Correct:

```text
One observation

↓

One Humanitarian Record
```

Incorrect:

```text
Several observations

↓

One Humanitarian Record
```

---

# Fictional Data

All examples shall use fictional information.

Examples must never contain:

- real people;
- real contact information;
- real organizations;
- real humanitarian incidents.

Illustrative data should be realistic while remaining fictional.

---

# Stable Examples

Examples should remain stable over time.

Avoid references to:

- current disasters;
- recent news;
- temporary organizations;
- changing political situations.

Examples should remain understandable many years after publication.

---

# UUIDs

Every Humanitarian Record should use a valid UUID.

Illustrative UUIDs should resemble realistic values.

Example:

```text
9b3d7d88-4f2d-4e75-a2a5-5aaf8b5c1d91
```

---

# Timestamps

Examples should use ISO 8601 UTC timestamps.

Example:

```text
2026-07-13T18:45:00Z
```

UTC timestamps improve consistency across implementations.

---

# Locations

Locations should remain sufficiently descriptive while avoiding unnecessary precision.

Illustrative examples include:

- Central Community Shelter
- Riverside District
- Regional General Hospital
- Northern Evacuation Route

Examples should avoid exact street addresses or GPS coordinates unless specifically required by the scenario.

---

# Recognition Features

Recognition Features should describe visible observations.

Illustrative examples include:

- blue jacket;
- gray hair;
- red collar;
- white backpack;
- scar on left arm.

Recognition Features should never contain conclusions or assumptions.

---

# Optional Fields

Optional fields should be omitted whenever their values are unknown.

Prefer:

```json
{
  "subject": {
    "type": "person"
  }
}
```

Instead of:

```json
{
  "subject": {
    "type": "person",
    "reported_label": "unknown"
  }
}
```

Missing information should remain absent whenever reasonably possible.

---

# Human Readability

Examples should prioritize readability over compactness.

Recommended formatting includes:

- two-space indentation;
- logical grouping of related fields;
- consistent ordering of properties.

Examples should be understandable without requiring additional explanation.

---

# Consistency

Examples describing related scenarios should reuse compatible fictional information whenever appropriate.

For example:

- similar reported names;
- compatible estimated ages;
- matching recognition features;
- nearby locations.

This consistency allows readers to understand how humanitarian correlation operates across multiple Humanitarian Records.

---

# Minimalism

Examples should contain only the information necessary to demonstrate the concept being explained.

Avoid unnecessary fields.

Avoid unnecessary complexity.

Smaller examples are easier to understand.

---

# Comments

Canonical JSON examples should never contain comments.

Only valid JSON should appear in `.json` files.

Explanations belong in accompanying Markdown documents.

---

# Canonical Structure

Whenever possible, examples should preserve the same property order.

Illustrative ordering:

```text
hcp_version

record_uuid

event_type

observation_timestamp

subject

observation

reported_by

public_contact

metadata
```

A consistent structure improves readability throughout the repository.

---

# Relationship with Markdown Examples

Every JSON example should have a corresponding Markdown document describing:

- the humanitarian scenario;
- the observation;
- synchronization;
- search;
- correlation;
- Humanitarian Case;
- human verification.

The Markdown document explains the scenario.

The JSON demonstrates the data.

Both should complement one another.

---

# Summary

The examples contained in this repository are designed to demonstrate the Humanitarian Connection Protocol in a clear, consistent and implementation-independent manner.

Every example should prioritize:

- simplicity;
- clarity;
- consistency;
- realism;
- semantic accuracy.

Examples should help readers understand HCP.

They should never redefine HCP.
