# SCI for OpenTelemetry Assembly

## Topic 2 - What Every Value Declares

## Candidate [Letter]: [Short title naming the position this candidate takes]

[One paragraph stating the position this candidate takes across the three decisions, and the trade-off it makes. States, does not explain or argue.]

[The three entries appear in whichever order the position turns on.]

### "Is this the same software, and what changed?"
* **Declares:** [What establishes that two values are about the same software, naming the existing OpenTelemetry attributes it builds on, and whether comparison is anchored at the service alone or also at its namespace or deployment environment.]
  * **Required on:** [Every value; every value where a stated condition holds, with the condition and what the value states when it does not; or only where a named ranked use case needs it.]
  * **Varies:** [Fixed for the software; changes with each release or stated change; changes with the producer; or can differ between values.]
* **Declares:** [What marks the change between a baseline and a changed system: a release, any new build, or a stated change event, naming the existing OpenTelemetry concept it builds on.]
  * **Required on:** [As above.]
  * **Varies:** [As above.]
* **Declares:** [Whether the infrastructure the software ran on is visible on the value, and which existing OpenTelemetry attributes show it.]
  * **Required on:** [As above.]
  * **Varies:** [As above.]
* **Declares:** [Where a value's producer cannot obtain the software's identity, whether that value can still serve the first-ranked use case, and what it states about the identity it lacks.]
  * **Required on:** [As above.]
  * **Varies:** [As above.]

### "Per what?"
* **Declares:** [Where a value's count of work comes from: existing metrics that already count work, a dedicated count, or both, naming any existing OpenTelemetry metric it builds on, and why where a dedicated count is added.]
  * **Required on:** [As above.]
  * **Varies:** [As above.]
* **Declares:** [How the kind of work is declared: as part of the count's unit, as a separate attribute, or both.]
  * **Required on:** [As above.]
  * **Varies:** [As above.]

### "How was it produced?"
* **Declares:** [The value's nature.]
  * **Required on:** [As above.]
  * **Varies:** [As above.]
  * **Distinguishes:**
    * **Measured:** [Definition an implementer can apply to a single value, and whether it falls under SCI measurement or calculation.]
    * **Calculated:** [Definition, and which SCI method it falls under.]
    * **Estimated:** [Definition, and which SCI method it falls under.]
    * **Forecast:** [Definition, and which SCI method it falls under, or that it falls under neither.]
* **Declares:** [What a value states about its method: name and version only, or also the source of its input data, and if so whether always or only for some natures, naming any existing OpenTelemetry concept it builds on.]
  * **Required on:** [As above.]
  * **Varies:** [As above.]
* **Declares:** [Whether a confidence indicator is part of the declaration: yes or no.]
  * **Required on:** [As above, or omitted where the answer is no.]
  * **Varies:** [As above, or omitted where the answer is no.]

### Example
[One service compared before and after one release. For each of the three decisions, what that service's values state, naming only existing OpenTelemetry attributes and no new attributes, metrics or units.]
