# SCI for OpenTelemetry Assembly
# Topic 1: Scope and Use Cases

> **About this document**
>
> This is the anonymised synthesis of one Discover round of the SCI for OpenTelemetry
> Assembly. Discover explores the problem space. **Nothing in this document is decided,
> agreed, or endorsed by the Assembly**, and it is not a consensus position of the Green
> Software Foundation or its members.
>
> Areas described as agreement are early signals only. Positions are tested in the
> Deliberate phase and settled in the Decide phase. Consensus decisions appear in
> `REPORT.md`, and nothing here should be cited as an Assembly outcome.
>
> The synthesis is AI-generated from participant responses and reviewed by the facilitator
> before publication. It selects the strongest signals rather than reporting everything;
> the complete record is held by the facilitator.
>
> Individual responses are never published, and no synthesis identifies who said what.
> Counts describe how many responses supported a point, not which participants.

## Discover, Round 1

24 responses received, from 37 invited participants.

## Where the group stands

The consumers named across the responses cluster into four groups:

- **Engineering, platform, and SRE teams** who operate the systems being observed, and want to find and fix hotspots.
- **Sustainability, ESG, and compliance teams**, along with **finance, FinOps, and leadership**, who want defensible numbers for reporting and investment decisions without operating the system themselves.
- **Parties outside the organisation altogether**: customers, government procurement teams, vendors, and consultancies who want to compare suppliers or verify claims.
- **Product managers and business owners**, who weigh feature value against footprint.

One response named a consumer that fits none of these: an automated system that would act on the data directly, selecting a lower-carbon implementation without a person in the loop.

The tension this creates is real. Teams that operate the system need granular, timely, attributable data. Teams and outside parties that do not operate it need numbers that are comparable and stay meaningful once aggregated. The conventions will need to satisfy both without one crowding out the other.

**The most useful reframe of the round** came from a response describing container orchestration, CI/CD, build tools, and cross-team user journeys. The real gap was not missing sensors but the absence of a consistent way to tag a unit of work and re-aggregate it across containers, stages, and owners. That shifts the design question from "how do we observe more precisely" to "how do we keep a unit of work identifiable as it crosses boundaries", which changes what the conventions need to prioritise early.

## Early agreement

**The conventions should represent quantities, not prescribe how to calculate them.**
Six responses independently drew this line, with no response arguing the other way. Between them they would keep estimation models, calculation methodology, universal calculation models, prescriptive scores, and carbon accounting standards themselves outside these conventions. If this holds, the conventions define what a value means and what metadata travels with it, and leave the derivation to the consumer.

**Values that are modelled, estimated, or defaulted need to say so, and say how confident they are.**
Eighteen responses asked for a field distinguishing measured from modelled, estimated, or defaulted, plus some indication of confidence or uncertainty, before they would trust a number. If this holds, every reported value needs a companion field for provenance and confidence, not just the number itself.

**Carbon and energy attach to a defined software entity, explicitly linked to the physical resource that consumed it.**
Eight responses described this in comparable terms: a service, workload, container, or unit of work such as a request or span, with the boundary stated rather than assumed. No response offered a competing concept, so agreement among those who addressed it is complete. Sixteen responses did not address the attachment point at all, which makes this a coverage gap as well as an early agreement.

**The telemetry needs to serve more than the team producing it.**
Every response that named a consumer named at least one group beyond the engineering team emitting the data, most often sustainability, finance, or an external party. This means the conventions cannot be designed only around what is convenient to instrument.

## Where views split

### Which use case should the conventions be designed for first?

- **Fourteen responses** put engineering-facing optimisation, hotspot detection, or attribution-driven comparison first, serving teams that operate the system.
- **Three responses** put cross-vendor or cross-hardware comparison first, serving customers and vendors.
- **One response** put reporting the energy and carbon of an application or service first, serving whoever consumes the report.
- **One response** put automated adaptation first, serving an automated scheduling system.
- **One response** put container-workload coverage first, serving platform teams.
- **Four responses** gave no ranking, or framed the question differently.

No single ordering holds a majority of all 24 responses, though the engineering-optimisation theme is the largest cluster. The clearest directional signal is at the other end: where a full ranking was given, sustainability or organisational reporting was placed last in nine responses.

### Should the conventions cover modelled, estimated, and defaulted values at all?

- **Twenty-three responses** said yes, arguing that restricting to direct measurement would exclude most cloud and shared infrastructure.
- **One response** argued for restricting the conventions to directly measured values, or values calculated from them.

This is a genuine minority position and will be tested directly in the next phase rather than treated as settled by weight of numbers.

## Still open

- **Boundary cases.** Nine responses flagged genuine uncertainty about embodied carbon at fine-grained attribution, mobile and web applications, firmware and embedded software, and shared or unobservable infrastructure such as content delivery networks, serverless platforms, and end-user devices. None settled where the line falls.
- **Corporate-level accounting.** A smaller group proposed excluding corporate-level carbon accounting and Scope 1 to 3 reporting frameworks specifically. This has not yet been tested against the wider group.
- **Broad and deep marking.** None of the 24 responses marked their use cases as broad or as deep, so that classification is still to be produced.

---

This covers the strongest signals only. The full record sits with the facilitator.
Nothing here is decided, and the specifics get tested in the next phase.
