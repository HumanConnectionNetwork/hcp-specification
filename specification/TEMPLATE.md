# HCP Specification Template

---

```
HCP-XXXX

Title:
<Specification Title>

Status:
Draft | Review | Stable | Deprecated | Superseded

Version:
0.1.0

Category:
Core | Networking | Security | Extension | Informational

Authors:
Human Connection Network Contributors

Created:
YYYY-MM-DD

Updated:
YYYY-MM-DD

Requires:
HCP-0000
HCP-0001

Supersedes:
(optional)

Superseded By:
(optional)
```

---

# Abstract

Provide a concise summary of the purpose of this specification.

The abstract SHOULD be understandable without reading the remainder of the document.

Recommended length:

100–250 words.

---

# Status of This Document

Describe the maturity level of this specification.

Possible values:

* Draft
* Review
* Stable
* Deprecated
* Superseded

Only **Stable** specifications are considered normative.

---

# Motivation

Explain the problem this specification solves.

Answer questions such as:

* Why does this specification exist?
* Which architectural problem does it address?
* Why is it part of HCP?

---

# Scope

Clearly define:

What this specification covers.

What this specification intentionally does NOT cover.

---

# Terminology

Define all domain-specific terms introduced by this document.

Previously defined terms SHOULD reference the Glossary instead of redefining them.

---

# Normative Language

The keywords

**MUST**

**MUST NOT**

**SHOULD**

**SHOULD NOT**

**MAY**

are to be interpreted according to RFC 2119.

---

# Specification

This section contains the normative protocol definition.

Everything described here is considered part of HCP.

Implementations claiming compliance MUST follow this section.

---

# Business Rules

Describe the mandatory business behavior.

Example:

* Every Record MUST have exactly one identifier.

* Every Node MUST expose its capabilities.

* Identity MUST NOT replace Records.

---

# State Model

Describe lifecycle or state transitions when applicable.

Example:

```
Created

↓

Validated

↓

Updated

↓

Archived
```

If the specification has no state transitions this section MAY be omitted.

---

# Data Requirements

Describe required fields, constraints and validation rules.

Reference JSON Schemas whenever possible.

Do not duplicate schema definitions.

---

# Interoperability Requirements

Describe what is required to ensure compatibility between implementations.

This section should answer:

"What must another implementation do to interoperate?"

---

# Examples

Provide practical examples.

Recommended examples:

* Valid example

* Invalid example

* Typical workflow

* Edge case

Examples are informative.

They are not normative.

---

# Security Considerations

Describe security implications.

Examples:

* Authentication

* Authorization

* Integrity

* Replay attacks

* Data leakage

Every specification SHOULD contain this section.

---

# Privacy Considerations

Describe any privacy implications.

Examples:

* Personal data

* Metadata

* Sensitive information

* Data minimization

---

# Extensibility

Describe how future protocol versions may extend this specification.

Extensions SHOULD preserve backward compatibility whenever possible.

---

# Implementation Notes

Optional guidance for implementers.

This section is informative.

It MUST NOT define protocol behavior.

---

# Compliance

Describe the minimum requirements an implementation must satisfy.

Example:

An implementation is compliant if it:

* validates all mandatory fields;

* preserves identifiers;

* follows lifecycle rules;

* exposes required capabilities.

---

# Future Work

List known areas for future improvements.

This section is informative.

---

# References

Normative references.

Examples:

* HCP-0001 Protocol

* HCP-0002 Data Model

* RFC 2119

Informative references MAY also be included.

---

# Appendix A — Examples

Optional.

Large examples should be placed here.

---

# Appendix B — Changelog

Version history for this specification.

Example:

Version 0.1

* Initial draft

Version 0.2

* Added Identity section

Version 1.0

* Stable release

```
```
