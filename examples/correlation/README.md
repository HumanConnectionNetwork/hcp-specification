# Correlation Examples

The examples contained in this directory demonstrate how Humanitarian Records are evaluated after a search has been completed.

Correlation is one of the fundamental architectural components of the Humanitarian Connection Protocol (HCP).

Its responsibility is to analyze independent humanitarian observations and determine whether they may describe the same humanitarian situation.

Unlike Search, Correlation does not retrieve information.

It interprets the information that has already been retrieved.

---

# Purpose

The purpose of Correlation is to transform humanitarian observations into humanitarian understanding.

Search retrieves Humanitarian Records.

Correlation evaluates relationships between those Humanitarian Records.

The result is not a new Humanitarian Record.

The result is a local humanitarian interpretation.

---

# Correlation Philosophy

HCP intentionally separates evidence from interpretation.

Humanitarian Records represent evidence.

Correlation produces interpretation.

Because interpretation depends upon local knowledge, operational policies and available observations, every HCP Node performs correlation independently.

Humanitarian understanding is therefore always local.

---

# Correlation Pipeline

Every HCP correlation follows the same conceptual flow.

```text
Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Correlation Candidates

        │

        ▼

Humanitarian Reasoning

        │

        ▼

Humanitarian Case
```

Unlike Humanitarian Records, Humanitarian Cases are never synchronized.

Only humanitarian observations participate in interoperability.

---

# Supporting Evidence

Correlation evaluates humanitarian evidence supporting possible relationships between observations.

Illustrative examples include:

- compatible reported names;
- compatible estimated ages;
- nearby reported locations;
- matching recognition features;
- compatible observation timestamps.

Supporting Evidence increases confidence.

It never proves identity.

---

# Conflicting Evidence

Correlation also evaluates information that weakens a possible relationship.

Illustrative examples include:

- incompatible estimated ages;
- distant reported locations;
- conflicting physical characteristics;
- incompatible observation times.

Conflicting Evidence does not automatically reject a correlation.

It contributes to humanitarian reasoning.

---

# Humanitarian Reasoning

Correlation should remain explainable.

Whenever possible, HCP Nodes should describe why observations appear related.

Humanitarian reasoning improves:

- transparency;
- explainability;
- human review;
- operational trust.

People should understand why a Humanitarian Case was generated.

---

# Humanitarian Cases

A Humanitarian Case represents the local understanding produced after correlation.

It summarizes:

- supporting evidence;
- conflicting evidence;
- humanitarian reasoning;
- correlation confidence.

A Humanitarian Case is not a Humanitarian Record.

It is an interpretation.

Humanitarian Cases remain local to each HCP Node.

They are never synchronized.

---

# Separation of Responsibilities

Search and Correlation intentionally remain independent.

```text
Search

↓

Retrieve Humanitarian Records
```

```text
Correlation

↓

Interpret Humanitarian Records
```

This separation preserves:

- implementation independence;
- organizational autonomy;
- explainability;
- interoperability.

---

# Local Interpretation

Different organizations may legitimately reach different conclusions using exactly the same Humanitarian Records.

This behavior is expected.

HCP standardizes humanitarian observations.

It does not standardize humanitarian interpretation.

Every participating HCP Node remains responsible for constructing its own humanitarian understanding.

---

# Examples

Illustrative examples contained in this directory include:

- correlation candidates;
- supporting evidence;
- conflicting evidence;
- humanitarian reasoning;
- Humanitarian Cases.

These examples demonstrate interpretation only.

Creation of Humanitarian Records is demonstrated separately in:

```text
examples/person/
examples/animal/
```

Search examples are demonstrated separately in:

```text
examples/search/
```

---

# Related Specifications

The examples contained in this directory illustrate concepts defined by:

- HCP-0012 — Correlation Model
- HCP-0014 — Explainable Correlation Model
- HCP-0015 — Result Presentation Model

---

# Summary

The examples contained in this directory demonstrate one of the central architectural principles of HCP.

**Search retrieves evidence.**

**Correlation creates understanding.**

Humanitarian understanding always remains local.

Only humanitarian observations participate in interoperability.
