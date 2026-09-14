# SCI for OpenTelemetry Assembly

> **About this document**
>
> This is the anonymised synthesis of one Deliberate round of the SCI for OpenTelemetry Assembly.
> **Nothing in this document is decided, agreed, or endorsed by the Assembly**, and it is not a consensus position of the Green Software Foundation or its members.
>
> This synthesis selects the strongest signals rather than reporting everything; the complete record is held by the facilitator and available if required.
> Individual responses are never published, and no synthesis identifies who said what.
> Counts describe how many responses supported a point.

## Topic 1: Scope and Use Cases - Deliberate, Round 3

This round received ratings and comments from 17 participants.

## Where the Group Stands

Ratings rose slightly compared to Round 2, and most feedback again refined specific wording rather than rejected the overall shape. Sixteen of the seventeen participants found this round's text acceptable, and fifteen rated it strongly.

The one rating that stands out is also the one that matters most. It fell compared to last round, and not because of noise. It reflects an objection that is getting stronger, not weaker: whether cross-provider comparison belongs in these conventions at all.

## Early Agreement

- **Engineer and team-level improvement remains the unconditional top priority.** No participant argued for demoting this use case.
- **A value's own declared boundary, method, and unit of work is the floor beneath every use case.** This continues to hold without challenge.
- **Verification and attribution are connected, but not sequential.** Confirming whether a change helped or hurt no longer has to wait on locating the exact component responsible.
- **A fast, automated signal must state what it is.** Measured, calculated, estimated, or forecast, rather than only listing what it might be missing.
- **A result missing a required component must be labeled incomplete.** It cannot be presented as final if something like embodied carbon is absent.

## Where Views Split

**Does cross-provider comparison belong in these conventions at all?**
This is now the central open question. Three participants, up from one last round, have independently concluded that this use case cannot be satisfied by a semantic convention. One put it this way: "Comparability across providers requires a standardized workload and test procedure, something like the WLTP cycle for cars. A semantic convention specifies how telemetry is named and shaped, not how work is executed."

## Still Open

- **Whether "unit of work" should be renamed.** It already carries other meanings elsewhere in OpenTelemetry, but renaming it is a decision for whichever Topic owns naming, not this one.
- **Whether comparison needs a fixed, shared measure of work.** This touches the functional unit and how an SCI value is composed, both reserved for a later Topic.
- **Whether monitoring effort for automated adaptation should stay proportionate to its benefit.** This is an implementation question rather than a requirement this Topic states.

## Insight of the Round

One participant reframed why cross-provider comparison might not fit here, beyond the practical problem of matching workloads across providers. Their point: the person asking this question doesn't control what's being compared, so the numbers involved aren't really telemetry, they're a vendor's disclosure about its own infrastructure. That distinction, between measuring your own system and reporting on someone else's, is now part of how the group is thinking about this use case.

## What Surprised Us

Last round, we said a further round would test whether the objection to cross-provider comparison would soften or harden. It hardened. Two more participants independently reached the same conclusion this round, including one who said partway through their own feedback that they were starting to agree with a concern someone else had raised. The group is converging on almost everything else. This is the exception.
