# SCI for OpenTelemetry Assembly

> **About this document**
>
> This is the anonymised synthesis of one Discover round of the SCI for OpenTelemetry
> Assembly. Discover explores the problem space. **Nothing in this document is decided,
> agreed, or endorsed by the Assembly**, and it is not a consensus position of the Green
> Software Foundation or its members.
>
> This synthesis selects the strongest signals rather than reporting everything;
> the complete record is held by the facilitator and available if required.
> Individual responses are never published, and no synthesis identifies who said what.
> Counts describe how many responses supported a point.

## Topic 2: What Every Value Declares - Discover, Round 1

This round received 15 responses from the 37 invited participants.

## Where the Group Stands

The strongest theme is that a version string is not enough to say two values are about the same software, or that two numbers were produced the same way. Across SRE, MLOps, HPC, and Kubernetes contexts alike, responses independently described a version number, or even a source-control commit hash, failing to catch the cases that actually mattered: a rebuilt image changing its digest with no code change, configuration drifting independently of the build, or a tool's underlying input data changing without its version changing at all. The same underlying concern showed up as a request for an artifact-level identifier on the software side, and as a request for declared input data — a carbon-intensity source, a power model — on the method side.

There is also broad agreement that a count of work should exclude what isn't really work, such as health checks, retries, or failed requests, and that a value's nature should keep measured, calculated, estimated, and forecast distinct, even though the SCI formula itself only names two quantification methods.

The one place this round did not converge is confidence: whether a value should carry an indicator of how much to trust it, and if so, who produces that indicator.

The consumers named across the responses cluster into four groups:
- **Engineers and SREs comparing their own releases**, the largest group, who want to know whether a specific change reduced energy or emissions for the same work.
- **Engineers or decision-makers comparing across providers or suppliers**, who need a number that means the same thing regardless of who produced it.
- **Automated schedulers or placement systems**, acting on a value to choose a lower-carbon option in real time.
- **Operators who run the system day to day**, who some responses placed in charge of judging a value's trustworthiness rather than its producer.

The tension this creates is real:
- Engineers comparing their own releases need granularity and timeliness: which CPU, which configuration, which scrape interval.
- Engineers and decision-makers comparing across providers need a number that is comparable across organisations, which is why they pushed hardest for declared carbon-intensity sources and power models rather than just a tool's name.

## Early Agreement

**A value should state the source of its inputs, not just its tool's name and version**
- Eleven of fifteen responses said a tool's name and version are not enough to trust that two values were produced the same way, because the same tool and version can be configured with a different carbon-intensity source, power model, or dataset and produce a different number.
- This was the most consistent reasoning in the round: a described failure where a number moved for reasons that had nothing to do with the software.
- If this holds, every value needs to carry its input source, not only the identity of the tool or model that produced it.

**Software identity needs an artifact-level marker below the version string**
- Six responses independently concluded that a version number or commit hash isn't reliable on its own, since the same source can produce different binaries and a rebuilt image can change its digest with no code change.
- No response argued the opposite; the rest either didn't address the question or used a weaker marker without defending it as sufficient.
- If this holds, a release is identified by a build-level digest or checksum, with configuration and infrastructure tracked as separate, declared context.

**A count of work should exclude what isn't really work**
- Six responses said raw counts bring in health checks, retries, failed requests, or warm-up traffic, and that a count needs to state what it included and excluded.
- No response argued these should be counted as real work.
- If this holds, a release that fails fast or serves less cannot look efficient purely because its raw count fell.

**Measured, calculated, estimated, and forecast should stay distinct, even though SCI only names two methods**
- Nine responses gave matching definitions: measured as a direct instrument reading, calculated as a deterministic formula over measured inputs, estimated as substituting a modelled or assumed input for something not directly observed.
- Several gave the same specific reason for keeping all four visible: collapsing calculated and estimated together hides a real difference in how much a number should be trusted.
- If this holds, a value's nature is one of four labels, not a binary measured-or-not flag, even where SCI's own formula treats three of the four the same way.

## Where Views Split

**Should a confidence indicator be assigned by whoever produced the value, or derived only from facts the value already declares?**

This split is close to even, not a majority-minority question.

- Six responses want a confidence indicator assigned directly by a producer, or in one case the system's operator — a simple scale, a percentage, or a certification process with defined thresholds.
- Six responses want either no separate indicator at all, or one computed only from what the value already states about itself, such as its nature and the source of its inputs, arguing a self-assessed score can't be calibrated and risks creating false certainty.

**Is a tool's name and version enough to trust two values were produced the same way?**

Most responses addressing this said no: the source of the tool's inputs has to be declared too, since the same tool and version can be configured differently and still produce a different result.

One response held that name and version are sufficient, on the basis that a tool should be treated as immutable, with any change in its behavior being the responsibility of whoever updates the tool to bump its version when that happens.

## Still Open

**Can a value that can't be traced back to a specific release still count?**
No response was asked, or answered, whether a value from an observer with no mapping back to the software's identity — a node agent with no workload metadata, for instance — can still serve the use case of comparing a baseline and a changed system, or what it would need to state about the identity it lacks.

**Does the kind of work belong inside the count's unit, or as a separate attribute?**
No response addressed this directly, and it turns out the two choices can conflict: reusing an existing metric to count work means that metric's own unit is already fixed, which may leave nowhere to attach a declaration of what's included or excluded without a separate field.

**Should functional units stay at request or transaction granularity, or move toward a weighted or outcome-level count?**
A couple of responses raised, without resolving, that a request-level count can distort comparisons when one request's real cost varies by orders of magnitude from another, or that counting requests at all can reward architectures that reduce request volume without reducing real work. Domains where unit cost varies most widely didn't get a direct question on this.
