# HCP-0001 — Core Record Format

**Document ID:** HCP-0001

**Title:** Core Record Format

**Status:** Draft

**Version:** 0.1

**Author:** Human Connection Network (HCN)

**Created:** June 2026

**Requires:** HCP-0000

---

# Abstract

This document defines the **Core Record Format** used by the Humanitarian Connection Protocol (HCP).

Every piece of humanitarian information exchanged through HCP MUST be represented as a **Record**.

Regardless of its purpose, every HCP Record follows the same core structure.

Specific record types may extend this format but MUST NOT violate its core principles.

---

# Motivation

During humanitarian emergencies, information is often fragmented across multiple independent systems.

Different organizations collect similar information using incompatible formats, making coordination difficult.

The Core Record Format provides a common structure that enables interoperability between independent implementations.

---

# Terminology

The key words **MUST**, **SHOULD**, **MAY**, **REQUIRED**, **OPTIONAL**, and **RECOMMENDED** are to be interpreted as described in RFC 2119.

---

# The HCP Record

Every HCP Record represents one humanitarian information object.

Examples include:

- Missing person
- Help request
- Available shelter
- Medical resource
- Volunteer
- Donation
- Humanitarian organization
- Incident report

Every record MUST contain the fields defined below.

---

# Core Structure

```json
{
  "hcp_version": "0.1",

  "record_id": "hcp:550e8400-e29b-41d4-a716-446655440000",

  "record_type": "missing_person",

  "status": "active",

  "created_at": "2026-06-30T18:22:41Z",

  "updated_at": "2026-06-30T18:22:41Z",

  "content_hash": "sha256:...",

  "source": {

  },

  "verification": {

  },

  "data": {

  }

}
```

---

# Field Definitions

## hcp_version

Protocol version used to create the record.

Type:

String

Example:

```
0.1
```

---

## record_id

Globally unique identifier.

Implementations SHOULD use UUID Version 4.

Example:

```
hcp:550e8400-e29b-41d4-a716-446655440000
```

The identifier MUST remain immutable.

---

## record_type

Defines the semantic meaning of the record.

Examples:

```
missing_person

help_request

resource

hospital

shelter

organization

volunteer

incident

donation
```

Future specifications define additional record types.

---

## status

Current lifecycle state.

Allowed values:

```
active

resolved

archived

deleted
```

Future specifications MAY introduce additional states.

---

## created_at

Creation timestamp.

MUST use ISO-8601 UTC.

Example:

```
2026-06-30T18:22:41Z
```

---

## updated_at

Last modification timestamp.

MUST use ISO-8601 UTC.

---

## content_hash

Cryptographic hash representing the current record content.

Purpose:

- Integrity verification

- Duplicate detection

- Synchronization optimization

Recommended algorithm:

```
SHA-256
```

---

# Source Object

Describes where the information originated.

Example:

```json
"source":{

    "platform":"telegram",

    "application":"RedConexionHumanaBot",

    "node":"hcp-node-brasil",

    "submitted_by":{

        "anonymous":true,

        "contact":null

    }

}
```

---

# Verification Object

Represents the confidence and verification state.

Example:

```json
"verification":{

    "state":"unverified",

    "confidence":0,

    "verified_by":null,

    "verified_at":null

}
```

Possible states:

```
unverified

pending

verified

disputed
```

---

# Data Object

Contains record-specific information.

The internal structure depends on the record type.

Examples:

- Missing Person

- Shelter

- Resource

- Help Request

Future specifications define these schemas.

---

# Extensibility

Implementations MAY include additional fields.

However:

- Core fields MUST preserve their semantics.

- Unknown fields MUST be ignored by compliant implementations.

This guarantees forward compatibility.

---

# Record Lifecycle

Typical lifecycle:

```
Created

↓

Verified

↓

Updated

↓

Resolved

↓

Archived
```

Implementations MAY support additional internal states.

---

# Interoperability

Any compliant HCP implementation MUST:

- Accept valid HCP Records.

- Preserve unknown fields.

- Preserve Record IDs.

- Preserve timestamps.

- Preserve protocol version.

---

# Privacy Considerations

The Core Record Format intentionally separates metadata from humanitarian data.

Implementations SHOULD minimize personally identifiable information whenever possible.

Privacy-sensitive information MAY be encrypted by higher-level specifications.

---

# Security Considerations

Integrity SHOULD be verified using the content_hash field.

Future versions of HCP will define:

- Digital signatures

- Record authenticity

- Trust models

- Node authentication

---

# Example Record

```json
{
  "hcp_version":"0.1",

  "record_id":"hcp:550e8400-e29b-41d4-a716-446655440000",

  "record_type":"help_request",

  "status":"active",

  "created_at":"2026-06-30T18:22:41Z",

  "updated_at":"2026-06-30T18:22:41Z",

  "content_hash":"sha256:8d89f1...",

  "source":{

      "platform":"telegram",

      "application":"RedConexionHumanaBot",

      "node":"hcp-node-brasil"

  },

  "verification":{

      "state":"unverified",

      "confidence":0

  },

  "data":{

      "message":"Need insulin for diabetic child.",

      "location":"Maracaibo"

  }

}
```

---

# Future Work

Future specifications will define:

- Standard Record Types

- Identity

- Synchronization

- Node Discovery

- Verification

- Attachments

- Digital Signatures

---

# References

- HCP-0000 — Protocol Overview

- RFC 2119 — Key words for use in RFCs

- ISO 8601 — Date and Time Format

- RFC 4122 — UUID

---

**End of HCP-0001**
