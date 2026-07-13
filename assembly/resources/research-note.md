# Assembly Research Note

## Overview

The Software Carbon Intensity (SCI) specification, ISO/IEC 21031:2024, measures software carbon as a rate of emissions per unit of useful work:

**SCI = (E x I + M) / R**

where **E** is the energy the software uses, **I** the carbon intensity of the grid supplying it, **M** the embodied carbon of the hardware, and **R** the unit of useful work the score is expressed per.

OpenTelemetry's semantic conventions are the shared vocabulary that makes telemetry mean the same thing everywhere. Today there is no agreed way to express SCI as native OpenTelemetry telemetry.

The Assembly's task is to agree how each part of that formula should be represented in OpenTelemetry. The SCI methodology is fixed by the ISO standard; what is open is its representation, not its definition. Track A explains the specification in full for readers coming to it fresh.

## How to read this note

All participants read the shared background. Read Track A if your background is OpenTelemetry rather than carbon measurement; read Track B if your background is carbon or sustainability measurement rather than OpenTelemetry. Read both where applicable. This note is reference material and is not part of the deliberation.

## Shared background

### From this Assembly to OpenTelemetry: the three steps

The work produces three distinct documents, each with a different owner, audience and level of commitment:

- **Step 1, the blueprint (this Assembly).** The agreed design: scope, namespace, signal decisions, composition model, in consensus prose, with the vote record and known-unknowns. Authored collectively by the Assembly and published to GSF membership. The only artefact participants directly author.
- **Step 2, the draft conventions (after the Assembly).** Once the blueprint is agreed, it is rendered into formal semantic conventions: definitions, registry entries and normative documentation. Participants do not draft this line by line, but they review the rendering before it is submitted, to confirm it stays faithful to what the Assembly agreed. It is then carried to the OpenTelemetry Semantic Conventions SIG.
- **Step 3, the OpenTelemetry conventions (the SIG's process).** The conventions that exist in OpenTelemetry after SIG review and revision through OpenTelemetry governance, hosted in the OpenTelemetry organisation at `development` stability. Owned by the OpenTelemetry community. The Assembly influences this step; it does not control it.

Two points follow. The Assembly does not bypass OpenTelemetry governance: Step 3 runs through the SIG's own process, and consensus in the Assembly does not pre-empt consensus at the SIG. And participation does not end with the blueprint: participants agree direction in Step 1 and review the draft conventions in Step 2 before submission. Detailed wording is settled at Steps 2 and 3, so the blueprint records decisions and direction rather than final phrasing.

### Prior-art register

The work does not start from nothing. The table lists the OpenTelemetry conventions it builds on, alongside the implementations and institutional direction that show the approach is feasible and supported.

| Prior art | What it is | Why it matters here |
| --- | --- | --- |
| OpenTelemetry hardware conventions | Energy and power metrics (`hw.energy`, `hw.power`, and host-level `hw.host.energy` and `hw.host.power`) in joules and watts, at `development` stability. A principal contribution from Sentry Software. | The reuse-first anchor for E: energy already has a home in OpenTelemetry. |
| OpenTelemetry system, Kubernetes, container and cloud conventions | Mature conventions for compute, orchestration and cloud location (`system.*`, `k8s.*`, `container.*`, `cloud.region`). | Existing signals the blueprint builds on rather than duplicates. |
| Kepler | eBPF-based energy attribution for Kubernetes workloads. | Workload-level energy is collectable in production. |
| Aether (re-cinq) | An OpenTelemetry exporter that calculates the carbon emissions of cloud infrastructure. | Carbon can be exported through OpenTelemetry today. |
| RETIT, with UAS Munich | A direct SCI calculation over OpenTelemetry, presented at the GSF Global Summit 2024. | The full SCI pipeline, including the functional unit R, is achievable. |
| GSF Real-Time Cloud | A GSF project that concluded cloud carbon metrics should be defined as OpenTelemetry semantic conventions. | Independent institutional direction toward this approach. |

Prior art is reference evidence only and confers no standing in the deliberation. Candidates are framed in terms of what a backend must be able to compute, not what any specific tool emits.

### Glossary

The terms used across this note, from both the SCI and OpenTelemetry worlds, are defined in the companion Glossary, which is the single source of truth for definitions.

## Track A: The SCI specification, for the OpenTelemetry reader

Track A summarises the Software Carbon Intensity (SCI) specification for readers whose background is OpenTelemetry rather than carbon measurement. Reference material, not a deliberation input.

The domain has one property unique among semantic-conventions areas: observing a system's carbon footprint itself consumes energy and emits carbon. Collectors, SDKs and exporters add to the quantity being measured. The measurement signal is not independent of the measured value.

**SCI is a rate, not a total.** It expresses emissions per unit of useful work, not absolute emissions. A total falls when a system does less work; a rate falls only when work is done more efficiently. SCI measures efficiency, and offsets cannot reduce it (see the ISO constraints below).

**The formula:**

**SCI = (E x I + M) / R**

Three carbon or energy quantities (E, I, M) over one unit of work (R).

**E, energy.** Energy consumed by the software within its defined boundary, in kWh. Corresponds to existing hardware conventions (`hw.energy`, `hw.host.energy`, joules). The open questions concern boundary and instrument type, not the definition of energy.

**I, carbon intensity.** Emissions per unit of energy, in gCO2e/kWh. The specification defines I as location-based and marginal: the emissions of the specific grid supplying the energy, at the time of use, for the next unit of demand. I is sourced from external grid data, not from the running system, and varies by region and by hour. Identical work in different regions yields different SCI scores.

**M, embodied carbon.** Emissions from manufacturing, transport and disposal of the hardware, in gCO2e, apportioned to the software by time-share and resource-share (the fraction of the hardware's life reserved, and the fraction of its resources used). M has the least available data and the least prior art of the four components.

**R, the functional unit.** The unit of useful work the score is expressed per, and the term that converts a total to a rate. The specification requires R to reflect how the application scales; candidate units include per user, per request, per job, per device. R is a modelling decision, not only a measurement, and it determines what every other component is measured against.

**ISO constraints.** SCI is published as ISO/IEC 21031:2024. The methodology is fixed: the Assembly decides how to represent SCI in OpenTelemetry, not how SCI is calculated. Two constraints are frequently unexpected. The formula is consequential: it counts only quantities the operator can act on. Offsets and neutralisations cannot reduce a score. SCI is therefore stricter than most organisational carbon accounting.

**Quantification methods.** The specification permits E and M to be either measured directly or calculated and estimated from models; practitioners select methods according to available data. Disclosure is mandatory: every SCI score must state its software boundary and its quantification method. Method and boundary disclosure is therefore itself information the conventions must carry, and recurs as a cross-cutting attribute rather than a per-component detail.

**Fixed versus open, for the sections.** Fixed by the specification: SCI is a rate; I is location-based and marginal; offsets do not count; boundary and method must be disclosed. Open for the Assembly: how each component becomes an OpenTelemetry signal, which existing conventions are reused, where boundaries sit, how R is expressed, and how the components compose. A question that appears to redefine SCI is asking how SCI is represented in telemetry, not what SCI is.

## Track B: The OpenTelemetry landscape, for the sustainability reader

Track B summarises how OpenTelemetry represents things, for readers whose background is carbon or sustainability measurement rather than OpenTelemetry. Reference material, not a deliberation input. It assumes the companion Glossary.

**Signals: the shapes telemetry can take.** OpenTelemetry defines a fixed set of signal types, and every convention chooses among them: metrics (numeric measurements over time), spans (timed operations within a trace), events (point-in-time occurrences), resources (the entity producing the telemetry) and profiles (code-level sampling). Carbon telemetry plausibly touches three: metrics for energy and carbon quantities, resources for the boundary the numbers belong to, and possibly events for a completed SCI calculation with its inputs. Which signal each SCI component becomes is a section decision, not a given.

**Metrics and instruments.** Most SCI components are numeric, so metrics are central. A metric is recorded through an instrument, and the instrument type carries meaning: a Counter accumulates a value that only rises (cumulative energy in joules), a Gauge reports an instantaneous value (power in watts), and a Histogram records a distribution. The choice is not cosmetic; it determines how a backend aggregates the data. The same choice recurs for every SCI quantity.

**Resources and entities: where a value belongs.** A metric is a number; a resource says what the number is about (a host, a container, a Kubernetes pod, a cloud region). OpenTelemetry formalises this through its entity model. It matters directly to SCI because embodied carbon (M) and the software boundary are properties of a thing, not events in a stream. Whether M is a metric emitted over time or an attribute declared on a resource is a genuine fork with different conventions on each side, and it is the heart of Section 4.

**Semantic conventions standardise measurable signals, not derived scores.** OpenTelemetry conventions describe things that are directly measured or observed. A composite value like the SCI score, calculated from other quantities, sits awkwardly in that model. The established preference is to standardise the measurable components (energy, intensity, embodied carbon, the functional unit) and to document how the score is computed over them, leaving tools and backends to derive it. Whether SCI should nonetheless be represented as a signal in its own right is a genuine open question for the Assembly, not a settled matter. Section 5 addresses it directly.

**Attributes and requirement levels.** Attributes are the key-value pairs that qualify a signal (region, boundary, method). Each attribute in a convention is assigned a requirement level: Required (always present), Recommended (present unless there is a reason not to), or Opt-In (off by default, enabled deliberately). The rules are strict and consequential. Only information that is essential and always available can be Required. Anything sensitive, expensive to collect, or high-cardinality must be Opt-In, because high-cardinality attributes multiply storage and cost in a backend. Carbon-intensity provenance and fine-grained boundary identifiers are likely Opt-In for this reason. Requirement-level direction is therefore a blueprint decision, not a drafting detail.

**Stability and ownership.** Every new convention starts at `development` stability, the signal that it may still change, and must declare it. It is written as YAML in the semantic-conventions registry, and it must have codeowners: named people responsible for maintaining it. There is no anonymous convention. OpenTelemetry also strongly recommends prototyping a convention against real telemetry before proposing it, to prove it is collectable, which is why feasibility evidence gathered during the Assembly has direct downstream value.

**The hardware conventions, in detail.** These are the most important existing conventions for this work, because energy already has a home. They define `hw.energy` as a Counter in joules and `hw.power` as a Gauge in watts, with `hw.host.energy` and `hw.host.power` for the whole physical host, and they explicitly recommend reporting energy in preference to power. Component identity is carried on `hw.*` attributes such as `hw.id` and `hw.type`; the identity of the host itself lives on resource attributes, not on the metric. This is the concrete pattern reuse-first points at: E should almost certainly build on this, plus `system.*`, `k8s.*`, `container.*` and `cloud.region`, rather than invent a parallel energy vocabulary.

**Units and namespace.** OpenTelemetry metric units follow UCUM, the Unified Code for Units of Measure. Energy fits cleanly: joules, as the hardware conventions already use. Carbon does not: gCO2e is not a UCUM unit, so how carbon quantities are expressed is a decision the Assembly must make rather than inherit. Naming is the same kind of choice: conventions live under a dotted namespace (the hardware conventions under `hw.*`), and where carbon conventions should live, for example `carbon.*` or `sustainability.*`, is an early decision that shapes everything named after it. Both are Section 2 questions.

**The strategic point: precedent carries unusual weight.** OpenTelemetry's own authoring guidance for defining new metrics is currently marked "to be determined." In the absence of settled guidance, existing conventions become the de facto template, and the hardware conventions are the closest and most authoritative precedent for this domain. This is why reuse-first is a necessity here, not a stylistic preference: departing from the established pattern means arguing against the only precedent the SIG has, with no written guidance to appeal to. The burden of proof sits with anything that duplicates or diverges from what already exists.

**How a proposal reaches OpenTelemetry.** New conventions are proposed to the Semantic Conventions SIG, reviewed in the open, and need a sponsoring approver from within the SIG to progress. A domain-specific area can be developed as its own convention set with its own codeowners inside the OpenTelemetry organisation, as the GenAI semantic conventions are; the same shape is available to carbon. The SIG engages iteratively and favours incremental proposals over large drops.

**Fixed versus open, for the sections.** Fixed by OpenTelemetry: the signal types available, the requirement-level rules, `development` stability and codeowners for anything new, and the reuse-first acceptance criterion. Open for the Assembly: which signal each SCI component becomes, whether the composite score is represented at all or only computed, which existing conventions are reused and where, the namespace and units, the requirement level and cardinality direction of each attribute, and how the whole composes. A question that appears to ask how OpenTelemetry works is really asking how SCI should be expressed within these rules.
