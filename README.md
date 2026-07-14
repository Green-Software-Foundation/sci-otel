# SCI for OpenTelemetry

Software Carbon Intensity (SCI) measurements have no shared semantic conventions in OpenTelemetry today. This project starts by drafting conventions covering energy consumption, carbon intensity, embodied carbon, and the functional unit, then builds the instrumentation that puts them into practice — so every observability stack can emit and consume carbon data consistently.

> **Status: Pre-Draft.** This project is in its initial development phase. The semantic conventions described here are not yet drafted or ratified. Nothing in this repository should be treated as stable.

## Overview

Software Carbon Intensity (SCI), defined in ISO/IEC 21031:2024, is a standardised method for measuring the carbon intensity of a software system. Its components, energy consumption, carbon intensity, embodied carbon and a functional unit, map directly onto concepts that observability practitioners already instrument. OpenTelemetry, however, has no agreed attribute names or metric definitions for any of them.

This project addresses that gap. It starts by drafting a baseline set of semantic conventions covering each component of the SCI formula, then builds the instrumentation that puts them into practice.

## What we are standardising

The SCI formula is:

```
SCI = ((E × I) + M) per R
```

where:

- **E**: energy consumed by the software, in kWh
- **I**: carbon emitted per kWh of energy consumed, in gCO2e/kWh
- **M**: embodied carbon, the emissions associated with the hardware the software runs on
- **R**: the functional unit, describing how the software scales, for example per user or per device

The initial deliverable is a draft baseline set of semantic conventions covering each component of the formula.

## How this project works

Rather than a small group drafting conventions on its own, the project begins with a GSF Assembly: a structured, time-boxed process for bringing a group of experts to consensus on a hard question.

- The Assembly brings the OpenTelemetry and Green Software communities together to work through the SCI formula.
- It produces an agreed blueprint covering scope, namespace, signal design and the composition model.
- That blueprint is handed to the OpenTelemetry Semantic Conventions SIG for formal specification work.

The Assembly produces the blueprint, not the conventions themselves. Formal semantic convention YAML is written only after consensus is reached.

## Repository structure

- `assembly/`: materials and output from the SCI for OpenTelemetry Assembly, including the blueprint (`REPORT.md`) once ratified
- `code-of-conduct.md`: expected standards of behaviour
- `LICENSE`: Apache License 2.0

## Getting involved

Applications to take part are open to anyone with relevant expertise, or who knows someone who has it. We are particularly looking for:

- OpenTelemetry semantic conventions experience
- Green software and carbon measurement expertise (SCI, Kepler, carbon intensity data sources)
- Instrumentation experience
- Observability backend vendors, to ensure carbon signals are consumable across the ecosystem

Ways to get involved:

1. **Register with GSF.** Required before you can subscribe to any project. See https://wiki.greensoftware.foundation/register
2. **Subscribe to the project.** Join the mailing list and meetings. See https://wiki.greensoftware.foundation/subscribe
3. **Apply to the Assembly.** The initial development work runs through an Assembly. Apply at https://greensoftware.foundation/assemblies/sci-for-open-telemetry/

## Relationship to OpenTelemetry

This project runs under Green Software Foundation governance. Its output is intended for review by the OpenTelemetry Semantic Conventions SIG. If a registry is hosted in the GSF organisation, the relationship between it and the OpenTelemetry copy, including codeowners and the process for porting changes across, will be documented explicitly.

## Related resources

- Project page: https://greensoftware.foundation/tools/sci-for-opentelemetry/
- SCI specification: https://sci.greensoftware.foundation/
- How GSF Assemblies work: https://greensoftware.foundation/assemblies/
- OpenTelemetry Semantic Conventions: https://github.com/open-telemetry/semantic-conventions

## Governance

The Green Software Foundation operates by consensus. This is a Software Standards Working Group project. Decisions are made openly and recorded.

## License

This project is licensed under the Apache License 2.0. See [`LICENSE`](LICENSE).

## Code of Conduct

Participation is governed by the Green Software Foundation Code of Conduct. See [`code-of-conduct.md`](code-of-conduct.md).
