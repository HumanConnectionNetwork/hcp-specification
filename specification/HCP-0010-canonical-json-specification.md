# HCP-0010

# Canonical JSON Specification

Version: 0.5 (Draft)

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
- HCP-0008 — Event Type Model

Replaces:
None

Replaced By:
None

---

# Abstract

This document defines the Canonical JSON Specification of the Humanitarian Connection Protocol (HCP).

The Canonical JSON is the normative semantic representation of every Humanitarian Record exchanged between compatible HCP implementations.

It is the shared humanitarian language of HCP.

Every Humanitarian Record exchanged between HCP Nodes shall be represented using this canonical structure.

The Canonical JSON standardizes humanitarian semantics.

It does not standardize databases, software architectures, communication technologies or internal implementation models.

Its purpose is to enable independent implementations to exchange Humanitarian Records while preserving semantic interoperability, implementation independence and long-term protocol evolution.

---

# 1. Introduction

The Humanitarian Connection Protocol defines a common semantic model for representing humanitarian observations.

The Canonical JSON is the official representation of that semantic model.

Every Humanitarian Record exchanged between compatible HCP Nodes shall follow this specification.

Internal implementations remain completely free to organize information according to their own technical requirements.

However, whenever Humanitarian Records are exchanged, every implementation should produce the same canonical semantic representation.

This separation between internal implementation and exchanged representation allows HCP to preserve semantic interoperability without constraining technological freedom.

The Canonical JSON is therefore the common humanitarian language spoken by every compatible HCP implementation.

---

# 2. Purpose

The purpose of the Canonical JSON Specification is to define the normative representation of Humanitarian Records exchanged by HCP.

Rather than defining internal software architectures or storage models, this specification defines the semantic structure that every compatible implementation shall exchange.

The Canonical JSON enables:

- semantic interoperability;
- implementation independence;
- explainable correlation;
- protocol evolution;
- long-term compatibility.

This specification answers one fundamental question:

> **How is a Humanitarian Record represented when exchanged?**

---

# 3. Canonical Representation

Every compliant HCP implementation shall be capable of exporting every Humanitarian Record using the Canonical JSON defined by this specification.

Likewise, every compliant implementation shall be capable of importing Canonical JSON representations produced by other compatible HCP Nodes.

Internal storage models remain entirely implementation-specific.

Examples include:

- relational databases;
- document databases;
- embedded storage;
- object models;
- flat files;
- distributed storage;
- future implementation technologies.

Only the exchanged semantic representation is standardized.

This distinction preserves both interoperability and implementation freedom.

---

# 4. Design Principles

The Canonical JSON follows the architectural principles of HCP.

## Semantic

The Canonical JSON standardizes humanitarian meaning.

It never standardizes implementation behavior.

---

## Observation-Based

Every Canonical JSON represents exactly one Humanitarian Observation through one Humanitarian Record.

It never represents:

- permanent identity;
- humanitarian history;
- centralized person profiles;
- Humanitarian Cases.

---

## Deterministic

Equivalent Humanitarian Records should always produce equivalent Canonical JSON representations regardless of implementation.

Deterministic representation guarantees semantic interoperability between independent HCP Nodes.

---

## Minimal

Only humanitarian information necessary to represent one Humanitarian Observation should be included.

Implementation-specific metadata should remain outside the Canonical JSON whenever possible.

---

## Stable

The Canonical JSON should evolve conservatively.

Equivalent Humanitarian Records should remain semantically compatible across protocol versions whenever reasonably possible.

---

## Portable

Canonical Humanitarian Records should be transferable through any compatible communication technology without semantic modification.

Examples include:

- HTTP;
- gRPC;
- Message Queues;
- MQTT;
- Mesh Networks;
- Satellite Communication;
- Offline Synchronization;
- removable media;
- future communication technologies.

---

## Extensible

Future protocol versions may introduce optional semantic elements while preserving compatibility whenever reasonably possible.

Older implementations should safely ignore unknown fields while preserving recognized humanitarian information.

---

## Correlation-Oriented

The Canonical JSON represents humanitarian evidence.

It does not establish identity.

Its purpose is to support explainable humanitarian correlation while allowing correlation algorithms to evolve independently.

The protocol standardizes semantics.

Implementations define correlation.

---

# 5. Canonical Structure

Every Humanitarian Record shall follow the semantic structure defined below.

The Canonical JSON represents exactly one Humanitarian Observation.

Conceptually, every Humanitarian Record consists of three semantic sections:

- Record Metadata;
- Subject;
- Observation.

Illustrative structure:

```json
{
  "id": "2d36d31d-c987-4c35-b0a8-74cb8eb9b62e",

  "schema_version": "0.5",

  "source_client": "hcp-client-telegram",

  "subject": {

    "type": "human",

    "reported_label": "Juan Pérez",

    "estimated_age": 42,

    "recognition_features": "Blue jacket, black backpack, glasses"

  },

  "observation": {

    "event_type": "hospital_admission",

    "reported_location": "Hospital Central",

    "reported_by": "hospital",

    "observed_at": "2026-07-13T18:30:00Z",

    "public_contact": "@hospital"
  }
}
```

Internal software architectures may organize information differently.

Only the exchanged semantic representation defined by this specification is normative.
---
# 6. Record Metadata

The Record Metadata identifies the Humanitarian Record itself.

Metadata belongs exclusively to the Humanitarian Record.

It never belongs to the observed Subject.

It never identifies a person or animal.

---

## id

Globally unique identifier of the Humanitarian Record.

Type:

```
UUID
```

The identifier uniquely identifies one Humanitarian Record.

It never identifies a Subject.

Every new Humanitarian Observation generates a new UUID.

---

## schema_version

Version of the Canonical JSON Specification used to generate the Humanitarian Record.

Example:

```
0.5
```

This field enables long-term protocol evolution while preserving interoperability between different HCP versions.

---

## source_client

Technical identifier of the implementation that generated the Humanitarian Record.

Examples:

```
hcp-client-telegram

hcp-client-web

hospital-system

veterinary-plugin
```

This field exists exclusively for interoperability diagnostics.

It shall never participate in:

- humanitarian correlation;
- ranking;
- identity determination.

---

# 7. Subject Object

The Subject object describes the observed Subject.

It contains humanitarian evidence describing the living being referenced by the Humanitarian Observation.

The Subject object intentionally avoids permanent identity concepts.

Its purpose is to describe the observed Subject rather than identify an individual.

Illustrative example:

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

The complete semantic definition of the Subject is provided by **HCP-0003 — Subject Model**.

---

## type

Defines the Subject Type.

Examples:

```
human

animal
```

Future HCP specifications may define additional Subject Types while preserving semantic compatibility.

---

## reported_label

Human-readable label reported by the observer.

Examples:

```
Juan Pérez

Unknown child

Adult male

White dog

Green parrot
```

The Reported Label is humanitarian evidence.

It is not:

- a protocol identifier;
- verified identity;
- permanent identifier.

Different Humanitarian Records concerning the same Subject may legitimately contain different Reported Labels.

Correlation evaluates this field together with all other humanitarian evidence.

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

Estimated Age contributes humanitarian evidence.

It never establishes identity.

---

## recognition_features

Free-text description of directly observable characteristics.

Examples for humans include:

- clothing;
- glasses;
- tattoos;
- scars;
- hairstyle;
- mobility aids;
- backpacks.

Examples for animals include:

- collar;
- coat color;
- distinctive markings;
- tail characteristics;
- ear shape;
- visible injuries.

Recognition Features represent one of the strongest sources of humanitarian evidence available for explainable correlation.

Implementations should encourage concise descriptions based exclusively on directly observable characteristics.

---

# 8. Observation Object

The Observation object preserves the humanitarian evidence observed at one specific moment in time.

Every Humanitarian Record contains exactly one Observation.

The Observation answers four fundamental questions:

- What happened?
- Where did it happen?
- Who reported it?
- When was it observed?

Illustrative example:

```json
{
  "observation": {

    "event_type": "hospital_admission",

    "reported_location": "Hospital Central",

    "reported_by": "hospital",

    "observed_at": "2026-07-13T18:30:00Z",

    "public_contact": "@hospital"

  }
}
```

The Observation preserves humanitarian evidence.

It does not establish identity.

It preserves one humanitarian observation exactly as it was reported.

---

# 9. Observation Fields

The Observation object contains the humanitarian evidence associated with the observed event.

---

## event_type

Defines the humanitarian meaning of the Observation.

Examples:

```
missing_report

hospital_admission

rescue

shelter_registration

family_reunification

veterinary_assistance
```

Every Observation contains exactly one Event Type.

Event Types answer one fundamental question:

> **What happened?**

The complete semantic definition is provided by **HCP-0008 — Event Type Model**.

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

Future protocol versions may introduce optional structured geographic information while preserving backward compatibility.

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

The reporting source contributes humanitarian context.

It never establishes identity or certainty.

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

It is independent of:

- record creation;
- synchronization;
- correlation.

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

It is never:

- a protocol identifier;
- humanitarian evidence;
- a correlation variable;
- a searchable identity directory.

Matching Public Contact information shall never increase or decrease correlation probability.

Implementations may hide, restrict or omit this field according to their local operational policies.
---
# 10. Humanitarian Evidence

Unlike traditional identity-based information systems, HCP represents humanitarian evidence rather than verified identities.

Every field contained within the Canonical JSON contributes humanitarian evidence.

Examples include:

- Reported Label;
- Estimated Age;
- Recognition Features;
- Event Type;
- Reported Location;
- Reporting Source;
- Observation Timestamp.

No individual field is sufficient to establish identity.

Correlation evaluates the complete humanitarian context represented by one or more independent Humanitarian Records.

Different HCP implementations may assign different relevance to different evidence while preserving semantic interoperability.

The protocol standardizes humanitarian evidence.

Implementations define correlation.

---

# 11. Unknown Information

Humanitarian emergencies frequently involve incomplete information.

Unknown values should simply be omitted whenever reasonably possible.

Missing information shall never invalidate a Humanitarian Record.

Partial humanitarian evidence remains valuable.

Future Humanitarian Observations may complement previously recorded information without modifying earlier Humanitarian Records.

The absence of information is itself part of the humanitarian context.

---

# 12. Future Compatibility

Future protocol versions may introduce additional optional fields.

Compatible implementations should safely ignore unknown fields while preserving all recognized humanitarian information.

Semantic compatibility should always be preserved whenever reasonably possible.

Breaking structural changes should occur only through a new major protocol version.

Stable semantic evolution is one of the architectural principles of HCP.

---

# 13. Security and Privacy

The Canonical JSON protects privacy primarily through protocol architecture rather than by prohibiting voluntary disclosure.

The protocol never requires:

- national identifiers;
- passports;
- medical record numbers;
- centralized identity registries;
- permanent protocol identities.

Interoperability depends on humanitarian observations rather than administrative identities.

---

## Voluntary Information

Reporters may voluntarily include personally identifiable information whenever they believe it contributes to humanitarian reunification.

Examples include:

- names;
- telephone numbers;
- email addresses;
- organization names;
- additional descriptive information.

Such information remains humanitarian evidence.

It never becomes protocol identity.

Correlation should never depend exclusively upon personally identifiable information.

---

## Data Minimization

Implementations should encourage reporters to provide only the information genuinely useful for humanitarian purposes.

Whenever equivalent humanitarian value can be achieved through humanitarian observations, implementations should prefer humanitarian evidence over personally identifiable information.

Additional privacy guidance is defined in **HCP-0021 — Privacy and Data Minimization**.

---

# 14. Interoperability

Every compatible HCP implementation shall exchange Humanitarian Records using the Canonical JSON defined by this specification.

Internal implementation details remain completely independent.

Implementations may freely choose:

- relational databases;
- document databases;
- flat files;
- cloud storage;
- embedded devices;
- offline storage;
- distributed synchronization;
- future storage technologies.

Only the exchanged semantic representation is standardized.

Shared semantics enable universal interoperability.

---

# 15. Relationship with Other Specifications

The Canonical JSON Specification defines the normative semantic representation exchanged between compatible HCP implementations.

Complementary specifications define the concepts represented by this structure.

```text
HCP-0001
Humanitarian Record
        │
        ▼
HCP-0003
Subject Model
        │
        ▼
HCP-0006
Observation Model
        │
        ▼
HCP-0008
Event Type Model
        │
        ▼
HCP-0010
Canonical JSON
        │
        ├───────────────┐
        ▼               ▼
HCP-0009          HCP-0011
Reference API     Query Model
        │               │
        └───────┬───────┘
                ▼
          HCP-0012
      Correlation Model
                │
                ▼
          HCP-0013
     Synchronization
```

Each specification has a distinct responsibility.

- **HCP-0001** defines the Humanitarian Record.
- **HCP-0003** defines the Subject.
- **HCP-0006** defines the Humanitarian Observation.
- **HCP-0008** defines the humanitarian meaning through Event Types.
- **HCP-0009** defines one recommended HTTP binding.
- **HCP-0010** defines the Canonical JSON representation.
- **HCP-0011** defines humanitarian queries.
- **HCP-0012** defines local correlation.
- **HCP-0013** defines synchronization.

Together, these specifications define how humanitarian observations are represented, exchanged and interpreted while preserving semantic interoperability.

---

# 16. Summary

The Canonical JSON Specification defines the official semantic representation of Humanitarian Records within the Humanitarian Connection Protocol.

Every exchanged Humanitarian Record contains one Subject and one Observation.

The Subject describes the observed living being.

The Observation preserves humanitarian evidence observed at one specific moment in time.

Within every Observation:

- **Event Type answers:**

> **What happened?**

The remaining Observation fields provide humanitarian context supporting explainable correlation.

The Canonical JSON does not standardize:

- databases;
- software architectures;
- programming languages;
- communication technologies;
- internal object models.

It standardizes humanitarian semantics.

Every compatible implementation speaks the same humanitarian language regardless of how information is internally stored, transported or processed.

Humanitarian Observations preserve evidence.

Humanitarian Records preserve observations.

Event Types define meaning.

Correlation creates local understanding.

Humanitarian Cases communicate interpretation.

People verify reality.

The Canonical JSON embodies one of the central architectural principles of HCP:

**The protocol standardizes humanitarian semantics.**

**The Canonical JSON standardizes semantic representation.**

**Nodes exchange Humanitarian Records.**

**Implementations remain independent.**

---

# 17. Canonical Architecture

The Canonical JSON reflects the conceptual architecture of the Humanitarian Connection Protocol.

```text
Humanitarian Record

├── Record Metadata
│     ├── id
│     ├── schema_version
│     └── source_client
│
├── Subject
│     ├── type
│     ├── reported_label
│     ├── estimated_age
│     └── recognition_features
│
└── Observation
      ├── event_type
      ├── reported_location
      ├── reported_by
      ├── observed_at
      └── public_contact
```

This structure is intentionally semantic.

It does not prescribe:

- software architectures;
- database schemas;
- programming languages;
- internal object models.

Different implementations may internally organize information in completely different ways.

Interoperability is achieved because every compatible implementation exchanges the same Canonical JSON representation.

The Canonical JSON is the common humanitarian language that enables autonomous HCP implementations to understand one another while preserving organizational autonomy, implementation independence and long-term protocol evolution.
