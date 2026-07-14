# HCP Conformance

This directory defines the conformance resources of the Humanitarian Connection Protocol (HCP).

Its purpose is to help developers verify whether an implementation behaves according to the normative requirements defined by the HCP Specification.

Unlike the JSON Schemas, which validate document structure, the resources contained here evaluate protocol behavior.

Conformance ensures that independent implementations remain interoperable while preserving humanitarian semantics.

---

# Purpose

The conformance resources allow developers to verify that an implementation correctly applies the behavioral requirements defined throughout the HCP Specification.

Conformance improves:

* interoperability;
* implementation consistency;
* compatibility testing;
* protocol reliability;
* long-term ecosystem stability.

Conformance evaluates how implementations behave.

It does not evaluate software architecture.

---

# Scope

The conformance resources verify protocol behavior rather than document structure.

Illustrative validation areas include:

* Humanitarian Record processing;
* Query processing;
* synchronization behavior;
* correlation behavior;
* privacy preservation;
* security requirements;
* interoperability;
* forward compatibility.

The objective is to verify that compatible implementations preserve standardized humanitarian semantics.

---

# Relationship with JSON Schema

JSON Schema and Conformance have different responsibilities.

```text
JSON Schema

        │

        ▼

Structural Validation

        │

        ▼

Conformance

        │

        ▼

Behavioral Validation

        │

        ▼

HCP Compatibility
```

A document may successfully pass JSON Schema validation while the implementation still fails protocol conformance.

Structural correctness alone is not sufficient.

---

# Validation Philosophy

HCP separates structural correctness from protocol behavior.

Schema validation verifies that information is correctly represented.

Conformance verifies that information is correctly processed.

Illustrative examples include:

* preserving immutable Humanitarian Records;
* keeping Humanitarian Cases local;
* distinguishing observations from interpretation;
* preserving unknown optional fields;
* maintaining protocol interoperability.

Conformance evaluates observable behavior.

It never prescribes implementation technology.

---

# Conformance Areas

The conformance resources currently focus on the following protocol areas.

| Area              | Purpose                                         |
| ----------------- | ----------------------------------------------- |
| Record Processing | Validation of Humanitarian Record handling      |
| Query Processing  | Validation of Query behavior                    |
| Synchronization   | Preservation of Canonical JSON during exchange  |
| Correlation       | Preservation of local interpretation            |
| Privacy           | Verification of privacy boundaries              |
| Security          | Verification of protocol integrity              |
| Interoperability  | Behavioral compatibility across implementations |

Additional conformance areas may be introduced in future versions.

---

# Conformance Levels

Implementations may describe their compatibility using the levels defined by HCP-0022.

```text
Core Conformance

↓

Full Conformance

↓

Extended Conformance
```

These levels distinguish between mandatory protocol behavior and optional implementation capabilities.

---

# Test Resources

This directory may contain:

```text
README.md

requirements.md

test-vectors/

valid/

invalid/
```

These resources allow independent implementations to verify protocol compatibility using common reference data.

---

# Implementation Independence

Conformance intentionally avoids prescribing:

* programming languages;
* frameworks;
* databases;
* deployment architectures;
* cloud providers;
* APIs;
* user interfaces.

Different implementations may use completely different technologies while remaining fully HCP compatible.

Compatibility depends upon humanitarian semantics.

---

# Relationship with the Specification

The HCP Specification defines what the protocol means.

The conformance resources verify that implementations preserve those meanings.

```text
HCP Specification

        │

        ▼

Normative Requirements

        │

        ▼

Conformance Validation

        │

        ▼

Compatible Implementation
```

The specification remains normative.

The conformance resources provide practical verification.

---

# Related Specifications

This directory complements:

* HCP-0010 — Canonical JSON Specification
* HCP-0011 — Query Model
* HCP-0012 — Correlation Model
* HCP-0013 — Synchronization Model
* HCP-0015 — Result Presentation Model
* HCP-0020 — Security Model
* HCP-0021 — Privacy and Data Minimization Model
* HCP-0022 — Conformance Requirements

---

# Summary

The resources contained in this directory verify whether an implementation behaves according to the Humanitarian Connection Protocol.

JSON Schema validates structure.

Conformance validates behavior.

Together, they enable independent implementations to exchange humanitarian observations while preserving shared humanitarian semantics.
