# HCP-0010
# Canonical JSON Specification

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0006 Observation Model
- HCP-0007 Status Model

---

# 1. Introduction

This document defines the canonical JSON representation used by the Humanitarian Connection Protocol (HCP).

Every HCP Node MUST exchange Humanitarian Records using this structure.

The canonical JSON is designed to be:

- Human-readable
- Machine-readable
- Deterministic
- Language-independent
- Extensible
- Offline-first

The canonical representation guarantees that any compliant implementation can create, exchange, store and correlate Humanitarian Records without requiring a centralized platform.

---

# 2. Design Principles

The canonical JSON follows five fundamental principles.

## Minimal

Only the information required to describe a humanitarian observation should be included.

## Portable

A record must be transferable through APIs, files, SMS gateways, radio relays or mesh networks without modification.

## Deterministic

The same observation should always produce the same field structure regardless of implementation.

## Extensible

Future protocol versions may introduce optional fields without breaking compatibility.

## Correlation-Oriented

The primary purpose of a Humanitarian Record is not merely to store information.

Its purpose is to maximize the probability that another HCP Node can correlate multiple independent observations describing the same humanitarian event.

Every field should therefore be considered a potential correlation variable.

---

# 3. Canonical Structure

A Humanitarian Record SHOULD follow the structure below.

```json
{
  "record_id": "2d36d31d-c987-4c35-b0a8-74cb8eb9b62e",

  "subject": "person",

  "event_type": "missing",

  "status": "reported",

  "reported_name": "Juan Pérez",

  "estimated_age": 42,

  "recognition_features": "Blue jacket, black backpack, glasses",

  "reported_location": "Caracas, Venezuela",

  "reported_by": "family",

  "created_at": "2026-07-07T16:30:00Z"
}
```

---

# 4. Required Fields

## record_id

Globally unique identifier.

Type:

```
UUID
```

Example:

```
2d36d31d-c987-4c35-b0a8-74cb8eb9b62e
```

---

## subject

Identifies what kind of subject is being reported.

Allowed values include:

```
person
animal
```

Future protocol versions may introduce additional subject types.

---

## event_type

Defines the humanitarian event being reported.

Examples:

```
missing
hospitalized
sheltered
located
```

Animal-specific event types are defined in HCP-0007.

---

## status

Current known status of the reported event.

Examples:

```
reported
confirmed
updated
closed
```

---

## reported_name

Name provided by the reporter.

The value is informational only.

It MUST NOT be interpreted as a unique identifier.

Unknown names MAY contain values such as:

```
Unknown
```

---

## estimated_age

Approximate age.

Integer.

If unknown, implementations MAY omit the field.

---

## recognition_features

Free-text field describing observable characteristics that help identify the reported subject.

This field is one of the primary correlation variables defined by HCP.

Typical examples include:

For persons:

- clothing
- colors
- glasses
- backpack
- tattoos
- scars
- hairstyle
- beard
- mobility aids

Examples:

```
Blue jacket
Black backpack
Long curly hair
Red shirt
Uses glasses
Tattoo on left arm
```

For animals:

- collar
- coat color
- visible injuries
- distinctive markings
- ear shape
- tail characteristics
- harness
- limp

Examples:

```
Red collar
Brown coat
White chest spot
Missing left ear tip
Limping front leg
```

Implementations SHOULD encourage reporters to provide concise, observable characteristics rather than narratives.

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

Coordinates MAY be added in future protocol versions.

---

## reported_by

Describes the origin of the observation.

Typical values include:

```
family
hospital
volunteer
police
fire_department
friend
unknown
```

Additional values MAY be introduced by future specifications.

---

## created_at

Timestamp indicating when the record was created.

Format:

```
ISO 8601 UTC
```

Example:

```
2026-07-07T16:30:00Z
```

---

# 5. Correlation Variables

Unlike traditional record formats, HCP defines every field as a potential correlation signal.

Typical correlation variables include:

- reported_name
- estimated_age
- recognition_features
- reported_location
- event_type
- status
- reported_by
- temporal proximity

Correlation algorithms MAY assign different weights to each variable depending on the implementation.

The protocol intentionally does not prescribe a mandatory correlation algorithm.

---

# 6. Unknown Information

Incomplete observations are expected during humanitarian emergencies.

Unknown values SHOULD be omitted whenever possible.

Placeholder values SHOULD only be used when required by a specific implementation.

The absence of a field MUST NOT invalidate a Humanitarian Record.

---

# 7. Future Compatibility

Future protocol versions MAY introduce optional fields.

Existing implementations MUST ignore unknown fields while preserving known fields.

This guarantees forward compatibility between protocol versions.

---

# 8. Security Considerations

The canonical JSON intentionally avoids relying on personally identifying information.

Humanitarian Records describe observations, not verified identities.

Nodes SHOULD minimize unnecessary personal information while maximizing useful correlation variables.

---

# 9. Interoperability

Every HCP implementation MUST generate compatible canonical JSON representations.

Programming language, database technology or transport protocol MUST NOT alter the semantic meaning of the record.

This canonical structure represents the common language exchanged between all HCP Nodes.
