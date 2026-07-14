# HCP Glossary

Version: 1.0 (Draft)

Status: Draft

Project: Human Connection Network (HCN)

---

# Introduction

This glossary provides concise definitions of the most important concepts used throughout the Humanitarian Connection Protocol (HCP).

It is intended as a quick reference for developers, implementers, humanitarian organizations and contributors.

Normative definitions remain in their corresponding specifications.

---

# A

## Autonomous Node

A Node that independently stores, exchanges and processes Humanitarian Records while remaining semantically compatible with other HCP implementations.

See:
HCP-0019 Federation Model

---

# C

## Correlation

The process of evaluating relationships between Humanitarian Records in order to identify possible humanitarian connections.

Correlation creates interpretation.

It never changes Humanitarian Records.

See:
HCP-0012 Correlation Model

---

## Correlation Candidate

A possible relationship identified during the correlation process.

A Correlation Candidate is only a potential result.

It does not represent a verified identity or a Humanitarian Case.

See:
HCP-0004 Correlation Candidate

---

# E

## Event Family

A high-level grouping used to organize Event Types.

Event Families simplify classification while preserving semantic consistency.

See:
HCP-0017 Event Classification

---

## Event Type

The canonical semantic meaning assigned to a Humanitarian Record.

Examples include:

- Missing Person
- Hospitalized Person
- Found Animal
- Shelter Registration

See:
HCP-0008 Event Type Model

---

# F

## Federation

A voluntary collaboration among autonomous Nodes.

Federation allows cooperation without requiring centralized control.

Federation does not imply synchronization.

See:
HCP-0019 Federation Model

---

# H

## Human Verification

The final validation performed by people.

HCP assists humanitarian decision making but never replaces human judgment.

See:
HCP-0020 Security Model

---

## Humanitarian Case

A local interpretation generated from one or more Humanitarian Records.

Humanitarian Cases are implementation-specific.

They are never synchronized across Nodes.

See:
HCP-0015 Result Presentation

---

## Humanitarian Observation

A real-world humanitarian observation made by an observer.

Observations exist before they are represented by HCP.

See:
HCP-0001 Humanitarian Record

---

## Humanitarian Record

The canonical representation of a Humanitarian Observation.

Humanitarian Records are immutable observations.

They do not represent identities or histories.

See:
HCP-0001 Humanitarian Record

---

# N

## Node

Any software implementation capable of creating, storing, querying or synchronizing Humanitarian Records using HCP.

Nodes remain autonomous.

See:
HCP-0005 Node Communication Protocol

---

# P

## Presentation

The process of displaying Humanitarian Cases to users.

Presentation is entirely local.

Different implementations may present the same evidence differently.

See:
HCP-0015 Result Presentation

---

## Public Contact

Optional contact information voluntarily provided by the reporter.

Public Contact is intended only to facilitate humanitarian communication.

It is never used for correlation.

See:
HCP-0010 Canonical JSON

---

# Q

## Query

A structured request describing humanitarian evidence to retrieve.

Queries search observations rather than identities.

See:
HCP-0011 Query Model

---

# R

## Recognition Feature

An observable characteristic that helps correlate Humanitarian Records.

Examples include:

- Clothing
- Visible injuries
- Tattoos
- Animal markings
- Collar color

Recognition Features are observational evidence.

They are not identifiers.

See:
HCP-0010 Canonical JSON

---

## Reported Label

A human-readable label reported by the observer.

It represents what was observed or reported.

It does not imply verified identity.

See:
HCP-0010 Canonical JSON

---

# S

## Semantic Interoperability

The ability of different implementations to exchange humanitarian meaning using compatible semantics.

Implementations may differ technically while remaining semantically compatible.

See:
HCP-0022 Interoperability Requirements

---

## Synchronization

The exchange of Humanitarian Records between Nodes.

Synchronization never exchanges Humanitarian Cases.

See:
HCP-0013 Synchronization Model

---

# Philosophy

HCP distinguishes between evidence and interpretation.

Humanitarian Records represent observations.

Humanitarian Cases represent interpretation.

Correlation evaluates evidence.

Presentation communicates interpretation.

Human verification determines reality.
