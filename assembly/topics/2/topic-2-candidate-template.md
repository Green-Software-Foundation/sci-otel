# SCI for OpenTelemetry Assembly

## Topic 2 - What Every Value Declares

## Candidate [Letter]: [Short title naming the position this candidate takes]

[One paragraph stating the position this candidate takes across the three decisions, and the trade-off it makes. States, does not explain or argue.]

[The three entries appear in whichever order the position turns on.]

### "Is this the same software, and what changed?"
* **Declares:** [What establishes that two values are about the same software, naming the existing OpenTelemetry attributes it builds on, and whether comparison is anchored at the service alone or also at its namespace or deployment environment.]
* **Declares:** [What marks the change between a baseline and a changed system: a release or any new build, naming the existing OpenTelemetry attribute it builds on.]
* **Declares:** [Where a value's producer cannot obtain the software's identity, whether that value can still serve the first-ranked use case, and what it states about the identity it lacks.]
* **Required on:** [Every value, or only where a named ranked use case needs it. One answer per declaration.]
* **Varies:** [Fixed for the software, changes with each release, or can differ between values. One answer per declaration.]

### "Per what?"
* **Declares:** [Where a value's count of work comes from: existing metrics that already count work, a dedicated count, or both, naming any existing OpenTelemetry metric it builds on.]
* **Declares:** [How the kind of work is declared: as part of the count's unit, as a separate attribute, or both.]
* **Required on:** [Every value, or only where a named ranked use case needs it. One answer per declaration.]
* **Varies:** [Fixed for the software, changes with each release, or can differ between values. One answer per declaration.]

### "How was it produced?"
* **Declares:** [What a value states about its method: name and version only, or also the source of its input data, and if so whether always or only for some natures, naming any existing OpenTelemetry concept it builds on.]
* **Declares:** [Whether a confidence indicator is part of the declaration: yes or no.]
* **Distinguishes:**
  * **Measured:** [Definition an implementer can apply to a single value, and whether it falls under SCI measurement or calculation.]
  * **Calculated:** [Definition, and which SCI method it falls under.]
  * **Estimated:** [Definition, and which SCI method it falls under.]
  * **Forecast:** [Definition, and which SCI method it falls under, or that it falls under neither.]
* **Required on:** [Every value, or only where a named ranked use case needs it. One answer per declaration.]
* **Varies:** [Fixed for the software, changes with each release, or can differ between values. One answer per declaration.]

### Example
[One service compared before and after one release. For each of the three decisions, what that service's values state, naming only existing OpenTelemetry attributes and no new attributes, metrics or units.]
