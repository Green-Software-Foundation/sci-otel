# Topic 2: What Every Value Declares

## Purpose

Establish what every value these conventions carry must state about itself. Topic 1 made this declaration the precondition for every ranked use case. The SCI specification makes it the first three steps of its procedure: Bound, Scale and Define. Topics 3 and 4 attach energy, carbon intensity and embodied carbon to the declaration settled here, so this Topic produces the shared contract every later signal must meet.

This Topic decides what each declaration states, not how OpenTelemetry carries it. Attribute keys, final requirement levels and any new entity definitions are settled later through OpenTelemetry's own review.

## What the Topic must decide

Three decisions. Together they must let the first-ranked use case's consumer show that a baseline and a changed system are the same software, measured against the same functional unit, using an identical methodology.

- **Sameness.** Which existing identifying attributes establish that two values are about the same software, and whether comparison includes the namespace or deployment environment. What marks the change between a baseline and a changed system: a release, meaning a version the team assigns; any new build; or a stated change event, such as a configuration or feature flag change. Whether the infrastructure the software ran on must be visible on the value, so a change of infrastructure is not mistaken for a change to the software. Whether a value whose producer cannot obtain the software's identity can still serve the first-ranked use case, and what it states about the identity it lacks.
- **Functional unit.** Where a value's count of work comes from: existing metrics that already count work, a dedicated count where no existing metric records it, or both. Reusing existing counts is the starting position; a position that adds a dedicated count states why. How the kind of work is declared: in the count's unit, as a separate attribute, or both.
- **Provenance.** What measured, calculated, estimated and forecast each mean, defined precisely enough that two implementers would assign the same nature to the same value, and how each maps onto the SCI's two quantification methods, measurement and calculation. Whether a value states its method by name and version only, or also the source of its input data. Whether a confidence indicator is part of the declaration.

For each answer, the candidate also states its carriage: whether every value carries it or only when a stated condition holds, and whether it is fixed for the software, changes with a release or stated change, changes with the producer, or can differ between values. This tells the spec writer where each declaration belongs.

## Agreement and difference

Candidates are generated from the Discover responses. Where the responses agree on an answer, every candidate gives that answer in the same words, so participants can see what is already shared. Candidates differ only where the responses disagree. Every disagreement the synthesis records has each side taken by at least one candidate, so no position participants raised is lost between generations. An alternative candidate challenges the emerging agreement only on answers a minority of responses supports. Each candidate's position sentence names the answers on which it differs from the others.

## What OpenTelemetry provides today

Facts that bear on these decisions. Stability is noted because Development items can still change.

- **Service identity.** `service.name` is identifying. `service.version` is descriptive and can change without changing identity. `service.instance.id` is replaced whenever an instance restarts or a release rolls out, so comparison cannot anchor on it. `deployment.environment.name` does not currently affect service identity. (Service: Stable. Deployment: in flux.)
- **Version in Kubernetes.** OpenTelemetry's non-normative guidance derives `service.version` from a pod annotation, then the `app.kubernetes.io/version` label, then the container image tag and digest, which change with every build.
- **Observers.** Energy is often observed outside the software, by a node agent or Collector receiver. Its values describe what the observer saw, such as the node. The Collector can add service identity while a workload exists, but nothing in OpenTelemetry keeps a history of which workload belonged to which service.
- **Infrastructure context.** Attributes describing where software runs, such as host type and region, appear on a value only when resource detectors or the Collector add them.
- **Change events.** Feature flag conventions are the nearest existing anchor for a change that ships without a release. (Not yet Stable.)
- **Producer identity.** Instrumentation scope identifies the producer by name and version. (Stable.)
- **Counts of work.** Existing metrics already count work, such as HTTP server request counts, labeled by what they count, such as `{request}`. These counts include health checks and retries. Counts derived from sampled spans are affected by sampling.
- **Cardinality.** A declaration that can differ between values creates a separate metric stream for each distinct value. SDKs cap streams per metric.
- **What does not exist.** No existing convention declares whether a value is measured, calculated, estimated or forecast, or how confident it is.

## Required shape and level of detail

Candidates follow the Topic 2 candidate template: a title, a one-sentence position, a short plain-language summary of how the position works with one example, a decision table with fixed rows in a fixed order, trade-offs, and where the candidate came from. The table carries the agreed answer to each decision, with its carriage. The summary states the principle that connects the answers and does not restate them. Word limits apply to each part so candidates stay comparable.

A candidate names at most the one existing OpenTelemetry attribute each answer is anchored on, such as `service.name` or `service.version`. It does not list attributes, give filter values or cover edge cases. Those are for the spec writer. It names, types and defines nothing new.

## What later Topics decide, and must not appear

**Topic 3:** how energy observed outside the software obtains the identity settled here in practice; how energy joins to the count of work, including matching windows and differing granularity; rollout timing, sampling and gaps in coverage; allocation of shared readings, including idle and unattributed energy and the effect of neighboring workloads; signal types, instruments and requirement levels of signals; what is emitted by default; carbon intensity type and granularity.

**Topic 4:** embodied carbon, its allocation and missing data.

**Topic 5:** which components a software boundary contains; whether an SCI value includes every component; converting functional units between components; whether comparison needs a fixed, shared functional unit; roll-up; the name the conventions use for the functional unit; namespace; units.

Material a later Topic owns is deferred, not excluded. Leave it out silently.

## Settled before this Topic, and not open

**From Topic 1, the ranked use cases, in this order:**

1. An application, platform or SRE engineer asks whether a release, configuration, architectural or dependency change reduced energy or emissions for the same work, and if they increased, which part of the system is responsible.
2. An engineer or technical decision-maker asks which provider, service or migration option produces less carbon for equivalent work. The conventions serve this only partially.
3. An automated scheduler, autoscaler or placement system asks which option available now would cost less carbon.

Where they conflict, the first prevails.

**From Topic 1, the floor:** every value declares its software boundary, quantification method, functional unit, nature, and completeness, including whether operational, embodied, or both are covered. A fast, modeled or partial value is labeled as such. The conventions require a declared functional unit and do not prescribe which one.

**From the SCI specification:** the functional unit is held consistent across all components in the software boundary; a value and its count of functional units cover the same time period; quantification method is measurement or calculation, decided per component; a baseline uses an identical methodology, including the same functional units.

**The SCI's two quantification methods:** measurement quantifies the real-world emissions of a component over a time period and divides them by the number of functional units in the same period. Calculation models what one functional unit of work looks like and quantifies the emissions of executing it, for example in a controlled lab environment. Applying a formula to real-world data from a period, such as multiplying observed energy by a grid's carbon intensity, is still measurement in the SCI's sense.

**Also settled:** "nature" is the Topic 1 term for whether a value is measured, calculated, estimated or forecast. "Functional unit" is the working term until the conventions' own name is chosen. Embodied carbon is inside these conventions. Market-based measures and cost and financial data are excluded.

## Outside the Assembly

YAML authoring. Attribute keys, final requirement levels, entity definitions and stability, which OpenTelemetry settles in its own review. Codeowner and SIG-sponsor arrangements. Submission logistics. Reference implementations. Upstream OpenTelemetry governance.