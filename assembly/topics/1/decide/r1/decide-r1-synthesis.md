# SCI for OpenTelemetry Assembly

> **About this document**
>
> This is the synthesis of a Decide round for Topic 1: Scope and Use Cases.
> This document is not a consensus position of the Green Software Foundation or its members.

## Topic 1: Scope and Use Cases — Decide, Round 1

### Consensus Reached, Zero Objections

* 15 of 37 participants voted.
* **10 Endorsed**, **5 Consented**, **0 Objected**. 22 gave silent Consent.
* Topic 1 is complete, as the group has reached consensus.

The approved text is in [the Topic 1 consensus candidate](https://github.com/Green-Software-Foundation/sci-otel/blob/main/assembly/topics/1/topic-1-consensus-candidate.md).

### Who Endorsed or Consented

**Endorsed (10):**

* Adam Spychala
* Anders Lybecker
* Angel Patricio Olivares Espinosa
* Dan Gomez Blanco
* Dipankar Das
* Divya Karthik
* Mary Baldwin Hughes
* Mia de Búrca
* Rémy Vuong
* Sunyanan Choochotkaew

**Consented (5):**

* Andreas Brunnert
* Manuel Leduc
* Richard Kavanagh
* Sarah Hsu
* Virginia Diana Todea

## How We Got Here

28 people helped shape the candidate, and 13 of them took part in every round.

**Discover.** 24 of 37 invited participants responded. The same problem kept surfacing: people can usually get a carbon or energy number, but cannot reliably say what it belongs to, such as a request, a release, or a shared workload. Two points settled immediately: estimated values are in scope provided they say so (22 of 23 responses agreed), and the conventions describe quantities, not how to calculate them.

**Deliberate.** Three candidates opened the round: "Improve what you Run", "Compare what you Buy" and "Act while it Runs". The engineer-focused candidate scored highest, with all 19 ratings at 6 or above. One comment changed the round by suggesting it should be the base, not the whole scope. The group stopped treating the three as rivals and started treating them as layers, and the final candidate keeps all three in priority order. Average ratings stayed high as the text improved: 8.1 in Round 2 and 8.2 in Round 3.

**Decide.** The candidate was put to the whole group with one question: do you accept it?

## What Was Decided

The conventions serve three use cases, in a fixed order:

1. An engineer or team improving their own system. This is the unconditional top priority. A value only counts if it carries its own declared boundary, method, and unit of work.
2. Comparing across providers or services. A real need, but the conventions can only partly support it, and the text says so plainly rather than promising more than it can deliver.
3. Automated, real-time workload placement. Placed last on purpose, something to build toward rather than something the conventions require today.

When these three conflict, the first always wins.

## How the Core Disagreement Was Resolved

One question came up in every Deliberate round: whether cross-provider comparison belongs in these conventions at all. It was resolved through three changes inside the candidate itself: the standardized workload limit was stated outright, procurement was excluded from this use case's consumers, and a second conflict rule was added, subordinating cross-provider ambition to the first use case's requirements.

## Carried Forward

A few questions this Topic could not settle are now handed to the Topics that own them: whether estimated values need a confidence indicator, whether the conventions reach client-side, embedded, or build-time software, which data should flow without configuration, whether an estimated component value must reconcile with a measured parent, and where vendors, consultancies, researchers, and benchmarkers sit in the ranking.

Consent comments also raised points for later Topics:

* **Terminology:** "unit of work" already means a span in OpenTelemetry traces, and "unit" means the unit of measurement in OpenTelemetry metrics. Here it means SCI's functional unit. The naming should be resolved when the resource-identity attributes are settled.
* **Precision:** the next stage needs exact definitions of boundary, method, unit of work, and the difference between measured, calculated, estimated, and forecast values, so signals are interpreted consistently across implementations.
* **Use case 3 latency:** whether automated placement needs a lower-latency signal at all, given that scheduling ahead of time must rely on an estimate in any case.
