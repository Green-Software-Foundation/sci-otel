# Candidate [Letter]: [Short plain-language title, 3 to 6 words]

[The position in one sentence of 25 words or fewer. Name only the answers on which this candidate differs from at least one of the other two, and what it says on them. Never present an answer all three candidates share as a difference. It states the position, not the reasons for it. A participant should be able to read it once and say how this candidate differs.]

## How It Works

[100 to 150 words in plain language, in the voice of the final Report ("A change is marked by...", not "This candidate proposes..."). First state the principle that connects this candidate's answers: what it treats as most important when a baseline and a changed system are compared. Then show that principle at work on one example: a single service compared before and after one release, including what each of its values would state and what the comparison could and could not conclude. Do not restate the table row by row; the table carries the answers. Name an existing OpenTelemetry attribute only where the example needs it. No material from later Topics.]

## What Every Value Declares

[Identical rows, in the same order, in all three candidates, so reviewers can compare answers row by row. Never drop a row. Each answer is the agreed text for that decision and must agree with How It Works. Name at most the one existing OpenTelemetry attribute the answer is anchored on: no attribute lists, filter values or edge cases. Where the Discover responses agree on an answer, every candidate gives it in the same words. Candidates differ only on rows where the responses disagree, and every disagreement the Discover synthesis records has each side taken by at least one candidate.]

[End every answer with its carriage in square brackets, in this form: who carries it, either "every value" or "when" followed by the condition; then what it changes with, one of "fixed for the software", "changes with each release or stated change", "changes with the producer" or "can differ between values". For example, a release marker carried on every value ends with the carriage "Every value; changes with each release or stated change" inside square brackets. Where an answer is "no", omit the carriage. A row's carriage must not contradict another row's answer: if a value can lack something another row allows to be absent, the carriage says when it is carried rather than "every value". Carriage does not count toward the word limit.]

| Decision | Answer |
|---|---|
| **Sameness: what identifies the software?** | [The identifying attribute comparison is anchored on, and whether the namespace or deployment environment is included. Up to 15 words.] |
| **Sameness: what marks the change?** | [A release, any new build, a stated change event, or a combination, with the one attribute it is carried in. Up to 25 words.] |
| **Sameness: is the infrastructure it ran on shown?** | [Yes or no, and if yes, what kind of infrastructure detail, without listing attributes. Up to 15 words.] |
| **Sameness: what if the software's identity is unavailable?** | [Whether the value can still serve the first-ranked use case, and what it states instead. Up to 25 words.] |
| **Functional unit: where does the count of work come from, and how is its kind declared?** | [Existing metrics, a dedicated count, or both, with the reason where a dedicated count is added; and whether the kind of work is in the count's unit, a separate attribute, or both. Up to 35 words.] |
| **Provenance: what do measured, calculated, estimated and forecast mean?** | [One definition per nature, in that order, precise enough that two implementers would assign the same nature to the same value, each naming the SCI method it falls under, or that it falls under neither. Up to 70 words.] |
| **Provenance: what does a value state about how it was produced?** | [Method name and version only, or also the source of its input data, and if so whether always or only in stated cases. Up to 25 words.] |
| **Provenance: is there a confidence indicator?** | [Begin with Yes or No. Any indicator that appears on some values, such as an uncertainty bound present only when substantiated, is Yes. If yes, what it is and when it appears. Up to 20 words.] |

## Trade-offs

**Gains:** [One or two sentences on who this position works best for among engineers comparing releases, producers of energy and carbon values, automated consumers and the spec writer, and what it makes possible or easier that the other two candidates do not. Draw only on the answers where this candidate differs; never claim a benefit all three share.]

**Gives up:** [One or two sentences on who bears the cost of this position and what it rules out, delays or makes harder compared with the other two candidates. Draw only on the answers where this candidate differs; never attribute to it a cost all three share. Include any effect on later Topics, for example how energy is joined to the count of work in Topic 3. Write it as a supporter of this candidate would describe its cost fairly. If this is hard to write, the candidate is not yet distinct enough from the other two.]

## Where This Came From

[Two sentences, with no attribution, linking this candidate to the Topic 2 Discover synthesis. The first names the theme or themes this candidate builds on, as the group expressed them, for example "Many participants..." or "A smaller group...". The second names a concern or disagreement raised in Discover that this candidate responds to, and how it responds. Use only themes that appear in the Discover synthesis. Describe the evidence, don't argue that the candidate follows from it.]