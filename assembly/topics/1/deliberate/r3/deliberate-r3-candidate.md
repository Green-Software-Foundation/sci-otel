# Candidate E — Improve, Then Compare, Then Adapt

This candidate keeps the engineer or team able to act on their own system as the unconditional top priority, treating change-verification and hotspot identification as one continuous use case rather than two. Cross-provider and cross-service comparison ranks second, and automated real-time adaptation ranks third as a capability worth building toward rather than a requirement met today. No ranked use case can be served by a value that fails to declare its own boundary, method, and unit of work, and that declaration is the floor beneath all three.

### 1st "Did this release, configuration, architectural, or dependency change reduce energy or emissions for the same work, and if not, which part of my system is responsible?"

- Asked by an **application, platform, or SRE engineer** who can change the code, configuration, architecture, or dependencies of the system they run.
- Acts by shipping, continuing to optimize, rolling back, or fixing forward, and by directing attention to whichever component the answer implicates.
- Needs energy and emissions attributable to a consistently identified software entity, aligned to the same measurement window as an explicit unit of useful work that the value itself declares, resolved finely enough to distinguish contributing components, and explicit about whether embodied emissions fall inside the measurement boundary.

### 2nd "Which of these providers, services, or migration options actually produces less carbon for equivalent work?"

- Asked by a **platform, procurement, or migration decision-maker** choosing between providers, services, or architectures they do not directly control.
- Acts by selecting, migrating to, or continuing to negotiate with whichever option's declared numbers hold up under scrutiny.
- Needs each compared value to declare its boundary and method clearly enough that a consumer can judge whether two numbers measure the same thing — the declaration is a precondition for comparison, not a guarantee that any two providers' figures are actually comparable.

### 3rd "Which of the options available to my system right now would cost less carbon if I used it instead?"

- Asked by an **automated scheduler, autoscaler, or workload-placement system** acting without a human in the loop.
- Acts by shifting, delaying, or placing the workload toward the lower-carbon option before the decision window closes.
- Needs a signal fast enough to arrive before the decision is made, even where that means accepting lower resolution, delayed confirmation, or a modeled rather than directly measured value.

### Conflict Resolution

- Where the top-ranked use case's need for a fully attributed, declared-boundary value conflicts with the third-ranked use case's need for speed, the first use case's completeness requirement prevails: a fast, modeled, or partial value must be labeled as such rather than presented as equivalent to a fully attributed one.
- Where the second- and third-ranked use cases compete for which gets a stable, audited value first, the second prevails, since its consumer acts less often but with more consequence per decision.
