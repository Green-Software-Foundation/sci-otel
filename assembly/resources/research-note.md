# Assembly Research Note

## How to read this note

All participants read the Shared Spine:

* Read Track A if your background is OpenTelemetry rather than carbon measurement;
* Read Track B if your background is carbon or sustainability measurement rather than OpenTelemetry.
* Read both where applicable.

This note is reference material and is not part of the deliberation.

## Shared Spine

### Source standard

Software Carbon Intensity is published as an international standard, ISO/IEC 21031:2024. The standard is fixed. The Assembly decides how to represent SCI in OpenTelemetry, not whether to alter the definition or calculation of SCI. Track A summarises the standard itself.

### From this Assembly to OpenTelemetry: the three steps

The work produces three distinct documents, each with a different owner, audience and level of commitment:

- **Step 1, the blueprint (this Assembly).** The agreed design: scope, namespace, signal decisions, composition model, in consensus prose, with the vote record and known-unknowns. Authored collectively by the Assembly and published to GSF membership. The only artefact participants directly author.
- **Step 2, the draft conventions (after the Assembly).** Once the blueprint is agreed, it is rendered into formal semantic conventions: definitions, registry entries and normative documentation. Participants do not draft this line by line, but they review the rendering before it is submitted, to confirm it stays faithful to what the Assembly agreed. It is then carried to the OpenTelemetry Semantic Conventions SIG.
- **Step 3, the OpenTelemetry conventions (the SIG's process).** The conventions that exist in OpenTelemetry after SIG review and revision through OpenTelemetry governance, hosted under the federated model at `development` stability. Owned by the OpenTelemetry community. The Assembly influences this step; it does not control it.

Two points follow. The Assembly does not bypass OpenTelemetry governance: Step 3 runs through the SIG's own process, and consensus in the Assembly does not pre-empt consensus at the SIG. And participation does not end with the blueprint: participants agree direction in Step 1 and review the draft conventions in Step 2 before submission. Detailed wording is settled at Steps 2 and 3, so the blueprint records decisions and direction rather than final phrasing.

### Prior-art register

Two categories of prior art are referenced in the questions.

**Existing OpenTelemetry conventions to build on.** OpenTelemetry's hardware conventions, currently at `development` stability, define component energy and power: `hw.energy` (a Counter, in joules) and `hw.power` (a Gauge, in watts), with `hw.host.energy` and `hw.host.power` for the whole physical host. The conventions recommend reporting energy in preference to power. Component identity is carried on `hw.*` attributes such as `hw.id` and `hw.type`, and host identity on resource attributes, not on the metrics themselves. Sentry Software was a principal contributor to this work. These sit alongside the `system.*`, `k8s.*`, `container.*` and `cloud.region` conventions. Reuse of existing conventions is an OpenTelemetry acceptance criterion.

**Existing implementations.** Software energy and carbon are measured in production by several projects, ordered here from narrowest to broadest scope. Kepler attributes energy consumption to Kubernetes workloads. Aether (by re-cinq) is an OpenTelemetry exporter that calculates the carbon emissions of cloud infrastructure. RETIT, with the University of Applied Sciences Munich and presented at the GSF Global Summit 2024, demonstrated a direct SCI calculation over OpenTelemetry, capturing both the functional unit (R) and the resource demands of a transaction. Each demonstrates a different segment of the pipeline is feasible.

**Prior institutional direction.** The GSF Real-Time Cloud project independently concluded that carbon metrics for cloud providers should be defined as OpenTelemetry semantic conventions, noting OpenTelemetry's support across AWS, Azure and GCP. The direction this Assembly takes is not a lone bet.

**Scope of prior art in the deliberation.** Prior art is reference evidence only and confers no standing in the deliberation. Candidates are framed in terms of what a backend must be able to compute, not in terms of what any specific tool emits.

### Glossary

Terms are grouped by originating domain.

**From the SCI world**

- **SCI:** Software Carbon Intensity, a rate of carbon emissions per unit of useful work, defined by the formula **SCI = (E x I + M) / R**.
- **E, energy:** the energy consumed by the software, in kilowatt-hours.
- **I, carbon intensity:** the carbon emitted per unit of energy for a given location and time, in grams of CO2-equivalent per kilowatt-hour.
- **M, embodied carbon:** the emissions from manufacturing and disposing of the hardware the software runs on, apportioned to the software.
- **R, functional unit:** the unit of useful work the score is expressed per, for example per user, per API call, or per transaction. R is what turns a total into a rate.
- **gCO2e:** grams of carbon-dioxide equivalent, the common unit for expressing a quantity of emissions.
- **Operational versus embodied:** operational emissions come from running the software (E and I); embodied emissions come from the hardware existing at all (M).

**From the OpenTelemetry world**

- **OpenTelemetry (OTel):** the open standard for telemetry, the traces, metrics, logs and related signals that systems emit.
- **Semantic conventions (semconv):** the shared definitions that make a piece of telemetry mean the same thing everywhere.
- **Signal:** a kind of telemetry. The taxonomy is spans, metrics, events, resources and profiles.
- **Attribute:** a key-value pair attached to a signal, for example `cloud.region`.
- **Metric and instrument:** a measured value over time; the instrument is how it is recorded (counter, gauge, histogram).
- **Span:** a timed operation within a trace. **Event:** a point-in-time occurrence. **Resource / entity:** the thing producing the telemetry, and its identity.
- **Namespace:** the naming home for a group of conventions, for example `hw.*`.
- **Requirement level:** how strongly an attribute is expected, one of Required, Recommended, or Opt-In.
- **Stability level:** how settled a convention is; new conventions start at `development`.
- **Cardinality:** how many distinct values an attribute can take; high-cardinality attributes are constrained to Opt-In.
- **UCUM:** the unit code system OpenTelemetry uses for metric units. Relevant because gCO2e is not a UCUM unit, which is a decision the Assembly must make.
- **Registry, codeowners, SIG:** the catalogue an attribute is registered in; the people responsible for a convention; and the Special Interest Group that governs semantic conventions.
- **Instrumentation:** the code that actually emits the telemetry.

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

*In preparation.*
