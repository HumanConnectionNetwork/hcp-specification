# HCP-0010

# Canonical JSON Specification

Version: 0.3 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-10

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0006 Observation Model
- HCP-0007 Status Model

---

# 1. Introduction

This document defines the canonical JSON representation used by the Humanitarian Connection Protocol (HCP).

Every HCP Node MUST exchange Humanitarian Records using this canonical structure.

The Canonical JSON is the common language shared by all HCP implementations, regardless of programming language, operating system, database technology or communication transport.

HCP does not define how information is stored internally.

It defines how humanitarian observations are represented and exchanged.

The canonical representation guarantees that any compliant implementation can create, exchange, store and correlate Humanitarian Records without requiring a centralized platform.

The same Humanitarian Record should be understandable by a Telegram client, a hospital information system, a mobile application, a humanitarian organization or any future HCP implementation.

---

# 2. Design Principles

The Canonical JSON follows six fundamental principles.

## Minimal

Only the information necessary to describe a humanitarian observation should be included.

The protocol intentionally avoids unnecessary complexity and excessive metadata.

---

## Portable

A Humanitarian Record should be transferable through:

- REST APIs
- JSON files
- SMS gateways
- Mesh networks
- Radio relays
- Offline synchronization
- Future communication transports

without requiring structural modifications.

---

## Deterministic

The same humanitarian observation should always produce the same canonical field structure regardless of implementation.

This guarantees interoperability between independent HCP Nodes.

---

## Extensible

Future protocol versions MAY introduce optional fields without breaking compatibility.

Older implementations MUST safely ignore unknown fields.

---

## Offline-First

The Canonical JSON is intentionally lightweight.

It is designed to be created, stored and exchanged even under limited connectivity conditions.

---

## Correlation-Oriented

A Humanitarian Record is not intended to identify people.

Its purpose is to describe humanitarian observations using structured information that allows independent observations to be correlated.

The Canonical JSON maximizes interoperability between implementations while allowing different correlation algorithms to evolve independently.

---

# 3. Canonical Structure

A Humanitarian Record SHOULD follow the structure below.

```json
{
  "id": "2d36d31d-c987-4c35-b0a8-74cb8eb9b62e",

  "schema_version": "0.3",

  "source_client": "hcp-client-telegram",

  "subject_type": "human",

  "event_type": "missing_person",

  "status": "reported",

  "reported_name": "Juan Pérez",

  "estimated_age": 42,

  "recognition_features": "Blue jacket, black backpack, glasses",

  "public_contact": "+58 412 5551234",

  "reported_location": "Caracas, Venezuela",

  "source": "family",

  "created_at": "2026-07-10T18:30:00Z"
}
```

Animal observations use the same structure while replacing the age field with animal-specific information.

Example:

```json
{
  "id": "...",

  "schema_version": "0.3",

  "source_client": "hcp-client-telegram",

  "subject_type": "animal",

  "event_type": "missing_animal",

  "status": "reported",

  "reported_name": "Luna",

  "animal_species": "dog",

  "animal_size": "medium",

  "animal_breed": "Golden Retriever",

  "recognition_features": "Red collar, white chest spot",

  "public_contact": "@juantelegram",

  "reported_location": "Rio de Janeiro",

  "source": "owner",

  "created_at": "2026-07-10T18:30:00Z"
}
```

---

# 4. Canonical Fields

## id

Globally unique identifier of the Humanitarian Record.

Type:

```
UUID
```

This identifier uniquely identifies the observation.

It MUST NOT be interpreted as the identity of a person or animal.

---

## schema_version

Version of the Canonical JSON used to generate the record.

Example:

```
0.3
```

This field allows future protocol evolution while maintaining backward compatibility.

---

## source_client

Identifies the HCP implementation that generated the record.

Examples:

```
hcp-client-telegram

hcp-client-web

hospital-system

veterinary-plugin
```

This field exists exclusively for technical interoperability and diagnostics.

It MUST NOT be used for correlation.

---

## subject_type

Defines what kind of subject is being described.

Allowed values include:

```
human

animal
```

Future protocol versions MAY introduce additional subject types.

---

## event_type

Defines the humanitarian observation.

Human examples include:

```
missing_person

hospitalized_person

sheltered_person

safe_person
```

Animal examples include:

```
missing_animal

found_animal
```

Future specifications MAY define additional event types.

---

## status

Current known state of the observation.

Typical values include:

```
reported

confirmed

updated

closed
```

Status describes the observation lifecycle.

It does not identify the person.

---

## reported_name

Name provided by the reporter.

The reported name is informational only.

It MUST NOT be interpreted as a unique identifier.

Different observations describing the same person may contain:

- spelling differences
- abbreviations
- nicknames
- incomplete names
- unknown names

Correlation algorithms should treat this field probabilistically.

---

## estimated_age

Approximate age of a human subject.

Type:

```
Integer
```

If unknown, implementations MAY omit this field.

Animal observations SHOULD omit this field.

---

## animal_species

Animal species.

Examples:

```
dog

cat

horse

bird

other
```

Only applicable when:

```
subject_type = animal
```

---

## animal_size

Approximate animal size.

Examples:

```
small

medium

large
```

Optional.

---

## animal_breed

Breed or specific animal type when known.

Examples:

```
Golden Retriever

Siamese

Quarter Horse
```

Optional.

---

## recognition_features

Free-text field describing observable characteristics that facilitate future correlation.

Typical human examples include:

- clothing
- colors
- glasses
- backpack
- tattoos
- scars
- hairstyle
- beard
- mobility aids

Typical animal examples include:

- collar
- harness
- coat color
- visible injuries
- distinctive markings
- ear shape
- tail characteristics
- limping
- eye color

Implementations SHOULD encourage concise descriptions of directly observable characteristics.

Recognition features are one of the primary correlation variables defined by HCP.

---

## public_contact

Optional public communication channel voluntarily provided by the reporter.

Examples:

```
+58 412 5551234

@telegram_user

person@example.org
```

This field exists solely to facilitate communication regarding the humanitarian observation.

It is NOT:

- a person identifier
- an identity attribute
- a correlation variable
- an indexable contact directory

The existence of this field does not imply the existence of a centralized contact database.

Nodes MAY hide, omit or restrict the visibility of this field according to local policies or security requirements.

---

## reported_location

Free-text location describing where the observation occurred.

Examples:

```
Hospital Central

Shelter A

Near Plaza Bolívar

Highway KM 18
```

Coordinates MAY be introduced by future protocol extensions.

---

## source

Describes the origin of the observation.

Examples:

```
family

hospital

volunteer

police

fire_department

friend

unknown
```

Future specifications MAY define additional source values.

---

## created_at

Timestamp indicating when the observation was created.

Format:

```
ISO 8601 UTC
```

Example:

```
2026-07-10T18:30:00Z
```

Every Humanitarian Record SHOULD include this field.
---

# 5. Correlation Variables

Unlike traditional record formats, HCP does not define Humanitarian Records as identity records.

Instead, they are structured humanitarian observations that may describe the same real-world event from different independent sources.

Correlation algorithms compare descriptive fields to estimate the probability that two or more observations refer to the same humanitarian case.

The protocol intentionally does not prescribe a mandatory correlation algorithm.

Each HCP implementation MAY adopt different scoring techniques provided that the semantic meaning of the Canonical JSON remains unchanged.

Typical correlation variables include:

- reported_name
- estimated_age
- animal_species
- animal_size
- animal_breed
- recognition_features
- reported_location
- event_type
- status
- source
- temporal proximity

Different implementations MAY assign different weights to each variable.

For example:

- a veterinary implementation may prioritize animal characteristics;
- a hospital may prioritize location and timestamps;
- a humanitarian organization may prioritize descriptive observations.

HCP intentionally allows implementations to innovate while preserving interoperability.

## Non-Correlation Fields

Some fields exist exclusively for technical interoperability or communication.

These fields MUST NOT participate in correlation.

They include:

- id
- schema_version
- source_client
- public_contact

Matching public contact information MUST NEVER increase or decrease the probability of correlation.

The purpose of public_contact is communication only.

---

# 6. Unknown Information

Incomplete observations are expected during humanitarian emergencies.

Implementations SHOULD encourage reporters to provide the best available information at the time of the observation.

Unknown information SHOULD simply be omitted whenever possible.

Placeholder values SHOULD only be used when required by a particular implementation.

Examples include:

```
Unknown
```

or

```
Not specified
```

The absence of a field MUST NOT invalidate a Humanitarian Record.

A partially completed observation can still contribute to humanitarian correlation.

---

# 7. Future Compatibility

Future protocol versions MAY introduce additional optional fields.

Existing implementations MUST ignore unknown fields while preserving all recognized fields.

This approach guarantees forward compatibility between protocol versions.

Canonical JSON evolution MUST preserve semantic compatibility whenever possible.

Breaking changes SHOULD only occur through a new major protocol version.

---

# 8. Security Considerations

Humanitarian Records intentionally minimize reliance on personally identifying information.

HCP is designed around observations rather than verified identities.

Implementations SHOULD collect only the information necessary to facilitate humanitarian correlation.

## Public Contact

The public_contact field is entirely optional.

It exists only when the reporter voluntarily decides to provide a public communication channel regarding that observation.

Examples include:

- telephone number
- Telegram username
- email address
- other publicly shareable contact

Nodes MAY:

- omit this field;
- hide this field;
- expose it only to authorized users;
- remove it during synchronization according to local policies.

Implementations MUST NOT interpret public_contact as proof of identity.

Implementations SHOULD avoid exposing public contacts through searchable directories or bulk exports.

The existence of public_contact does not imply the existence of a centralized contact database.

## Privacy

HCP implementations SHOULD avoid collecting unnecessary personal information.

The protocol encourages describing observable humanitarian facts rather than personal identity attributes.

Whenever possible, observations should remain useful even if no direct contact information is available.

---

# 9. Interoperability

Every HCP implementation MUST generate Canonical JSON representations compatible with this specification.

Programming language, database technology, operating system, communication protocol or storage mechanism MUST NOT modify the semantic meaning of a Humanitarian Record.

The Canonical JSON represents the common language exchanged between all HCP Nodes.

Applications implementing HCP are free to use:

- relational databases;
- document databases;
- flat files;
- cloud storage;
- offline storage;
- distributed synchronization;
- future storage technologies.

The protocol defines the exchanged representation, not the internal implementation.

Consequently, two completely independent systems can interoperate as long as both produce and consume Canonical HCP Records.

---

# 10. Philosophy

The Humanitarian Connection Protocol is not a centralized platform.

It is not a humanitarian database.

It is not an identity registry.

HCP is an interoperability standard.

Its purpose is to enable independent organizations, institutions, governments, humanitarian initiatives, volunteers and software applications to exchange structured humanitarian observations using a common language.

Every new implementation strengthens the value of every existing implementation.

The protocol grows through interoperability rather than centralization.

Humanitarian observations remain distributed.

The language used to exchange them remains shared.

This distinction is one of the fundamental principles of the Humanitarian Connection Protocol.
