# HCP Examples

The `examples/` directory contains informative examples demonstrating how the Humanitarian Connection Protocol (HCP) is expected to be used in real humanitarian scenarios.

These examples are intended to help developers, architects and organizations understand how the protocol operates beyond the normative specifications.

Examples are **informative**.

They are **not normative**.

Whenever differences exist between an example and the Core Specification, the Core Specification always takes precedence.

---

# Purpose

The examples included in this directory demonstrate how Humanitarian Records are created, exchanged, searched and interpreted throughout the HCP lifecycle.

Each example illustrates one or more concepts defined by the Core Specification.

Examples are designed to answer questions such as:

- How is a Humanitarian Record represented?
- What information should be included?
- How are observations synchronized?
- How does humanitarian search operate?
- How are Humanitarian Cases constructed?
- Why are Humanitarian Cases never synchronized?

Rather than introducing new protocol rules, the examples demonstrate how the existing specifications work together.

---

# Directory Structure

```text
examples/

README.md

person/

animal/

hospital/

shelter/

volunteer/

disaster/

search/

correlation/

federation/

privacy/

security/
```

Each directory focuses on a specific humanitarian scenario or protocol capability.

---

# Example Structure

Whenever possible, every example should follow the same structure.

```text
Scenario

↓

Humanitarian Context

↓

Humanitarian Record

↓

Synchronization

↓

Search

↓

Correlation

↓

Humanitarian Reasoning

↓

Humanitarian Case
```

Not every example includes every stage.

Simple examples may demonstrate only Humanitarian Record creation.

More advanced examples may demonstrate complete end-to-end interoperability.

---

# Humanitarian Records

Examples containing Humanitarian Records use the Canonical JSON Specification defined by HCP.

Illustrative fields may include:

- Record UUID
- Event Type
- Subject
- Observation Timestamp
- Reported Location
- Recognition Features
- Public Contact

Field values are illustrative.

They do not represent real humanitarian situations.

---

# Complete Scenarios

Some examples demonstrate complete humanitarian workflows rather than isolated Humanitarian Records.

Illustrative scenarios include:

- volunteer reports a missing person;
- hospital admits an unidentified patient;
- family performs a humanitarian search;
- correlation identifies compatible observations;
- Humanitarian Case is presented;
- human verification confirms reality.

These complete examples illustrate how multiple specifications interact during real humanitarian operations.

---

# Privacy

All examples use fictional information.

Names, locations, organizations and observations are provided exclusively for educational purposes.

Examples should never contain real personal information.

---

# Relationship with the Specification

This directory complements the normative specifications contained in:

```text
specification/
```

The examples demonstrate practical protocol usage.

The specifications define protocol behavior.

Both resources should be read together.

---

# Recommended Reading Order

Developers new to HCP are encouraged to follow this order:

```text
README.md

↓

ARCHITECTURE.md

↓

Core Specification

↓

examples/

↓

schema/

↓

reference/
```

This progression moves naturally from conceptual understanding to practical implementation.

---

# Contributing

Contributors are encouraged to submit additional examples covering new humanitarian scenarios.

Examples should:

- follow the Canonical JSON Specification;
- preserve HCP semantics;
- remain implementation independent;
- use fictional data only;
- clearly explain the humanitarian scenario being demonstrated.

Examples should improve understanding.

They should never introduce new protocol behavior.

---

# Summary

The examples contained in this directory demonstrate how independent HCP implementations exchange humanitarian observations while preserving semantic interoperability.

They complement the Core Specification by showing how the protocol behaves in realistic humanitarian situations.

The examples reinforce one of the central architectural principles of HCP:

**HCP synchronizes observations.**

**HCP does not synchronize conclusions.**

**Every HCP Node constructs its own humanitarian understanding locally.**
