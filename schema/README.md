# HCP JSON Schemas

This directory contains the official JSON Schemas of the Humanitarian Connection Protocol (HCP).

These schemas provide a machine-readable representation of the protocol structures defined throughout the HCP Specification.

Their purpose is to enable automatic validation of HCP data while preserving the semantic rules defined by the protocol.

The schemas complement the written specification.

They do not replace it.

---

# Purpose

The JSON Schemas contained in this directory allow developers to verify that HCP data structures conform to the protocol specification.

Schema validation improves:

- interoperability;
- implementation consistency;
- automated testing;
- software reliability;
- long-term compatibility.

Validation ensures that exchanged data follows the canonical structure expected by HCP implementations.

---

# Scope

The schemas validate the structure of protocol objects.

Illustrative examples include:

- Humanitarian Records;
- Queries;
- Humanitarian Cases.

The schemas validate:

- required fields;
- optional fields;
- data types;
- field formats;
- allowed values;
- structural constraints.

The schemas do not validate humanitarian meaning.

Semantic interpretation remains defined by the HCP Specification.

---

# Relationship with the Specification

The HCP Specification defines humanitarian semantics.

The JSON Schemas define structural validation.

Both are required for a complete implementation.

```text
HCP Specification

        │

        ▼

Humanitarian Semantics

        │

        ▼

Canonical JSON

        │

        ▼

JSON Schema

        │

        ▼

Automatic Validation
```

Semantic interoperability depends upon both.

---

# Validation Philosophy

Schema validation verifies that a document is structurally correct.

It does not determine whether the humanitarian observation is true.

Validation confirms:

- correct structure;
- required fields;
- supported data types;
- valid formatting.

Validation never confirms:

- humanitarian correctness;
- identity;
- correlation quality;
- humanitarian interpretation.

People verify reality.

---

# Available Schemas

This directory currently contains the following schemas.

| Schema | Purpose |
|---------|---------|
| `hcp-record.schema.json` | Validates Humanitarian Records |
| `query.schema.json` | Validates Queries |
| `humanitarian-case.schema.json` | Validates Humanitarian Cases |

Additional schemas may be introduced in future protocol versions.

---

# Version Compatibility

Every schema corresponds to a specific HCP protocol version.

Implementations should validate data using the schema matching the protocol version they support.

Whenever reasonably possible, future versions should preserve backward compatibility.

---

# Implementation Independence

The schemas define protocol structure only.

They intentionally avoid prescribing:

- programming languages;
- frameworks;
- databases;
- APIs;
- storage engines;
- deployment models.

Implementations remain free to choose their own technologies.

Only protocol structure is standardized.

---

# Relationship with Conformance

Passing JSON Schema validation does not automatically imply HCP conformance.

Schema validation verifies structural correctness.

Conformance additionally requires implementations to preserve the semantic and behavioral requirements defined throughout the HCP Specification.

```text
JSON Schema

        │

        ▼

Structural Validation

        │

        ▼

Conformance Requirements

        │

        ▼

HCP Compatibility
```

Schema validation is therefore a necessary—but not sufficient—condition for claiming HCP compatibility.

---

# Related Specifications

The schemas contained in this directory implement structures defined by:

- HCP-0001 — Humanitarian Record
- HCP-0010 — Canonical JSON Specification
- HCP-0011 — Query Model
- HCP-0015 — Result Presentation Model
- HCP-0022 — Conformance Requirements

---

# Summary

The JSON Schemas provide the machine-readable structural definition of HCP.

The specification defines humanitarian semantics.

The schemas validate protocol structure.

Together, they enable consistent, interoperable and automatically verifiable HCP implementations while preserving implementation independence.
