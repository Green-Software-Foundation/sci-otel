# Topic 2: What Every Value Declares

## Purpose

Establish what every value these conventions carry must state about itself. Topic 1 made this declaration the precondition for every ranked use case. The SCI specification makes it the first three steps of its procedure (Bound, Scale, Define) and part of its Report step. Topics 3 and 4 attach energy, carbon intensity and embodied carbon to the declaration settled here, so this Topic produces the shared contract every later signal must meet.

## What the Topic must decide

One decision: the declaration every value carries. It must let the first-ranked use case's consumer show that a baseline and a changed system were quantified using an identical methodology, against the same functional unit, over the same window.

For each element, a candidate states what it declares, whether it is required on every value or only where a named ranked use case needs it, and which existing OpenTelemetry concept it builds on, or that nothing existing fits. Each element is defined precisely enough that two independent implementations, observing the same software, would produce the same declaration.

- **Software boundary.** What Topic 1 calls a consistently identified software entity. How a value identifies the software boundary it belongs to and, where relevant, the component within it. Either existing OpenTelemetry resource identity is sufficient, or a value declares a software boundary composed of existing identities. Which parts of that identity stay the same across a release, so that a baseline and a changed system count as the same software, and which part marks the change. Whether component identity is required on every value, or only where a value is used to locate which part of a system is responsible. How the declaration accounts for components inside the software boundary that these conventions may not instrument themselves.
- **Functional unit.** What Topic 1 calls the unit of useful work, which is the SCI's functional unit (R). Every value declares the functional unit it is measured against, and the conventions do not prescribe which one it is. The choice here is how the count of that unit over the same window becomes available: emitted alongside the value for the same entity and window, or referenced from telemetry that already records the work. A position also names the term the conventions use for it, distinct from "unit of work", which in OpenTelemetry tracing describes a span, and from "unit", which in OpenTelemetry metrics means the unit of measurement.
- **Quantification method.** Either a value identifies its method by name and version only, or it also states the source of the input data its result depends on. Neither carries the methodology itself.
- **Nature.** A definition of each of measured, calculated, estimated and forecast that tells an implementer which one applies to a given value, and how the four map onto the SCI's two quantification methods, measurement and calculation. In the SCI, calculation means a modeled result for one functional unit, typically from a lab or benchmark run, so "calculated" cannot simply carry its everyday meaning. Whether a confidence indicator is required, optional, or absent from the declaration.
- **Where the declaration is carried.** Either declarations are stated once per component and inherited by its values, or repeated on each value.

There is no required order. Lead with whichever element the position turns on.

## Required shape

Four headed entries, using these headings:

- **What is this value about?** (software boundary)
- **Per what, and over which window?** (functional unit)
- **How was it produced, and was it produced the same way last time?** (quantification method)
- **Was it measured or modeled?** (nature)

Under each heading, three labeled fields:

- **Declares**
- **Required on:** every value, or the named ranked use case that needs it
- **Builds on:** the existing OpenTelemetry concept, or "nothing existing fits"

The nature entry adds a fourth field, **Distinguishes**, defining each of measured, calculated, estimated and forecast.

Close with one short paragraph stating where the declaration is carried, followed by one concrete example: a single service compared before and after one release, described in plain terms (the service, the release, the work it did) and naming no new attributes, metrics or units.

## Length

No word target. Length follows what precision requires. Every sentence either declares something or defines a term. A candidate that runs long because it explains, argues, compares itself with alternatives or reaches into a later Topic is wrong, and the fix is to cut that material. A candidate that runs long because it defines precisely is right, and is never shortened by loosening a definition, dropping an element or abstracting a declaration into a description.

## What later Topics decide, and must not appear

New attribute, metric or entity names. Namespace. Units. Signal types and instrument selection. The levels at which energy is reported. Carbon intensity type and granularity. Idle and unattributed energy. Allocation methods for embodied carbon, and what an allocation declaration contains. How an SCI value is composed, including roll-up across software boundaries and whether component values must reconcile with a parent. Which software is instrumented directly, and what is emitted by default. Definitions of SCI itself or of OpenTelemetry mechanics.

A candidate may name existing OpenTelemetry attributes, resources and entities it builds on. It does not name, type or define anything new, with one exception: it chooses the term the blueprint and the conventions use for the functional unit. The attribute and metric names built from that term are decided later. "Builds on existing service identity" is a position. Naming a new attribute is not.

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

YAML authoring. Codeowner and SIG-sponsor arrangements. Submission logistics, phasing, hosting and publication sequencing. Selection or coordination of reference implementations. Upstream OpenTelemetry governance. Responses reaching for these are noted and set aside, not deliberated.
