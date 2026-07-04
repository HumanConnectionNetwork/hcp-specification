# HCP-0011

# Humanitarian Connection Protocol
## Query Model

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
- HCP-0010 — Canonical JSON Specification

---

# 1. Abstract

The Query Model defines how information is requested from an HCP Node.

Rather than exposing database operations, HCP standardizes humanitarian queries.

A Query represents the intent to discover humanitarian information.

The internal implementation remains the responsibility of each Node.

---

# 2. Purpose

The purpose of this specification is to define a common semantic model for humanitarian searches.

Applications should be able to submit equivalent humanitarian queries regardless of programming language, transport protocol or database technology.

---

# 3. Fundamental Principle

A Query requests humanitarian information.

A Query never requests database records directly.

The Node interprets the Query and determines how to retrieve, correlate and present the appropriate humanitarian information.

---

# 4. Humanitarian Query

A Humanitarian Query is a structured request processed by an HCP Node.

Conceptually:

```text
Client

↓

Humanitarian Query

↓

HCP Node

↓

Humanitarian Records

↓

Person Correlation

↓

Search Results
```

The Query does not define how the Node performs the search.

It defines only what humanitarian information is requested.

---

# 5. Query Targets

Every Query shall specify one target.

Examples include:

- Person
- Family
- Community
- Facility
- Resource
- Organization
- Humanitarian Record

Future specifications may introduce additional targets.

---

# 6. Query Criteria

A Query may include one or more search criteria.

Examples:

- Name
- Approximate age
- Gender
- Municipality
- Country
- Observation date
- Status
- Observation type
- Institution
- UUID

Nodes remain responsible for interpreting these criteria.

---

# 7. Partial Information

Queries are expected to operate with incomplete information.

Example:

A family member may only know:

- first name;
- approximate age;
- city.

The Query Model therefore assumes that humanitarian searches are probabilistic rather than exact.

---

# 8. Correlation

Every Query may trigger the Person Correlation process.

The Node may correlate multiple Humanitarian Records before presenting results.

Correlation remains an internal Node operation.

---

# 9. Search Scope

Queries may be executed against:

- local records only;
- synchronized records;
- future distributed searches.

The scope depends on Node capabilities.

---

# 10. Ranking

The protocol does not prescribe ranking algorithms.

Nodes may rank results using:

- name similarity;
- temporal consistency;
- geographic consistency;
- validator participation;
- correlation confidence;
- local intelligence.

---

# 11. Query Result

The Query itself does not define the response format.

The purpose of the Query is to request humanitarian information.

The presentation of results is defined by the Search Result Model.

---

# 12. Performance

Nodes may optimize query execution through:

- indexes;
- caching;
- probabilistic search;
- local optimization.

These implementation details remain outside HCP.

---

# 13. Privacy

Queries should request only the humanitarian information necessary.

Nodes may restrict access according to local policies.

Privacy policies remain implementation-specific.

---

# 14. Extensibility

Future HCP specifications may introduce:

- new query targets;
- additional search criteria;
- advanced filtering;
- distributed search capabilities.

Existing implementations should ignore unsupported optional query elements whenever possible.

---

# 15. Compliance

A compliant implementation shall:

- accept structured Humanitarian Queries;
- support standardized query semantics;
- preserve protocol interoperability;
- remain independent of database technology.

---

# 16. Summary

The Query Model defines how humanitarian information is requested within HCP.

Rather than exposing database operations, HCP standardizes humanitarian intent.

Clients formulate Humanitarian Queries.

Nodes interpret those queries, search Humanitarian Records, perform local correlation and prepare meaningful humanitarian results for presentation.
