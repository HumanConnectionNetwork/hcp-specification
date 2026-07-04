# HCP-0002

# Humanitarian Connection Protocol
## Humanitarian Record

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-04

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Fundamental Principles

---

# 1. Abstract

The Humanitarian Record (HR) is the fundamental data unit of the Humanitarian Connection Protocol (HCP).

Every operation performed by HCP Nodes revolves around Humanitarian Records.

A Humanitarian Record represents a structured humanitarian observation describing a person, situation, event or resource at a specific moment in time.

It is intentionally designed to be independent from identity systems, governments, organizations and database implementations.

---

# 2. Purpose

The purpose of a Humanitarian Record is to allow independent organizations to exchange humanitarian observations using a common, interoperable format.

A Humanitarian Record is not intended to establish legal identity.

Instead, it preserves humanitarian observations in a structured, portable and verifiable manner.

---

# 3. Design Goals

A Humanitarian Record shall be:

- Globally interoperable
- Technology independent
- Extensible
- Immutable once published
- Privacy aware
- Evidence-oriented
- Easy to exchange
- Easy to validate

---

# 4. Observation Model

A Humanitarian Record represents an observation.

Examples include:

- A missing person report.
- A medical assistance request.
- A shelter registration.
- A food distribution event.
- A victim located by rescuers.
- A family reunification request.
- A humanitarian resource.

The protocol records observations rather than identities.

---

# 5. Humanitarian Subject

Every Humanitarian Record contains one Humanitarian Subject.

The subject may represent:

- an individual;
- a family;
- a group;
- a community;
- an organization;
- a location;
- a resource.

Future specifications define each subject type.

---

# 6. Record Identity

Every Humanitarian Record receives a globally unique identifier (UUID).

The UUID identifies the record itself.

It never identifies the humanitarian subject.

Multiple records may legitimately describe the same subject.

---

# 7. Record Lifecycle

A Humanitarian Record follows a simple lifecycle:

Created

↓

Published

↓

Discovered

↓

Referenced

↓

Validated

↓

Archived

Validation never replaces the original record.

Instead, additional information increases confidence over time.

---

# 8. Record Immutability

Once published, a Humanitarian Record shall never be modified.

Corrections must generate new Humanitarian Records referencing previous observations.

Historical integrity must always be preserved.

---

# 9. Core Metadata

Every Humanitarian Record shall contain at minimum:

Record UUID

Creation Timestamp

Node Identifier

Protocol Version

Subject Type

Observation Type

Observation Timestamp

Geographic Reference

Record Status

Schema Version

These fields are mandatory for interoperability.

---

# 10. Humanitarian Data

The humanitarian payload depends on the observation.

Examples include:

Person name

Approximate age

Gender

Physical description

Medical condition

Current needs

Location

Contact information

Photographs

Documents

Evidence references

Future specifications define optional fields.

---

# 11. Evidence

Humanitarian Records may contain evidence supporting the observation.

Examples:

Photographs

Videos

Medical reports

GPS coordinates

Official documents

Witness statements

External references

Evidence increases confidence but does not guarantee truth.

---

# 12. Relationships

Humanitarian Records may reference other Humanitarian Records.

Examples:

Same subject

Family member

Duplicate observation

Correction

Status update

Medical follow-up

Resource delivery

This allows independent observations to become interconnected over time.

---

# 13. Trust

The protocol never classifies a record as absolutely true or false.

Confidence emerges through:

Independent observations

Supporting evidence

Validator participation

Temporal consistency

Geographic consistency

Organizational reputation

Trust is cumulative.

---

# 14. Privacy

Humanitarian Records should contain only information necessary for humanitarian purposes.

Sensitive information should be minimized whenever possible.

Applications remain responsible for complying with local privacy regulations.

---

# 15. Ownership

No organization owns a Humanitarian Record after publication.

Each Node maintains its own local copy.

Synchronization distributes observations without transferring ownership.

---

# 16. Transport Independence

A Humanitarian Record is independent of transport protocols.

It may be exchanged through:

REST APIs

Message queues

File exports

Offline synchronization

Future transports

Its structure remains identical regardless of transport.

---

# 17. Serialization

Nodes may serialize Humanitarian Records using formats such as:

JSON

YAML

Protocol Buffers

CBOR

Other future formats

Serialization does not alter semantics.

---

# 18. Extensibility

Future protocol versions may introduce optional fields.

Existing implementations shall ignore unknown fields whenever possible to preserve forward compatibility.

---

# 19. Compliance

A Humanitarian Record is considered HCP compliant when:

- it satisfies the required schema;
- it contains mandatory metadata;
- it follows protocol semantics;
- it preserves immutability.

---

# 20. Summary

The Humanitarian Record is the atomic information unit exchanged by the Humanitarian Connection Protocol.

Rather than identifying people, it preserves humanitarian observations.

Multiple observations may describe the same humanitarian subject.

Through evidence, relationships and independent validation, these observations collectively form a progressively more reliable humanitarian information network while preserving decentralization and interoperability.
