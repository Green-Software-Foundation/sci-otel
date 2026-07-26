# Assembly Glossary

Terms are grouped by originating domain.

## **From the SCI world**

- **SCI:** Software Carbon Intensity, a rate of carbon emissions per unit of useful work, defined by the formula **SCI = (E x I + M) / R**.
- **E, energy:** the energy consumed by the software, in kilowatt-hours.
- **I, carbon intensity:** the carbon emitted per unit of energy for a given location and time, in grams of CO2-equivalent per kilowatt-hour.
- **M, embodied carbon:** the emissions from manufacturing and disposing of the hardware the software runs on, apportioned to the software.
- **R, functional unit:** the unit of useful work the score is expressed per, for example per user, per API call, or per transaction. R is what turns a total into a rate.
- **gCO2e:** grams of carbon-dioxide equivalent, the common unit for expressing a quantity of emissions.
- **Operational versus embodied:** operational emissions come from running the software (E and I); embodied emissions come from the hardware existing at all (M).

## **From the OpenTelemetry world**

- **OpenTelemetry (OTel):** the open standard for telemetry, the traces, metrics, logs and related signals that systems emit.
- **Semantic conventions (semconv):** the shared definitions that make a piece of telemetry mean the same thing everywhere.
- **Signal:** a kind of telemetry. The taxonomy is spans, metrics, events, resources and profiles.
- **Attribute:** a key-value pair attached to a signal, for example `cloud.region`.
- **Metric and instrument:** a measured value over time; the instrument is how it is recorded (counter, gauge, histogram).
- **Span:** a timed operation within a trace. **Event:** a point-in-time occurrence. **Resource / entity:** the thing producing the telemetry, and its identity.
- **Namespace:** the naming home for a group of conventions, for example `hw.*`.
- **Requirement level:** how strongly an attribute is expected, one of Required, Recommended, or Opt-In.
- **Stability level:** how settled a convention is; new conventions start at `development`.
- **Cardinality:** how many distinct values an attribute can take; high-cardinality attributes are constrained to Opt-In.
- **UCUM:** the unit code system OpenTelemetry uses for metric units. Relevant because gCO2e is not a UCUM unit, which is a decision the Assembly must make.
- **Registry, codeowners, SIG:** the catalogue an attribute is registered in; the people responsible for a convention; and the Special Interest Group that governs semantic conventions.
- **Instrumentation:** the code that actually emits the telemetry.
- **Kepler:** an open-source tool that measures the energy consumption of workloads running on Kubernetes and exports it as metrics. Named here as an example of existing cloud-native energy tooling the conventions might build on.
- **Federated semantic conventions:** an approach where conventions for a specific domain are maintained by that domain's own group within a shared registry, rather than centrally. Raised during orientation as one possible shape for the output; not a decision the Assembly has taken.

## **From the Assembly world**

- **Assembly:** a structured, time-bound process convened by GSF for a group of experts to reach documented agreement on a specific question, run asynchronously by email.
- **Harmony:** the tooling and templates that run an Assembly end to end, covering participant management, round emails, response capture, synthesis, and the decision record.
- **Facilitator:** the neutral role that runs the process, sets the rhythm, and never takes a side on the substance. Decisions belong to participants; facilitation ensures a fair hearing.
- **Project Lead:** the substantive owner of the question the Assembly is convened around. Shapes scope and content, but does not run the process.
- **Participant:** an expert confirmed into the Assembly, holding equal standing regardless of seniority or organisation.
- **Topic:** bounded questions the Assembly works through end to end. Topics run in order, close fully before the next opens, and do not reopen.
- **Round:** one pass through a single phase of a topic, with its own email, response window, and deadline.
- **Phase:** one of the three stages a topic moves through, always in the order Discover, Deliberate, Decide.
- **Discover:** the opening phase. Participants receive open questions and reply free-form and privately. Discover is the entry ticket for the rest of the topic.
- **Deliberate:** the middle phase. Participants receive three candidate positions and rate each 0 to 10 with comments, using shared anchors so ratings mean the same thing across participants.
- **Decide:** the closing phase. Participants receive one proposed position and return a single verdict: Endorse, Consent, or Object.
- **Candidate statement:** a possible answer to a design question, drafted for the group to assess in Deliberate or Decide.
- **Endorse / Consent / Object:** the three verdicts available in Decide. Endorse is active support; Consent is "I can live with this"; Object means the position cannot go forward as written and must be accompanied by what would need to change.
- **Silence-is-consent:** the rule that a non-response inside a Decide window is recorded as consent. There is no abstention.
- **Objection:** a formal block in Decide. Triggers discussion, a revised candidate, and a further Decide round. Objectors commit to helping resolve the objection.
- **Synthesis:** the anonymised write-up shared back after a round closes, opening with what changed because of the group's input.
