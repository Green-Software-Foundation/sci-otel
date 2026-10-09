# Topic 2: What Every Value Declares

## Purpose

Establish what every value these conventions carry must state about itself. Topic 1 made this declaration the precondition for every ranked use case. The SCI specification makes it the first three steps of its procedure (Bound, Scale, Define) and part of its Report step. Topics 3 and 4 attach energy, carbon intensity and embodied carbon to the declaration settled here, so this Topic produces the shared contract every later signal must meet.

This Topic decides what each part of the declaration states and where it is intended to sit in OpenTelemetry's existing data model. It builds on what OpenTelemetry provides today, set out below, and says plainly where nothing existing fits. Attribute keys, final requirement levels and any new entity definitions are settled later through OpenTelemetry's own review.

## What the Topic must decide

One decision: the declaration every value carries. It must let the first-ranked use case's consumer show that a baseline and a changed system were quantified using an identical methodology, against the same functional unit, over the same window.

For each element, a candidate states what it declares, its intended requirement level, which existing OpenTelemetry concept it builds on (or that nothing existing fits), and where it is carried. Each element is defined precisely enough that two independent implementations, observing the same software, would produce the same declaration.

- **Entity identity.** What Topic 1 calls a consistently identified software entity. Which existing identifying attributes establish that a baseline and a changed system are the same software, and which existing attribute marks the change between them. Whether comparison is anchored at the service, or also at the namespace or deployment environment. When a value is produced by an observer outside the software, such as a node agent or a Collector receiver, rather than by the software's own SDK, which identity the value must carry, and whether service identity is required on it or may be attached later by mapping from infrastructure identity.
- **Boundary composition.** What a value states about the SCI software boundary it belongs to: which components are inside it, which of those are observed through telemetry, and which are inside but not observed. Either this is carried in telemetry, or it is disclosed alongside the reported SCI value and not carried in telemetry.
- **Functional unit.** What Topic 1 calls the unit of useful work, which is the SCI's functional unit (R). Every value is measured against a declared functional unit, and the conventions do not prescribe which one. The choice is how the count of R becomes available: existing semantic convention metrics that already count work are designated as eligible sources of R, a dedicated count is defined for work no existing convention records, or both. Also, whether the kind of R is declared through the metric's unit annotation, through an attribute, or both. A position names the term the conventions use for the concept, given that "unit of work", "operation" and "unit" already carry meanings in OpenTelemetry.
- **Window alignment.** How a value and its count of R are shown to cover the same period. Either both are required to come from the same producer with the same temporality and collection interval, or values from different producers are aligned at query time from their declared start and end times, which then makes the start time required on these values.
- **Quantification method.** Either a value identifies its method by name and version only, or it also states the source of its input data, either always or only when its nature is calculated, estimated or forecast. Neither carries the methodology itself.
- **Nature.** A definition of each of measured, calculated, estimated and forecast that tells an implementer which one applies to a given value, and how each maps onto the SCI's two quantification methods, measurement and calculation. A nature that is neither says so. Whether a confidence indicator is part of the declaration at all, and if so at what intended requirement level.
- **Completeness.** What a value states about what it covers. Either it states which SCI terms it covers (operational, embodied, or both), or it also states whether every component inside its declared software boundary is included.

There is no required order. Lead with whichever element the position turns on.

## What OpenTelemetry provides today

Facts candidates build on. Stability is noted because Development items can still change.

- **Resource and entities.** Every signal exported over OTLP is associated with a Resource describing the observed entity. A Resource is composed of entities. An entity's identifying attributes must not change during its lifespan; its descriptive attributes may. (Resource and entity data models: Development.)
- **Service identity.** In the `service` entity, `service.name` is identifying and `service.version` is descriptive, with its format undefined by the conventions. `service.namespace` and `service.instance` are separate entities. `service.instance.id` is recommended to be a random UUID, so it changes when instances are replaced. (Stable.)
- **Infrastructure identity.** `host.*`, `container.*` and `k8s.*` identify infrastructure. Container and pod identifiers change on each rollout. (Mixed stability.)
- **Deployment environment.** `deployment.environment.name` does not currently affect service identity. A proposal to make it identifying for a deployment entity is open. (In flux.)
- **Observers.** OpenTelemetry's own guidance notes that some identity, such as `service.instance.id`, is hard to detect consistently from both outside and inside an SDK. The Collector can enrich telemetry with Kubernetes and resource attributes after it is produced.
- **Instrumentation scope.** Telemetry is associated with the scope that produced it, identified by name, version, schema URL and attributes. (Stable.)
- **Metric data points.** Sums carry a start and end time and a temporality (delta or cumulative). The start time is optional but strongly encouraged. (Stable.)
- **Metric descriptors.** Every metric has a name, a UCUM unit and a description. Counts use curly-brace annotations, such as `{request}`. The description does not identify a metric stream. (Stable.)
- **Existing work counts.** Existing conventions already count work, for example the request duration histograms for HTTP servers, whose counts give the number of requests in a window.
- **Vocabulary already in use.** A span represents a unit of work or operation. "Unit" is a metric's unit of measurement. "Operation" appears in attribute and metric names.
- **Requirement levels.** Required, Conditionally Required (with a stated condition), Recommended and Opt-In. Required expects an absolute majority of instrumentations to populate the attribute efficiently. Metric attributes that may have high cardinality can only be Opt-In. (Stable.)
- **Out-of-band entity information.** Entity events can describe entities and their attributes separately from the telemetry that references them. (Development.)
- **What does not exist.** No existing convention declares whether a value is measured, calculated, estimated or forecast, or how confident it is. No existing convention describes an SCI software boundary or a functional unit.

## Required shape

Seven headed entries, using these headings:

- **Which software is this value about?** (entity identity)
- **What does its boundary include?** (boundary composition)
- **Per what?** (functional unit)
- **Over which window?** (window alignment)
- **How was it produced, and was it produced the same way last time?** (quantification method)
- **Was it measured, calculated, estimated or forecast?** (nature)
- **What does it cover?** (completeness)

Under each heading, four labeled fields:

- **Declares:** what the element states.
- **Intended level:** Required, Conditionally Required (with the condition), Recommended or Opt-In, subject to OpenTelemetry review.
- **Builds on:** the existing OpenTelemetry concept from the list above, or "nothing existing fits".
- **Carried in:** resource or entity, instrumentation scope, data point attribute, metric descriptor, entity event, or disclosed alongside the reported SCI value and not carried in telemetry.

The nature entry adds a fifth field, **Distinguishes**, defining each of measured, calculated, estimated and forecast.

Close with one concrete example: a single service compared before and after one release, showing what each element states for that service, naming only existing OpenTelemetry attributes and no new attributes, metrics or units.

## Length

No word target. Length follows what precision requires. Every sentence either declares something or defines a term. A candidate that runs long because it explains, argues, compares itself with alternatives or reaches into a later Topic is wrong, and the fix is to cut that material. A candidate that runs long because it defines precisely is right, and is never shortened by loosening a definition, dropping an element or abstracting a declaration into a description.

## What later Topics decide, and must not appear

Namespace. Units, apart from whether the kind of functional unit is declared through a unit annotation. Signal types and instrument selection. The levels at which energy is reported. Carbon intensity type and granularity. Idle and unattributed energy. Allocation methods for embodied carbon, and what an allocation declaration contains. How an SCI value is composed, including roll-up across software boundaries and whether component values must reconcile with a parent. Which software is instrumented directly, and what is emitted by default. Definitions of SCI itself or of OpenTelemetry mechanics.

A candidate may name existing OpenTelemetry attributes, entities, mechanisms and metrics. It does not name, type or define anything new, with one exception: it chooses the term the blueprint uses for the functional unit.

Material a later Topic owns is deferred, not excluded. Leave it out silently rather than noting that it sits elsewhere.

## Settled before this Topic, and not open

**From Topic 1, the ranked use cases, in this order:**

1. An application, platform or SRE engineer asks whether a release, configuration, architectural or dependency change reduced energy or emissions for the same work, and if they increased, which part of the system is responsible.
2. An engineer or technical decision-maker asks which provider, service or migration option produces less carbon for equivalent work. The conventions serve this only partially.
3. An automated scheduler, autoscaler or placement system asks which option available now would cost less carbon.

Where they conflict, the first prevails.

**From Topic 1, the floor:** every value declares its software boundary, quantification method, functional unit, nature, and completeness, including whether operational, embodied, or both are covered. A fast, modeled or partial value is labeled as such. The conventions require a declared functional unit and do not prescribe which one.

**From the SCI specification:**

- The functional unit is chosen for the software being measured and held consistent across all components in the software boundary.
- Quantification method is decided per component, as measurement or calculation.
- A baseline uses an identical methodology.
- The software boundary includes all supporting infrastructure that significantly contributes to operation, including end user, IoT and edge devices and build and deploy pipelines.

**Also settled:**

- Embodied carbon is inside these conventions.
- Market-based measures, meaning offsets, renewable energy certificates and similar instruments, are excluded.
- Cost and financial data are not quantities these conventions carry.

## Outside the Assembly

YAML authoring. Attribute keys, final requirement levels, entity definitions and stability, which OpenTelemetry settles in its own review. Codeowner and SIG-sponsor arrangements. Submission logistics, phasing, hosting and publication sequencing. Selection or coordination of reference implementations. Upstream OpenTelemetry governance. Responses reaching for these are noted and set aside, not deliberated.
