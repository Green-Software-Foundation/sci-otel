# Assembly Research Note

## Read this first

### What this Assembly is deciding

We are not redefining SCI. We are deciding how SCI should be represented in OpenTelemetry.

### The core question

How should each part of **SCI = (E x I + M) / R** be expressed through OpenTelemetry semantic conventions?

### What you need to know before deliberation

- SCI is a rate, not a total.
- SCI is fixed by ISO/IEC 21031:2024; the Assembly decides representation, not methodology.
- OpenTelemetry standardises telemetry structures, not organisational carbon accounting.
- Energy already has OpenTelemetry precedent through `hw.energy`.
- New conventions need codeowners, YAML definitions, `development` stability and prototype evidence.

## Overview

The Software Carbon Intensity (SCI) specification, ISO/IEC 21031:2024, measures software carbon as a rate of emissions per unit of useful work:

**SCI = (E x I + M) / R**

where **E** is the energy the software uses, **I** the carbon intensity of the grid supplying it, **M** the embodied carbon of the hardware, and **R** the unit of useful work the score is expressed per.

OpenTelemetry's semantic conventions are the shared vocabulary that makes telemetry mean the same thing everywhere. Today there is no agreed way to express SCI as native OpenTelemetry telemetry.

The Assembly's task is to agree how each part of that formula should be represented in OpenTelemetry. The SCI methodology is fixed by the ISO standard; what is open is its representation, not its definition.

### What participants are not being asked to decide

- Whether SCI is the right formula.
- Whether offsets should count.
- Whether SCI should use market-based measures for carbon intensity.
- Whether OpenTelemetry governance should accept the proposal.
- The final YAML wording of the semantic conventions.
- The final implementation details for every instrumentation.

## Suggested reading paths

### If you know OpenTelemetry but not SCI

Read: Overview → Track A → Track B recap.

### If you know carbon or sustainability measurement but not OpenTelemetry

Read: Overview → Track B → Track A recap.

## Glossary

| Term | Plain-English meaning |
| --- | --- |
| SCI | Carbon emissions per unit of useful work. |
| E | Energy used by software for a functional unit of work. |
| I | Region-specific carbon intensity of electricity. |
| M | Embodied emissions of hardware allocated to software. |
| R | Useful work unit, such as request, user, job or device. |
| Metric | Numeric measurement captured at runtime. |
| Resource | Entity producing telemetry. |
| Attribute | Key-value metadata attached to telemetry. |
| Semantic convention | Shared naming and structure rules for telemetry. |
| Cardinality | Number of unique attribute combinations. |

The companion Glossary is the single source of truth for full definitions.

## Track A: The SCI specification, for the OpenTelemetry reader

Track A summarises the Software Carbon Intensity (SCI) specification for readers whose background is OpenTelemetry rather than carbon measurement. Reference material, not a deliberation input.

### What SCI is

SCI is a rate, not a total. It expresses emissions per unit of useful work, not absolute emissions. A total falls when a system does less work; a rate falls only when work is done more efficiently. SCI measures efficiency, and offsets cannot reduce it.

**The formula:**

**SCI = (E x I + M) per R**

This is often written compactly as `(E x I + M) / R`, but the specification frames R as the functional unit the score is expressed per.

### The SCI procedure

The specification defines five steps:

1. **Bound:** decide the software boundary.
2. **Scale:** pick the functional unit that describes how the application scales.
3. **Define:** decide the quantification method for each component in the boundary.
4. **Quantify:** calculate a rate for every component; the whole application SCI is the sum of the component SCI values.
5. **Report:** disclose the SCI score, software boundary and calculation methodology.

### What each formula component means

**E, energy.** Energy consumed by the software system for a functional unit of work, in kWh. Energy consumption should include all hardware reserved or provisioned for the software, not only the hardware actually used. In OpenTelemetry terms, energy corresponds to existing hardware conventions such as `hw.energy` and `hw.host.energy`, though OpenTelemetry reports energy in joules. The open questions concern boundary and instrument type, not the definition of energy.

**I, carbon intensity.** Emissions per unit of energy, in gCO2eq/kWh. The specification defines I as region-specific grid carbon intensity. If electricity consumption is connected to a grid, short-run marginal, long-run marginal, or average emissions grid intensity may be used, excluding market-based measures. I is location-based rather than market-based, and identical work in different regions or times can yield different SCI scores.

**M, embodied emissions.** Emissions from the creation and disposal of hardware, in gCO2eq, allocated to the software through time-share and resource-share. The SCI equation defines this as `M = TE * TS * RS`, where TE is total embodied emissions, TS is the time-share reserved for the software, and RS is the resource-share reserved for the software. M must not include market-based measures.

**R, the functional unit.** The unit of useful work the score is expressed per, and the term that converts a total to a rate. The specification requires R to reflect how the application scales; candidate units include per user, per request, per job, per device. R is a modelling decision, not only a measurement, and it determines what every other component is measured against. A consistent R must be used across all components in the software boundary. If a component uses a different functional unit, it must be converted to the aggregate functional unit, and any conversion factors must be disclosed.

### What is fixed by ISO

SCI is fixed for this Assembly by the GSF SCI specification, published as ISO/IEC 21031:2024. The methodology is fixed: the Assembly decides how to represent SCI in OpenTelemetry, not how SCI is calculated.

Two constraints are frequently unexpected:

- **SCI is action-oriented.** The specification is designed so the score falls when software uses less energy, uses less hardware, or shifts work to lower-carbon energy sources.
- **Offsets and neutralisations cannot reduce a score.** SCI is stricter than most organisational carbon accounting.

The software boundary is not limited to application code. The SCI calculation shall include supporting infrastructure and systems that significantly contribute to operation, such as compute, storage, networking, memory, monitoring, logging, build and deploy pipelines, testing, ML training, backup, redundancy, failover and relevant end-user, IoT or edge devices.

The specification permits each component in the software boundary to be quantified through measurement using real-world data or calculation using models. The goal is to quantify carbon emitted per one unit of R. Disclosure is mandatory: the SCI score, software boundary and calculation methodology must be reported. Method and boundary disclosure is therefore itself information the conventions must carry, and recurs as a cross-cutting attribute rather than a per-component detail.

### What is open for this Assembly

The Assembly decides how SCI is represented in telemetry:

- how each component becomes an OpenTelemetry representation
- which existing conventions are reused
- where boundaries sit
- how R is expressed
- how the components compose
- whether the SCI score is represented or derived

### Track A recap

For this Assembly, the important SCI rules are:

- SCI is fixed by ISO/IEC 21031:2024.
- SCI is a rate, not a total.
- SCI measures emissions per unit of useful work.
- Offsets and neutralisations do not reduce SCI.
- I is region-specific and excludes market-based measures.
- Boundary and quantification method must be disclosed.
- The Assembly decides representation, not methodology.

## Track B: The OpenTelemetry landscape, for the sustainability reader

Track B summarises how OpenTelemetry represents things, for readers whose background is carbon or sustainability measurement rather than OpenTelemetry. Reference material, not a deliberation input. It assumes the companion Glossary.

### What OpenTelemetry represents

**What OpenTelemetry says:** OpenTelemetry currently supports traces, metrics, logs and baggage as signals. Profiles are emerging, and events are treated as a specific type of log. Spans are the units that make up traces, while resources describe the entity producing telemetry rather than being a signal in their own right.

**Why the Assembly cares:** Carbon telemetry may touch several parts of this model: metrics for numeric quantities, resources for the entities and boundaries those quantities belong to, logs or events for completed calculation records, and possibly traces or spans where carbon data needs to be attached to units of work. Which representation each SCI component uses is a section decision, not a given.

### What metrics are

**What OpenTelemetry says:** A metric is recorded through an instrument, and the instrument type carries meaning. Common instrument kinds include Counter, UpDownCounter, Gauge and Histogram, with synchronous and asynchronous variants. A Counter accumulates a value that only rises. A Gauge reports a current value. A Histogram records a distribution.

**Why the Assembly cares:** Most SCI components are numeric, so metrics are central. The instrument choice is not cosmetic; it determines how a backend aggregates the data. The same choice recurs for every SCI quantity.

### What resources and entities are

**What OpenTelemetry says:** A resource describes the entity producing the telemetry, while metric attributes describe individual measurements. OpenTelemetry formalises this through its entity model.

**Why the Assembly cares:** Embodied carbon (M) and the software boundary may be properties of a thing, not events in a stream. Whether M is a metric emitted over time, an attribute declared on a resource, or represented through an entity model is a genuine fork with different conventions on each side.

### What semantic conventions are

**What OpenTelemetry says:** Semantic conventions standardise common names and structures for telemetry data across traces, metrics, logs, profiles and resources.

**Why the Assembly cares:** In practice, this favours standardising the observable components of a calculation. A composite score like SCI therefore needs an explicit decision: either represent it as telemetry in its own right, or standardise the components and document how backends derive it.

### Attributes and requirement levels

**What OpenTelemetry says:** Attributes are the key-value pairs that qualify telemetry, such as region, boundary or method. Each attribute referenced by a convention needs a requirement level. Only attributes that are absolutely essential and always available should be Required. Attributes that may include sensitive information, are expensive to obtain, are verbose, or are likely to create cardinality pressure should be Opt-In.

**Why the Assembly cares:** Carbon-intensity provenance, detailed boundary identifiers and method-disclosure fields are design-sensitive rather than harmless metadata. Requirement-level direction is a blueprint decision, not a drafting detail.

### Attribute discipline and complexity

**What OpenTelemetry says:** Convention authors are expected to reuse existing attributes where possible, define new attributes only where there is clear end-user value, and avoid capturing every available detail. Complex or structured attributes are hard for backends to index and query, so conventions should use flat attributes where possible.

**Why the Assembly cares:** Boundaries, method disclosures, hardware allocation models and provenance chains can become nested quickly. The Assembly should start from the smallest useful set of components and attributes, then add detail incrementally through prototype feedback.

### Stability, ownership and prototyping

**What OpenTelemetry says:** New semantic conventions must have codeowners, should be defined in YAML, and should begin at `development` stability. OpenTelemetry strongly recommends prototyping proposed conventions in one or more instrumentations before or alongside proposal work.

**Why the Assembly cares:** Feasibility evidence gathered during the Assembly has direct downstream value. A proposal backed by real telemetry, reasonable overhead and cross-technology terminology will be easier to progress than an abstract design.

### The hardware conventions, in detail

These are the most important existing conventions for this work, because energy already has a home. They define `hw.energy` as a Counter in joules and `hw.power` as a Gauge in watts, with `hw.host.energy` and `hw.host.power` for the whole physical host, and they explicitly recommend reporting energy in preference to power.

Component identity is carried on `hw.*` attributes such as `hw.id` and `hw.type`; the identity of the host itself lives on resource attributes, not on the metric.

**Why the Assembly cares:** E should almost certainly build on this, plus `system.*`, `k8s.*`, `container.*` and `cloud.region`, rather than invent a parallel energy vocabulary.

### Units and namespace

**What OpenTelemetry says:** OpenTelemetry metric units should follow UCUM, the Unified Code for Units of Measure. Naming follows dotted namespaces.

**Why the Assembly cares:** Energy fits cleanly through joules, as the hardware conventions already use. Carbon-equivalent units such as gCO2e need explicit design treatment, because they do not appear as a straightforward inherited unit from the existing OpenTelemetry concepts. Where carbon conventions should live, for example `carbon.*` or `sustainability.*`, is an early decision that shapes everything named after it.

### Spans, events and completed calculations

**What OpenTelemetry says:** Spans describe individual executions of specific operations within a trace, and are appropriate when the operation is significant and has duration. Point-in-time occurrences should use events instead.

**Why the Assembly cares:** A completed SCI calculation is a point-in-time record, so if represented directly it is more naturally an event or log candidate. A span would only be appropriate for the calculation process itself if that operation has duration and observability value.

### Track B recap

For this Assembly, the important OpenTelemetry rules are:

- Use existing conventions where possible.
- Metrics fit numeric quantities.
- Resources describe telemetry-producing entities.
- Spans are for operations with duration.
- Events and logs fit point-in-time records.
- Attributes must be controlled for sensitivity, cost, verbosity and cardinality.
- New conventions need codeowners, YAML, `development` stability and prototype evidence.

## Prior-art register

The work does not start from nothing. Energy already has OpenTelemetry precedent; workload energy is collectable; carbon export exists; full SCI calculation has been demonstrated; GSF has already concluded cloud carbon metrics belong in OpenTelemetry semantic conventions.

| Prior art | What it is | Why it matters here |
| --- | --- | --- |
| OpenTelemetry hardware conventions | Energy and power metrics (`hw.energy`, `hw.power`, and host-level `hw.host.energy` and `hw.host.power`) in joules and watts, at `development` stability. A principal contribution from Sentry Software. | The reuse-first anchor for E: energy already has a home in OpenTelemetry. |
| OpenTelemetry system, Kubernetes, container and cloud conventions | Mature conventions for compute, orchestration and cloud location (`system.*`, `k8s.*`, `container.*`, `cloud.region`). | Existing signals the blueprint builds on rather than duplicates. |
| Kepler | eBPF-based energy attribution for Kubernetes workloads. | Workload-level energy is collectable in production. |
| Aether (re-cinq) | An OpenTelemetry exporter that calculates the carbon emissions of cloud infrastructure. | Carbon can be exported through OpenTelemetry today. |
| RETIT, with UAS Munich | A direct SCI calculation over OpenTelemetry, presented at the GSF Global Summit 2024. | The full SCI pipeline, including the functional unit R, is achievable. |
| GSF Real-Time Cloud | A GSF project that concluded cloud carbon metrics should be defined as OpenTelemetry semantic conventions. | Independent institutional direction toward this approach. |

Prior art is reference evidence only and confers no standing in the deliberation. Candidates are framed in terms of what a backend must be able to compute, not what any specific tool emits.
