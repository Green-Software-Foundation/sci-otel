# Candidate C - Act while it Runs

**This candidate prioritizes an automated system first, a scheduler choosing where to run work while the workload is still running, ahead of any person reading a dashboard. It is the only one that trades away knowing where a number came from.**

### 1st "Which of several currently available options runs the same work for less carbon right now?"
- Asked by the **automated system** that decides, while a workload is still running, where to place it or which configuration to use: a scheduler, a self-adaptation manager, or a model-routing layer.
- Acts by shifting the workload, switching an implementation, or throttling, immediately.
- Needs energy or carbon signals refreshed at operational speed, tied to the specific location and time the candidates would run in, and identified consistently enough across options that a ranking is not an artifact of mismatched methods.
- Accepts the number driving the decision need not carry the audit-grade provenance a human reviewer would demand, only enough consistency between candidate options to rank them correctly, delivered fast enough to act on before the window for the decision closes.


### 2nd "Did this version use less than the one before it?"
- Asked by **engineers** comparing a change against its predecessor.
- Acts by keeping the change, or reverting it.
- Accepts a batch of data rather than a live feed, provided the same entity and window are aligned across both versions.

### 3rd "What was our footprint over the period?"
- Asked by **reporting to customers, auditors, or procurement.**
- Acts by answering a question rather than changing a system.
- Accepts losing timeliness and granularity entirely, working from monthly, regional, aggregated figures instead.

### Where these conflict
- Speed prevails over provenance, since a decision that arrives after the workload has run is not a decision.

### What falls outside
- These conventions describe values in a form an automated consumer can compare and rank without a human interpreting method or caveats first. 
- They do not prescribe the scheduling policy, the adaptation logic, or which option a system should choose once it can compare them.
