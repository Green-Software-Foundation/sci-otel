# SCI for OpenTelemetry Assembly

## Topic 1 - Scope & Use Cases

> With zero objections in Decide, consensus has been reached on this candidate.
> 
> This candidate received:  
> - 10 Endorse votes  
> - 5 Consent votes
> - 0 Objections  
> - 22 silent consents
>

## Candidate F — Improve, Then Compare, Then Adapt

This candidate keeps the engineer or team able to act on their own system as the unconditional top priority, treating change-verification and hotspot identification as one continuous use case rather than two. Cross-provider and cross-service comparison ranks second: a real use case these conventions can only partially serve, and whose limits this candidate states rather than hides. Automated real-time adaptation ranks third, trading resolution and directness of measurement for speed. No ranked use case is served by a value that fails to declare its own boundary, method, and unit of work — including whether operational, embodied, or both are covered — and that declaration is the floor beneath all three.

### 1st "Did this release, configuration, architectural, or dependency change reduce energy or emissions for the same work, and if energy or emissions increased, which part of my system is responsible?"
* Asked by an **application, platform, or SRE engineer** who can change the code, configuration, architecture, or dependencies of the system they run.
* Acts by shipping, continuing to optimize, rolling back, or fixing forward, and by directing attention to whichever component the answer implicates.
* Needs energy and emissions attributable to a consistently identified software entity, aligned to the same measurement window as an explicit unit of useful work that the value itself declares, resolved finely enough to distinguish contributing components, and explicit about whether embodied emissions fall inside the measurement boundary.

### 2nd "Which of these providers, services, or migration options actually produces less carbon for equivalent work?"
* Asked by an **application or platform engineer, or a technical decision-maker**, choosing between infrastructure options they do not always control directly.
* Acts by selecting, migrating to, or contracting for whichever option the comparison favors.
* Needs every value entering the comparison to declare its own boundary, method, and unit of work as a precondition for any comparison attempt — a precondition, not a guarantee, since a declared unit of work does not by itself make two providers' work equivalent, and closing that gap fully would require a standardized workload and test procedure that these conventions cannot supply. Where the comparing party does not directly operate the infrastructure being measured, what they are reading is a provider's own declared or advertised figure, not a directly measured value — a distinction this candidate treats as a property the comparison consumer must weigh, not a gap to design away.

### 3rd "Which of the options available to my system right now would cost less carbon if I used it instead?"
* Asked by an **automated scheduler, autoscaler, or workload-placement system** acting without a human in the loop.
* Acts by shifting, delaying, or placing the workload toward the lower-carbon option before the decision window closes.
* Needs a lower-latency signal than the first two use cases require, accepting lower resolution, delayed confirmation, or a modelled rather than directly measured value — but needs that signal to carry an explicit declaration of its own nature, whether measured, calculated, estimated, or forecast, so the automated consumer can weigh a forecast differently from a measurement.

### Conflict Resolution
* Where the top-ranked use case's need for a fully attributed, declared-boundary value conflicts with the third-ranked use case's need for speed, the first use case's completeness requirement prevails: a fast, modeled, or partial value must be labeled as such rather than presented as equivalent to a fully attributed one.
* Where the second-ranked use case's ambition for cross-provider equivalence would otherwise demand a universally defined unit of work, the first-ranked use case's requirement prevails: a value need only declare its boundary, method, and unit of work consistently for its own release-over-release use, and comparison across providers is only as good as how far that declaration travels.
* Any value covered by these conventions must state its own boundary, method, unit of work, and nature — including whether it is complete against what it claims to represent, covering operational and embodied emissions as declared — before any ranked use case can rely on it.
