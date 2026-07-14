# Humanitarian Connection Protocol

# Architecture Guide

Version: 0.3 (Draft)

Project: Human Connection Network (HCN)

License: Apache-2.0

Last Updated: 2026-07-13

---

# Introduction

The Humanitarian Connection Protocol (HCP) is an open interoperability protocol designed to exchange humanitarian observations between independent organizations, applications and communities.

Unlike traditional humanitarian platforms, HCP is not a centralized database, a cloud service or a humanitarian application.

It is a common language.

Its purpose is to allow completely independent systems to exchange humanitarian observations while preserving organizational autonomy, implementation independence and semantic interoperability.

Every participating organization remains free to choose its own:

- software;
- infrastructure;
- database;
- communication technology;
- operational procedures.

HCP standardizes only one thing:

**The meaning of humanitarian observations.**

Everything else remains independent.

---

# Why HCP Exists

Large humanitarian emergencies generate enormous amounts of information.

Hospitals register patients.

Emergency responders perform rescues.

Shelters receive displaced families.

Volunteers publish missing person reports.

Communities organize local assistance.

Governments coordinate emergency response.

Each organization observes part of reality.

Unfortunately, those observations are usually collected using incompatible systems.

As a result:

- humanitarian information becomes fragmented;
- duplicate records appear;
- conflicting reports become common;
- humanitarian understanding becomes difficult;
- families struggle to locate reliable information.

The problem is rarely the absence of information.

The problem is the absence of a shared language.

HCP was created to solve exactly that problem.

Rather than centralizing humanitarian information into one global platform, HCP allows every organization to continue using its own systems while exchanging humanitarian observations through a common protocol.

Interoperability replaces centralization.

---

# Design Philosophy

Every architectural decision within HCP follows a small set of fundamental principles.

These principles appear repeatedly throughout the specification because they define the identity of the protocol.

---

## Observations Instead of Identities

HCP exchanges humanitarian observations.

It does not exchange complete personal identities.

A Humanitarian Record describes something that was observed at a particular place and time.

It is not intended to become a permanent personal profile.

This architectural decision simultaneously improves:

- interoperability;
- privacy;
- decentralization;
- long-term sustainability.

---

## Evidence Instead of Conclusions

Organizations frequently interpret humanitarian information differently.

For this reason, HCP never synchronizes conclusions.

It synchronizes observations.

Each HCP Node receives humanitarian observations and independently constructs its own humanitarian understanding.

This allows organizations to apply:

- different operational policies;
- different correlation algorithms;
- different presentation models.

While preserving semantic interoperability.

---

## Meaning Instead of Technology

Different organizations use different technologies.

Some use relational databases.

Others use document databases.

Some expose REST APIs.

Others synchronize using offline media.

Some operate entirely through mobile devices.

Others use enterprise systems.

None of these technical decisions affect HCP.

The protocol standardizes humanitarian meaning.

It intentionally avoids standardizing implementation technology.

---

## Decentralization Instead of Centralization

No central HCP server exists.

No mandatory cloud platform exists.

No global database exists.

Every organization owns its own infrastructure.

Every organization controls its own data.

Every organization determines its own operational policies.

HCP simply enables those independent organizations to exchange humanitarian observations using the same language.

---

# Core Principles

The entire protocol can be summarized using a few architectural principles.

---

## One Observation

One Humanitarian Record represents one humanitarian observation.

Nothing more.

Whenever reality changes, a new observation generates a new Humanitarian Record.

Historical observations remain immutable.

---

## Local Understanding

Humanitarian understanding is always constructed locally.

Synchronization exchanges observations.

Search retrieves observations.

Correlation interprets observations.

Presentation communicates humanitarian understanding.

Every HCP Node remains responsible for its own interpretation.

---

## Shared Semantics

Independent implementations remain interoperable because they preserve shared humanitarian meaning.

Programming languages may differ.

Databases may differ.

Communication technologies may differ.

Humanitarian meaning remains identical.

---

## Organizational Independence

Every participating organization remains operationally independent.

Organizations determine:

- governance;
- authentication;
- synchronization policies;
- federation participation;
- privacy policies;
- operational procedures.

The protocol governs interoperability.

Organizations govern themselves.

---

# The HCP Architecture

The Humanitarian Connection Protocol separates humanitarian observation from humanitarian understanding.

Rather than exchanging conclusions, HCP exchanges structured observations that every HCP Node interprets independently.

The complete architecture can be summarized as follows.

```text
                        REAL WORLD

                             │

                             ▼

                 Humanitarian Observation

                             │

                             ▼

                Humanitarian Record (Canonical JSON)

                             │

                             ▼

                       Local HCP Node

                    ╱                ╲

          Synchronization         Search

                    ╲                ╱

                 Humanitarian Records

                             │

                             ▼

                       Correlation

                             │

                             ▼

                Humanitarian Reasoning

                             │

                             ▼

                  Humanitarian Case

                             │

                             ▼

                   Client Presentation

                             │

                             ▼

                  Human Verification
```

Each stage has a single responsibility.

Reality generates observations.

Observations become Humanitarian Records.

Humanitarian Records are exchanged between HCP Nodes.

Each HCP Node independently correlates the available observations.

The resulting humanitarian understanding is presented to people.

People remain responsible for verifying reality.

This separation between evidence and interpretation is one of the fundamental architectural decisions of HCP.

It allows independent organizations to cooperate without requiring centralized decision making or identical software implementations.
# Humanitarian Observation Lifecycle

Everything within HCP begins with reality.

A person is found.

An animal disappears.

A hospital admits an injured patient.

A shelter receives displaced families.

A rescue team evacuates survivors.

These are not database events.

They are humanitarian observations.

Each observation generates exactly one Humanitarian Record.

That Humanitarian Record becomes immutable.

If reality changes later, HCP does not modify the previous record.

Instead, a new Humanitarian Record is created.

This simple rule preserves the complete humanitarian history without rewriting previous observations.

The lifecycle can be summarized as follows.

```text
Reality

        │

        ▼

Observation

        │

        ▼

Humanitarian Record

        │

        ▼

Synchronization

        │

        ▼

Search

        │

        ▼

Correlation

        │

        ▼

Humanitarian Reasoning

        │

        ▼

Humanitarian Case

        │

        ▼

Presentation

        │

        ▼

Human Verification
```

Every stage has one clearly defined responsibility.

---

# Humanitarian Search

Search is often misunderstood.

Many humanitarian systems search for people.

HCP does not.

HCP searches for Humanitarian Records.

A Query retrieves humanitarian observations that may be relevant to a particular situation.

Search itself never decides whether those observations describe the same person or animal.

Search simply retrieves humanitarian evidence.

For this reason, the Search Protocol intentionally separates retrieval from interpretation.

```text
Query

        │

        ▼

Search

        │

        ▼

Humanitarian Records
```

Search ends here.

Everything afterwards belongs to another protocol component.

---

# Humanitarian Correlation

Once humanitarian observations have been collected, each HCP Node begins its own interpretation.

This process is called Correlation.

Correlation evaluates the available Humanitarian Records looking for relationships that may describe the same humanitarian situation.

Unlike traditional systems, HCP never synchronizes these conclusions.

Every HCP Node performs correlation locally.

Different organizations may therefore reach different humanitarian interpretations using exactly the same observations.

This is intentional.

HCP standardizes evidence.

It does not standardize interpretation.

```text
Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Correlation Candidates
```

Correlation never modifies Humanitarian Records.

It only evaluates relationships between immutable observations.

---

# Humanitarian Reasoning

Finding a possible relationship is not enough.

People need to understand *why* a relationship exists.

For this reason, every correlation may generate an explanation describing the evidence supporting that interpretation.

Illustrative examples include:

- similar reported names;
- compatible estimated ages;
- nearby reported locations;
- matching physical characteristics;
- compatible observation timestamps.

This reasoning remains local.

Different organizations may explain the same humanitarian situation differently while preserving semantic interoperability.

```text
Correlation Candidates

        │

        ▼

Humanitarian Reasoning
```

Reasoning improves transparency.

It never replaces human judgement.

---

# Humanitarian Cases

One of the most important architectural concepts in HCP is the distinction between Humanitarian Records and Humanitarian Cases.

A Humanitarian Record is synchronized.

A Humanitarian Case is not.

A Humanitarian Case represents the local understanding constructed by an HCP Node after evaluating multiple Humanitarian Records.

It is therefore an interpretation rather than an observation.

```text
Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Humanitarian Case
```

This distinction prevents organizations from synchronizing conclusions as if they were objective facts.

Instead, organizations exchange observations and independently construct humanitarian understanding.

This separation is one of the fundamental architectural decisions of HCP.

---

# Human Verification

The final stage of the protocol always belongs to people.

Technology assists humanitarian coordination.

It never replaces human responsibility.

After presentation, humanitarian professionals, volunteers, family members or affected individuals evaluate the available information and determine whether additional verification is necessary.

```text
Presentation

        │

        ▼

Human Verification
```

HCP intentionally recognizes that humanitarian reality is often uncertain.

The protocol therefore avoids claiming objective truth.

Instead, it provides structured humanitarian evidence that supports informed human decisions.

---

# Why Humanitarian Cases Are Never Synchronized

This question appears frequently.

If Humanitarian Cases already represent humanitarian understanding, why not synchronize them?

The answer is simple.

Because understanding depends upon interpretation.

Interpretation depends upon local context.

Two organizations may receive exactly the same Humanitarian Records while reaching different operational conclusions.

Both interpretations may be reasonable.

Synchronizing Humanitarian Cases would therefore distribute interpretations rather than observations.

HCP intentionally avoids this.

Instead, synchronization always exchanges immutable Humanitarian Records.

Every participating HCP Node remains free to build its own Humanitarian Cases using its own operational knowledge.

This architectural decision preserves:

- organizational autonomy;
- implementation independence;
- explainability;
- interoperability;
- long-term protocol evolution.

The protocol synchronizes evidence.

People synchronize understanding.
# Humanitarian Federation

HCP allows completely independent organizations to cooperate without requiring centralized infrastructure.

A hospital.

A humanitarian organization.

A volunteer initiative.

A university.

A government agency.

Each one may operate its own HCP Node.

These organizations may voluntarily establish operational relationships to exchange Humanitarian Records.

This relationship is called a Humanitarian Federation.

A federation is not a database.

It is not a cloud platform.

It is not a governing authority.

It is simply an operational agreement between independent organizations.

```text
Hospital

        │

        ▼

HCP Node

        │

──────────── Synchronization ────────────

        │

        ▼

NGO Node

        │

──────────── Synchronization ────────────

        │

        ▼

Volunteer Node
```

Every participant remains completely autonomous.

Organizations govern themselves.

HCP governs interoperability.

---

# Why There Is No Central Database

This is one of the most common questions about HCP.

Traditional humanitarian platforms usually collect information into a single centralized database.

HCP intentionally avoids this architecture.

Instead, every participating organization maintains ownership of its own information.

Each HCP Node stores only the Humanitarian Records that belong to its own operational environment.

Synchronization exchanges observations between Nodes whenever organizations choose to cooperate.

No mandatory central repository exists.

```text
Hospital Database

        │

        ▼

Hospital HCP Node

                │

                ▼

Synchronization

                ▲

                │

Volunteer HCP Node

        ▲

        │

Volunteer Database
```

The protocol standardizes how humanitarian observations are exchanged.

It never standardizes where they are stored.

This architectural decision provides several advantages.

Organizations preserve ownership of their information.

Infrastructure remains decentralized.

Local operation continues during network failures.

Interoperability survives independently of any particular platform.

---

# End-to-End Example

The following simplified example illustrates the complete flow of HCP.

A volunteer finds an elderly woman walking alone after a flood.

The volunteer opens an HCP-compatible mobile application.

The application creates a Humanitarian Record describing the observation.

```text
Observation

↓

Humanitarian Record
```

The volunteer's HCP Node synchronizes this observation with several cooperating organizations.

```text
Volunteer Node

↓

Synchronization

↓

Hospital

Shelter

Emergency Operations Center
```

Hours later, a hospital receives a report describing an elderly patient with similar characteristics.

The hospital creates another Humanitarian Record.

Neither organization knows whether both observations describe the same person.

Later, a family searches for their missing relative.

The local HCP Node retrieves both Humanitarian Records.

Correlation identifies compatible observations.

Humanitarian Reasoning explains why they appear related.

A Humanitarian Case is generated and presented.

Finally, the family confirms the identity directly with the hospital.

Throughout the entire process:

The observations were synchronized.

The interpretation remained local.

Human verification confirmed reality.

---

# The Human Connection Network Ecosystem

The Humanitarian Connection Protocol is only one component of a larger ecosystem.

The Human Connection Network (HCN) promotes the development of open humanitarian technologies built upon HCP.

Illustrative examples include:

- Telegram Clients;
- Web Clients;
- Mobile Applications;
- Hospital Systems;
- NGO Platforms;
- Government Systems;
- Community Response Tools.

Every implementation speaks the same humanitarian language.

Each implementation remains technically independent.

```text
                Human Connection Network

                           │

      ┌────────────────────┼────────────────────┐

      ▼                    ▼                    ▼

 Telegram Client      Web Client       Hospital System

      │                    │                    │

      └────────────────────HCP──────────────────┘

                           │

                 Independent HCP Nodes

      ┌────────────────────┼────────────────────┐

      ▼                    ▼                    ▼

 Volunteer           Shelter             Emergency Center
```

The ecosystem encourages interoperability rather than technological uniformity.

Organizations collaborate by sharing humanitarian observations.

They remain free to choose their own software and infrastructure.

---

# Repository Guide

The HCP Specification repository contains the normative definition of the protocol.

The repository is organized into several complementary areas.

```text
README.md

│

├── ARCHITECTURE.md

├── specification/

├── reference/

├── schema/

├── examples/

├── proposals/

└── media/
```

Each directory has a different purpose.

- **README.md** introduces the project.
- **ARCHITECTURE.md** explains how the protocol works.
- **specification/** contains the normative RFC-style specifications.
- **reference/** contains implementation guidance and supporting documents.
- **schema/** contains the Canonical JSON Schema.
- **examples/** contains complete interoperability examples.
- **proposals/** contains future protocol proposals.
- **media/** contains diagrams and graphical resources.

Developers are encouraged to read the documents in that order.

---

# One Protocol — Many Implementations

One of the central ideas behind HCP is that interoperability should not require identical software.

Every compatible implementation remains free to innovate.

Different implementations may use:

- different programming languages;
- different databases;
- different communication technologies;
- different deployment architectures;
- different user interfaces.

Yet all remain interoperable because they preserve the same humanitarian semantics.

Technology evolves.

Shared meaning remains stable.

That principle allows HCP to remain useful across many generations of software without requiring organizations to abandon their existing systems.
# How to Read the Specification

The HCP documentation has been organized so that different audiences can approach the protocol at different levels of detail.

Readers interested in understanding the overall architecture should begin with:

```text
README.md

↓

ARCHITECTURE.md
```

Developers planning to implement HCP should then continue with the Core Specification.

A recommended reading order is:

```text
HCP-0000

↓

HCP-0001

↓

HCP-0002

↓

...

↓

HCP-0022
```

Once the Core Specification is understood, the following resources provide practical implementation guidance:

- reference/
- schema/
- examples/

This progressive structure allows readers to move naturally from conceptual understanding to implementation.

---

# Protocol Evolution

The Humanitarian Connection Protocol has been designed to evolve without disrupting existing implementations whenever reasonably possible.

Future protocol versions may introduce:

- additional Event Types;
- new optional Canonical JSON fields;
- improved synchronization capabilities;
- additional security mechanisms;
- new privacy-preserving technologies;
- future interoperability extensions.

Whenever possible, protocol evolution should preserve backward compatibility.

Implementations are encouraged to preserve unknown optional fields and ignore unsupported extensions whenever technically possible.

This approach allows HCP to evolve gradually while maintaining interoperability across different protocol versions.

---

# Implementing HCP

Organizations do not need to replace their existing systems to adopt HCP.

Instead, HCP can be introduced incrementally.

A typical implementation process consists of:

1. Understanding the Core Specification.

2. Mapping local humanitarian information to the Canonical JSON model.

3. Implementing Humanitarian Record creation.

4. Supporting synchronization with compatible HCP Nodes.

5. Implementing humanitarian search.

6. Performing local correlation.

7. Presenting Humanitarian Cases.

Each organization remains free to determine the pace of adoption according to its own operational requirements.

HCP encourages gradual interoperability rather than disruptive migration.

---

# Design Goals

Every architectural decision within HCP supports a small number of long-term objectives.

The protocol aims to remain:

- open;
- decentralized;
- implementation independent;
- privacy-aware;
- security-conscious;
- explainable;
- interoperable;
- extensible;
- resilient.

These goals have guided every specification contained in this repository.

Future protocol evolution should continue preserving these same principles.

---

# Vision

Humanitarian emergencies will continue to generate enormous volumes of information.

No single organization can observe every event.

No single platform can represent every humanitarian reality.

The Humanitarian Connection Protocol proposes a different approach.

Instead of building another centralized platform, it defines a shared language that allows independent organizations to cooperate while preserving their own autonomy.

Every humanitarian observation contributes to a broader understanding.

Every organization contributes its own perspective.

Every implementation enriches the humanitarian ecosystem.

HCP is therefore not a humanitarian application.

It is not a database.

It is not a cloud platform.

It is an open interoperability protocol designed to improve humanitarian coordination through shared meaning.

---

# Final Thoughts

The Humanitarian Connection Protocol intentionally separates:

- observation from interpretation;
- interoperability from implementation;
- coordination from centralization;
- humanitarian evidence from humanitarian understanding.

These separations are the foundation upon which the protocol is built.

By preserving them, HCP enables independent organizations to cooperate without sacrificing autonomy, technological diversity or local decision making.

The protocol does not attempt to centralize humanitarian information.

Instead, it allows humanitarian knowledge to emerge from the responsible exchange of structured observations.

Every Humanitarian Record represents one observation.

Every HCP Node constructs its own humanitarian understanding.

Every organization remains responsible for its own decisions.

The protocol simply provides the common language that makes cooperation possible.

---

# One Final Diagram

The complete architecture of HCP can be summarized in a single conceptual flow.

```text
                         REAL WORLD

                              │

                              ▼

                 Humanitarian Observation

                              │

                              ▼

                   Humanitarian Record

                              │

                              ▼

                     Synchronization

                              │

                              ▼

                           Search

                              │

                              ▼

                        Correlation

                              │

                              ▼

                 Humanitarian Reasoning

                              │

                              ▼

                   Humanitarian Case

                              │

                              ▼

                       Presentation

                              │

                              ▼

                   Human Verification
```

Every specification contained in this repository contributes to one or more stages of this architecture.

Together they define an open, decentralized and implementation-independent interoperability protocol for humanitarian observations.

---

# Closing Statement

The Humanitarian Connection Protocol does not standardize software.

It does not standardize infrastructure.

It does not standardize organizations.

It standardizes humanitarian meaning.

By allowing independent systems to exchange structured humanitarian observations through a shared semantic model, HCP enables long-term interoperability without requiring centralized platforms or identical technologies.

Technology will continue to evolve.

Organizations will continue to change.

Humanitarian challenges will continue to emerge.

The Humanitarian Connection Protocol is designed so that the shared language connecting those systems can endure.
