# Candidate A: Declare Everything That Moves the Number

*Rationale: The position closest to the centre of gravity of the group's views, aiming to raise average satisfaction.*

Marks change by release or stated change event, always states input data sources, and carries an uncertainty bound only when its producer substantiates it.

## How It Works

A difference is credited to the software only when everything else that could move the number is declared beside it. Take a checkout service compared before and after release 2.4. Each value names the service in `service.name`, the release in `service.version`, and the instance type and region it ran on. Its count of work is completed orders, taken from an existing request metric. Energy derived from a power model is estimated, and the value names that model and its carbon intensity source, each with its version. If all of these match on both sides, a fall in energy per order can be read as the release's effect. Sometimes more than the release changed: the region moved, a stated change event switched a feature flag inside the window, or the carbon intensity source was updated. The values then show this, and the comparison cannot credit the difference to the release alone.

## What Every Value Declares

| Decision | Answer |
|---|---|
| **Sameness: what identifies the software?** | `service.name`, compared within the same namespace and deployment environment. [When the producer can obtain the software's identity; fixed for the software] |
| **Sameness: what marks the change?** | A release, carried in `service.version`, or a stated change event for configuration or feature flag changes that ship without a release. [When the producer can obtain the software's identity; changes with each release or stated change] |
| **Sameness: is the infrastructure it ran on shown?** | Yes: the hardware type, architecture and region the software ran on. [Every value; can differ between values] |
| **Sameness: what if the software's identity is unavailable?** | Not as evidence of a release's effect; it states the infrastructure the observer saw and that the software's identity is absent. [When the software's identity is unavailable; changes with the producer] |
| **Functional unit: where does the count of work come from, and how is its kind declared?** | Existing metrics that count work; a dedicated count only where none records the chosen work. Kind is declared in the count's unit and a separate attribute stating what it includes. [Every value; fixed for the software] |
| **Provenance: what do measured, calculated, estimated and forecast mean?** | Measured: read from a meter or hardware energy counter for the boundary it covers; SCI measurement. Calculated: a fixed formula over measured inputs and factors published for that system and period; SCI measurement. Estimated: a model, assumption or value from elsewhere stands in for an unobserved input; SCI calculation. Forecast: a prediction for a future period; neither. A value takes the last nature, in this order, that any input has. [Every value; can differ between values] |
| **Provenance: what does a value state about how it was produced?** | Method name and version, and always the source and version of each input, such as its carbon intensity source or power model. [Every value; changes with the producer] |
| **Provenance: is there a confidence indicator?** | Yes: an uncertainty bound and how it was obtained, carried only when the producer substantiates it; absent means unknown. [When the producer substantiates it; can differ between values] |

## Trade-offs

**Gains:** Engineers comparing releases can see configuration and feature flag changes that shipped without a version, and can tell a coefficient or data source update apart from a regression. Producers are never asked to rate confidence they cannot back up.

**Gives up:** Producers must name every input source and version on every value, which adds metric streams whenever an input changes. Automated consumers get no confidence level to filter on for most values. A rebuild without a release goes unmarked. Joining energy to the count of work in Topic 3 must also account for stated change events that fall inside a window.

## Where This Came From

Many participants described changes that shipped without a version, through configuration, feature flags or the hardware underneath, and most held that a tool's name and version alone could not show two numbers were produced the same way. Participants divided on confidence: some wanted a stated level, and others warned that no producer can calibrate one today. This candidate carries an uncertainty bound only where the producer can substantiate it.
