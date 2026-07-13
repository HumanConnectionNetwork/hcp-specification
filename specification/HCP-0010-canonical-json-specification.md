# HCP-0010

# Canonical JSON Specification

Version: 0.4 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Humanitarian Record
- HCP-0003 — Subject Model
- HCP-0006 — Observation Model
- HCP-0007 — Status Model
- HCP-0008 — Event Type Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Canonical JSON Specification of the Humanitarian Connection Protocol (HCP).

The Canonical JSON is the standardized semantic representation exchanged between compatible HCP implementations.

It is the shared humanitarian language of HCP.

Every Humanitarian Record exchanged between compatible HCP Nodes shall be represented using this canonical structure.

The Canonical JSON standardizes semantic meaning rather than software architecture, database models or communication technologies.

Its purpose is to enable independent implementations to exchange humanitarian observations while preserving interoperability, implementation independence and long-term protocol evolution.

---

# 1. Introduction

The Humanitarian Connection Protocol defines a common semantic model for representing humanitarian observations.

The Canonical JSON is the official representation of that model.

Every Humanitarian Record exchanged by HCP Nodes shall follow this specification.

The Canonical JSON is independent of:

- programming language;
- operating system;
- database technology;
- communication protocol;
- storage mechanism;
- software architecture.

Different implementations may internally organize information in completely different ways.

However, when exchanging humanitarian information they shall produce the same semantic representation.

The Canonical JSON is therefore the shared humanitarian language spoken by all compatible HCP implementations.

---

# 2. Design Principles

The Canonical JSON follows the fundamental architectural principles of HCP.

---

## Semantic

The Canonical JSON standardizes humanitarian meaning.

It does not standardize software implementation.

---

## Observation-Based

Every Canonical JSON represents exactly one Observation.

It never represents an identity record, a humanitarian history or a centralized person profile.

---

## Minimal

Only humanitarian information necessary to describe an Observation should be included.

The protocol intentionally avoids unnecessary complexity and implementation-specific metadata.

---

## Deterministic

Equivalent humanitarian observations should always produce the same canonical semantic structure regardless of implementation.

This guarantees interoperability between independent HCP Nodes.

---

## Portable

Canonical Humanitarian Records should be transferable through any compatible communication technology including:

- HTTP APIs
- JSON files
- Message Queues
- SMS Gateways
- Mesh Networks
- Satellite Communication
- Offline Synchronization
- Future communication technologies

without requiring semantic modifications.

---

## Extensible

Future protocol versions may introduce optional semantic elements while preserving compatibility whenever reasonably possible.

Older implementations should safely ignore unknown fields without losing recognized humanitarian information.

---

## Offline-First

The Canonical JSON is intentionally lightweight.

It is designed to be created, exchanged and preserved even under severely constrained communication environments.

---

## Correlation-Oriented

The Canonical JSON represents humanitarian evidence.

It does not identify people.

Its purpose is to facilitate explainable correlation between independent humanitarian observations while allowing correlation algorithms to evolve independently.

The protocol standardizes semantics.

Implementations define correlation.
---

# 3. Canonical Structure

Every Humanitarian Record shall follow the semantic structure defined below.

The Canonical JSON represents one humanitarian observation.

It is composed of three conceptual sections:

- Record Metadata
- Subject
- Observation

Illustrative structure:

```json
{
  "id": "2d36d31d-c987-4c35-b0a8-74cb8eb9b62e",

  "schema_version": "0.4",

  "source_client": "hcp-client-telegram",

  "subject": {

    "type": "human",

    "reported_label": "Juan Pérez",

    "estimated_age": 42,

    "recognition_features": "Blue jacket, black backpack, glasses"

  },

  "observation": {

    "event_type": "hospital_admission",

    "status": "stable",

    "reported_location": "Hospital Central",

    "reported_by": "hospital",

    "observed_at": "2026-07-13T18:30:00Z",

    "public_contact": "@hospital"
  }
}
```

The internal organization of software systems may differ.

Only the exchanged semantic representation is standardized.

---

# 4. Record Metadata

The Record Metadata identifies the Humanitarian Record itself.

Metadata belongs to the Record.

It does not belong to the observed Subject.

---

## id

Globally unique identifier of the Humanitarian Record.

Type:

```
UUID
```

The identifier uniquely identifies the Observation.

It never identifies a person or animal.

---

## schema_version

Version of the Canonical JSON Specification used to generate the Humanitarian Record.

Example:

```
0.4
```

This field enables protocol evolution while preserving interoperability.

---

## source_client

Technical identifier of the implementation that generated the Humanitarian Record.

Examples include:

```
hcp-client-telegram

hcp-client-web

hospital-system

veterinary-plugin
```

This field exists exclusively for interoperability diagnostics.

It shall never participate in humanitarian correlation.

---

# 5. Subject Object

The Subject object describes the observed living being.

It contains descriptive humanitarian evidence concerning the Subject itself.

The Subject object intentionally avoids permanent identity concepts.

Its purpose is to describe the observed Subject rather than identify an individual.

Example:

```json
{
  "subject": {

    "type": "human",

    "reported_label": "Juan Pérez",

    "estimated_age": 42,

    "recognition_features": "Blue jacket, black backpack"
  }
}
```

---

## type

Defines the Subject Type.

Examples:

```
human

animal
```

Future specifications may define additional Subject Types while preserving semantic compatibility.

---

## reported_label

Human-readable label provided by the reporter.

Examples:

```
Juan Pérez

NN

Adult male

White dog

Green parrot

Unknown child
```

The reported label is humanitarian evidence.

It is not a protocol identifier.

Different Observations concerning the same Subject may legitimately contain different reported labels.

Correlation evaluates this field probabilistically together with all other available humanitarian evidence.

---

## estimated_age

Approximate age of a human Subject.

Type:

```
Integer
```

Applicable only when:

```
type = human
```

If unknown, this field may be omitted.

---

## recognition_features

Free-text description of directly observable characteristics.

Examples for humans include:

- clothing;
- glasses;
- tattoos;
- scars;
- hairstyle;
- backpack;
- mobility aids.

Examples for animals include:

- collar;
- coat color;
- distinctive markings;
- ear shape;
- tail characteristics;
- visible injuries.

Recognition Features represent one of the strongest sources of humanitarian evidence available for correlation.

Implementations should encourage concise descriptions based on directly observable characteristics.

---

# 6. Observation Object

The Observation object describes the humanitarian evidence recorded at a specific moment in time.

Every Humanitarian Record contains exactly one Observation.

An Observation answers four fundamental questions:

- What happened?
- What was observed?
- Where was it observed?
- Who reported it?

Example:

```json
{
  "observation": {

    "event_type": "hospital_admission",

    "status": "stable",

    "reported_location": "Hospital Central",

    "reported_by": "hospital",

    "observed_at": "2026-07-13T18:30:00Z",

    "public_contact": "@hospital"
  }
}
```

The Observation object contains humanitarian evidence.

It does not establish identity.

It preserves one humanitarian observation exactly as it was reported.
---

# 7. Observation Fields

The Observation object contains the humanitarian evidence associated with the reported event.

---

## event_type

Classifies the humanitarian event that generated the Observation.

Examples:

```
missing_report

hospital_admission

rescue

shelter_registration

family_reunification

veterinary_assistance
```

Event Types answer one question:

> **What happened?**

The complete semantic model is defined in **HCP-0008 — Event Type Model**.

---

## status

Describes the humanitarian condition observed at the time of the Observation.

Examples:

```
missing

stable

critical

safe

receiving_care

reunified
```

Status answers one question:

> **What was the observed condition?**

The complete semantic model is defined in **HCP-0007 — Status Model**.

---

## reported_location

Free-text description indicating where the Observation occurred.

Examples:

```
Hospital Central

Shelter A

Near Plaza Bolívar

Highway KM 18
```

Future protocol extensions may introduce structured geographic information while preserving compatibility.

---

## reported_by

Describes the humanitarian source that reported the Observation.

Examples:

```
family

hospital

volunteer

fire_department

police

friend

unknown
```

This field contributes humanitarian context.

It does not establish identity or certainty.

---

## observed_at

Timestamp describing when the humanitarian Observation occurred.

Format:

```
ISO 8601 UTC
```

Example:

```
2026-07-13T18:30:00Z
```

The Observation Timestamp represents when humanitarian evidence was observed.

It is independent of when the Humanitarian Record was created or synchronized.

---

## public_contact

Optional communication channel voluntarily provided by the reporter.

Examples:

```
+58 412 5551234

@telegram_user

person@example.org
```

This field exists exclusively to facilitate humanitarian communication.

It is not:

- a protocol identifier;
- an identity attribute;
- a correlation variable;
- a searchable identity directory.

Nodes may hide, omit or restrict this field according to local operational policies.

Matching public contact information shall never increase or decrease correlation probability.

---

# 8. Humanitarian Evidence

Unlike traditional identity-based information systems, HCP represents humanitarian evidence rather than verified identities.

Correlation evaluates multiple independent pieces of humanitarian evidence, including:

- reported_label;
- estimated_age;
- Recognition Features;
- reported_location;
- event_type;
- status;
- reported_by;
- temporal proximity.

No individual field is sufficient to establish identity.

Correlation emerges from the combined interpretation of multiple compatible observations.

Different HCP implementations may assign different weights to different evidence while preserving semantic interoperability.

---

# 9. Unknown Information

Humanitarian emergencies frequently involve incomplete information.

Unknown values should simply be omitted whenever reasonably possible.

The absence of information shall never invalidate an Observation.

Partial humanitarian evidence remains valuable.

Future Observations may complement previously recorded information without modifying earlier Humanitarian Records.

---

# 10. Future Compatibility

Future protocol versions may introduce additional optional fields.

Existing implementations should ignore unknown fields while preserving all recognized humanitarian information.

Semantic compatibility should be preserved whenever reasonably possible.

Breaking structural changes should occur only through a new major protocol version.

---

# 11. Security and Privacy

HCP protects privacy primarily through protocol design rather than by prohibiting voluntary disclosure.

The protocol never requires permanent identifiers for interoperability.

Correlation never depends on identity documents, national identifiers or centralized identity registries.

---

## Voluntary Identity Disclosure

Users may voluntarily include personally identifiable information within humanitarian observations if they believe it helps humanitarian reunification.

Examples include:

- full names;
- national identity numbers;
- telephone numbers;
- email addresses;
- additional descriptive information.

Such information is treated as humanitarian evidence.

It never becomes protocol identity.

Interoperability never depends upon personally identifiable information.

---

## Data Minimization

Implementations should encourage reporters to provide only the information genuinely useful for humanitarian purposes.

Whenever possible, humanitarian observations should remain valuable even without personally identifiable information.

---

# 12. Interoperability

Every compatible HCP implementation shall exchange Humanitarian Records using the Canonical JSON defined by this specification.

Internal implementation details remain completely independent.

Different implementations may use:

- relational databases;
- document databases;
- flat files;
- cloud storage;
- embedded devices;
- offline storage;
- distributed synchronization;
- future technologies.

Only the exchanged semantic representation is standardized.

---

# 13. Philosophy

The Canonical JSON is the shared humanitarian language of the Humanitarian Connection Protocol.

It is not:

- a database schema;
- an identity registry;
- a centralized platform;
- an application data model.

It is the semantic representation exchanged between independent humanitarian implementations.

Every Humanitarian Record preserves one humanitarian observation.

Observations preserve humanitarian evidence.

Correlation relates compatible observations.

Humanitarian Timelines emerge through correlated observations.

People interpret results.

People verify reality.

By separating semantic meaning from implementation architecture, HCP enables independent organizations to exchange meaningful humanitarian information without requiring shared software, centralized databases or global identity systems.

The Canonical JSON embodies one of the fundamental principles of HCP:

**The protocol standardizes humanitarian semantics.**

**The Canonical JSON standardizes semantic representation.**

**Implementations remain independent.**
---

# 14. Relationship with Other Specifications

The Canonical JSON Specification defines the standardized semantic representation exchanged between compatible HCP implementations.

Complementary specifications define the concepts represented by this structure.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0003** defines the Subject Model.
- **HCP-0006** defines the Observation Model.
- **HCP-0007** defines the Status Model.
- **HCP-0008** defines the Event Type Model.
- **HCP-0009** defines the Reference HTTP API.
- **HCP-0011** defines the Query Model.
- **HCP-0012** defines the Correlation Model.

Together, these specifications define both the semantic meaning and the canonical representation of humanitarian observations exchanged throughout the HCP ecosystem.

---

# 15. Summary

The Canonical JSON Specification defines the official semantic representation of Humanitarian Records within the Humanitarian Connection Protocol.

Every exchanged Humanitarian Record contains one Subject and one Observation.

The Subject describes the observed living being.

The Observation preserves the humanitarian evidence reported about that Subject at a specific moment in time.

Within every Observation:

- Event Type answers:

> **What happened?**

- Status answers:

> **What was the observed condition?**

This semantic separation allows HCP to represent humanitarian information with clarity while preserving interoperability across independent implementations.

The Canonical JSON does not standardize databases, software architectures or communication technologies.

It standardizes humanitarian meaning.

Every compatible implementation speaks the same humanitarian language regardless of how it stores, transports or internally processes information.

Humanitarian observations remain independent.

Correlation relates compatible observations.

Humanitarian Timelines emerge from correlated observations.

People interpret results.

People verify reality.

The Canonical JSON embodies one of the central architectural principles of HCP:

**The protocol standardizes humanitarian semantics.**

**The Canonical JSON standardizes semantic representation.**

**Nodes exchange observations.**

**Implementations remain independent.**

---

# 16. Canonical Architecture

The Canonical JSON reflects the conceptual architecture of the Humanitarian Connection Protocol.

```text
Humanitarian Record

├── Metadata
│
├── Subject
│     ├── type
│     ├── reported_label
│     ├── estimated_age
│     └── recognition_features
│
└── Observation
      ├── event_type
      ├── status
      ├── reported_location
      ├── reported_by
      ├── observed_at
      └── public_contact
```

This structure is intentionally semantic.

It does not prescribe software architecture, database schemas or internal object models.

Different implementations may organize information internally in completely different ways.

Interoperability is achieved because every implementation exchanges the same semantic representation.

The Canonical JSON is therefore the shared humanitarian language that allows independent HCP implementations to understand one another while preserving organizational autonomy, implementation independence and long-term protocol evolution.
