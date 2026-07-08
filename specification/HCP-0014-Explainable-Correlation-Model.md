# HCP-0014
# Explainable Correlation Model

Version: 0.2 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-07

Depends On:

- HCP-0011 Query Model
- HCP-0012 Correlation Model
- HCP-0015 Result Presentation Model

---

# 1. Introduction

This document defines the Explainable Correlation Model used by the Humanitarian Connection Protocol (HCP).

The purpose of this model is to ensure that correlation results are understandable by both humans and software.

Rather than simply returning a probability score, HCP encourages implementations to explain which correlation variables contributed to the result.

Explainability improves transparency, trust and decision-making during humanitarian operations.

---

# 2. Purpose

The Explainable Correlation Model enables HCP Nodes to communicate not only **what** was correlated, but also **why**.

This information helps:

- families searching for missing relatives;
- hospitals verifying possible matches;
- humanitarian organizations reviewing reports;
- emergency responders evaluating candidate records;
- developers building user interfaces.

The protocol does not require a specific explanation format but defines common principles for interoperable implementations.

---

# 3. Design Principles

Every explanation should follow these principles.

## Human Readable

Explanations should be understandable by non-technical users.

---

## Machine Readable

Implementations should expose structured information that applications can interpret automatically.

---

## Transparent

Users should understand which correlation variables contributed to the result.

---

## Independent

The explanation should describe the evidence, not the internal implementation details of the correlation algorithm.

Different algorithms may produce similar explanations.

---

## Optional

Implementations with limited computational resources may provide simplified explanations.

Explainability is strongly recommended but not mandatory.

---

# 4. Correlation Variables

Explanations are built from the correlation variables evaluated during the matching process.

Typical variables include:

- reported_name
- estimated_age
- recognition_features
- reported_location
- subject
- event_type
- status
- temporal proximity
- reported_by

Future protocol versions may introduce additional variables.

---

# 5. Example Explanation

A node may determine that two observations are highly correlated.

Instead of returning only:

```json
{
  "probability": 0.91
}
```

it may return:

```json
{
  "probability": 0.91,
  "explanation": {
    "matched_variables": [
      "reported_name",
      "estimated_age",
      "recognition_features",
      "reported_location"
    ]
  }
}
```

Applications may present this information in different ways.

---

# 6. Human-Friendly Presentation

User interfaces are encouraged to present explanations using natural language.

Example:

```
High probability because:

• Similar reported name

• Estimated age differs by approximately two years

• Matching recognition features

• Nearby reported location

• Reports created within a short time interval
```

The presentation format is implementation-specific.

---

# 7. Recognition Features

Recognition Features are one of the most valuable correlation variables.

Implementations are encouraged to identify similarities such as:

For persons:

- clothing
- colors
- glasses
- backpack
- scars
- tattoos
- hairstyle
- beard

For animals:

- collar
- coat color
- visible markings
- injuries
- ear shape
- tail characteristics

Applications may highlight which recognition features contributed to the correlation.

---

# 8. Confidence vs Explanation

A probability score and an explanation represent different concepts.

The probability estimates how likely two observations describe the same humanitarian event.

The explanation identifies which evidence contributed to that estimation.

Different implementations may compute probability differently while producing similar explanations.

---

# 9. Explainability and Artificial Intelligence

HCP does not prescribe a specific correlation engine.

Implementations may use:

- deterministic rules;
- weighted scoring;
- statistical models;
- machine learning;
- artificial intelligence;
- hybrid approaches.

Regardless of the algorithm, implementations are encouraged to expose human-understandable explanations whenever possible.

---

# 10. Privacy

Explanations should avoid exposing unnecessary sensitive information.

Only the information required to justify the correlation should be presented.

Privacy considerations defined in HCP-0021 remain applicable.

---

# 11. Interoperability

Explainability should remain independent from the implementation technology.

Applications may present explanations differently while preserving the same semantic meaning.

This allows diverse HCP Nodes to exchange transparent correlation results.

---

# 12. Relationship with Other Specifications

This document defines how HCP Nodes explain correlation results.

Related specifications include:

- HCP-0011 Query Model
- HCP-0012 Correlation Model
- HCP-0015 Result Presentation Model
- HCP-0021 Privacy and Data Minimization

Together these specifications ensure that HCP not only correlates humanitarian observations, but also explains the reasoning behind every candidate presented to users.
