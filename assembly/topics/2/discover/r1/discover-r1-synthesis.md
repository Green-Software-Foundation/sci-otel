# SCI for OpenTelemetry Assembly

> **About this document**
>
> This is the anonymised synthesis of one Discover round of the SCI for OpenTelemetry Assembly. Discover explores the problem space. **Nothing in this document is decided, agreed, or endorsed by the Assembly**, and it is not a consensus position of the Green Software Foundation or its members.
>
> This synthesis selects the strongest signals rather than reporting everything; the complete record is held by the facilitator and available if required.
> Individual responses are never published, and no synthesis identifies who said what.
> Counts describe how many responses supported a point.

## Topic 2: What Every Value Declares - Discover, Round 1

This round received 15 responses from the 37 invited participants.

## Where the Group Stands

The clearest result of this round is simple. A version number alone is not enough. It does not prove that two values describe the same software. It also does not prove that two values were produced in the same way.

Many responses described the same problem. A value changed, but the version number did not show why. This came up in two places:

- **Software identity.** Responses asked for an identifier at the level of the built artifact, such as an image digest or checksum, not only a version number.
- **Method.** Responses asked each value to state the source of its input data, such as its carbon intensity source or power model. The name and version of the tool are not enough. This was the strongest agreement in the round.

The group did not agree on confidence. The question is who should judge how much a value can be trusted. About half the responses want the producer or operator to state it. The other half want no separate judgment. They prefer that trust comes from the facts the value already states.

## Early Agreement

- **A value should state the source of its input data, not only the name and version of the tool.** The same tool and version can use a different carbon intensity source or power model. The result is then different, even when the software has not changed. Eleven of 15 responses supported this. They came from different settings, including HPC, cloud and Kubernetes.
- **Software identity needs an identifier below the version number.** Six responses said a version number or commit hash is not reliable on its own. The same source code can produce different binaries. A rebuilt image can get a new digest with no code change. No response disagreed.
- **A count of work should leave out activity that is not real work.** Six responses said raw counts include health checks, retries, failed requests or warm-up traffic. They said a count should state what it includes and what it leaves out. No response said these should count as work.
- **Measured, calculated, estimated and forecast should stay four separate labels.** The SCI names only two methods: measurement and calculation. Even so, nine responses gave matching definitions of all four labels. They said that joining "calculated" and "estimated" hides a real difference in how far a value can be trusted.

## Where Views Split

**Who should judge how far a value can be trusted?**
The responses split almost evenly. Six responses want the producer or the operator to give each value a confidence indicator. Examples were a simple scale, a percentage, or a certification with clear thresholds. Six other responses want either no confidence indicator, or one that is worked out only from facts the value already states, such as its nature and its input sources. They said a producer cannot reliably rate its own values, and a rating may give false certainty.

**Is the name and version of a tool enough to show two values were produced in the same way?**
Most responses said no, for the reason given above. One response said yes. In this view, a tool should never change without a new version. If its behavior changes, the people who maintain the tool are responsible for releasing a new version.

## Still Open

- **Can a value count if it cannot be linked to the software that produced it?** Some values come from an observer, such as a node agent, that cannot tell which release it was observing. No response said whether such a value can still be used to compare a system before and after a change.
- **Should the kind of work be part of the count's unit, or a separate attribute?** No response answered this directly. The two options can conflict. An existing metric already has a fixed unit. If a value reuses that metric, its unit may have no room to say what was included or left out.
- **Is a count of requests or transactions always the right unit?** Two responses raised this without settling it. One request can cost far more than another. In that case, a simple count can give a misleading comparison. Responses from fields where this is common, such as machine learning and high-performance computing, were not asked about it directly.

## Insight of the Round

One response changed how the question of work can be seen. Most responses asked which existing counter to use. This response asked a different question: what effect does the choice of unit have on how engineers behave?

If the unit is a request or a transaction, a change that removes unnecessary requests could look worse, even when users get the same result. The unit could then discourage the improvements the conventions are meant to support. This moves the question from "which metric do we reuse?" to "what does any fixed unit reward?"

## What Surprised Us

Before the round, stating input data looked like a smaller, technical point next to software identity. It became the strongest agreement in the round. Only one response disagreed.

Confidence went the opposite way. At first, it looked as if most responses wanted a confidence indicator. A closer count showed a different picture. The real question is who makes the judgment: the producer, or nobody. On that question the group is split almost exactly in half.
