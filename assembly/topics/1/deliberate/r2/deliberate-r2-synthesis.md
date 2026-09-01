# SCI for OpenTelemetry Assembly

> **About this document**
>
> This is the anonymised synthesis of one Deliberate round of the SCI for OpenTelemetry
> Assembly. **Nothing in this document is decided,
> agreed, or endorsed by the Assembly**, and it is not a consensus position of the Green
> Software Foundation or its members.
>
> This synthesis selects the strongest signals rather than reporting everything;
> the complete record is held by the facilitator and available if required.
> Individual responses are never published, and no synthesis identifies who said what.
> Counts describe how many responses supported a point.

## Topic 1: Scope and Use Cases - Discover, Round 1

This round received 24 responses from the 37 invited participants.

## Where the Group Stands

The strongest theme is a gap in **attribution**, not measurement. Participants repeatedly described being unable to connect an energy or carbon number to a specific unit of software work: a request, transaction, release, component, or shared workload. The missing piece is a reliable way to say which part of a system a number belongs to, especially in serverless, containerized, multi-tenant, or cloud environments.

Most participants who ranked use cases put engineering and operational decisions first: comparing implementations, catching regressions, and deciding where to optimize. Organizational or external sustainability reporting usually came later because it can tolerate coarser, delayed, or aggregated data. A smaller group prioritized cross-service comparison by cloud customers, or treating the conventions as a technical substrate for experts.

There is near-unanimous agreement that the conventions must accept modelled, estimated, and defaulted values, not only directly measured ones. The condition is equally clear: each value needs metadata about where it came from, how it was produced, and how much it can be trusted. A number with no method, source, or confidence attached is unusable or misleading.

**The consumers named across the responses cluster into four groups:**
- **Engineering, platform, and SRE teams** who operate the systems being observed, and want to find and fix hotspots.
- **Sustainability, ESG, and compliance teams**, along with **finance, FinOps, and leadership**, who want defensible numbers for reporting and investment decisions without operating the system themselves.
- **Parties outside the organisation altogether**: customers, government procurement teams, vendors, and consultancies who want to compare suppliers or verify claims.
- **Product managers and business owners**, who weigh feature value against footprint.

**The tension this creates is real:**
- Teams that operate the system need granular, timely, attributable data.
- Teams and outside parties that do not operate it need numbers that are comparable and stay meaningful once aggregated.

## Early Agreement

**The gap is attributing a value to a unit of software work**
- Responses from very different domains independently described the same failure: a figure exists at host, account or provider level with no dependable way to say what share belongs to a given service, request or release.
- Responses differ on which unit of work the attribution hangs from, which is what later Topics have to settle.
- If this holds, the conventions are primarily an attribution mechanism, and any signal that cannot be tied back to identifiable software work is doing less than it appears to.

**The conventions should represent quantities, not how to calculate them.**
- Five responses independently drew this line, with no response arguing the other way.
- Between them they would keep estimation models, calculation methodology, universal calculation models, prescriptive scores, and carbon accounting standards themselves outside these conventions.
- If this holds, the conventions define what a value means and what metadata travels with it, and leave the derivation to the consumer.

**Modelled, estimated, and defaulted values should be included.**
- 22 of 23 responses that addressed this said yes, arguing that restricting to direct measurement would exclude most cloud and shared infrastructure.
- Almost every response that addressed modelled values asked for a field distinguishing measured from modelled, estimated, or defaulted, plus some indication of confidence or uncertainty, before they would trust a number.
- If this holds, every reported value needs a companion field for provenance and confidence, not just the number itself.

**The telemetry needs to serve more than the team producing it.**
- Almost every response that named a consumer named at least one group beyond the team emitting the data, most often sustainability, finance, or an external party.
- This means the conventions cannot be designed only around what is convenient to instrument.

## Where Views Split

**Which use case should the conventions be designed for first?**
- Engineering-facing optimisation, serving teams that operate the system
- Cross-vendor or cross-hardware comparison, serving customers and vendors
- Reporting the energy and carbon of an application or service, serving whoever consumes the report
- Automated adaptation, serving an automated scheduling system
- Container-workload coverage, serving platform teams

Engineering-facing optimisation is the largest group by a clear margin, but it's a grouping rather than a single shared use case: it spans hotspot detection, release-to-release regression comparison, per-action attribution, and resource management. Those responses agree on who the first consumer is more than on what that consumer does first.

Where a full ranking was given, sustainability or organisational reporting was placed last in nine responses. No response placed it first.

**Should any carbon or energy telemetry be emitted by default, or should all of it be opt-in?**
- Most responses addressing defaults: a small always-on baseline such as a coarse energy figure, workload identity, resource usage or a correlation identifier, with richer data opt-in, producing conventions with a defined minimum emitted without configuration.
- One response: all carbon data opt-in with no default baseline, producing conventions that define only what is available when deliberately enabled and leave ecosystem-wide visibility at zero by default.

## Still Open

**At what granularity is embodied carbon credible?**
- Several responses raised it unprompted and were explicit that they had not resolved it; nobody argued it should be invisible. The unease was about allocating a slice of hardware manufacturing emissions to a single span or request, implying a precision the underlying manufacturing data does not support.

**Embodied carbon: inside or alongside.**
- Five responses raised this, framed two ways. Either embodied carbon is reported through these conventions like any other quantity, or it sits outside them as a separate, slowly changing figure that consumers combine with the operational telemetry themselves.

**How should client-side, mobile, and end-user-device software be treated?**
- A few participants flagged uncertainty about whether device-side and end-user-facing software fit the same attribution model as server-side systems, while also noting that ignoring this half of the picture leaves a real share of software's footprint invisible.

*This covers the strongest signals only. The full record sits with the facilitator. Nothing here is decided, and the specifics get tested in the next phase.*

---
