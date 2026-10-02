# SCI for OpenTelemetry Assembly

> **About this document**
>
> This is the anonymised synthesis of one Deliberate round of the SCI for OpenTelemetry Assembly.
> **Nothing in this document is decided, agreed, or endorsed by the Assembly**, and it is not a consensus position of the Green Software Foundation or its members.
>
> This synthesis selects the strongest signals rather than reporting everything; the complete record is held by the facilitator and available if required.
> Individual responses are never published, and no synthesis identifies who said what.
> Counts describe how many responses supported a point.

## Topic 1: Scope and Use Cases - Deliberate, Round 1

This round received ratings and comments from 19 participants on Topic 1: Scope and Use Cases.

## Where the Group Stands

Engineer-facing, entity-attributed telemetry turned out to be where the group actually landed, not one option among three. Attribution and provenance were treated as effectively non-negotiable across all three candidates, and Candidate A (engineer-first) held up best under scrutiny: every one of the 19 raters put it at 6 or higher, and 16 rated it 7 or higher. Candidate B (comparison-first) drew similar average ratings, but one rating fell to 3. Candidate C (automation-first) drew the most divided ratings: 7 raters gave it 7 or higher, while 4 rated it below 5, including one rating of 1.

The disagreement is not about whether attribution matters. It is about how far past that foundation the conventions should reach right now, toward cross-provider comparability, toward real-time automated action, or not yet at all.

## Early Agreement

- **Attribution and provenance are the non-negotiable core.** A carbon or energy figure is only actionable if it traces back to a stable source, method, and time window. Every candidate assumed this, and no response argued otherwise.
- **Energy and activity must share the same window.** Multiple participants independently flagged that "per unit of useful work" is meaningless unless the energy figure and the activity count are aligned to the same entity and period.
- **Freshest practical data is the standard, not the requirement.** Delayed or aggregated data is an acceptable, clearly labeled fallback, never presented as equivalent to a fresher, more complete result.
- **Location-based grid intensity is the only basis.** Market-based instruments such as offsets, RECs, PPAs, and EACs were rejected across the board as a way to adjust a reported figure.

## Where Views Split

**How far outside the organization should the scope reach?**
Some participants want the conventions strictly limited to consumers inside the organization running the software. Others want a path to external transparency and cross-vendor comparability, and see an org-internal-only scope as too narrow for procurement or supplier accountability.

**Is real-time automated action a use case this Topic should serve?**
A small group sees carbon-aware, real-time workload placement as the highest-value use of this data and wants it named explicitly. A larger group rejects it as a first priority, not because it lacks value, but because the live grid-intensity data and consistent methods it would depend on do not yet reliably exist, and because dropping audit-grade provenance for automation speed reads as a hard line for most reviewers, not a trade-off.

**Does cross-provider comparison belong in a telemetry convention?**
Some participants value it directly for procurement decisions. Others worry it pulls the conventions toward an accounting or assurance standard, or depends on a cross-supplier benchmark that does not exist yet.

## Still Open

- **What actually counts as "a unit of useful work."** Several participants called the denominator undefined and asked for it to be an explicit, emitted activity count rather than assumed.
- **Default versus opt-in telemetry behavior.** Nothing rated so far states what should ship without configuration versus what a consumer has to turn on.
- **Unattributable and idle energy.** Idle replicas, warm pools, and cross-region egress burn power with no request behind them, and no candidate says how that residual should be reported or allocated.
- **How realistic "rolling back" or "migrating" is as an action.** Several participants noted that many organizations can only fix forward, and that switching costs and embodied emissions can outweigh the benefit of a provider migration.
- **Concrete examples and consistent wording.** Participants asked for worked examples, such as a service viewed at different levels of aggregation, and for the same underlying requirement to use the same words across candidates.

## Insight of the Round

One participant's comment on Candidate A changed the direction of the round. Responding to its org-internal framing, they wrote: "My concern is that A stops at the org boundary... I'd support A as a floor, not as the full scope." Up to that point, the three candidates were being treated as three separate answers to the same question. After this comment, participants increasingly treated Candidate A as a foundation the other candidates could build on, rather than a competing option. This shift is reflected in how this round's synthesis is structured.

## What Surprised Us

Cross-provider comparison was expected to draw the most resistance, since it raises the clearest concern about scope creep toward an accounting standard. Instead, it received broad, if qualified, support from most participants. Real-time automation produced the most divided response: a few participants supported it strongly, while most others objected, consistently citing the same concern, that it would trade away provenance.
