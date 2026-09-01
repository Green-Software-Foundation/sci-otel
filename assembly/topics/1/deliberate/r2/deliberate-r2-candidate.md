# Candidate D - Attribute First, Compare Fairly, Prepare for Real Time

**This candidate keeps the engineer improving their own system as the first, unconditional priority, and folds in what the other two candidates got right: comparing across providers, and reacting while a workload runs. Provenance is never traded away for speed or breadth.**

### 1st "Did this release, configuration, architectural, or dependency change reduce energy or emissions per unit of useful work?"
* Asked by an **application or platform engineer**.
* Acts by shipping, continuing to optimize, or rolling back where feasible, since many organizations can only fix forward. Covers architectural and dependency changes, not only version and configuration.
* Needs telemetry attributable to a stable software entity, aligned in time with an explicit measure of useful work, and marked with the method and source that produced it. Idle or unattributed energy is reported openly rather than hidden.

### 2nd "Which workloads or components drive the largest hotspots, at whatever boundary the actor chooses?"
* Asked by whoever is **responsible for ranking work at that boundary**, a platform or SRE team where one exists, or the same engineers where it does not.
* Acts by ranking, to decide where to invest; the convention does not dictate the ranking method.
* Needs the same telemetry as the 1st use case, aggregated to the chosen boundary.

### 3rd "Did this change reduce energy or carbon for the same unit of work well enough to hold up against a number produced by a different organization or provider?"
* Asked by a **team comparing options** before selecting or migrating a provider.
* Acts by selecting or migrating, recognizing that switching costs and embodied emissions can outweigh short-term savings.
* Needs a value that declares its own boundary and method clearly enough that two numbers are never read as equivalent when they are not. Undeclared values are non-comparable, not approximately equal.

### 4th "Which of several currently available options runs the same work for less carbon right now?"
* Asked by an **automated system**, such as a scheduler or model-routing layer, deciding while a workload is still running where to place it.
* Acts by placing or shifting the workload, or leaving it as-is.
* Accepts that this is the direction to grow into, not a first-wave requirement, since live signals and cross-option methods are not yet reliable enough. A lightweight method and confidence marker still travels with the number.

### Conflict Resolution
* Attribution and provenance prevail throughout: the engineer's need to trace a value to a stable entity holds even where an automated consumer would prefer a faster, lighter number.

### Rationale
* **From the engineer-focused candidate**: the synthesis keeps entity-level attribution, the shipping/optimizing decision loop, and the hotspot-ranking use case. It incorporates the suggestion to broaden the first use case to architectural and dependency changes, and to soften "rolling back" to acknowledge that many organizations can only fix forward. It also drops the platform/SRE-specific framing in favor of "whoever is responsible for ranking."
* **From the comparison-focused candidate**: the synthesis keeps the requirement that energy and activity be reported over the same window, the denominator/unit-of-work fix requested independently by two participants, and the requirement that a value declare its own boundary and method. It adds an explicit rule that undeclared or mismatched values are treated as non-comparable rather than approximately equal.
* **From the automation-focused candidate**: the synthesis keeps the recognition of an automated consumer and the value of real-time placement, but demotes it to a fourth, forward-looking priority. It reattaches a lightweight method and confidence marker rather than dropping provenance, per the strong and broad pushback against trading away traceability, and reframes "revert" as "place, shift, or leave as-is."
* **Kept without contest:** naming the monitoring-as-a-service team as a consumer, and requiring idle or unattributed energy to be reported openly rather than hidden. Neither was contested by any participant.
