# HCP-0001
# Humanitarian Record

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0000 Architecture and Overview

---

# 1. Introduction

A Humanitarian Record is the fundamental information unit of the Humanitarian Connection Protocol (HCP).

It represents a structured humanitarian observation describing a person, animal or other supported subject involved in a humanitarian event.

A Humanitarian Record is not a digital identity.

It is not a personal profile.

It is not a medical history.

It is an independent observation that can be exchanged between HCP Nodes and correlated with other observations describing the same humanitarian event.

---

# 2. Purpose

The purpose of a Humanitarian Record is to enable humanitarian interoperability.

Instead of storing isolated reports, HCP enables independent organizations, governments, hospitals, volunteers and humanitarian platforms to exchange observations using a common language.

Multiple Humanitarian Records may describe the same real-world event.

The protocol is designed to maximize the probability that these independent observations can later be correlated.

---

# 3. Design Principles

Every Humanitarian Record follows these principles.

## Observation-Based

Records describe observations rather than verified facts.

The reporter documents what is known at the time of reporting.

Future observations may confirm, update or contradict previous ones.

---

## Correlation-Oriented

A Humanitarian Record is primarily composed of correlation variables.

Each variable contributes evidence that may help determine whether two or more records refer to the same humanitarian event.

The protocol intentionally avoids relying on a single identifier.

Instead, correlation emerges from the combination of multiple independent variables.

---

## Independent

Every record exists independently.

Records are never overwritten.

New information should generate new observations or updates according to the lifecycle defined by HCP.

---

## Decentralized

Any HCP Node may create Humanitarian Records.

No central authority is required for a record to exist.

Nodes remain responsible for the quality of the observations they publish.

---

## Minimal

Only the information necessary to improve humanitarian correlation should be collected.

Implementations should avoid unnecessary personal information.

---

# 4. Humanitarian Observation

A Humanitarian Record represents a humanitarian observation.

Examples include:

- A volunteer reports seeing a missing child.
- A hospital reports admitting an unidentified patient.
- A shelter reports a family arriving safely.
- A firefighter reports rescuing an injured person.
- A citizen reports finding a lost dog.

Each observation creates a new Humanitarian Record.

Different organizations may independently report the same event.

HCP allows those observations to be correlated without requiring centralized databases.

---

# 5. Correlation Variables

Unlike traditional information systems, HCP considers every meaningful field to be a correlation variable.

Typical correlation variables include:

- reported_name
- estimated_age
- recognition_features
- reported_location
- event_type
- subject
- reported_by
- temporal proximity

No single variable uniquely identifies a Humanitarian Record.

Correlation emerges from the combination of multiple variables.

Different implementations may assign different correlation weights.

---

# 6. Recognition Features

One of the most important correlation variables is:

```
recognition_features
```

This field contains observable characteristics that help identify the reported subject.

Examples for persons include:

- clothing
- colors
- tattoos
- scars
- glasses
- backpacks
- hairstyle
- beard
- mobility aids

Examples for animals include:

- collar
- coat color
- visible markings
- ear shape
- injuries
- harness
- tail characteristics

The goal is not to describe the complete situation.

The goal is to provide concise information that improves future correlation.

---

# 7. Humanitarian Record Lifecycle

A Humanitarian Record evolves throughout its lifecycle.

Typical stages include:

```
Reported

↓

Correlated

↓

Validated

↓

Updated

↓

Closed
```

The detailed lifecycle is defined in HCP-0016.

---

# 8. Identity

Humanitarian Records are intentionally independent from personal identity.

The protocol does not require government identifiers, passports or national databases.

Names are treated as reported information rather than unique identifiers.

This allows HCP to function even in environments where official identification is unavailable.

---

# 9. Interoperability

Every compliant HCP Node exchanges Humanitarian Records using the canonical JSON structure defined by HCP-0010.

Nodes may internally use any database, programming language or infrastructure.

Interoperability exists because all implementations exchange the same semantic structure.

---

# 10. Security and Privacy

Humanitarian Records should contain only the information necessary for humanitarian coordination.

Sensitive personal information should be minimized.

Implementations should favor observable correlation variables over personally identifying information.

The protocol is designed to maximize humanitarian usefulness while reducing unnecessary privacy risks.

---

# 11. Relationship with Other Specifications

This document defines what a Humanitarian Record is.

Other specifications define complementary aspects:

- HCP-0006 defines the Observation Model.
- HCP-0007 defines Status Models.
- HCP-0010 defines the Canonical JSON representation.
- HCP-0011 defines the Query Model.
- HCP-0012 defines Correlation Rules.
- HCP-0016 defines the Humanitarian Record Lifecycle.

Together these documents define how Humanitarian Records are created, exchanged, correlated and maintained across the HCP ecosystem.
