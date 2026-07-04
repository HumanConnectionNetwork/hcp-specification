# HCP-0010

# Humanitarian Connection Protocol
## Canonical JSON Specification

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-04

Depends On:

- HCP-0000 — Architecture and Overview
- HCP-0001 — Fundamental Principles
- HCP-0002 — Humanitarian Record
- HCP-0003 — Subject Model
- HCP-0004 — Person Correlation Model
- HCP-0005 — Node Architecture
- HCP-0006 — Observation Model
- HCP-0007 — Status Model
- HCP-0008 — Record Schema
- HCP-0009 — Node Communication Protocol

---

# 1. Abstract

This specification defines the canonical JSON representation of a Humanitarian Record.

JSON is the reference serialization format for HCP Core.

Every HCP Node shall be able to create, receive, validate, store and exchange Humanitarian Records using this canonical JSON structure.

---

# 2. Purpose

The purpose of this specification is to define a minimum interoperable JSON format for humanitarian observations.

The canonical JSON structure is designed to support:

- humanitarian event registration;
- person search;
- record correlation;
- last known status discovery;
- node-to-node exchange;
- future protocol extensions.

---

# 3. Fundamental Principle

HCP stores humanitarian observations as JSON events.

A Humanitarian Record does not identify a person globally.

It identifies one humanitarian observation involving a Subject at a specific time and place.

---

# 4. Canonical Structure

Every Humanitarian Record shall follow this structure:

```json
{
  "metadata": {},
  "subject": {},
  "observation": {},
  "context": {},
  "relationships": [],
  "extensions": {}
}
