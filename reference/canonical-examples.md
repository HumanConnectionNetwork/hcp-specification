# HCP Canonical Examples

Version: 1.0 (Draft)

Status: Draft

Project: Human Connection Network (HCN)

---

# Purpose

This document describes the official example dataset provided with the Humanitarian Connection Protocol (HCP).

These examples are intended to help implementers understand how Humanitarian Records should be represented and exchanged.

The examples are informative.

Normative requirements remain defined in the HCP Core Specification.

---

# Goals

The canonical examples serve several purposes:

- illustrate valid Humanitarian Records;
- demonstrate correct use of the Canonical JSON format;
- provide reference data for implementations;
- support interoperability testing;
- simplify SDK development;
- provide a common dataset for tutorials and documentation.

---

# Design Principles

All examples follow the official HCP specifications.

Each example represents a single Humanitarian Observation.

Examples are intentionally realistic while avoiding unnecessary personal information.

Examples prioritize semantic clarity over complexity.

---

# Available Examples

The official examples are organized by humanitarian scenario.

```text
examples/

    person/
        missing-person.json
        hospitalized-person.json
        refugee-registration.json
        located-person.json
        public-emergency.json

    animal/
        missing-animal.json
        found-animal.json

    hospital/
        hospital-admission.json

    shelter/
        shelter-registration.json

    disaster/
        disaster-observation.json

    rescue/
        rescue-operation.json

    volunteer/
        volunteer-assistance.json
```

---

# Example Characteristics

Every example demonstrates the use of:

- Canonical JSON
- Event Type
- Event Family
- Recognition Features
- Reported Label
- Observation metadata
- Public Contact (when applicable)

Examples intentionally avoid implementation-specific fields.

---

# Correlation Examples

Some examples are designed to be related.

For example:

- two observations describing the same missing person;
- hospital admission following a disaster;
- volunteer observation confirming a previous report.

These examples demonstrate how independent Humanitarian Records may later produce a Humanitarian Case through local correlation.

---

# Synchronization Examples

Examples illustrate synchronization between independent Nodes.

The synchronized data always consists of Humanitarian Records.

Humanitarian Cases are never exchanged.

---

# Query Examples

Example queries demonstrate how Nodes retrieve humanitarian evidence.

Queries describe observations rather than identities.

Different implementations may return different Humanitarian Cases from identical queries.

---

# Explainability Examples

Several examples include supporting data for explainable correlation.

These examples demonstrate:

- Supporting Evidence
- Conflicting Evidence
- Correlation Score
- Humanitarian Timeline

The interpretation remains local to each implementation.

---

# Privacy Examples

Examples intentionally demonstrate Privacy by Architecture.

Personal information is minimized.

Recognition Features are observational rather than identifying.

Reported Labels do not imply verified identity.

---

# Future Extensions

Additional examples may be published as new humanitarian scenarios emerge.

New examples should remain semantically compatible with existing specifications.

Previously published examples should remain valid whenever possible.

---

# Summary

The canonical examples provide a common reference dataset for the HCP ecosystem.

They help ensure that different implementations interpret and exchange Humanitarian Records consistently while preserving the protocol's architectural principles of semantic interoperability, local interpretation and human verification.
