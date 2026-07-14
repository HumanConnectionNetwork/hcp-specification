# Missing Person Correlation

This example demonstrates how an HCP Node evaluates multiple Humanitarian Records after a humanitarian search has been completed.

The purpose of correlation is not to identify a person.

Its purpose is to determine whether multiple independent humanitarian observations may describe the same humanitarian situation.

The result is a local humanitarian interpretation.

---

# Humanitarian Scenario

A family searches for an elderly relative following severe flooding.

The search operation retrieves four Humanitarian Records created independently by different organizations:

- Missing Person
- Hospitalized Person
- Refugee Person
- Found Person

Each Humanitarian Record represents one immutable observation.

None of the records confirms identity.

The HCP Node now performs local correlation.

---

# Input Records

The correlation process receives the Humanitarian Records returned by Search.

```text
Query

        │

        ▼

Search

        │

        ▼

4 Humanitarian Records
```

These observations become the input for the Correlation Model.

---

# Correlation Analysis

The HCP Node evaluates the available observations looking for compatible humanitarian evidence.

Illustrative Supporting Evidence includes:

- reported names are compatible;
- estimated ages are compatible;
- reported locations are geographically consistent;
- recognition features are highly similar;
- observation timestamps follow a plausible humanitarian timeline.

The HCP Node also evaluates potential Conflicting Evidence.

In this example, no significant conflicts are identified.

---

# Humanitarian Reasoning

Based on the available observations, the HCP Node generates humanitarian reasoning explaining why the observations appear related.

Illustrative reasoning:

- the reported names are compatible ("María" and "María González");
- all observations describe an elderly woman;
- physical characteristics are highly consistent;
- locations are compatible with the evacuation route;
- timestamps describe a plausible sequence of humanitarian events.

This reasoning improves transparency.

It does not establish identity.

---

# Humanitarian Case

After evaluating all available evidence, the HCP Node generates a Humanitarian Case summarizing the humanitarian interpretation.

The Humanitarian Case may indicate that the observations are likely to describe the same humanitarian situation.

The Humanitarian Case remains local.

It is never synchronized with other HCP Nodes.

---

# Human Verification

Correlation assists humanitarian decision making.

Final confirmation remains the responsibility of people.

Family members, hospitals, volunteers and emergency responders determine whether the observations actually describe the same person.

Technology provides structured evidence.

People confirm reality.

---

# Separation from Search

Search and Correlation intentionally remain independent.

Search answers:

> Which Humanitarian Records may be relevant?

Correlation answers:

> Which observations appear to describe the same humanitarian situation?

These responsibilities should never be combined.

---

# Related Specifications

This example illustrates concepts defined by:

- HCP-0012 — Correlation Model
- HCP-0014 — Explainable Correlation Model
- HCP-0015 — Result Presentation Model

---

# Summary

This example demonstrates how an HCP Node transforms humanitarian observations into humanitarian understanding.

The Humanitarian Records remain immutable.

The Humanitarian Case remains local.

Only humanitarian observations participate in interoperability.

Correlation does not synchronize conclusions.

It explains them.
