# SCI for OpenTelemetry Assembly

> **About this document**
>
> This is the anonymised synthesis of one Deliberate round of the SCI for OpenTelemetry Assembly.
> **Nothing in this document is decided, agreed, or endorsed by the Assembly**, and it is not a consensus position of the Green Software Foundation or its members.
>
> This synthesis selects the strongest signals rather than reporting everything; the complete record is held by the facilitator and available if required.
> Individual responses are never published, and no synthesis identifies who said what.
> Counts describe how many responses supported a point.

## Topic 1: Scope and Use Cases - Deliberate, Round 2

This round received ratings and comments from 22 participants.

## Where the Group Stands

The merged candidate did what we hoped it would. It landed better with the group than any of the three individual candidates did in Round 1, and almost everyone found it acceptable, with most finding it strong.

What is left is mostly about tightening language rather than resolving genuine disagreement. A handful of terms, like what counts as a "stable software entity" or what "aligned in time" means, need to be made more precise, and that is a wording problem, not a values problem. The one real exception is a single objection that cross-provider comparison does not belong in these conventions at all. That is a disagreement about scope, and it is the one thing still standing between here and a decision.

## Early Agreement

- **Engineer and team-level attribution and optimization remain the unconditional top priority.** No participant argued for demoting this use case.
- **Provenance is a floor, not a preference.** Undeclared or mismatched values should not be treated as roughly comparable, and this line drew explicit support as one of the most important parts of the text.
- **Real-time reaction belongs last, honestly.** Participants continued to support naming it as a capability to build toward rather than a present requirement.
- **Declaring a boundary and method is necessary but not sufficient for comparison.** Multiple participants pushed back on the idea that declaration alone makes two organizations' numbers comparable, and the text was changed to reflect that distinction directly.

## Where Views Split

**Does cross-provider comparison belong in these conventions at all?**
Most participants accept it as a legitimate second-priority use case that needs more careful framing. One participant maintains it is out of scope for OpenTelemetry-derived data entirely, questions of workload, system, runtime environment, and load intensity go beyond what this data can support, in their view. This is the clearest remaining source of risk heading into a decision.

**Where should real-time reaction sit relative to provider comparison?**
Most feedback on ordering favored keeping real-time reaction last, since its underlying signals are less mature. A smaller number of participants argued the opposite, that real-time reaction should outrank provider comparison because it serves the engineer's own improvement loop more directly.

## Still Open

- **What grounds a "consistently identified software entity."** Several participants want this tied to OpenTelemetry's existing resource identity concepts rather than left as an undefined term.
- **What metadata travels with every value.** No fixed set has been agreed, and participants have different expectations of what a value must carry.
- **How idle and unattributed energy gets allocated.** Raised as needing a consistent, named strategy rather than being left to individual implementations.
- **What happens when embodied carbon data is missing.** Participants want this addressed, not only how embodied carbon is reported when present.
- **Whether example metrics exist today for the real-time use case.** Several participants asked for concrete illustrations rather than the requirement alone.

## Insight of the Round

One participant's objection to the comparison use case changed how the group came to describe what a declared boundary actually does. Their comment: "This raises the question of comparability again (workload, system, runtime environment, load intensity, etc.), which I consider to be outside the scope of this effort." Before this, declaring a boundary and method was treated as if it settled comparability. Afterward, the requirement was rewritten to say that declaration is a precondition for comparison, not a guarantee that two organizations' figures are actually comparable. The underlying disagreement about scope is not resolved, but the distinction it surfaced is now part of the text.

## What Surprised Us

Broader support and a sharper objection arrived together. More people rated the merged candidate highly than rated any single Round 1 candidate that way, but the lowest rating it received was a point lower than the lowest rating Candidate A received, because folding in cross-provider comparison brought in a scope objection that a narrower, engineer-only candidate never had to face. Winning over more of the room and taking on a harder objection turned out to be the same move.
