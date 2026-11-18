# Candidate B: Every Build Marked, Confidence From Nature

*Rationale: The position the least satisfied participant could still accept, aiming to raise the floor rather than the average.*

Marks any new build, adds a dedicated count to exclude non-work, states inputs unless the method version fixes them, and reads confidence from nature alone.

## How It Works

A comparison rests only on facts a producer can show, never on its own judgment, at the cost of marking changes a team may think trivial. Take a checkout service compared before and after release 2.4. Each value names the service in `service.name` and the build in `service.version`, so a base-image rebuild between them also shows as a change. Work is completed orders from a dedicated count, since the request metric includes health checks and retries. Energy read from a hardware counter is measured, and the value states that the counter reports an on-chip model. The grid intensity source is named with its version. If nothing besides the release differs, a fall in energy per order is credited to the release. If the baseline was estimated, its lower confidence rank shows that the difference rests partly on a model.

## What Every Value Declares

| Decision | Answer |
|---|---|
| **Sameness: what identifies the software?** | `service.name`, compared within the same namespace and deployment environment. [When the producer can obtain the software's identity; fixed for the software] |
| **Sameness: what marks the change?** | Any new build, carried in `service.version`, and a stated change event for configuration or feature flag changes that ship without a build. [When the producer can obtain the software's identity; changes with each release or stated change] |
| **Sameness: is the infrastructure it ran on shown?** | Yes: the hardware type, architecture and region the software ran on. [Every value; can differ between values] |
| **Sameness: what if the software's identity is unavailable?** | Not as evidence of a release's effect; it states the infrastructure the observer saw and that the software's identity is absent. [When the software's identity is unavailable; changes with the producer] |
| **Functional unit: where does the count of work come from, and how is its kind declared?** | Existing metrics, plus a dedicated count where they cannot separate completed work from health checks, retries and failures. Kind is declared in the count's unit and a separate attribute stating what it includes and excludes. [Every value; fixed for the software] |
| **Provenance: what do measured, calculated, estimated and forecast mean?** | Measured: read from a meter or hardware energy counter for the boundary it covers; SCI measurement. Calculated: a fixed formula over measured inputs and factors published for that system and period; SCI measurement. Estimated: a model, assumption or value from elsewhere stands in for an unobserved input; SCI calculation. Forecast: predicts a future period; SCI calculation. A value takes the last nature, in this order, that any input has. [Every value; can differ between values] |
| **Provenance: what does a value state about how it was produced?** | Method name and version; also each input's source, version and whether it is sensed or modeled, unless the method's version changes whenever an input does. [Every value; changes with the producer] |
| **Provenance: is there a confidence indicator?** | Yes: its nature serves as the confidence level, ranked measured, calculated, estimated, forecast; producers assign no separate score. [Every value; can differ between values] |

## Trade-offs

**Gains:** Engineers comparing releases see rebuilds and dependency updates that ship without a version, and get counts free of health checks, retries and failures. Automated consumers get a confidence rank on every value that no producer has to calibrate.

**Gives up:** A rebuild with unchanged code splits a baseline, and producers may need new instrumentation for a dedicated count. Values carry no uncertainty bound even where one is known, and joining energy to the count of work in Topic 3 must handle a count that may not be an existing metric.

## Where This Came From

Many participants identified versions by build or image digest, and several warned that request counts include health checks, retries and failures that are not work. Participants divided on confidence: some warned that producers cannot calibrate a score, while others wanted a level with clear rules, and this candidate derives that level from the declared nature.
