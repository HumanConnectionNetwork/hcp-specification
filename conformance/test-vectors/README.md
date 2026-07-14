# HCP Test Vectors

This directory contains behavioral test vectors for the Humanitarian Connection Protocol (HCP).

Test vectors describe complete protocol scenarios together with their expected observable outcomes.

Their purpose is to help developers verify that independent HCP implementations preserve the semantic and behavioral requirements defined by the protocol.

Test vectors evaluate implementation behavior.

They do not merely validate JSON structure.

---

# Purpose

The test vectors contained in this directory provide common reference scenarios for evaluating HCP implementations.

They help verify areas such as:

* Humanitarian Record processing;
* synchronization;
* humanitarian search;
* correlation;
* explainability;
* result presentation;
* privacy boundaries;
* interoperability.

By executing the same scenarios against different implementations, developers can determine whether those implementations preserve compatible HCP behavior.

---

# Relationship with Valid and Invalid Examples

The `valid/` and `invalid/` directories evaluate individual machine-readable documents.

```text
valid/

↓

Documents expected to pass validation
```

```text
invalid/

↓

Documents expected to fail validation
```

Test vectors evaluate complete protocol behavior.

```text
Input

        │

        ▼

Implementation Behavior

        │

        ▼

Expected Outcome
```

A test vector may contain multiple valid documents together with behavioral expectations.

---

# Test Vector Philosophy

HCP test vectors focus on observable protocol behavior.

They do not prescribe:

* internal algorithms;
* programming languages;
* database technologies;
* software architecture;
* deployment models;
* user interfaces.

Different implementations may process a test vector differently internally.

They remain compatible when their observable behavior preserves the humanitarian semantics defined by HCP.

---

# Directory Structure

The test vectors may be organized by protocol capability.

```text
test-vectors/

README.md

record-processing/

synchronization/

search/

correlation/

presentation/

privacy/

interoperability/
```

Each directory contains scenarios focused on one area of protocol behavior.

---

# Test Vector Structure

Whenever possible, each test vector should use its own directory.

Illustrative structure:

```text
search/

missing-person-search/

README.md

input-query.json

available-records.json

expected-results.json
```

More complex behavioral scenarios may include additional files.

Illustrative example:

```text
correlation/

missing-person-correlation/

README.md

query.json

records.json

expected-evidence.json

expected-behavior.md
```

The Markdown file explains the scenario and expected behavior.

The JSON files provide machine-readable test data.

---

# Required Test Vector Information

Every test vector should clearly define:

* test identifier;
* protocol capability being evaluated;
* humanitarian scenario;
* input data;
* required preconditions;
* expected behavior;
* prohibited behavior;
* applicable specifications;
* conformance level.

This information allows different implementations to execute the same test consistently.

---

# Test Identifiers

Every test vector should use a stable identifier.

Recommended format:

```text
HCP-TV-AREA-NNN
```

Illustrative examples:

```text
HCP-TV-REC-001

HCP-TV-SYNC-001

HCP-TV-SEARCH-001

HCP-TV-CORR-001

HCP-TV-PRIV-001
```

Where:

| Prefix   | Area                           |
| -------- | ------------------------------ |
| `REC`    | Humanitarian Record processing |
| `SYNC`   | Synchronization                |
| `SEARCH` | Humanitarian search            |
| `CORR`   | Correlation                    |
| `PRES`   | Result presentation            |
| `PRIV`   | Privacy                        |
| `SEC`    | Security                       |
| `INT`    | Interoperability               |

Stable identifiers allow test results to be compared across implementations and protocol versions.

---

# Input Data

Input data should use the machine-readable structures defined by HCP.

Illustrative inputs include:

* Humanitarian Records;
* Queries;
* synchronization payloads;
* existing local records;
* peer responses;
* implementation configuration relevant to the scenario.

Every Humanitarian Record used as valid input should validate against:

```text
schema/hcp-record.schema.json
```

Every Query used as valid input should validate against:

```text
schema/query.schema.json
```

---

# Expected Behavior

Each test vector must describe the observable behavior expected from a conformant implementation.

Expected behavior may include:

* accepting a valid Humanitarian Record;
* rejecting an invalid Humanitarian Record;
* preserving a synchronized Record UUID;
* returning complete Humanitarian Records from search;
* keeping correlation local;
* exposing Supporting Evidence;
* preserving unknown optional fields;
* preventing Humanitarian Cases from synchronization.

Expected behavior should be precise enough to test while remaining implementation-independent.

---

# Prohibited Behavior

Whenever relevant, a test vector should also describe behavior that would violate HCP.

Illustrative prohibited behavior includes:

* modifying synchronized Humanitarian Records;
* merging independent observations;
* returning Humanitarian Cases as search evidence;
* using Public Contact as a correlation variable;
* treating a Correlation Score as identity confirmation;
* synchronizing Correlation Candidates;
* rejecting valid records solely because of unknown optional fields.

Documenting prohibited behavior helps distinguish semantic compatibility from merely successful processing.

---

# Exact and Semantic Expectations

Test vectors may define two kinds of expectations.

## Exact Expectations

Exact expectations require a specific machine-readable result.

Illustrative examples include:

* validation succeeds;
* validation fails;
* one UUID remains unchanged;
* four Humanitarian Records are returned;
* an unsupported Subject Type is rejected.

---

## Semantic Expectations

Semantic expectations require preservation of protocol meaning without prescribing exact output formatting.

Illustrative examples include:

* correlation remains local;
* the implementation distinguishes evidence from interpretation;
* Public Contact does not affect correlation confidence;
* the presentation communicates uncertainty;
* unknown optional fields are preserved whenever technically possible.

Semantic expectations allow different implementations to remain compatible without producing identical internal or presentation objects.

---

# Correlation Test Vectors

Correlation behavior requires special treatment because HCP does not prescribe a specific algorithm.

A correlation test vector should not normally require every implementation to produce exactly the same numeric score.

Instead, it may verify that the implementation:

* evaluates the relevant Humanitarian Records;
* identifies compatible humanitarian evidence;
* identifies conflicting humanitarian evidence;
* does not modify the source records;
* does not claim verified identity;
* keeps the resulting interpretation local;
* provides explainable reasoning when supported.

Illustrative expectation:

```text
The implementation should identify the four Humanitarian Records as a plausible Correlation Candidate and explain the compatible Reported Labels, Estimated Age, Recognition Features, locations and Observation Timestamps.
```

The exact score may remain implementation-specific.

---

# Search Test Vectors

Search test vectors should verify that search remains separate from correlation.

A conformant implementation should:

* accept a valid Query;
* retrieve Humanitarian Records;
* preserve the returned records;
* avoid generating interpretation during the search stage.

Search results may vary when a test explicitly permits different local datasets.

For deterministic tests, the available Humanitarian Records should be provided as part of the test vector.

---

# Synchronization Test Vectors

Synchronization test vectors should verify that Humanitarian Records remain immutable during exchange.

Illustrative expectations include:

* the Record UUID remains unchanged;
* the Canonical JSON remains semantically unchanged;
* duplicate transmissions are ignored;
* unknown optional fields are preserved whenever technically possible;
* Humanitarian Cases are never synchronized.

Synchronization tests should distinguish duplicate transmission from duplicate humanitarian observations.

Two records with different UUIDs must remain independent even when their humanitarian evidence is similar.

---

# Presentation Test Vectors

Presentation test vectors evaluate whether humanitarian understanding is communicated responsibly.

A conformant presentation should:

* distinguish observations from interpretation;
* communicate Supporting Evidence;
* communicate Conflicting Evidence when available;
* communicate uncertainty;
* avoid claiming verified identity;
* preserve privacy restrictions;
* keep Humanitarian Cases local.

Presentation wording and user interface design remain implementation-specific.

---

# Privacy Test Vectors

Privacy test vectors verify protocol boundaries related to data minimization and local control.

Illustrative scenarios include:

* Public Contact excluded from correlation;
* restricted Humanitarian Record excluded from distributed search;
* optional personal information omitted;
* local presentation redacts Public Contact;
* unsynchronized local records remain private.

Privacy tests evaluate observable behavior.

They do not evaluate compliance with specific national laws.

---

# Interoperability Test Vectors

Interoperability test vectors involve two or more independent implementations or simulated Nodes.

Illustrative scenario:

```text
Node A

Creates Humanitarian Record

        │

        ▼

Node B

Imports Humanitarian Record

        │

        ▼

Node B exports the same semantic representation
```

The test verifies that humanitarian meaning survives exchange between implementations.

Internal storage formats may differ.

Canonical HCP semantics must remain compatible.

---

# Versioning

Every test vector should identify the HCP specification and schema versions it evaluates.

Illustrative metadata:

```text
Test ID: HCP-TV-SEARCH-001

HCP Specification Version: 0.1 Draft

Canonical JSON Version: 0.5

Query Model Version: 0.4
```

When protocol behavior changes, existing test vectors should remain preserved whenever possible.

Superseded vectors may be moved to the archive rather than silently modified.

---

# Expected Result Status

Test executions should use clear result statuses.

Recommended statuses include:

| Status           | Meaning                                                                                |
| ---------------- | -------------------------------------------------------------------------------------- |
| `PASS`           | The implementation satisfied every mandatory expectation                               |
| `FAIL`           | At least one mandatory expectation was violated                                        |
| `PARTIAL`        | Mandatory behavior passed, but one or more recommended expectations were not satisfied |
| `NOT_APPLICABLE` | The implementation does not claim the tested optional capability                       |
| `NOT_TESTED`     | The vector was not executed                                                            |

A test runner may expose additional diagnostic information.

---

# Conformance Levels

Test vectors may apply to one or more conformance levels.

Illustrative mapping:

```text
Core Conformance

Record processing
Canonical JSON
Immutability
Synchronization boundaries
```

```text
Full Conformance

Query processing
Correlation
Explainability
Presentation
Security and Privacy recommendations
```

```text
Extended Conformance

Implementation-specific capabilities preserving HCP semantics
```

The authoritative conformance requirements remain defined by:

* HCP-0022 — Conformance Requirements

---

# Test Vector Independence

Every test vector should be independently executable whenever reasonably possible.

A vector should not depend on the previous execution of another test unless that dependency is explicitly documented.

Independent tests improve:

* reproducibility;
* debugging;
* automation;
* cross-implementation comparison.

---

# Fictional Data

All test vectors must use fictional humanitarian information.

They must not contain:

* real personal information;
* real telephone numbers;
* real humanitarian victims;
* confidential organizational data;
* real emergency records.

Test data should remain realistic while protecting privacy.

---

# Automation

Test vectors should be designed for both:

* manual review;
* automated execution.

Machine-readable inputs and expected results should be used whenever practical.

Human-readable Markdown should explain semantic expectations that cannot be fully expressed through JSON.

Future test runners may consume these vectors directly.

---

# Relationship with Conformance

The test vectors provide practical evidence of protocol behavior.

They complement:

```text
conformance/requirements.md
```

The relationship is:

```text
HCP Specification

        │

        ▼

Normative Requirements

        │

        ▼

Conformance Requirements

        │

        ▼

Test Vectors

        │

        ▼

Observable Test Results
```

The HCP Specification remains normative.

Test vectors provide repeatable implementation verification.

---

# Related Specifications

The test vectors may evaluate requirements defined by:

* HCP-0001 — Humanitarian Record
* HCP-0002 — HCP Node
* HCP-0005 — Node Communication Protocol
* HCP-0010 — Canonical JSON Specification
* HCP-0011 — Query Model
* HCP-0012 — Correlation Model
* HCP-0013 — Synchronization Model
* HCP-0014 — Explainable Correlation Model
* HCP-0015 — Result Presentation Model
* HCP-0018 — Search Protocol
* HCP-0020 — Security Model
* HCP-0021 — Privacy and Data Minimization Model
* HCP-0022 — Conformance Requirements

---

# Summary

HCP test vectors evaluate complete protocol behavior using common humanitarian scenarios and expected outcomes.

Valid and invalid examples verify individual data structures.

Test vectors verify implementation behavior.

They allow independent implementations to demonstrate that they preserve:

* Humanitarian Record integrity;
* semantic interoperability;
* search boundaries;
* local correlation;
* explainability;
* privacy;
* human verification.

HCP does not require identical implementations.

It requires compatible humanitarian behavior.

