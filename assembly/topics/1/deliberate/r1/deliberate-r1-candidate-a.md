# Candidate A - Improve what you Run

**This candidate prioritizes the engineer improving their own systems first, and every consumer it names sits inside the organisation running the software. Nothing here gives up knowing where a number came from.**

### 1st "Did this release, configuration, or workload change reduce energy or emissions per unit of useful work?"
- Asked by an **application or platform engineer**.
- Acts by shipping the change, rolling it back, or continuing to optimize.
- Needs telemetry attributable to a stable software entity, aligned in time with the activity it covers, and marked with the method that produced it, so a real improvement can be told apart from noise or a shift in usage.


### 2nd "Which workloads or nodes drive the largest hotspots?"
- Asked by **platform and SRE teams**. 
- Acts by ranking them to decide where to invest and how to place work.
- Needs the same telemetry at coarser grain.


### 3rd "Is our fleet's or product's footprint falling?"
- Asked by **sustainability and reporting teams**.
- Acts by answering customer and regulatory questions.
- Accepts monthly or regional aggregation, modeled values, and delayed data. Not the loss of provenance: an aggregated figure must still state its source, boundary, and time resolution rather than presenting as equivalent to a finer measurement.

### Where these conflict
- The engineer's need for attribution prevails, since numbers that cannot be traced to what produced them cannot be trusted enough to act on.

### What falls outside
- These conventions describe what a value represents rather than how it must be calculated or what an organization must report.
- They cover measured, modeled, estimated, and defaulted values alike, since restricting to direct measurement would exclude most cloud and shared infrastructure. 
- Every use above turns on attribution: whether a value can be tied to a stable software entity, over a defined window, so someone can act on it.
