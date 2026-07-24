# Orientation Sessions: Minutes

**SCI for OpenTelemetry Assembly**

Two identical orientation sessions were held to welcome participants, explain how the Assembly works, and answer questions before the first round.

- **Western session:** Wednesday 22 July 2026, 14:00 GMT
- **Eastern session:** Thursday 23 July 2026, 08:30 GMT

Both sessions covered the same material and are recorded together below. Recordings and slides were shared with all participants afterwards.

## Summary

The Green Software Foundation held two orientation sessions for the SCI for OpenTelemetry Assembly on 22 and 23 July 2026, attended by participants across a broad range of time zones. The sessions introduced the project's purpose, the Software Carbon Intensity specification (ISO/IEC 21031:2024) as the fixed input, and the consensus-based, asynchronous process by which the Assembly will develop a blueprint for representing the SCI as OpenTelemetry semantic conventions. The first Discover round, on Scope, opens on Monday 27 July 2026.

## Purpose of the Assembly

The Assembly brings together practitioners, maintainers and researchers from the OpenTelemetry and green software communities to agree a blueprint for representing the Software Carbon Intensity specification within OpenTelemetry's semantic conventions.

The Assembly produces the blueprint, not the conventions themselves. The formal conventions are drafted from the blueprint after the Assembly closes and carried to the OpenTelemetry Semantic Conventions SIG, the group that governs them, as the community's proposed design.

## The SCI as fixed input

The Software Carbon Intensity specification and its formula are the fixed starting point for the Assembly. The formula covers operational emissions (energy multiplied by carbon intensity), embodied emissions, and a functional unit against which intensity is expressed. The Assembly's task is to represent these faithfully within OpenTelemetry, not to amend the specification.

Reuse of existing OpenTelemetry conventions is a core principle. Where a suitable convention already exists, the Assembly builds on it rather than creating something new. The reuse of existing cloud-native energy tooling was discussed, including work such as Kepler, with maintainers of relevant tooling present in the group. Whether hardware representation is handled within this Assembly or routed to the GSF hardware group was noted as an open question to be resolved during the work.

## How the process works

Each section of the work moves through three phases: Discover, Deliberate and Decide. The process is asynchronous and runs entirely over email. Participants respond in their own time within each round's window.

Participant responses are synthesised into candidate positions for the group to react to. A human reviews every synthesis before it reaches participants. Participants never see each other's raw responses; only anonymised synthesis is shared back.

Consensus is defined as the absence of unresolved objections rather than unanimous endorsement. Participants are encouraged to object where they disagree, and every objection is accompanied by an explanation of what would need to change to resolve it. Mechanisms are in place to prevent a single objection blocking progress indefinitely. Silence is recorded as consent so that the process keeps moving.

## Engagement with OpenTelemetry

The Assembly will keep the OpenTelemetry Semantic Conventions SIG informed and intends to engage with the OpenTelemetry community throughout. All outputs are held in an open GitHub repository. The intent is to do the difficult alignment work among the right experts up front, so that the formal OpenTelemetry process is not where those trade-offs have to be argued.

## Consensus rehearsal

Each session included a short practical exercise to rehearse the consensus mechanics. The exercise walked the group through rating candidate options, raising an objection, and resolving that objection by improving the proposal rather than discarding it. The exercise demonstrated that objection is a constructive part of the process rather than a confrontational one.

## Key decisions

- Discover Round 1, on Scope, opens Monday 27 July 2026.
- The Assembly is estimated to run for approximately 10 to 12 weeks, dependent on deliberation rounds.
- Timelines will flex through August for leave, with forward progress maintained on a quorum basis.
- Non-member participants must complete the participation agreement before the first round. Member-organisation participants are covered under existing membership.
- Silence is treated as consent at each stage.

## Next steps

- Participants complete any outstanding participation agreements ahead of Monday 27 July.
- Questions raised during the sessions are captured and answered in this repository.
- Discover Round 1 (Scope) questions are issued on Monday 27 July.

The Assembly proceeds asynchronously from this point. Optional drop-in calls will be offered for connection alongside the written process.

## Questions raised during orientation

Participants raised a number of questions during the two sessions. Those about how the Assembly is run were answered at the time and, where they have lasting relevance, are captured in the FAQ. The questions below concern the substance of the work. They are recorded here and carried into the relevant rounds rather than answered now, as several are themselves matters for the Assembly to settle.

- **The boundary between operational and embodied emissions.** How the embodied term (M) and the operational term (E) relate, given that software draws energy only through hardware, and how hardware is referenced within the operational term. This bears on Scope and on the energy section, and existing OpenTelemetry hardware metrics such as `hw.energy` were noted as relevant prior art.
- **Reuse of existing cloud-native tooling.** Whether adoption or prototyping of the proposed conventions by existing tooling, such as Kepler, is an objective of the work. Maintainers of relevant tooling are among the participants.
- **The form of the deliverable within OpenTelemetry.** Whether the output should take the form of a federated semantic-convention registry, with updates on stability and prototypes, in line with the direction of other recent semantic conventions. This was raised as an expectation from the OpenTelemetry community and is noted for the Assembly to consider.
- **Engagement with the wider OpenTelemetry community.** Whether and how the Assembly's work is taken back to the OpenTelemetry community to build consensus beyond the Assembly itself.

In addition, a request was made for the user journeys referenced during the session to be shared with participants.
