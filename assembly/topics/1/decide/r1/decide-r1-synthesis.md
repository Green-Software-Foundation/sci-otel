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
