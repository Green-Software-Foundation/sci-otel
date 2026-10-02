---
version: 1.0.0
title: "Software Carbon Intensity for OpenTelemetry (SCI for OTel)"
facilitator: "Russell Trow (russell@greensoftware.foundation)"
lead: "Sarah Hsu"

# Rules
discover_quorum: "66%"        # of Topic-eligible participants; 50% is the defensible floor
deliberate_quorum: "66%"      # of Topic-eligible participants; 50% is the defensible floor
decide_quorum: "100%"         # satisfied by silence-is-consent; no separate quorum mechanism
round_duration: "4 days"
max_discover_rounds: 3
max_deliberate_rounds: 3
max_decide_rounds: 3
---

## Deliverable

**What the Assembly produces.** `REPORT.md`, the blueprint: the agreed framework from which OpenTelemetry semantic conventions representing the Software Carbon Intensity specification (ISO/IEC 21031:2024) can subsequently be written. It is consensus prose plus supporting artefacts, covering scope and use cases, namespace and reuse strategy, operational emissions, embodied carbon, and functional unit and composition. Published in the Green Software Foundation's `sci-otel` repository, accompanied by vote records, anonymised synthesis history, documented known-unknowns, and cryptographic inclusion proofs.

**What the Assembly does not produce.** The semantic conventions. `REPORT.md` is not a specification and carries no YAML, registry entries, or normative convention text. Rendering the blueprint into draft conventions is a separate piece of work that happens after the Assembly closes. Those drafts go to the OpenTelemetry General Semantic Conventions SIG, which runs its own governance over whatever eventually exists upstream. Participants review the rendering for fidelity to the blueprint before submission; they do not author it.

**Also out of scope, handled operationally elsewhere.** The YAML authoring itself, codeowner and SIG-sponsor arrangements, submission logistics and phasing, hosting mechanics, publication sequencing, and reference implementation selection. Responses reaching for these are noted and set aside, not deliberated.

**The structural test the blueprint must pass:** a specification writer holding `REPORT.md` can draft the semantic conventions without needing a single further group decision. Every Topic definition below states the drafting input its consensus must contain.

---

## Constraints

Non-negotiable requirements the deliverable must satisfy. These bound the playing field. A consensus that ignores them produces output the SIG will reject, so every Topic's questions must sit inside them.

- **ISO fidelity** (prior_decision): The conventions must accurately represent SCI as specified. The Assembly decides how to represent ISO/IEC 21031:2024 in OpenTelemetry, never whether to change it. Source: ISO/IEC 21031:2024; GSF Assembly charter.
- **Blueprint, not conventions** (scope): The output is the agreed framework in consensus prose, not YAML, registry entries, or normative specification text. Source: Design Document v3, Purpose.
- **Use-case and benefit clarity is the acceptance gate** (technical): A new attribute is added only if it provides a clear benefit to end users by enhancing telemetry, there is a clear plan to use it when defining signals, and there is a clear plan for how instrumentations will populate it. Maintainers may reject an addition whose benefits and use cases are not yet clear. This is the closest thing in the authoring guidance to a hard acceptance criterion, and it is why Topic 1 exists. Source: OpenTelemetry, How to write semantic conventions, Defining attributes.
- **Conventions define signals, not just attributes** (technical): New conventions SHOULD include telemetry signal definitions (spans, metrics, events, resources, profiles) and MAY include new attribute definitions. Attributes are secondary to the signals they describe. Source: OpenTelemetry, How to write semantic conventions, Defining new conventions.
- **Metric units follow UCUM** (technical): Energy aligns to joules, as `hw.energy` already does. gCO2e is not a UCUM unit, so carbon quantities require a decision within that rule (a UCUM annotation or a documented non-standard unit), not a free choice. Source: OpenTelemetry general metric guidelines.
- **New conventions MUST have a group of codeowners** (technical): Codeowners is a MUST in the authoring guidance and is the one governance requirement that binds absolutely. New conventions SHOULD also be defined at `development` stability, and SHOULD be defined in YAML. Note that `hw.energy`, which SCI's E would build on, is itself at `development` stability. Source: OpenTelemetry, How to write semantic conventions, Defining new conventions.
- **Requirement-level and cardinality rules bind** (technical): A Required attribute expects that an absolute majority of instrumentation libraries and applications can efficiently retrieve and populate it, while also meeting cardinality and security requirements. Metric attributes that may have high cardinality can **only** be defined at Opt-In. Opt-In is additionally recommended for attributes that are particularly expensive to retrieve or that pose a security or privacy risk. Source: OpenTelemetry, Attribute requirement levels.
- **Scope anchor: software carbon** (scope): The subject is the carbon emissions of software systems, which is SCI's remit. It does not widen to energy, water, or general sustainability. Source: Design Document v3, Topic 1 constraints.
- **Market-based instruments are excluded** (prior_decision): SCI excludes renewable energy certificates and offsets, so the conventions do not represent them. Source: ISO/IEC 21031:2024.
- **Upstream governance is handled outside the Assembly** (policy): Non-trivial changes to semantic conventions require the creation of a project in the OpenTelemetry community repository, which may or may not also require forming a SIG, and pull requests touching areas marked inactive are auto-closed. Reuse carries a governance cost alongside the technical one: `system.*` and `k8s.*` are owned by their own active approver groups, so anything the blueprint touches there needs those groups as well as the semantic conventions approvers. Recorded so that the blueprint's normative references are accurate for Topics 2 to 5. This is not an Assembly deliberation, does not constrain any Topic's candidate space, and is handled by GSF. Source: OpenTelemetry AREAS.md and CONTRIBUTING.md; OpenTelemetry community project-management guide.
- **Tool and vendor agnostic** (policy): The process never names, singles out, or tracks any tool community or organisational group. Candidates are framed exclusively in terms of what a backend must be able to compute, never in terms of what any existing tool emits. Source: GSF operating principles; Linux Foundation anti-trust policy.
- **Terminology register** (policy): The scope-level verb is *observed*, not *measured*, because some SCI components are estimated or defaulted rather than sensed. Where a Topic discusses a directly sensed quantity, *measured* or *instrumented* is used. Source: Design Document v3, Constraints and norms from OpenTelemetry.

---

## Strong norms

SIG preferences that frame a question without settling it. Unlike the constraints above, these are open to the group, but a candidate that runs against one must argue its way past it.

- **Reuse existing attributes when possible.** Look to the existing registry before defining anything new, and use attributes from other namespaces where they fit. Anything duplicating `hw.*`, `system.*`, `k8s.*`, `container.*` or `cloud.*` carries the burden of proof. This sits in the authoring guidance's explicitly non-normative best-practice section, so it is a strong norm rather than a constraint. Combined with the use-case gate above, it still makes gratuitous new attributes hard to land. Source: OpenTelemetry, How to write semantic conventions, Defining attributes.
- **Semantic conventions standardise measurable signals, not derived scores.** This does not appear in OpenTelemetry's published guidance. It is the judgement of Mike Goldsmith (Honeycomb), semantic conventions contributor, given in external technical review, and is carried here because it reflects how the SIG is expected to respond rather than because it is documented. It biases the composite-SCI question toward standardising the components and documenting the computation. The representation of SCI itself remains a deliberated decision in Topic 5, and a first-class SCI metric is the candidate that must argue its way past it.
- **Prototyping evidence strengthens a proposal.** OpenTelemetry strongly recommends prototyping proposed conventions in one or more instrumentations: to validate that the information is available and can be gathered with reasonable overhead, to confirm the terminology holds across diverse libraries and technologies, to give actionable guidance to instrumentation authors, and to check how the telemetry integrates with other instrumentation layers. Collection-feasibility evidence harvested through Discover addresses the first of these, and only partially: it is evidence, not a prototype. The blueprint should say so rather than imply the recommendation has been met. Selecting or coordinating reference implementations remains out of scope. Source: OpenTelemetry, How to write semantic conventions, Prototyping.

---

## Prior art

**Prior art for the target document.** The SCI for Web Assembly `REPORT.md` is the format precedent for what this Assembly produces: consensus prose per section, vote records, minority positions. It is also the negative precedent on section size, its sections having run to thousands of words each.

**Reference material for what the blueprint must enable.** These are examples of the artefact written *from* a blueprint, not examples of the blueprint itself. The OpenTelemetry hardware semantic conventions show what a namespace, reuse map, metric definitions and attribute requirement levels look like when they pass SIG review; their author is on the roster, and OpenTelemetry's own metric-definition authoring guidance is currently marked TBD, so this precedent carries unusual weight. Existing working instrumentations (RETIT OTJAE, Kepler, CodeCarbon) are recorded as prior-art prototype evidence.

---

## Section Sequence

The five Topics trace the SCI formula: SCI = (E × I + M) / R. Each runs Discover, Deliberate and Decide and closes fully before the next opens. Settled Topics do not reopen.

Consensus text targets are sized by the number of distinct decisions each Topic carries, within a band of 150 to 300 words. Where a Topic must produce structured content prose cannot carry, that content is a separate consensus artefact alongside the capped statement. The statement is voted; the artefact is the evidence beneath it.

> Throughout these Topic definitions, "the conventions" means the semantic conventions that will be written from this blueprint. Each Topic settles decisions about them. No Topic produces them.
> 

---

### 1. Scope and Use Cases

**Depends on:** none

**Word count target:** 250 to 300 words, plus the ranked use-case set as a separate artefact

**Discover rounds:** up to 3

- **Purpose:** Establish why software carbon belongs in OpenTelemetry, who the resulting telemetry serves, what decisions it enables, and what it attaches to. Topic 1 fixes the frame inside which Topics 2 to 5 make their decisions.
- **Contains:**
    - Purpose and ranked use cases: who the telemetry serves, the decision each consumer takes with it, and the priority order between them. The order is the decision, not the list. Each use case is also marked broad or deep, per OpenTelemetry's T-shaped signals guidance: broadly applicable signals give baseline coverage across a domain and serve most users, rich deep signals serve investigation of a specific system, and the guidance recommends establishing the broad tier first. The marking tells a specification writer which conventions are baseline and which are extensions.
    - The software boundary anchor: what carbon attaches to in an instrumented system, at the level of concept rather than enumeration.
    - Whether the conventions are in scope for modelled, estimated and defaulted quantities alongside directly measured ones.
    - The out-of-scope list, stated explicitly.
- **Does NOT contain:** Namespace or naming, signal types, units, instrument selection, boundary-level enumeration, allocation methods, anything about R. Nor definitions of SCI itself or of OpenTelemetry mechanics, which are pre-Assembly Research Note material.
- **Constraints:** All deliverable constraints apply. Additionally, reuse-first is stated at scope level, so the scope statement records that the conventions reference existing hardware and system conventions rather than define hardware telemetry. Three exclusions are given rather than deliberated: adoption and prototyping by existing tooling (the Assembly produces collection-feasibility evidence but does not select or coordinate reference implementations), market-based instruments, and cost and financial data, which sit outside the scope anchor in the same way energy and water do. Carbon-aware scheduling is not carried as a separate exclusion, because the question underneath it, whether the conventions carry signals designed to drive future decisions rather than record what happened, is settled by the purpose ranking. Beyond these given exclusions, the group determines what else sits outside through Discover. Topic 1 settles scope; where and how in-scope material composes with existing OpenTelemetry conventions is a Topic 2 decision under its reuse map.
- **Why this matters:** OpenTelemetry maintainers reject attributes without a clear end-user benefit, so this Topic determines whether anything downstream is acceptable to the SIG. It is also the one Topic whose primary experts are the practitioners who would consume the telemetry rather than the people who would author the conventions.
- **Connection to other Topics:** All of them. Topic 2 names things inside this scope and against this reuse boundary. Topics 3 and 4 attach signals to the boundary anchored here. Topic 5's worked example is tested against the use cases ranked here.
- **Discover structure:** Discover rounds are iterative depth over the whole Topic, not a partition of it. Round 1 asks broadly across all four decisions, with questions grounded in the respondent's own practice. Round 2 is designed from what Round 1 returns: depth where the group diverged, and coverage where it did not answer. Round 3 is held in reserve. One Deliberate and one Decide follow over the combined output. Voting the scope statement votes the use-case ranking, because the statement names and ranks the use cases in compressed form; the expanded use-case detail is evidence beneath it rather than separately voted text.
- **Drafting input produced:** The use-case justification every new convention must carry, the scope statement bounding all signal definitions, the software boundary the conventions attach to, and the provenance requirement that follows from the estimated-values decision.

---

### 2. Namespace and Reuse Strategy

**Depends on:** Topic 1

**Word count target:** 150 to 200 words, plus the reuse map as a separate structured artefact

- **Purpose:** Decide where these conventions live in the OpenTelemetry namespace, which existing conventions are referenced rather than redefined, and how carbon quantities are expressed.
- **Contains:** The namespace root and its rationale, for example `carbon.*` versus `sustainability.*`. The reuse map: which existing attributes and metrics from the hardware, system, container, Kubernetes and cloud conventions are referenced. The unit decision for carbon quantities. Naming conventions governing anything defined new.
- **Does NOT contain:** Which signals exist and what they measure (Topics 3 to 5), instrument types, boundary levels, allocation methods, R. Nor any attribute whose need has not been established by a Topic 1 use case.
- **Constraints:** Reuse-first, so anything defined new rather than referenced carries the burden of proof. UCUM binds, and gCO2e is not a UCUM unit, so the carbon unit decision must resolve within that rule rather than around it. The namespace must be viable for OpenTelemetry registry placement.
- **Why this matters:** Naming is the first thing a SIG reviewer reads, and a namespace root shapes every attribute named after it. It is also the cheapest decision to make now and the most expensive to change after adoption.
- **Connection to other Topics:** Inherits the scope and reuse boundary from Topic 1. Every attribute named in Topics 3 to 5 sits in the namespace settled here, and the units decision is applied throughout.
- **Drafting input produced:** The registry location for every attribute, the list of attributes referenced rather than defined, and the units line of every metric definition, including the deliberated answer to gCO2e not being a UCUM unit.

---

### 3. Operational Emissions (E and I)

**Depends on:** Topics 1 and 2

**Word count target:** 200 to 250 words

- **Purpose:** Settle how operational energy (E) and carbon intensity (I) are represented as OpenTelemetry signals.
- **Contains:** Instrument type for energy. The boundary levels at which E is reported. How I attaches to E, whether as attribute, separate metric, or resource-level declaration. Carbon intensity provenance and granularity. Quantification method disclosure. Requirement-level and cardinality direction per attribute. Collection-feasibility evidence: what is collectable today with reasonable overhead.
- **Does NOT contain:** Embodied carbon (Topic 4). R or the composition of the SCI score (Topic 5). Namespace and units (Topic 2, applied here). The YAML rendering of the metrics.
- **Constraints:** Reuse-first bites hardest here. E builds on the existing hardware and system conventions, so the questions concern what those conventions are missing for SCI and how I attaches to them, not how to design energy telemetry from scratch. A Required attribute expects that an absolute majority of instrumentations can efficiently retrieve and populate it; metric attributes that may have high cardinality can only be Opt-In, so cardinality direction is a blueprint decision rather than a drafting one. All candidates are framed around what a backend must be able to compute, never around what any specific tool emits.
- **Why this matters:** This is where the roster's deep energy measurement expertise sits, and where the most working implementations already exist. It is also the largest single block of the specification a writer will draft.
- **Connection to other Topics:** Names things per Topic 2 and attaches to the boundary anchored in Topic 1. Topic 4 apportions embodied carbon to the same boundary. Topic 5 composes E and I with M into the SCI computation.
- **Drafting input produced:** Metric definitions and attribute sets for the E and I signals: instrument types, units, boundary levels, requirement-level direction, cardinality expectations per attribute, and collection-feasibility evidence serving the prototyping validation OpenTelemetry recommends.

---

### 4. Embodied Carbon (M)

**Depends on:** Topics 1, 2 and 3

**Word count target:** 150 to 200 words, plus the known-unknowns register as a separate artefact

- **Purpose:** Settle how embodied carbon is represented, how it is apportioned to a software boundary over time, and what the blueprint must be honest about not knowing.
- **Contains:** The representation decision: runtime signal versus configuration-derived attribute, which lead to different YAML. The allocation approach for apportioning embodied carbon to a software boundary over time. Honest treatment of data availability, captured in the known-unknowns register.
- **Does NOT contain:** Operational emissions (Topic 3). R or composition (Topic 5). Specific embodied carbon datasets or vendor figures. A forced resolution of data gaps the evidence does not support.
- **Constraints:** ISO fidelity governs M's definition. The `development` stability declaration requires documented limitations, and the register is the accompanying candour rather than the justification. Where data does not exist, the blueprint records the gap rather than inventing a source.
- **Why this matters:** M has the least prior art, the most modelling ambiguity and the thinnest data availability of any component. Giving it an undiluted Topic is deliberate. Documented known-unknowns are a feature of the output, not a weakness, and a blueprint that overclaims here will not survive SIG review.
- **Connection to other Topics:** Uses the boundary anchored in Topic 1 and the levels settled in Topic 3. Feeds Topic 5's composition and worked example. Opens with a pre-commissioned neutral evidence brief on embodied carbon data sources.
- **Drafting input produced:** Either a metric definition or a resource and entity attribute definition, the allocation methodology the conventions document normatively, and the known-unknowns register accompanying the `development` stability declaration.

---

### 5. Functional Unit and Composition (R and the SCI computation)

**Depends on:** Topics 1 to 4

**Word count target:** 150 to 200 words, plus the worked example as a separate artefact

- **Purpose:** Settle how the functional unit R is expressed, and how a complete SCI value is composed from the standardised components.
- **Contains:** How R is expressed: telemetry attribute, resource-level declaration, or documented query-time guidance. The composition decision: SCI as a documented computation over standardised components, a first-class metric, or an event recording a completed calculation with its inputs, method and boundary. Cross-cutting glue attributes the composition requires: quantification method disclosure, software boundary identification, provenance. The worked example: given the signals settled in Topics 2 to 4, how a backend computes an SCI score for a defined software boundary and functional unit.
- **Does NOT contain:** Any reopening of settled signals. If the composition exposes a gap, Topic 5 adds glue (a missing shared attribute, a unit clarification); it does not revisit Topics 2 to 4. Nor the YAML, nor submission and publication logistics.
- **Constraints:** The strong norm applies directly here: semantic conventions standardise measurable signals rather than derived scores, so a first-class SCI metric must argue its way past that norm. Forward-only holds. The full OpenTelemetry signal taxonomy is in the candidate space.
- **Why this matters:** The functional unit turns accumulated totals into a rate, which is what makes SCI a rate rather than a sum, so R and composition are the same deliberation. The worked example is the blueprint's own integration test: it exposes composition gaps before the SIG does.
- **Connection to other Topics:** The capstone. Consumes Topics 1 to 4 and tests the blueprint against the use cases ranked in Topic 1.
- **Drafting input produced:** The normative computation documentation, any remaining shared attributes, and the coherence proof supplied by the worked example.

---

## Process rules

Recorded here so this document is self-contained for the phase prompts. Full rationale sits in Design Document v3.

- **Forward only.** Settled Topics do not reopen.
- **Participation gating.** Participation in Discover for a Topic earns full standing in that Topic's later phases. A participant who has not engaged in the prior phases retains the right to object in principle, but their objection is not counted in the fallback vote. Full standing is restored at the next Topic.
- **Anonymised attribution.** Individual responses are never published with attribution. Only consensus decisions and anonymised synthesis are published. No synthesis, candidate, or output shared with participants identifies who said what. Cryptographic proofs over responses, ratings and votes make the record auditable without publishing it, which is what allows participation from organisations that restrict public positions.
- **Silence is consent** in Decide. A non-response within the window is recorded as consent by default. There is no abstention.
- **Object requires text.** An objection must state specifically what would need to change, ideally with proposed wording. Objecting commits the objector to participating in its resolution.
- **Rating calibration.** 0 means you would fundamentally object, 5 means you could probably accept it, 10 means you would fully endorse.
- **Candidates** are capped at roughly 150 words and presented as three types: consensus, popular, anti-consensus. Every participant rates all three 0 to 10 and comments on each.
- **Objection-resolution ladder.** An objection unresolved after a revision round activates a live resolution session in the next standing slot, with at least 72 hours' notice. Attendance is mandatory for objectors and for a representative of the endorsing position.
- **Fallback** after three Decide rounds: most endorsements plus consents (defaults count), then most endorsements, then most active responses, then scored 0 to 10 with highest minimax winning.
- **Minimax of 5 or above** on the leading candidate is advisory guidance for moving from Deliberate to Decide, not a gate.
- **Quorum failure** extends the window automatically by a few days, then becomes a facilitator judgment call recommended to the Lead.
- **All deadlines are Anywhere on Earth.**
- **Phase transitions** are decided by the Lead on the facilitator's recommendation, bounded by the round caps.
- **Human decisions, AI processing.** The AI synthesises and surfaces patterns; it decides nothing. The facilitator reviews every AI output before it reaches participants and never expresses an opinion on substance.
