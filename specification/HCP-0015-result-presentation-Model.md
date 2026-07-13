# HCP-0015
# Result Presentation Model

Version: 0.1 (Draft)

Status: Draft

Category: Core Specification

Authors: Human Connection Network Foundation

License: Apache-2.0

Last Updated: 2026-07-05

Depends On:

- HCP-0001 Humanitarian Record
- HCP-0006 Trust Model
- HCP-0012 Correlation Candidate
- HCP-0014 Query & Discovery Model

---

# 1. Abstract

The HCP Result Presentation Model defines how search results are presented to users and software applications.

HCP does not present identified persons.

Instead, it presents Humanitarian Records that are likely to describe the requested humanitarian situation.

Results are organized to help human decision-making while avoiding false certainty.

---

# 2. Purpose

The objective of result presentation is to transform a collection of independent observations into information that is understandable, transparent and actionable.

The protocol assists humanitarian responders by organizing evidence.

It never claims definitive identification.

---

# 3. Fundamental Principle

Every result returned by HCP represents one or more humanitarian observations.

The protocol never states:

"This is the person."

Instead it states:

"These observations are likely related to the humanitarian situation being searched."

---

# 4. Result Structure

Each result should include, whenever available:

- Correlation Candidate identifier
- Correlation Score
- Trust Score
- Current humanitarian status
- Estimated location
- Estimated age
- Reported name
- Event type
- Observation timeline
- Reporting sources
- Number of independent observations

Additional information may be included by each implementation.

---

# 5. Confidence Levels

Implementations should classify results using human-readable confidence levels.

Suggested categories include:

- Very High
- High
- Medium
- Low
- Insufficient Evidence

These levels are informational only.

They do not constitute identity verification.

---

# 6. Ranking

Results should be ordered according to:

- Correlation Score
- Trust Score
- Observation consistency
- Number of independent reports
- Geographic proximity
- Temporal proximity

The highest-confidence candidates appear first.

---

# 7. Multiple Candidates

More than one candidate may be presented for a single query.

Example:

Candidate A

Correlation: High

Trust: High

Hospital observation

-------------------------

Candidate B

Correlation: Medium

Trust: High

Volunteer observation

-------------------------

Candidate C

Correlation: Medium

Trust: Medium

Shelter registration

The protocol intentionally avoids hiding uncertainty.

---

# 8. Observation Timeline

Whenever possible, results should present observations chronologically.

Example:

08:20

Reported trapped

↓

10:15

Rescued

↓

11:40

Hospital admission

↓

18:10

Discharged

The timeline represents independent observations.

---

# 9. Source Transparency

Every observation should indicate its reporting source.

Examples include:

- Hospital
- Fire Department
- Civil Defense
- NGO
- Volunteer
- Family Member
- Government Agency

Users should understand where each observation originated.

---

# 10. Contradictory Information

Conflicting observations should remain visible.

Example:

Observation A

Status:
Hospitalized

Observation B

Status:
Evacuated

Observation C

Status:
Missing

Contradictions are not removed.

They provide additional context for human evaluation.

---

# 11. Historical Preservation

Previous observations should remain accessible.

Newer observations do not erase older ones.

The complete humanitarian history should remain available.

---

# 12. Machine Readability

Results must be suitable for:

- user interfaces
- APIs
- SDKs
- mobile applications
- humanitarian dashboards
- automated analysis

Presentation formats may differ while preserving semantic meaning.

---

# 13. Human Readability

Implementations should prioritize clarity.

Users operating during emergencies should quickly understand:

- what is known
- what remains uncertain
- which observations are most reliable
- where the information originated

---

# 14. Warning Messages

Implementations should clearly communicate uncertainty.

Recommended wording includes:

- Probable Match
- Possible Match
- Limited Evidence
- Additional Verification Recommended

Implementations should avoid wording that implies certainty unless supported by independent verification outside the HCP protocol.

---

# 15. Accessibility

Results should remain understandable regardless of platform.

Interfaces should support:

- mobile devices
- low-bandwidth environments
- multilingual presentation
- screen readers
- printable reports

Accessibility improves humanitarian response.

---

# 16. Privacy Considerations

Nodes remain responsible for determining which fields may be displayed.

Sensitive information may be omitted or redacted according to local policy.

The protocol does not mandate public disclosure of all stored data.

---

# 17. Extensibility

Future versions may support:

- interactive timelines
- geographic visualization
- confidence heat maps
- multilingual presentation
- AI-assisted summaries
- media attachments
- verification badges

These additions should remain compatible with the core HCP model.

---

# 18. Summary

The Result Presentation Model defines how humanitarian information is communicated after discovery.

Instead of presenting identities, HCP presents organized humanitarian observations, ranked by probability and trust.

This approach improves transparency, preserves uncertainty where appropriate, and supports informed human decision-making during emergencies.
