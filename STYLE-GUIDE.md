# HCP Editorial Style Guide

This document defines the editorial conventions used throughout the Humanitarian Connection Protocol (HCP) specification.

Its purpose is to maintain consistency, readability and technical precision across all specification documents.

This guide applies to all normative HCP documents, examples and future protocol proposals.

---

# Editorial Principles

Every HCP document should strive to be:

* technically precise
* implementation-independent
* easy to understand
* internally consistent
* interoperable
* future-proof
* security-conscious
* privacy-aware

The specification should describe **protocol behavior**, not implementation details.

---

# Language

The official language of the HCP specification is **English**.

English should follow a neutral technical style.

Avoid regional expressions, slang or conversational language.

Use short and direct sentences whenever possible.

---

# Writing Style

Authors SHOULD:

* write in active voice
* define terminology before using it
* explain concepts before describing behavior
* prefer clarity over brevity
* avoid ambiguity
* avoid repetition
* keep sections focused on a single responsibility

Authors SHOULD NOT:

* describe implementation-specific code
* prescribe programming languages
* prescribe database technologies
* prescribe deployment architectures
* prescribe user interface behavior unless required for interoperability

---

# Terminology

The following terms should be written consistently throughout the specification.

## Humanitarian Connection Protocol

Always write:

**Humanitarian Connection Protocol (HCP)**

After the first occurrence, **HCP** may be used.

---

## Humanitarian Record

Always capitalize:

**Humanitarian Record**

Never use variations such as:

* humanitarian record
* humanitarian object
* humanitarian entry

unless required by normal sentence grammar.

---

## HCP Node

Always write:

**HCP Node**

Do not use:

* server
* backend
* API server

unless referring to implementation details.

---

## HCP Client

Always write:

**HCP Client**

Examples include:

* Telegram Client
* Mobile Client
* SMS Client

---

## Correlation Candidate

Always capitalize:

**Correlation Candidate**

This is a protocol concept.

---

## Canonical JSON

Prefer:

**Canonical HCP JSON Representation**

Avoid simply writing:

* canonical json
* protocol json

when referring to the normative representation.

---

# Normative Language

Normative requirements should use the following keywords:

* **MUST**
* **MUST NOT**
* **SHOULD**
* **SHOULD NOT**
* **MAY**

These keywords indicate implementation requirements.

Do not use alternative wording such as:

* has to
* needs to
* required to

when a normative keyword is appropriate.

---

# Titles

Document titles should use Title Case.

Examples:

* Humanitarian Record
* Query Model
* Security Model

File names should use lowercase with hyphens.

Example:

```text
HCP-0012-correlation-model.md
```

---

# File Naming Convention

Normative specification documents should follow:

```text
HCP-XXXX-descriptive-name.md
```

Examples:

```text
HCP-0001-humanitarian-record.md

HCP-0009-node-api.md

HCP-0012-correlation-model.md
```

Avoid:

* spaces
* underscores
* ampersands
* accented characters
* mixed capitalization

---

# Document Structure

Normative HCP documents should generally follow this structure:

1. Metadata
2. Abstract
3. Introduction
4. Motivation
5. Scope
6. Definitions
7. Specification
8. Data Model (when applicable)
9. Processing Rules
10. Examples
11. Error Handling
12. Security Considerations
13. Privacy Considerations
14. Interoperability Considerations
15. Dependencies
16. References

Not every document requires every section, but the overall structure should remain as consistent as possible.

---

# Examples

Examples are informative.

Examples are not normative.

Whenever possible:

* use Canonical HCP JSON
* keep examples minimal
* avoid fictional complexity
* clearly distinguish examples from requirements

If an example conflicts with the normative text, the normative text always takes precedence.

---

# Tables

Prefer tables for:

* enumerations
* status values
* field descriptions
* requirement levels
* comparison summaries

Avoid large narrative paragraphs when structured information is more appropriate.

---

# JSON

JSON examples should:

* use two-space indentation
* preserve field ordering defined by the specification
* avoid unnecessary attributes
* remain valid JSON

Do not include comments inside JSON examples.

---

# Diagrams

Simple diagrams are encouraged when they improve understanding.

Prefer flow diagrams over implementation diagrams.

Example:

```text
Observation
        │
        ▼
Humanitarian Record
        │
        ▼
HCP Node
        │
        ▼
Correlation
```

Diagrams should illustrate protocol concepts rather than software architecture.

---

# References

When referencing another specification, use its official identifier.

Example:

```text
HCP-0010 — Canonical HCP JSON Specification
```

Avoid informal references such as:

* previous document
* another HCP
* earlier specification

---

# Versioning

Each specification document should include:

* Version
* Status
* Last Updated
* Depends On

When applicable, also include:

* Replaces
* Replaced By

---

# Backward Compatibility

Changes should preserve backward compatibility whenever reasonably possible.

Breaking changes should be documented explicitly and justified.

---

# Editorial Philosophy

The Humanitarian Connection Protocol defines **shared meaning**, not implementation details.

The specification standardizes how humanitarian observations are represented and understood across independent systems.

It does not standardize programming languages, databases, frameworks or deployment architectures.

Editorial decisions should always reinforce this principle.

Every document should help implementers understand **what** the protocol requires, not **how** a particular application chooses to implement it.
