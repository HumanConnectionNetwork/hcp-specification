# HCP Validation Rules

Version: 0.1 (Draft)

Status: Draft

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-14

---

# Introduction

This document defines the validation rules applicable to machine-readable structures used by the Humanitarian Connection Protocol (HCP).

Its purpose is to explain how HCP data should be validated using:

* JSON Schema validation;
* semantic validation;
* protocol conformance validation;
* local operational validation.

This document complements the schemas contained in:

```text
schema/
```

It does not replace the normative HCP specifications.

Whenever this document conflicts with a normative HCP specification, the normative specification takes precedence.

---

# Purpose

Validation protects semantic interoperability between independent HCP implementations.

A valid HCP structure should preserve:

* the expected JSON structure;
* required protocol fields;
* correct data types;
* canonical field formats;
* humanitarian semantic meaning;
* protocol compatibility.

Validation confirms that information can be processed according to HCP.

It does not confirm that the humanitarian information is true.

---

# Validation Layers

HCP validation is divided into four conceptual layers.

```text
JSON Syntax

        │

        ▼

Schema Validation

        │

        ▼

Semantic Validation

        │

        ▼

Conformance and Operational Validation
```

Each layer has a different responsibility.

---

# 1. JSON Syntax Validation

Every machine-readable HCP document MUST be valid JSON before additional validation is attempted.

Syntax validation verifies:

* valid JSON encoding;
* correctly paired braces and brackets;
* valid strings;
* valid numbers;
* valid property separators;
* absence of comments.

Illustrative invalid JSON:

```json
{
  "subject": {
    "type": "human",
  }
}
```

The trailing comma makes the document invalid JSON.

Syntax validation does not evaluate HCP semantics.

---

# 2. JSON Schema Validation

JSON Schema validation verifies the structural requirements defined by the machine-readable HCP schemas.

Current schemas include:

```text
hcp-record.schema.json

query.schema.json

humanitarian-case.schema.json
```

Schema validation may verify:

* required properties;
* property types;
* UUID formats;
* timestamp formats;
* minimum string lengths;
* allowed Subject Types;
* conditional field restrictions;
* canonical token formatting;
* nested object structure.

Passing schema validation means only that the document is structurally compatible with the corresponding schema.

It does not automatically imply complete HCP conformance.

---

# 3. Semantic Validation

Semantic validation verifies relationships and rules that may not be completely expressible through JSON Schema.

Illustrative semantic rules include:

* `source_client` MUST NOT participate in humanitarian correlation;
* `public_contact` MUST NOT increase or decrease correlation confidence;
* a Humanitarian Record MUST represent exactly one Humanitarian Observation;
* a Humanitarian Record UUID identifies the record, never the Subject;
* a Humanitarian Case MUST remain local;
* Correlation Candidates MUST NOT be synchronized;
* unknown optional fields SHOULD be preserved whenever technically possible;
* unknown Event Types MUST NOT automatically invalidate otherwise compatible Humanitarian Records.

Semantic validation requires protocol-aware processing.

It cannot always be reduced to structural schema checks.

---

# 4. Conformance Validation

Conformance validation verifies whether an implementation preserves the normative behavioral requirements of HCP.

Conformance includes more than validating individual JSON documents.

Illustrative conformance requirements include:

* preserving immutable Humanitarian Records;
* exchanging complete Canonical JSON representations;
* keeping correlation local;
* distinguishing humanitarian evidence from interpretation;
* preserving unknown optional fields when technically possible;
* preventing Humanitarian Cases from being synchronized;
* maintaining transport-independent humanitarian semantics.

Conformance requirements are defined by:

* HCP-0022 — Conformance Requirements

Schema validation is necessary for interoperability.

It is not sufficient for complete conformance.

---

# 5. Operational Validation

Organizations may apply additional local validation according to their operational environment.

Illustrative local rules include:

* authorization requirements;
* accepted Event Types;
* synchronization permissions;
* geographic scope;
* maximum field lengths;
* permitted Public Contact formats;
* retention policies;
* federation policies;
* legal requirements.

Operational validation remains implementation-specific.

Local rules MUST NOT redefine standardized HCP semantics.

---

# Humanitarian Record Validation

Humanitarian Records are validated using:

```text
hcp-record.schema.json
```

A structurally valid Humanitarian Record contains:

```text
id

schema_version

source_client

subject

observation
```

---

## Record Identifier

The `id` property MUST:

* be present;
* be a valid UUID;
* identify exactly one Humanitarian Record;
* never identify the observed Subject.

Every new Humanitarian Observation MUST generate a new Humanitarian Record identifier.

Implementations MUST NOT reuse an existing Record UUID for a different observation.

---

## Schema Version

The `schema_version` property MUST identify the Canonical JSON version used by the Humanitarian Record.

For the current schema:

```json
"schema_version": "0.5"
```

Documents using another Canonical JSON version should be validated using the corresponding versioned schema.

Implementations SHOULD advertise the schema versions they support.

---

## Source Client

The `source_client` property MUST:

* be a non-empty string;
* identify the implementation that generated the Humanitarian Record.

The property MUST NOT be interpreted as:

* humanitarian evidence;
* source credibility;
* identity evidence;
* a correlation variable.

Its purpose is limited to technical interoperability and diagnostics.

---

# Subject Validation

Every Humanitarian Record and every Query contains a Subject structure.

The Subject `type` MUST be present.

Current allowed values are:

```text
human

animal
```

---

## Reported Label

When present, `reported_label` MUST be a non-empty string.

A Reported Label:

* MAY contain a reported name;
* MAY contain a descriptive label;
* MUST NOT be treated as verified identity;
* MUST NOT be treated as a unique identifier.

Examples include:

```text
María González

Unknown child

Max

White dog
```

Unknown Reported Labels SHOULD be omitted rather than represented using empty strings or null values.

---

## Estimated Age

When present, `estimated_age` MUST:

* be an integer;
* be greater than or equal to zero;
* apply only to a human Subject.

An animal Subject MUST NOT contain `estimated_age` under the current Canonical JSON model.

Unknown age values SHOULD be omitted.

---

## Recognition Features

When present, `recognition_features` MUST be a non-empty string in Canonical JSON version 0.5.

Recognition Features SHOULD:

* describe directly observable characteristics;
* remain concise;
* avoid conclusions;
* avoid speculative identity claims;
* avoid unnecessary sensitive information.

Illustrative valid value:

```text
Blue jacket, small black backpack, gray hair
```

Illustrative inappropriate value:

```text
This is definitely María González
```

The second value contains a conclusion rather than observable humanitarian evidence.

---

# Observation Validation

Every Humanitarian Record MUST contain one `observation` object.

The Observation MUST contain:

```text
event_type

reported_by

observed_at
```

`reported_location` and `public_contact` remain optional.

---

## Event Type

The `event_type` property MUST:

* be a non-empty string;
* use a language-independent canonical value;
* follow lowercase `snake_case` formatting.

Illustrative values include:

```text
missing_report

hospital_admission

shelter_registration

rescue

family_reunification

public_emergency_report

found_animal
```

Unknown Event Types MUST NOT automatically invalidate an otherwise compatible Humanitarian Record.

This rule preserves forward compatibility.

An implementation MAY restrict unsupported Event Types for local operations, but it SHOULD preserve their original semantic value whenever technically possible.

---

## Reported Location

When present, `reported_location` MUST be a non-empty string.

Reported Location:

* MAY identify a facility;
* MAY identify a neighborhood or area;
* MAY contain a descriptive location;
* SHOULD avoid unnecessary precision when equivalent humanitarian value can be achieved with a broader location.

HCP currently treats Reported Location as free text.

Geographic interpretation remains implementation-specific.

---

## Reporting Source

The `reported_by` property MUST:

* be a non-empty string;
* use a canonical lowercase token;
* follow `snake_case` formatting.

Illustrative values include:

```text
family

hospital

volunteer

fire_department

police

friend

unknown
```

The reporting source provides humanitarian context.

It does not establish humanitarian truth.

---

## Observation Timestamp

The `observed_at` property MUST:

* be present;
* be a valid ISO 8601 / RFC 3339 date-time value;
* represent when the humanitarian situation was observed.

Illustrative valid value:

```text
2026-07-14T09:20:00Z
```

The Observation Timestamp is independent of:

* record creation time;
* synchronization time;
* query execution time;
* correlation time.

Implementations SHOULD use UTC timestamps whenever reasonably possible.

---

## Public Contact

When present, `public_contact` MUST be a non-empty string.

Public Contact MAY contain:

* a telephone number;
* a username;
* an email address;
* another voluntary communication channel.

Public Contact:

* MUST NOT identify the Humanitarian Record;
* MUST NOT identify the Subject as a protocol identity;
* MUST NOT participate in correlation;
* MAY be hidden or restricted by local privacy policies.

Unknown Public Contact information SHOULD be omitted.

---

# Humanitarian Record Immutability

Schema validation alone cannot guarantee immutability.

Every conformant implementation MUST ensure that a published Humanitarian Record is never modified.

If new humanitarian information becomes available:

```text
New Observation

        │

        ▼

New Humanitarian Record
```

The previous Humanitarian Record remains unchanged.

Implementations MUST NOT:

* overwrite the original observation;
* change the Event Type of a published record;
* replace the Record UUID;
* modify synchronized humanitarian evidence.

---

# Query Validation

Queries are validated using:

```text
query.schema.json
```

A Query represents the humanitarian evidence currently known by the person initiating a search.

A Query is not a Humanitarian Record.

---

## Required Query Information

Every Query MUST contain:

```text
subject
```

Every Query Subject MUST contain:

```text
type
```

The Observation Query remains optional.

---

## Partial Queries

Incomplete Queries are valid.

Illustrative valid Query:

```json
{
  "subject": {
    "type": "human",
    "reported_label": "María González"
  }
}
```

Another valid Query:

```json
{
  "subject": {
    "type": "animal",
    "recognition_features": "Light brown coat, red collar"
  }
}
```

Unknown information SHOULD be omitted.

Implementations MUST NOT require complete identity information.

---

## Query Observation

When present, the Query `observation` object MUST contain at least one property.

Supported properties currently include:

```text
event_type

reported_location
```

A present but empty Observation Query is invalid:

```json
{
  "subject": {
    "type": "human"
  },
  "observation": {}
}
```

---

## Query Exclusions

A Query SHOULD NOT contain Humanitarian Record metadata such as:

```text
id

schema_version

source_client

reported_by

observed_at

public_contact
```

A Query MUST NOT contain:

* Correlation Scores;
* Supporting Evidence;
* Conflicting Evidence;
* Humanitarian Cases;
* identity confirmation.

Queries describe known humanitarian evidence.

They do not contain results or conclusions.

---

# Search Result Validation

Search results consist of Humanitarian Records retrieved in response to a Query.

Every returned Humanitarian Record MUST independently validate against:

```text
hcp-record.schema.json
```

Search result containers may be implementation-specific unless standardized by a future HCP specification.

Search results MUST NOT introduce correlation conclusions during the retrieval stage.

Search returns Humanitarian Records.

Correlation begins only after retrieval concludes.

---

# Humanitarian Case Validation

Humanitarian Cases may be validated using:

```text
humanitarian-case.schema.json
```

This is a reference schema.

Humanitarian Cases are local implementation objects.

Their representation is not part of Canonical HCP JSON interoperability.

---

## Local Identifier

The `case_id` property identifies one local Humanitarian Case.

It MUST NOT be interpreted as:

* a Subject identifier;
* a Humanitarian Record identifier;
* a globally synchronized identifier;
* verified identity.

---

## Humanitarian Summary

The `humanitarian_summary` property MUST:

* be a non-empty string;
* describe the current humanitarian interpretation;
* avoid presenting interpretation as verified fact.

Recommended wording includes uncertainty terms such as:

```text
may

likely

appears

suggests

possibly
```

---

## Correlation Score

A Correlation Score MUST be numeric when represented by the reference schema.

HCP does not prescribe:

* a range;
* a probability model;
* a formula;
* weighting rules.

Implementations MUST document the meaning of their local score where necessary.

A Correlation Score MUST NOT be presented as identity confirmation.

---

## Evidence Validation

Each Supporting Evidence or Conflicting Evidence item MUST contain:

```text
type

description
```

Evidence descriptions SHOULD:

* explain humanitarian relevance;
* remain human-readable;
* avoid exposing implementation algorithms;
* avoid claiming certainty.

---

## Related Records

Every related record reference MUST identify an existing immutable Humanitarian Record.

Related Humanitarian Records MUST NOT be modified when included in a Humanitarian Case.

A Humanitarian Case references evidence.

It does not replace evidence.

---

## Human Verification

Every reference Humanitarian Case contains a `verification` object.

When:

```json
"status": "human_verified"
```

the reference schema requires:

```text
verified_at
```

Verification remains a local operational decision.

A verified Humanitarian Case MUST NOT be synchronized as humanitarian evidence.

Human verification does not convert a Humanitarian Case into a Humanitarian Record.

---

# Null Values

Optional unknown values SHOULD be omitted rather than represented as `null`.

Preferred:

```json
{
  "subject": {
    "type": "human",
    "estimated_age": 78
  }
}
```

Avoid:

```json
{
  "subject": {
    "type": "human",
    "reported_label": null,
    "estimated_age": 78
  }
}
```

Omitting unknown values improves:

* structural clarity;
* interoperability;
* schema compatibility;
* future extensibility.

---

# Empty Values

Empty strings SHOULD NOT be used to represent unknown information.

Avoid:

```json
{
  "reported_label": ""
}
```

Prefer omitting the property.

Empty arrays and objects SHOULD be avoided unless the relevant schema explicitly permits and semantically requires them.

---

# Additional Properties

Current schemas allow unknown additional properties.

This design supports:

* forward compatibility;
* optional extensions;
* preservation of future fields.

Unknown properties MUST NOT alter the meaning of standardized HCP properties.

Implementations SHOULD preserve unknown optional fields during import, export and synchronization whenever technically possible.

An implementation MAY ignore unknown fields during local processing.

It SHOULD NOT discard them unnecessarily when relaying an otherwise valid Humanitarian Record.

---

# Canonical Field Names

Implementations MUST preserve the official field names defined by the applicable schema version.

For Canonical JSON version 0.5, preferred field names include:

```text
id

schema_version

source_client

subject

observation

type

reported_label

estimated_age

recognition_features

event_type

reported_location

reported_by

observed_at

public_contact
```

Legacy alternatives such as the following are not part of Canonical JSON version 0.5:

```text
record_uuid

hcp_version

observation_timestamp

metadata

relationship
```

Implementations MAY provide migration tools for legacy structures.

Legacy structures MUST be normalized before being exchanged as Canonical JSON version 0.5.

---

# Canonical Value Formatting

Protocol token values SHOULD follow lowercase `snake_case`.

Examples:

```text
missing_report

hospital_admission

fire_department

public_emergency_report
```

Natural-language content MAY preserve normal capitalization, accents and punctuation.

Examples:

```text
María González

Hospital Regional

Praça Central
```

Protocol tokens remain language-independent.

Human-readable information may be localized.

---

# Duplicate Detection

Humanitarian Records are deduplicated using their Record UUID.

When two Humanitarian Records contain the same `id`:

* they represent the same protocol record;
* duplicate transmission SHOULD be ignored;
* conflicting payloads require integrity review.

Two records containing similar humanitarian information but different UUIDs MUST remain independent Humanitarian Records.

Similarity does not imply duplication.

---

# Integrity Validation

A receiving HCP Node SHOULD validate:

* JSON syntax;
* schema compatibility;
* Record UUID;
* required fields;
* timestamp format;
* supported schema version;
* digital signatures when present;
* preservation of immutable content.

Integrity validation confirms technical preservation.

It does not confirm humanitarian truthfulness.

---

# Invalid Humanitarian Records

A Humanitarian Record is structurally invalid when it fails the applicable JSON Schema.

Illustrative reasons include:

* missing required properties;
* invalid UUID;
* invalid timestamp;
* unsupported Subject Type;
* empty required string;
* disallowed field for the Subject Type;
* invalid canonical token formatting.

Invalid Humanitarian Records SHOULD be rejected before synchronization or stored separately for review according to local policy.

An invalid Humanitarian Record MUST NOT be silently converted into a different humanitarian meaning.

---

# Unsupported Versions

When an implementation receives an unsupported `schema_version`, it SHOULD:

1. preserve the original payload when operationally permitted;
2. avoid silently reinterpreting unknown semantics;
3. report the unsupported version;
4. attempt compatible migration only when an explicit migration rule exists.

Unsupported versions do not imply that the humanitarian observation is false.

They indicate structural or semantic incompatibility with the receiving implementation.

---

# Validation Errors

Validation errors SHOULD be machine-readable whenever reasonably possible.

Illustrative error structure:

```json
{
  "error": "schema_validation_failed",
  "schema": "hcp-record.schema.json",
  "path": "/observation/observed_at",
  "message": "Value must be a valid RFC 3339 date-time."
}
```

Error formats remain implementation-specific unless standardized by a future HCP specification.

Error responses SHOULD avoid exposing unnecessary internal implementation details.

---

# Validation and Humanitarian Truth

Validation confirms technical compatibility.

It never confirms humanitarian truth.

A structurally valid Humanitarian Record may still contain:

* incomplete information;
* inaccurate information;
* contradictory information;
* intentionally misleading information.

HCP addresses uncertainty through:

* independent Humanitarian Records;
* local correlation;
* Supporting Evidence;
* Conflicting Evidence;
* explainability;
* human verification.

```text
Schema Validation

        │

        ▼

Structurally Valid Evidence

        │

        ▼

Correlation

        │

        ▼

Humanitarian Reasoning

        │

        ▼

Human Verification
```

People verify reality.

---

# Recommended Validation Sequence

Implementations SHOULD validate HCP documents using the following sequence:

```text
1. Parse JSON

2. Identify object type

3. Identify schema version

4. Apply the matching JSON Schema

5. Apply semantic validation rules

6. Apply security and integrity validation

7. Apply local operational policies

8. Accept, reject or quarantine the document
```

This sequence separates protocol structure from organizational policy.

---

# Relationship with Conformance

Passing validation does not automatically establish full HCP conformance.

A conformant implementation must also preserve behavioral requirements such as:

* immutable Humanitarian Records;
* semantic interoperability;
* local correlation;
* local Humanitarian Cases;
* synchronization boundaries;
* privacy principles;
* security principles;
* human verification.

Conformance is defined by:

* HCP-0022 — Conformance Requirements

---

# Related Specifications

This document complements:

* HCP-0001 — Humanitarian Record
* HCP-0003 — Subject Model
* HCP-0006 — Observation Model
* HCP-0008 — Event Type Model
* HCP-0010 — Canonical JSON Specification
* HCP-0011 — Query Model
* HCP-0012 — Correlation Model
* HCP-0015 — Result Presentation Model
* HCP-0016 — Humanitarian Record Lifecycle Model
* HCP-0020 — Security Model
* HCP-0021 — Privacy and Data Minimization Model
* HCP-0022 — Conformance Requirements

---

# Summary

HCP validation operates at multiple layers.

JSON syntax validation verifies valid JSON.

JSON Schema validation verifies protocol structure.

Semantic validation verifies humanitarian meaning.

Conformance validation verifies implementation behavior.

Operational validation applies local organizational policies.

Validation protects interoperability.

It does not determine humanitarian truth.

Humanitarian Records preserve observations.

Schemas validate structure.

Correlation creates local understanding.

People verify reality.
