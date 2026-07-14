# HCP Conformance Checklist

Version: 1.0 (Draft)

Status: Draft

Project: Human Connection Network (HCN)

---

# Purpose

This document provides a practical checklist for evaluating whether an implementation conforms to the Humanitarian Connection Protocol (HCP).

The checklist is intended for developers, organizations and auditors implementing HCP.

This document is informative.

Normative requirements remain defined in the Core Specification.

---

# What Does It Mean to Implement HCP?

An implementation conforms to HCP when it preserves the protocol's semantic model, regardless of its programming language, database, infrastructure or deployment architecture.

HCP measures semantic compatibility rather than technical uniformity.

---

# Core Architecture

## Humanitarian Records

- [ ] Humanitarian Records represent humanitarian observations.
- [ ] Humanitarian Records do not represent identities.
- [ ] Humanitarian Records are immutable.
- [ ] New observations create new Humanitarian Records.

Reference:

HCP-0001

---

## Observation Model

- [ ] Every Humanitarian Record represents exactly one observation.
- [ ] Observations are represented using the Canonical JSON format.

Reference:

HCP-0006

HCP-0010

---

## Event Types

- [ ] Every Humanitarian Record includes a valid Event Type.
- [ ] Event Types preserve their official semantic meaning.
- [ ] Event Families are not used as Event Types.

Reference:

HCP-0008

HCP-0017

---

# Synchronization

- [ ] Synchronization exchanges Humanitarian Records.
- [ ] Humanitarian Cases are never synchronized.
- [ ] Synchronization preserves Humanitarian Record integrity.

Reference:

HCP-0013

---

# Query

- [ ] Queries describe humanitarian evidence.
- [ ] Queries do not require verified identities.

Reference:

HCP-0011

---

# Correlation

- [ ] Correlation evaluates Humanitarian Records.
- [ ] Correlation never modifies Humanitarian Records.
- [ ] Correlation produces local interpretation only.

Reference:

HCP-0012

---

# Explainability

- [ ] Correlation results can be explained.
- [ ] Supporting Evidence can be identified.
- [ ] Conflicting Evidence can be identified.

Reference:

HCP-0014

---

# Presentation

- [ ] Humanitarian Cases are generated locally.
- [ ] Humanitarian Cases are never synchronized.
- [ ] Users can distinguish observations from interpretation.

Reference:

HCP-0015

---

# Privacy

- [ ] Personal information is minimized.
- [ ] Recognition Features are observational.
- [ ] Public Contact is never used for correlation.

Reference:

HCP-0010

HCP-0021

---

# Federation

- [ ] Nodes remain autonomous.
- [ ] Federation is voluntary.
- [ ] Discovery does not imply federation.
- [ ] Federation does not imply synchronization.

Reference:

HCP-0019

---

# Security

- [ ] Authenticity is treated independently from correctness.
- [ ] Human verification remains the final authority.
- [ ] Layered Verification principles are respected.

Reference:

HCP-0020

---

# Interoperability

- [ ] Humanitarian meaning is preserved.
- [ ] Canonical JSON is semantically compatible.
- [ ] Different implementations remain interoperable.

Reference:

HCP-0022

---

# Recommended Validation

An implementation should also verify:

- JSON Schema validation
- Canonical JSON compatibility
- Synchronization interoperability
- Query interoperability
- Correlation consistency
- Explainability support
- Example compatibility
- Test Suite compatibility

---

# Levels of Conformance

## Level 1 — Record Compatible

The implementation can create and consume valid Humanitarian Records.

---

## Level 2 — Node Compatible

The implementation can synchronize Humanitarian Records with other Nodes.

---

## Level 3 — Search Compatible

The implementation supports HCP Query semantics.

---

## Level 4 — Correlation Compatible

The implementation performs explainable local correlation.

---

## Level 5 — Fully Compatible

The implementation follows all semantic principles defined by the HCP Core Specification.

---

# Summary

An HCP implementation is not defined by its technology.

It is defined by its ability to preserve the semantic meaning of humanitarian observations while remaining interoperable with other independent implementations.
