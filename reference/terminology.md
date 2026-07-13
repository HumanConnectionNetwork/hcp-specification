# HCP Terminology Reference

Version: 1.0 (Draft)

Status: Draft

Project: Human Connection Network (HCN)

---

# Purpose

This document defines the official terminology used throughout the Humanitarian Connection Protocol (HCP).

Its purpose is to ensure semantic consistency across the entire specification.

Every normative document within the HCP Core Specification should use these terms consistently.

This document is informative.

The normative definitions remain in their respective specifications.

---

# Terminology Principles

The following principles apply to all HCP documents.

- One concept should have one official name.
- Each concept should have one normative definition.
- Terminology should remain stable across protocol versions.
- Different documents may reference a concept but should not redefine it.
- Semantic consistency has priority over writing style.

---

# Official Concepts

## Humanitarian Observation

A real-world humanitarian observation made by an observer at a specific moment in time.

A Humanitarian Observation exists independently of HCP.

Normative Definition:

HCP-0001 Humanitarian Record

---

## Humanitarian Record

The canonical representation of a Humanitarian Observation.

A Humanitarian Record represents observed humanitarian evidence.

It does not represent identity.

It does not represent history.

It does not represent truth.

Normative Definition:

HCP-0001 Humanitarian Record

---

## Humanitarian Case

A local interpretation created from one or more Humanitarian Records.

Humanitarian Cases are never synchronized between Nodes.

Different implementations may generate different Humanitarian Cases from the same Humanitarian Records.

Normative Definition:

HCP-0015 Result Presentation

---

## Correlation

The process of evaluating relationships between Humanitarian Records.

Correlation creates interpretation.

Correlation never modifies Humanitarian Records.

Normative Definition:

HCP-0012 Correlation Model

---

## Correlation Candidate

A possible relationship identified during correlation.

A Correlation Candidate is not a Humanitarian Case.

A Correlation Candidate is not a verified identity.

Normative Definition:

HCP-0004 Correlation Candidate

---

## Recognition Feature

An observable characteristic that helps correlate Humanitarian Records.

Recognition Features are humanitarian evidence.

They are never identifiers.

Normative Definition:

HCP-0010 Canonical JSON

---

## Reported Label

A human-readable label reported by the observer.

The Reported Label represents what was reported.

It does not imply verified identity.

Normative Definition:

HCP-0010 Canonical JSON

---

## Event Type

The canonical semantic meaning assigned to a Humanitarian Record.

Normative Definition:

HCP-0008 Event Type Model

---

## Event Family

A logical grouping of Event Types.

Event Families organize humanitarian meaning.

They do not redefine Event Types.

Normative Definition:

HCP-0017 Event Classification

---

## Query

A structured description of humanitarian evidence to retrieve.

Queries describe observations rather than identities.

Normative Definition:

HCP-0011 Query Model

---

## Synchronization

The exchange of Humanitarian Records between Nodes.

Synchronization never exchanges Humanitarian Cases.

Normative Definition:

HCP-0013 Synchronization Model

---

## Federation

A voluntary collaboration among autonomous Nodes.

Federation never implies synchronization.

Synchronization never implies federation.

Normative Definition:

HCP-0019 Federation Model

---

## Presentation

The local visualization of Humanitarian Cases.

Presentation belongs entirely to the implementation.

Presentation is never synchronized.

Normative Definition:

HCP-0015 Result Presentation

---

## Human Verification

The final validation performed by people.

Algorithms assist.

People determine reality.

Normative Definition:

HCP-0020 Security Model

---

## Semantic Interoperability

The ability of different implementations to exchange humanitarian meaning while using different technologies.

Semantic interoperability is the primary interoperability goal of HCP.

Normative Definition:

HCP-0022 Interoperability Requirements

---

# Ownership Rule

Each architectural concept has one normative definition.

Other documents may reference the concept but should not redefine it.

---

# Naming Rules

The following terminology should be used consistently throughout HCP.

| Preferred Term | Avoid |
|----------------|-------|
| Humanitarian Record | Record |
| Humanitarian Observation | Observation Record |
| Humanitarian Case | Case |
| Correlation Candidate | Match |
| Recognition Feature | Description |
| Reported Label | Reported Name |
| Event Type | Event |
| Event Family | Category |
| Human Verification | Manual Verification |
| Semantic Interoperability | Technical Compatibility |

---

# Writing Guidelines

Normative specifications should prefer the following verbs.

- creates
- retrieves
- synchronizes
- evaluates
- explains
- presents
- exchanges
- represents
- organizes

Avoid informal alternatives such as:

- gets
- finds
- stores
- looks for
- groups
- connects

---

# Philosophy

The terminology of HCP reflects its architectural principles.

Humanitarian Records represent observations.

Humanitarian Cases represent interpretation.

Synchronization exchanges observations.

Correlation creates understanding.

Presentation communicates interpretation.

Human verification determines reality.
