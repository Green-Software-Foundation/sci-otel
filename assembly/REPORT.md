# SCI for OpenTelemetry: Assembly Report

> **About this document**
>
> This is a **blueprint**: the agreed framework from which OpenTelemetry semantic conventions representing the Software Carbon Intensity specification (ISO/IEC 21031:2024) can be written.
>
> **It is not a specification.** Rendering this blueprint into draft semantic conventions is separate work that happens after the Assembly closes. Those drafts go to the OpenTelemetry General Semantic Conventions SIG, which runs its own governance over whatever eventually exists upstream.
>
> **How it was produced.** Approximately 40 practitioners from the OpenTelemetry and green software communities worked through five Topics in sequence using the 4Ds consensus process (Discover, Deliberate, Decide). Each Topic closed with no unresolved objections, or with the documented fallback applied. Individual Discover and Deliberate responses are private. Decide votes are published by name in each Decide synthesis. Every other position recorded here is anonymized, and contributors are credited by name only with their consent.

---

## Progress

| Topic | Status | Consensus reached |
| --- | --- | --- |
| 1. Scope and Use Cases | Concluded | 2026-10-01 |
| 2. What Every Value Declares | In Progress | |
| 3. Operational Emissions (E and I) | Not Started | |
| 4. Embodied Carbon (M) | Not Started | |
| 5. Functional Unit and Composition (R) | Not Started | |

---

## Executive summary

<!-- WRITTEN LAST. Five settled consensuses in five paragraphs, one per Topic. Plain language, no process detail. This is the section a SIG reviewer, a GSF member, or a journalist reads first and may read only. -->

*[To be written on completion of Topic 5.]*

---

## Topic 1: Scope and Use Cases

**Topic 1 asked who these conventions are for and what people can do with them.** It is the first of five Topics and it bounds the rest: every signal defined later has to serve a use named here. OpenTelemetry's authoring guidance asks that a new convention show a clear benefit to end users, a clear plan to use it when defining signals, and a clear plan for how instrumentations will populate it. The ranked use cases below are that justification.

### Consensus text

> Reproduced verbatim from the [Topic 1 consensus candidate](https://github.com/Green-Software-Foundation/sci-otel/blob/main/assembly/topics/1/topic-1-consensus-candidate.md). This is the only part of this section that carries consensus.

#### Candidate F: Improve, Then Compare, Then Adapt

This candidate keeps the engineer or team able to act on their own system as the unconditional top priority, treating change-verification and hotspot identification as one continuous use case rather than two. Cross-provider and cross-service comparison ranks second: a real use case these conventions can only partially serve, and whose limits this candidate states rather than hides. Automated real-time adaptation ranks third, trading resolution and directness of measurement for speed. No ranked use case is served by a value that fails to declare its own boundary, method, and unit of work — including whether operational, embodied, or both are covered — and that declaration is the floor beneath all three.

#### 1st "Did this release, configuration, architectural, or dependency change reduce energy or emissions for the same work, and if energy or emissions increased, which part of my system is responsible?"
* Asked by an **application, platform, or SRE engineer** who can change the code, configuration, architecture, or dependencies of the system they run.
* Acts by shipping, continuing to optimize, rolling back, or fixing forward, and by directing attention to whichever component the answer implicates.
* Needs energy and emissions attributable to a consistently identified software entity, aligned to the same measurement window as an explicit unit of useful work that the value itself declares, resolved finely enough to distinguish contributing components, and explicit about whether embodied emissions fall inside the measurement boundary.

#### 2nd "Which of these providers, services, or migration options actually produces less carbon for equivalent work?"
* Asked by an **application or platform engineer, or a technical decision-maker**, choosing between infrastructure options they do not always control directly.
* Acts by selecting, migrating to, or contracting for whichever option the comparison favors.
* Needs every value entering the comparison to declare its own boundary, method, and unit of work as a precondition for any comparison attempt — a precondition, not a guarantee, since a declared unit of work does not by itself make two providers' work equivalent, and closing that gap fully would require a standardized workload and test procedure that these conventions cannot supply. Where the comparing party does not directly operate the infrastructure being measured, what they are reading is a provider's own declared or advertised figure, not a directly measured value — a distinction this candidate treats as a property the comparison consumer must weigh, not a gap to design away.

#### 3rd "Which of the options available to my system right now would cost less carbon if I used it instead?"
* Asked by an **automated scheduler, autoscaler, or workload-placement system** acting without a human in the loop.
* Acts by shifting, delaying, or placing the workload toward the lower-carbon option before the decision window closes.
* Needs a lower-latency signal than the first two use cases require, accepting lower resolution, delayed confirmation, or a modelled rather than directly measured value — but needs that signal to carry an explicit declaration of its own nature, whether measured, calculated, estimated, or forecast, so the automated consumer can weigh a forecast differently from a measurement.

#### Conflict Resolution
* Where the top-ranked use case's need for a fully attributed, declared-boundary value conflicts with the third-ranked use case's need for speed, the first use case's completeness requirement prevails: a fast, modeled, or partial value must be labeled as such rather than presented as equivalent to a fully attributed one.
* Where the second-ranked use case's ambition for cross-provider equivalence would otherwise demand a universally defined unit of work, the first-ranked use case's requirement prevails: a value need only declare its boundary, method, and unit of work consistently for its own release-over-release use, and comparison across providers is only as good as how far that declaration travels.
* Any value covered by these conventions must state its own boundary, method, unit of work, and nature — including whether it is complete against what it claims to represent, covering operational and embodied emissions as declared — before any ranked use case can rely on it.

### Advisory from Discover

Two points drew near-unanimous agreement in Discover. They are carried forward as advice to later Topics, not as consensus:

* Estimated values are in scope, provided they declare that they are estimated (22 of 23 responses that addressed this).
* The conventions describe quantities, not how to calculate them.

### How this Topic was settled

- **Discover rounds:** 1
- **Deliberate rounds:** 3
- **Decide rounds:** 1
- **Fallback applied:** No

**Vote record (final Decide round)**

* 10 Endorse votes
* 5 Consent votes
* 0 Objections
* 22 silent consents

**Candidates not chosen**

* **Deliberate Round 1:** Candidate A "Improve what you Run", Candidate B "Compare what you Buy" and Candidate C "Act while it Runs". Candidate A held up best, with all 19 raters placing it at 6 or above. Candidate C drew the most divided ratings, including one rating of 1. One comment ("I'd support A as a floor, not as the full scope") changed the round: the group stopped treating the three as rivals and started treating them as layers.
* **Deliberate Round 2:** Candidate D "Attribute First, Compare Fairly, Prepare for Real Time" merged all three in priority order. Average rating 8.1; 20 of 22 rated it 7 or higher.
* **Deliberate Round 3:** Candidate E "Improve, Then Compare, Then Adapt". Average rating 8.2; 15 of 17 rated it 7 or higher. It was revised into Candidate F, which went to Decide.

**Objections and how they were resolved**

One question ran through every Deliberate round: whether cross-provider comparison belongs in these conventions at all. One participant objected in Round 2, and by Round 3 two more had reached the same conclusion. One argued that no semantic convention can substitute for a standardized workload procedure. Another argued that the figures being compared are vendor disclosures rather than telemetry, because the person asking the question does not control what is being measured.

It was resolved inside the candidate through three changes: the standardized workload limit was stated outright, procurement was excluded from the second use case's consumers, and a second conflict rule was added, subordinating cross-provider ambition to the first use case's requirements. The objection was withdrawn before Decide, and no objections were cast in Decide.

**Minority positions recorded**

* **Cross-provider comparison should rank lower, or not at all.** Two participants would have preferred it removed from the ranked list, or placed below automated adaptation, one holding that cross-provider comparison is not what OpenTelemetry is for. Both accepted rank 2 because the candidate states its limitation in its own words and the second Conflict Resolution clause prevents it from driving the design.
* **Use case 3 may not need a lower-latency signal.** One participant noted that workload placement schedules ahead of time and must rely on an estimate in any case, so a measurement taken now adds little for a placement decision that may be minutes away.
* **The declaration terms need precise definitions.** One participant asked that later Topics define boundary, method, unit of work, and the distinction between measured, calculated, estimated, and forecast values exactly, so signals are interpreted consistently across implementations.
* **"Unit of work" collides with existing OpenTelemetry terms.** One participant noted that it already suggests a span in traces, and "unit" already means the unit of measurement in metrics, whereas here it means SCI's functional unit. Recorded as a naming decision for a later Topic, not a scope one.

**Carried forward to later Topics**

Questions Topic 1 could not settle, handed to the Topics that own them:

* Whether estimated values need a confidence indicator (Topic 2).
* What data should be emitted by default and what should be opt-in (Topic 3).
* How idle and unattributed energy is allocated (Topic 3).
* What happens when embodied carbon data is missing, not only how it is reported when present (Topic 4).
* The name the conventions use for "unit of work", SCI's functional unit (Topic 5).
* Whether an estimated component value must reconcile with a measured parent (Topic 5).
* Whether the conventions reach client-side, embedded, or build-time software (owner to be confirmed).
* Where vendors, consultancies, researchers, and benchmarkers sit in the ranking (owner to be confirmed).

---

## Topic 2: What Every Value Declares

### Consensus text

<!-- REPLACED BY PR ON TOPIC 2 CLOSE. Three decisions: sameness (same software?), functional unit (per what?) and provenance (how was it produced?), closing with one concrete before-and-after example that names only existing OpenTelemetry attributes. -->

*[Awaiting consensus.]*

### How this Topic was settled

*[Same structure as Topic 1: rounds, vote record, candidates not chosen, objections, minority positions, carried forward.]*

---

## Topic 3: Operational Emissions (E and I)

### Consensus text

<!-- REPLACED BY PR ON TOPIC 3 CLOSE. Target 200 to 250 words. -->

*[Awaiting consensus.]*

### Supporting evidence: collection feasibility

<!-- Drawn from Discover responses. Supporting evidence, not consensus material. Serves the prototyping validation OpenTelemetry recommends. Framed as what is collectable, never as an endorsement of any tool. -->

*[What is collectable today with reasonable overhead, and where the evidence came from. Existing working instrumentations are recorded as prior-art prototype evidence.]*

### How this Topic was settled

*[Same structure as Topic 1.]*

---

## Topic 4: Embodied Carbon (M)

### Consensus text

<!-- REPLACED BY PR ON TOPIC 4 CLOSE. Target 150 to 200 words. If a known-unknowns register is retained (what we do not know, why it matters, what would resolve it), it must sit inside the Topic 4 candidate. It supports the `development` stability declaration. Pending Topic 4 reshaping. -->

*[Awaiting consensus.]*

### How this Topic was settled

*[Same structure as Topic 1.]*

---

## Topic 5: Functional Unit and Composition (R)

### Consensus text

<!-- REPLACED BY PR ON TOPIC 5 CLOSE. Target 150 to 200 words. If the end-to-end worked example is retained (how a backend computes an SCI value for a defined software boundary and functional unit from the signals settled in Topics 2 to 4), it must sit inside the Topic 5 candidate. It is the blueprint's own integration test: if it cannot be written cleanly, the blueprint has a gap the SIG would have found. Pending Topic 5 reshaping. -->

*[Awaiting consensus.]*

### How this Topic was settled

*[Same structure as Topic 1.]*

---

## Traceability: what a specification writer needs, and where it is

This table is the drafting work plan. Each row is a task with its input already located in this document.

| Drafting requirement (per OTel authoring guidance) | Produced by | Section |
| --- | --- | --- |
| Use cases and end-user benefit justification | Topic 1 | Topic 1: Scope and Use Cases |
| Declaration floor (boundary, method, functional unit, nature, completeness) | Topic 1 | Topic 1: Scope and Use Cases |
| Software identity and change marker (sameness) | Topic 2 | |
| Functional unit: source of the count and how the kind of work is declared | Topic 2 | |
| Provenance: nature, method, input sources, confidence indicator | Topic 2 | |
| Reuse of existing attributes | Topic 2 onward | |
| Metric definitions: signal types, instrument types, reporting levels | Topic 3 (E, I), Topic 4 (M, if metric) | |
| Requirement levels and default emission | Topic 3 onward | |
| Idle, unattributed and shared energy | Topic 3 | |
| Resource and entity representation decisions | Topic 3 (observer identity), Topic 4 (M), Topic 5 (boundary) | |
| Namespace | Topic 5 | |
| Units, including the non-UCUM gCO2e decision | Topic 5 | |
| Functional unit naming and conversion | Topic 5 | |
| Normative computation documentation | Topic 5 | |
| Feasibility and coherence evidence | Topic 3 supporting evidence, Topic 5 | |
| Stability-level rationale and honest limitations | Topic 4 | |
| "Who agreed and why" evidence for the SIG | Every Topic's vote record and proofs | |

**Out of scope for this blueprint.** YAML authoring, codeowner and SIG-sponsor arrangements, submission logistics and phasing, hosting mechanics, publication sequencing, and reference implementation selection. These are operational matters handled outside the Assembly.

**Component separability.** E, I and M are individually addressable in this document, so a phased submission (E, then I, then M, composite last) remains possible if the SIG or the Lead judges it the better route. Nothing here fixes that choice.

---

## What happens next

1. **Rendering.** This blueprint is rendered into draft semantic conventions: YAML definitions, registry entries, normative documentation.
2. **Fidelity review.** The full participant roster is invited to a single review round over the rendering. One question only: does this faithfully express what the Assembly agreed? Decisions are closed; only the rendering is in scope.
3. **Submission.** The reviewed draft goes to the OpenTelemetry General Semantic Conventions SIG.
4. **OpenTelemetry governance.** Whatever eventually exists upstream is owned by the OpenTelemetry community, hosted in the OpenTelemetry organization with its own codeowners, starting at `development` stability. The Assembly influences it; the Assembly does not control it.

---

## Appendix A: Participation

**Organizations represented.** *[List.]*

**Response rates per round.**

| Topic | Phase | Round | Eligible | Responded | Rate |
| --- | --- | --- | --- | --- | --- |
| 1 | Discover | 1 | 37 | 24 | 65% |
| 1 | Deliberate | 1 | 37 | 19 | 51% |
| 1 | Deliberate | 2 | 37 | 22 | 59% |
| 1 | Deliberate | 3 | 37 | 17 | 46% |
| 1 | Decide | 1 | 37 | 15 | 41% |

Topic 1: 28 distinct people responded across the five rounds and 13 took part in every round. Everyone who voted in Decide had taken part in an earlier round.

**Eligible-pool evolution.** Participation in Discover for a Topic earns full standing in that Topic's later phases. A participant who has not engaged in the prior phases retains the right to object, but that objection is not counted in the fallback vote. Full standing is restored at the next Topic.

*[How the eligible pool moved across the Assembly.]*

**Note on interpretation.** Participation breadth is reported for transparency. It is not the success criterion. The Assembly succeeded on the basis that the blueprint carries no unresolved objections.

---

## Appendix B: Contributors

Credited with consent. Participation is credited; Discover and Deliberate positions are never attributed. Everyone listed is a founding contributor to a prospective OpenTelemetry convention.

*[Names and organizations, opt-in.]*

---

## Appendix C: Verifiability

**Synthesis history.** Every round's synthesis, as distributed to participants, is published under `assembly/topics/<topic number>/`.

**Cryptographic proofs.** Merkle roots over responses, ratings and votes were published in the corresponding synthesis emails at the time, committing to the record before results were known. Individual inclusion proofs allow any participant to verify their response was counted without any response being published with attribution.

| Topic | Phase | Round | Merkle root | Published in |
| --- | --- | --- | --- | --- |
| 1 | Discover | 1 | `d9151b45db4070da16e3984de2f991da474b23b2e2e74621fe4bcb4a4aff7feb` | Discover Round 1 synthesis email |
| 1 | Deliberate | 1 | *[To be confirmed from the sent email]* | Deliberate Round 1 synthesis email |
| 1 | Deliberate | 2 | *[To be confirmed from the sent email]* | Deliberate Round 2 synthesis email |
| 1 | Deliberate | 3 | *[To be confirmed from the sent email]* | Deliberate Round 3 synthesis email |
| 1 | Decide | 1 | `395217ccd9d80f13d1d712772846dba489062af2dc300cbaadeb39db6d962600` | Decide Round 1 synthesis email |

**Process reference.** The Assembly ran the 4Ds process. The assembly document governing it is at `assembly/assembly-document.md`; recorded deviations from the 4Ds guide are listed there.

---

## License and citation

*[To confirm with GSF and LF legal before publication.]*
