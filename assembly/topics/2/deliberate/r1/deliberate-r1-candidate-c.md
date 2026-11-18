# Candidate C: Changes Anchored in Time

*Rationale: A coherent alternative that challenges the emerging agreement, so the group has to articulate what it rejects and why.*

Marks every change, releases included, by a stated change event, lets values without software identity serve comparison across one, and carries no confidence indicator.

## How It Works

A change is anchored in time by a stated change event, so a value can serve a before-and-after comparison without naming the software it describes. In exchange, the comparison holds only while infrastructure stays unchanged across the change, and no value reports its producer's confidence. Take a checkout service, where a stated change event records that release 2.4 of the service in `service.name` took effect at 14:00. Orders are counted by an existing request metric. Energy comes from an observer that sees only the node. Its values state the node's hardware type and region, their period, missing identity, estimated nature, power model and carbon intensity source. If node, model and source match on both sides of 14:00 and no other change event intervenes, a fall in energy per order is read as the release's effect. A node type change at 14:00 would block that reading.

## What Every Value Declares

| Decision | Answer |
|---|---|
| **Sameness: what identifies the software?** | `service.name`, compared within the same namespace and deployment environment. [When the producer can obtain the software's identity; fixed for the software] |
| **Sameness: what marks the change?** | A stated change event for every change, releases included, stating when it took effect; the release itself carried in `service.version`. [When the producer can obtain the software's identity; changes with each release or stated change] |
| **Sameness: is the infrastructure it ran on shown?** | Yes: the hardware type, architecture and region the software ran on. [Every value; can differ between values] |
| **Sameness: what if the software's identity is unavailable?** | Yes, where a stated change event separates baseline and changed periods on unchanged infrastructure; it states the observed infrastructure, its period, and identity as absent. [When the software's identity is unavailable; can differ between values] |
| **Functional unit: where does the count of work come from, and how is its kind declared?** | Existing metrics that count work; a dedicated count only where none records the chosen work. Kind is declared in the count's unit and a separate attribute stating what it includes. [Every value; fixed for the software] |
| **Provenance: what do measured, calculated, estimated and forecast mean?** | Measured: read from a meter or hardware energy counter for the boundary it covers; SCI measurement. Calculated: a fixed formula over measured inputs and factors published for that system and period; SCI measurement. Estimated: a model, assumption or value from elsewhere stands in for an unobserved input; SCI calculation. Forecast: a prediction for a future period; neither. A value takes the last nature, in this order, that any input has. [Every value; can differ between values] |
| **Provenance: what does a value state about how it was produced?** | Method name and version, and always the source and version of each input, such as its carbon intensity source or power model. [Every value; changes with the producer] |
| **Provenance: is there a confidence indicator?** | No: a value states its nature and inputs, which consumers judge; it carries no confidence level, score or bound. |

## Trade-offs

**Gains:** Producers whose observers see only the node can serve release comparisons without first obtaining the software's identity. Engineers can also place a dependency or configuration change in time even when nothing on their own values changed.

**Gives up:** Teams must record a change event for every release, and a comparison fails whenever infrastructure changed across the event or other events fall between the periods. Automated consumers get no confidence signal and must weigh nature and inputs themselves, and joining energy to the count of work in Topic 3 must align periods with event times.

## Where This Came From

A smaller group compared systems by the moment a deployment or configuration change took effect, often with no version in the telemetry, and many relied on node agents that carry no software identity. Participants divided on confidence, and some held that no producer can calibrate one today, so this candidate leaves consumers to judge from the declared nature and inputs.
