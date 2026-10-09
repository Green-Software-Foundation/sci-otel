# Topic 1: Scope and Use Cases

## Purpose

Establish why software carbon belongs in OpenTelemetry, who these semantic conventions are for and what people can do with them and what decisions it enables. Everything a
later Topic decides is bounded by the answer, so this Topic produces the use-case justification each proposed convention must carry.

## What the Topic must decide

- **The ranked use cases.** Two to four, in committed priority order. For each: who the
  consumer is, the question they need answered, and what they do differently once they
  have the answer. A consumer named without its question and its decision is not a use
  case. State the question as the consumer would ask it. "Engineering optimization" is an
  audience with a topic; "did this release use less energy for the same work, and if not
  which part is responsible" is a use case.

  Where two use cases conflict, say which prevails. The order is the substance of this
  Topic, not a presentational choice.

- **What the top-ranked use case requires of the telemetry.** What must be observable, at
  what grain, and attributable to what, for that consumer to answer their question. This
  is stated as a requirement the use case imposes, not as a design for the signals that
  meet it.

- **What the lowest-ranked use case accepts losing.** Resolution, timeliness, coverage, or
  directness of measurement. A ranking that costs nothing is not a ranking.

- **What falls outside.** The boundary that follows from the ranking: what these
  conventions do not undertake to serve, and what a value must state about itself for any
  of the ranked uses to be possible at all.

**There is no required order.** Lead with whichever of the four the position turns on. A
candidate that works through them as printed has taken the shape of the brief.

## What later Topics decide, and must not appear

Namespace and naming. Units. Signal types and instrument selection. Enumeration of
boundary levels. Which attributes carry provenance, method, confidence or uncertainty, and
their form. Allocation methods. The functional unit and the composition of an SCI value.
Definitions of SCI itself or of OpenTelemetry mechanics.

A candidate states what a use case requires. It does not design what meets the
requirement. "This use needs consumption attributable to a stable software entity across
releases" is a requirement. Naming the entity levels, the attributes, or the instrument is
not.

Embodied carbon is inside this Assembly and inside SCI. A position that places it outside
the conventions is not available here.

Material a later Topic owns is deferred, not excluded. Leave it out silently rather than
noting that it sits elsewhere.

## Settled before this Topic, and not open

- Market-based instruments, meaning offsets and renewable energy certificates.
- Cost and financial data as a quantity the conventions carry. Finance and procurement
  teams remain legitimate consumers, and cost as an input to an estimation model remains
  live. Only monetary cost as a reported quantity is excluded.
- Adoption and prototyping by existing tooling, and selection of reference
  implementations.
- The subject is the carbon emissions of software systems, with energy in scope as a
  component of that calculation. It does not widen to water, primary energy, abiotic
  depletion or general sustainability indicators.
- That the conventions cover values which are not directly measured. What such a value
  must state about itself is open; whether it is covered is not.
- Reuse-first at scope level: the conventions reference existing hardware and system
  conventions rather than define hardware telemetry.

## Standing constraint

Metric attributes that may have high cardinality can only be defined as opt-in, as can
attributes that are expensive to retrieve or that carry a security or privacy risk. A use
case requiring per-request, per-function or per-user attribution as a default contradicts
this. The attribute-level decisions belong to later Topics, so a candidate has no need to
address the constraint directly.

## Out of the assembly's hands entirely

YAML authoring, codeowners and SIG sponsorship, submission logistics, hosting, publication
sequencing.
