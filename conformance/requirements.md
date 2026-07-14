# HCP Conformance Requirements

Version: 0.1 (Draft)

Status: Draft

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-14

---

# Introduction

This document describes the practical requirements used to evaluate whether an implementation conforms to the Humanitarian Connection Protocol (HCP).

It complements:

* HCP-0022 — Conformance Requirements

The HCP specification defines the normative behavior.

This document explains how that behavior may be evaluated.

---

# Purpose

The purpose of these requirements is to provide a common evaluation framework for independent HCP implementations.

Conformance testing promotes:

* interoperability;
* predictable behavior;
* implementation consistency;
* long-term protocol compatibility.

Conformance evaluates protocol behavior.

It does not evaluate implementation technology.

---

# Evaluation Philosophy

HCP evaluates observable protocol behavior.

Implementations remain free to choose:

* programming languages;
* databases;
* deployment models;
* APIs;
* communication protocols;
* internal architectures.

Only humanitarian semantics are evaluated.

---

# Conformance Categories

A complete HCP evaluation considers the following areas.

| Category            | Purpose                                               |
| ------------------- | ----------------------------------------------------- |
| Record Processing   | Correct creation and handling of Humanitarian Records |
| Query Processing    | Correct processing of humanitarian Queries            |
| Synchronization     | Preservation of Canonical JSON                        |
| Correlation         | Local humanitarian interpretation                     |
| Result Presentation | Separation of evidence and interpretation             |
| Security            | Preservation of protocol integrity                    |
| Privacy             | Data minimization and local privacy boundaries        |
| Interoperability    | Compatibility with independent HCP implementations    |

---

# Mandatory Requirements

Every implementation claiming HCP compatibility MUST satisfy the mandatory requirements defined by HCP-0022.

Illustrative examples include:

* preserve immutable Humanitarian Records;
* exchange valid Canonical JSON;
* preserve humanitarian semantics;
* distinguish observations from interpretation;
* keep Humanitarian Cases local;
* avoid modifying synchronized Humanitarian Records.

Failure to satisfy a mandatory requirement results in non-conformance.

---

# Recommended Requirements

Implementations SHOULD satisfy all recommended requirements whenever reasonably possible.

Illustrative examples include:

* preserve unknown optional fields;
* support distributed search;
* preserve unknown Event Types;
* advertise supported protocol versions;
* validate protocol integrity before synchronization.

Failure to satisfy a recommended requirement does not automatically invalidate conformance.

However, it may reduce interoperability.

---

# Optional Requirements

Implementations MAY provide additional capabilities beyond those defined by HCP.

Illustrative examples include:

* Artificial Intelligence assistance;
* GIS integration;
* notification systems;
* analytics;
* dashboards;
* offline synchronization;
* mobile optimization.

Optional functionality MUST preserve standardized humanitarian semantics.

Extensions MUST NOT reduce interoperability.

---

# Conformance Process

A typical conformance evaluation follows the sequence below.

```text
Implementation

        │

        ▼

Schema Validation

        │

        ▼

Behavior Validation

        │

        ▼

Conformance Evaluation

        │

        ▼

Compatibility Decision
```

Each stage evaluates a different aspect of the implementation.

---

# Evaluation Criteria

An implementation should demonstrate that it correctly:

## Humanitarian Records

* creates valid Humanitarian Records;
* preserves immutable observations;
* generates unique Record UUIDs;
* exchanges Canonical JSON.

---

## Queries

* accepts partial humanitarian Queries;
* retrieves Humanitarian Records;
* distinguishes search from correlation.

---

## Synchronization

* preserves Canonical JSON;
* preserves protocol metadata;
* preserves Record UUIDs;
* preserves observation timestamps;
* does not modify humanitarian meaning.

---

## Correlation

* performs correlation locally;
* does not synchronize Humanitarian Cases;
* separates evidence from interpretation;
* preserves explainability.

---

## Result Presentation

* distinguishes observations from conclusions;
* presents Supporting Evidence;
* presents Conflicting Evidence;
* avoids presenting interpretation as verified identity.

---

## Privacy

* minimizes unnecessary personal information;
* preserves local organizational control;
* excludes Public Contact from correlation.

---

## Security

* validates protocol integrity;
* detects malformed Humanitarian Records;
* rejects structurally invalid synchronized records;
* preserves immutable humanitarian evidence.

---

# Conformance Levels

Implementations may describe compatibility using the levels defined by HCP.

## Core Conformance

Implements every mandatory (**MUST**) requirement.

---

## Full Conformance

Implements mandatory (**MUST**) and recommended (**SHOULD**) requirements.

---

## Extended Conformance

Implements HCP while adding compatible implementation-specific capabilities.

Extensions must preserve humanitarian semantics.

---

# Test Resources

The remaining resources contained in this directory provide practical conformance examples.

Illustrative structure:

```text
conformance/

README.md

requirements.md

valid/

invalid/

test-vectors/
```

These resources are informative.

The normative requirements remain defined by the HCP Specification.

---

# Relationship with JSON Schema

Passing JSON Schema validation alone does not establish HCP compatibility.

```text
JSON Schema

        │

        ▼

Valid Structure

        │

        ▼

Behavior Validation

        │

        ▼

Conformance

        │

        ▼

HCP Compatible
```

Schema validation verifies structure.

Conformance verifies behavior.

---

# Relationship with the Specification

This document evaluates implementation behavior according to:

* HCP-0010 — Canonical JSON Specification
* HCP-0011 — Query Model
* HCP-0012 — Correlation Model
* HCP-0013 — Synchronization Model
* HCP-0015 — Result Presentation Model
* HCP-0020 — Security Model
* HCP-0021 — Privacy and Data Minimization Model
* HCP-0022 — Conformance Requirements

The specification remains normative.

This document provides an implementation-oriented evaluation framework.

---

# Summary

HCP conformance evaluates whether an implementation preserves the standardized humanitarian semantics defined by the protocol.

Conformance does not prescribe technology.

Conformance evaluates behavior.

Compatible implementations may differ internally while remaining interoperable through shared humanitarian semantics.

Conformance preserves interoperability.

Interoperability preserves humanitarian cooperation.
