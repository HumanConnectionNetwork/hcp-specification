# Search Examples

The examples contained in this directory demonstrate how Humanitarian Records are retrieved using the Humanitarian Connection Protocol (HCP).

Search is one of the core architectural components of HCP.

Its responsibility is intentionally limited.

Search retrieves humanitarian observations.

Search does not interpret humanitarian observations.

Understanding this distinction is essential for understanding the architecture of HCP.

---

# Purpose

The examples contained in this directory illustrate how HCP Nodes retrieve Humanitarian Records matching a humanitarian query.

Search is responsible only for locating relevant humanitarian observations.

It never determines whether multiple observations describe the same humanitarian situation.

Interpretation belongs to the Correlation Model.

---

# Search Philosophy

Unlike traditional humanitarian systems, HCP does not search for people or animals.

It searches for Humanitarian Records.

Each Humanitarian Record represents one immutable humanitarian observation.

A search operation retrieves one or more observations that may be relevant to a humanitarian situation.

Those observations may:

- describe the same subject;
- describe different subjects;
- partially overlap;
- contradict one another.

Search makes no attempt to resolve these possibilities.

---

# Search Pipeline

Every HCP search follows the same conceptual flow.

```text
Humanitarian Query

        │

        ▼

Search

        │

        ▼

Humanitarian Records
```

The search process ends once the relevant Humanitarian Records have been retrieved.

No humanitarian interpretation is produced during search.

---

# Separation of Responsibilities

Search and Correlation have different responsibilities.

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

This architectural separation preserves explainability, implementation independence and organizational autonomy.

---

# Search Results

A search operation may return:

- one Humanitarian Record;
- multiple Humanitarian Records;
- no Humanitarian Records.

Search results represent humanitarian observations only.

They are not humanitarian conclusions.

Search results may later become the input for correlation.

---

# Relationship with Correlation

Search retrieves evidence.

Correlation evaluates evidence.

The output of Search becomes the input of the Correlation Model.

```text
Query

        │

        ▼

Search

        │

        ▼

Humanitarian Records

        │

        ▼

Correlation
```

Search and Correlation intentionally remain independent protocol components.

---

# Examples

Illustrative examples contained in this directory include:

- humanitarian queries;
- search requests;
- search results;
- distributed search scenarios.

These examples demonstrate retrieval only.

Interpretation is demonstrated separately in:

```text
examples/correlation/
```

---

# Related Specifications

The examples contained in this directory illustrate concepts defined by:

- HCP-0011 — Query Model
- HCP-0012 — Correlation Model
- HCP-0013 — Synchronization Model
- HCP-0018 — Search Protocol

---

# Summary

The examples contained in this directory demonstrate one of the central architectural principles of HCP.

**Search retrieves observations.**

**Search does not create understanding.**

Humanitarian understanding emerges only after local correlation of the retrieved Humanitarian Records.
