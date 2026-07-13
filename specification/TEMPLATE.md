# HCP Document Template

This template defines the recommended structure for Humanitarian Connection Protocol (HCP) specification documents.

All new HCP documents SHOULD follow this structure unless there is a compelling technical reason to deviate.

The goal is to maintain consistency, readability and interoperability across the entire specification.

---

# Document Metadata

Every HCP document SHOULD begin with the following metadata.

```text
HCP-XXXX

Title

Version:

Status:

Category:

Authors:

License:

Last Updated:

Depends On:

Replaces:

Replaced By:
```

## Metadata Fields

| Field        | Description                                                   |
| ------------ | ------------------------------------------------------------- |
| HCP          | Unique document identifier                                    |
| Title        | Official specification title                                  |
| Version      | Current document version                                      |
| Status       | Draft, Review, Experimental, Stable or Deprecated             |
| Category     | Core, Record Model, Search, Networking, Security, etc.        |
| Authors      | Document maintainers                                          |
| License      | Document license                                              |
| Last Updated | Last editorial revision                                       |
| Depends On   | Other HCP documents required to understand this specification |
| Replaces     | Previous specification superseded by this document            |
| Replaced By  | Future specification replacing this document                  |

---

# 1. Introduction

Briefly describe:

* what this specification defines
* why it exists
* how it relates to the protocol

Avoid implementation details.

---

# 2. Motivation

Explain the problem this specification solves.

Focus on interoperability rather than implementation.

---

# 3. Scope

Clearly define:

What this specification covers.

What this specification intentionally does not cover.

---

# 4. Definitions

Define important protocol concepts introduced by this document.

Use precise terminology.

Whenever possible, reference previously defined HCP concepts instead of redefining them.

---

# 5. Specification

This section contains the normative protocol definition.

Normative requirements should use the keywords:

* MUST
* MUST NOT
* SHOULD
* SHOULD NOT
* MAY

These keywords indicate the expected behavior of compatible implementations.

---

# 6. Data Model

If applicable, define:

* structures
* fields
* attributes
* allowed values
* constraints

Representations should remain implementation-independent.

---

# 7. Processing Rules

Describe how compatible implementations are expected to process the information defined by this specification.

Focus on observable behavior rather than internal implementation.

---

# 8. Examples

Provide informative examples whenever appropriate.

Examples are not normative.

Examples should illustrate correct protocol usage.

Whenever possible include Canonical JSON examples.

---

# 9. Error Handling

Describe expected behavior when invalid, incomplete or incompatible information is received.

If not applicable, explicitly state so.

---

# 10. Security Considerations

Describe relevant security implications introduced by this specification.

Examples may include:

* spoofing
* tampering
* denial of service
* trust assumptions
* authentication
* authorization

If none apply, explicitly state:

> This specification introduces no additional security considerations.

---

# 11. Privacy Considerations

Discuss any privacy implications.

Examples include:

* personal information
* data minimization
* observation sensitivity
* metadata exposure
* contact information

If not applicable, explicitly state so.

---

# 12. Interoperability Considerations

Explain how this specification contributes to interoperability.

Document any compatibility requirements with other HCP specifications.

---

# 13. Dependencies

List all related HCP documents.

For example:

* HCP-0000
* HCP-0001
* HCP-0010

Avoid circular dependencies whenever possible.

---

# 14. References

References may include:

* other HCP specifications
* RFCs
* W3C Recommendations
* academic publications
* open standards

Informative references should be distinguished from normative references whenever appropriate.

---

# Writing Guidelines

Authors SHOULD:

* write in clear technical English
* use active voice whenever possible
* define new terminology before using it
* avoid unnecessary repetition
* maintain implementation independence
* preserve backward compatibility whenever practical

Authors SHOULD NOT:

* prescribe programming languages
* prescribe database technologies
* prescribe deployment architectures
* prescribe user interface behavior unless strictly necessary
* describe implementation details that do not affect interoperability

---

# Normative Language

Requirement keywords should be interpreted consistently throughout the specification.

| Keyword    | Meaning               |
| ---------- | --------------------- |
| MUST       | Mandatory requirement |
| MUST NOT   | Prohibited behavior   |
| SHOULD     | Strong recommendation |
| SHOULD NOT | Generally discouraged |
| MAY        | Optional behavior     |

---

# Editorial Principles

Every HCP document should strive to be:

* technically precise
* implementation-independent
* human-readable
* machine-readable where applicable
* internally consistent
* interoperable
* privacy-aware
* security-conscious
* future-proof

---

# Philosophy

Humanitarian Connection Protocol specifications describe **shared meaning**, not implementation details.

The protocol defines how humanitarian observations are represented and understood across independent systems.

Implementations remain free to choose their own technologies, infrastructure and internal architecture.

The specification standardizes interoperability—not software.
