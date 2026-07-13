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
