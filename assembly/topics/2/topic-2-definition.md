# Topic 2: What Every Value Declares

## Purpose

Establish what every value these conventions carry must state about itself. Topic 1 made this declaration the precondition for every ranked use case. The SCI specification makes it the first three steps of its procedure: Bound, Scale and Define. Topics 3 and 4 attach energy, carbon intensity and embodied carbon to the declaration settled here, so this Topic produces the shared contract every later signal must meet.

This Topic decides three things: what makes two values about the same software, what work a value is measured against, and how a value says it was produced. It decides what each states, not how OpenTelemetry carries it. Where each declaration sits in OpenTelemetry's data model follows from whether it is fixed for the software, changes with each release, or can differ between values, and is drafted from that answer. Attribute keys, final requirement levels and any new entity definitions are settled later through OpenTelemetry's own review.

## What the Topic must decide

Three decisions. Together they must let the first-ranked use case's consumer show that a baseline and a changed system are the same software, measured against the same functional unit, using an identical methodology.

Each is defined precisely enough that two independent implementations, observing the same software, would produce the same declaration.

- **Sameness.** Which existing identifying attributes establish that two values are about the same software, and whether comparison is anchored at the service alone or also at its namespace or deployment environment. What marks the change between a baseline and a changed system: a release, meaning a version the team assigns, or any new build. Where a value's producer cannot obtain the software's identity, such as an observer outside the software with no mapping available, whether that value can still serve the first-ranked use case, and what it states about the identity it lacks.
- **Functional unit.** Where a value's count of work comes from: existing metrics that already count work, a dedicated count where no existing metric records the work, or both. How the kind of work is declared: as part of the count's unit, as OpenTelemetry already does for counts such as `{request}`, or as a separate attribute.
- **Provenance.** A definition of each of measured, calculated, estimated and forecast that tells an implementer which applies to a given value, and how each maps onto the SCI's two quantification methods, measurement and calculation. A nature that is neither says so. Whether a value states its method by name and version only, or also states the source of its input data, either always or only when it is calculated, estimated or forecast. Whether a confidence indicator is part of the declaration: yes or no.

There is no required order. Lead with whichever decision the position turns on.

## What OpenTelemetry provides today

Facts candidates build on. Stability is noted because Development items can still change.

- **Resource and identity.** Every signal exported over OTLP is associated with a Resource describing the observed entity. Resource attributes identify that entity, so a declaration that changes them makes a value look like different software. Attributes recorded on individual values can differ between values without changing identity. (Resource and entity data models: Development.)
- **Service identity.** In the `service` entity, `service.name` is identifying and `service.version` is descriptive, with its format undefined by the conventions. `service.namespace` is a separate entity. `deployment.environment.name` does not currently affect service identity, and a proposal to change that is open. (Service: Stable. Deployment: in flux.)
- **Service identity in Kubernetes.** OpenTelemetry's non-normative guidance derives `service.version` from, in order: a `resource.opentelemetry.io/service.version` pod annotation, the well-known `app.kubernetes.io/version` label, then the container image tag and digest. The image fallback changes with every build. (Non-normative.)
- **Observers.** Energy is often observed outside the software, by a node agent or a Collector receiver. The Collector's Kubernetes attributes processor can add service identity as telemetry passes through, using metadata about workloads that currently exist. No OpenTelemetry component keeps a history of which workload belonged to which service. Outside Kubernetes there is no equivalent standard mapping.
- **Instrumentation scope.** Telemetry is associated with the scope that produced it, identified by name and version. (Stable.)
- **Counts of work.** Existing conventions already count work, for example the request duration histograms for HTTP servers, whose counts give the number of requests in a window. Counts use UCUM curly-brace annotations for what is counted, such as `{request}`. (Stable.)
- **Vocabulary already in use.** A span represents a unit of work or operation. "Unit" is a metric's unit of measurement. "Operation" appears in attribute and metric names.
- **What does not exist.** No existing convention declares whether a value is measured, calculated, estimated or forecast, or how confident it is. No existing convention describes a functional unit.

## Required shape

Three headed entries, using these headings:

- **Is this the same software, and what changed?** (sameness)
- **Per what?** (functional unit)
- **How was it produced?** (provenance)

Under each heading, three labeled fields:

- **Declares:** what the decision states, naming any existing OpenTelemetry concept it builds on.
- **Required on:** every value, or only where a named ranked use case needs it.
- **Varies:** fixed for the software, changes with each release, or can differ between values. Where an entry declares more than one thing, give the answer for each.

The provenance entry adds a fourth field, **Distinguishes**, defining each of measured, calculated, estimated and forecast.

Close with one concrete example: a single service compared before and after one release, showing what each decision states for that service, naming only existing OpenTelemetry attributes and no new attributes, metrics or units.

Candidates do not state where a declaration sits in OpenTelemetry's data model. The "Varies" answer determines that.

## Length

No word target. Length follows what precision requires. Every sentence either declares something or defines a term. A candidate that runs long because it explains, argues, compares itself with alternatives or reaches into a later Topic is wrong, and the fix is to cut that material. A candidate that runs long because it defines precisely is right, and is never shortened by loosening a definition, dropping a decision or abstracting a declaration into a description.

## What later Topics decide, and must not appear

**Topic 3:** how energy observed outside the software obtains the identity settled here in practice; temporality, start times and gaps in coverage within a window; the levels at which energy is reported; signal types and instrument selection; requirement levels of signals; what is emitted by default; carbon intensity type and granularity; idle, unattributed and shared energy, including how a value's share changes when neighboring workloads change.

**Topic 4:** representation of embodied carbon, allocation methods and what an allocation declaration contains, and missing embodied data.

**Topic 5:** which components a software boundary contains, including other containers sharing a workload; whether an SCI value includes every component in its boundary; converting functional units between components; whether comparison needs a fixed, shared functional unit; roll-up across boundaries; the name the conventions use for the functional unit; namespace; units.

A candidate may name existing OpenTelemetry attributes, entities, mechanisms and metrics. It does not name, type or define anything new.

Material a later Topic owns is deferred, not excluded. Leave it out silently rather than noting that it sits elsewhere.

## Settled before this Topic, and not open

**From Topic 1, the ranked use cases, in this order:**

1. An application, platform or SRE engineer asks whether a release, configuration, architectural or dependency change reduced energy or emissions for the same work, and if they increased, which part of the system is responsible.
2. An engineer or technical decision-maker asks which provider, service or migration option produces less carbon for equivalent work. The conventions serve this only partially.
3. An automated scheduler, autoscaler or placement system asks which option available now would cost less carbon.

Where they conflict, the first prevails.

**From Topic 1, the floor:** every value declares its software boundary, quantification method, functional unit, nature, and completeness, including whether operational, embodied, or both are covered. A fast, modeled or partial value is labeled as such. The conventions require a declared functional unit and do not prescribe which one. Values are resolved finely enough to distinguish the components that contribute to them.

**From the SCI specification:**

- The functional unit is chosen for the software being measured and held consistent across all components in the software boundary.
- A value and its count of functional units cover the same time period.
- Quantification method is decided per component, as measurement or calculation.
- A baseline uses an identical methodology, including the same functional units.
- The software boundary includes all supporting infrastructure that significantly contributes to operation, including end user, IoT and edge devices and build and deploy pipelines.

**Also settled:**

- "Functional unit" is the working term until the conventions' own name is chosen.
- Embodied carbon is inside these conventions.
- Market-based measures, meaning offsets, renewable energy certificates and similar instruments, are excluded.
- Cost and financial data are not quantities these conventions carry.

## Outside the Assembly

YAML authoring. Attribute keys, final requirement levels, entity definitions and stability, which OpenTelemetry settles in its own review. Codeowner and SIG-sponsor arrangements. Submission logistics, phasing, hosting and publication sequencing. Selection or coordination of reference implementations. Upstream OpenTelemetry governance. Responses reaching for these are noted and set aside, not deliberated.
