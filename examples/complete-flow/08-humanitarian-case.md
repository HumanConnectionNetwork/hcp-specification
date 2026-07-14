# Humanitarian Case

This example demonstrates the final output produced by the local Correlation Model of an HCP Node.

A Humanitarian Case represents the humanitarian understanding constructed after evaluating multiple independent Humanitarian Records.

It is the result of local interpretation.

It is not a Humanitarian Record.

It is never synchronized with other HCP Nodes.

---

# Humanitarian Scenario

A family searched for an elderly relative following severe flooding.

The search operation retrieved four independent Humanitarian Records created by different organizations.

The local HCP Node evaluated those observations through the Correlation Model.

The result is the Humanitarian Case presented below.

---

# Humanitarian Interpretation

Based on the available humanitarian observations, the HCP Node concludes that the retrieved Humanitarian Records are highly compatible and are likely to describe the same humanitarian situation.

This conclusion is based on the available humanitarian evidence.

It is not a confirmation of identity.

Human verification remains necessary.

---

# Supporting Evidence

The Humanitarian Case summarizes the evidence supporting the humanitarian interpretation.

Illustrative Supporting Evidence includes:

- compatible reported labels;
- identical estimated ages;
- highly consistent recognition features;
- geographically compatible reported locations;
- chronologically plausible observation sequence.

Each element strengthens the humanitarian hypothesis.

None of them independently proves identity.

---

# Conflicting Evidence

The Humanitarian Case also records evidence that weakens or introduces uncertainty into the humanitarian interpretation.

Illustrative examples include:

- incomplete reported labels;
- minor differences in reported locations;
- missing information in individual observations.

Recording conflicting evidence improves transparency and explainability.

---

# Humanitarian Reasoning

The Humanitarian Case explains why the observations appear related.

Illustrative reasoning includes:

- all observations describe an elderly woman;
- physical characteristics remain highly consistent;
- locations follow a plausible evacuation path;
- timestamps describe a realistic humanitarian sequence.

This reasoning allows humanitarian professionals to understand how the HCP Node reached its local interpretation.

---

# Human Verification

The Humanitarian Case assists humanitarian decision making.

It never replaces direct human verification.

Identity confirmation remains the responsibility of:

- family members;
- hospitals;
- volunteers;
- humanitarian organizations;
- emergency responders.

Technology organizes humanitarian evidence.

People confirm reality.

---

# Local Object

One of the fundamental principles of HCP is that Humanitarian Cases remain local.

The Humanitarian Case is created after correlation.

It is never synchronized.

Only Humanitarian Records participate in interoperability.

```text
Humanitarian Records

        │

        ▼

Correlation

        │

        ▼

Humanitarian Case

        │

        ▼

Local Decision
```

Different HCP Nodes may therefore generate different Humanitarian Cases using exactly the same Humanitarian Records.

This behavior is expected.

---

# Relationship with the Protocol

The Humanitarian Case is the final product of the complete HCP workflow.

```text
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

Humanitarian Case

        │

        ▼

Human Verification
```

The protocol ends here.

Operational decisions begin here.

---

# Related Specifications

This example illustrates concepts defined by:

- HCP-0012 — Correlation Model
- HCP-0014 — Explainable Correlation Model
- HCP-0015 — Result Presentation Model

---

# Summary

The Humanitarian Case represents the local humanitarian understanding produced by an HCP Node after evaluating multiple independent Humanitarian Records.

It summarizes humanitarian evidence.

It explains humanitarian reasoning.

It supports humanitarian decision making.

It never replaces human judgement.

Most importantly, the Humanitarian Case is never synchronized.

Only humanitarian observations participate in interoperability.
