# Candidate F - Verify, Compare Honestly, Adapt Fast

This candidate keeps the engineer or team able to act on their own system as the unconditional top priority, treating verification of whether a change reduced energy or emissions and identification of the responsible component as one continuous use case whose second half is never a precondition for the first. Cross-provider and cross-service comparison ranks second: a real use case these conventions can only partially serve, and whose limits this candidate states rather than hides. Automated real-time adaptation ranks third, trading resolution and directness of measurement for speed. No ranked use case is served by a value that fails to declare its own boundary, method, and unit of work — including whether operational, embodied, or both are covered — and that declaration is the floor beneath all three.

### 1st "Did this release, configuration, architectural, or dependency change reduce energy or emissions for the same work, and if energy or emissions increased, which part of my system is responsible?"
* Asked by an **application, platform, or SRE engineer**, or the team, business unit, or organization to which that engineer's scope rolls up.
* Acts by shipping, reverting, or keeping the change, and by directing further optimization at whichever component the answer implicates.
* Needs the top-line before-and-after comparison to stand on its own without waiting on finer attribution, and needs consumption attributable to a stable software entity across releases only when the comparison shows a regression that must be located.

### 2nd "Which of these providers, services, or migration options actually produces less carbon for equivalent work?"
* Asked by an **application or platform engineer, or a technical decision-maker**, choosing between infrastructure options they do not always control directly.
* Acts by selecting, migrating to, or contracting for whichever option the comparison favors.
* Needs every value entering the comparison to declare its own boundary, method, and unit of work as a precondition for any comparison attempt — a precondition, not a guarantee, since a declared unit of work does not by itself make two providers' work equivalent, and closing that gap fully would require a standardized workload and test procedure that these conventions cannot supply. Where the comparing party does not directly operate the infrastructure being measured, what they are reading is a provider's own declared or advertised figure, not a directly measured value — a distinction this candidate treats as a property the comparison consumer must weigh, not a gap to design away.

### 3rd "Can an automated scheduler, orchestrator, or workload-placement system detect a shift in carbon intensity or demand in time to act on it without a human in the loop?"
* Asked by an **automated scheduling, orchestration, or workload-placement system**, consuming a signal published or forecast by a provider or grid operator.
* Acts by shifting, throttling, or timing workload placement in direct response to the signal, with no human confirmation step.
* Needs a lower-latency signal than the first two use cases require, accepting lower resolution, delayed confirmation, or a modelled rather than directly measured value — but needs that signal to carry an explicit declaration of its own nature, whether measured, calculated, estimated, or forecast, so the automated consumer can weigh a forecast differently from a measurement.

### Conflict Resolution
* Where the second-ranked use case's ambition for cross-provider equivalence would otherwise demand a universally defined unit of work, the first-ranked use case's requirement prevails: a value need only declare its boundary, method, and unit of work consistently for its own release-over-release use, and comparison across providers is only as good as how far that declaration travels.
* Where the third-ranked use case's need for speed conflicts with the first and second use cases' need for a verified, attributable value, the third accepts materially lower accuracy and directness rather than waiting for a fully attributed value, provided its provenance and confidence are marked.
* Any value covered by these conventions must state its own boundary, method, unit of work, and nature — including whether it is complete against what it claims to represent, covering operational and embodied emissions as declared — before any ranked use case can rely on it.
