# Assembly Participant Handbook

Welcome. You have been confirmed as a participant in the SCI for OpenTelemetry Assembly. This is the one document to keep. Everything you need to take part lives here, so when a question comes up later you look it up rather than wait for a reply.

---

# Project and Assembly overview

Start here. This gives you the whole picture: who is convening this, what an Assembly is, what we are building and why it matters, and what taking part involves. Everything after it is reference you can return to.

## Who is convening this

The Green Software Foundation (GSF) is a non-profit consortium of more than 60 organisations, spanning companies, universities and non-profits, working towards a future where software has no harmful environmental impact. We pursue that by building standards, tooling and best practices through the consensus of our members and the wider community. This Assembly is a GSF initiative.

## What an Assembly is

An Assembly is how the GSF brings a focused group of experts to a clear, documented agreement on a specific question. It runs entirely by email, over a fixed period, in structured rounds, and it is designed so that a real consensus emerges from written deliberation rather than from whoever is loudest or most available. There is nothing to install and no standing meeting to attend. You reply to emails, on your own schedule, inside each round's window. Running this way is also a deliberate choice for a foundation focused on software's environmental impact: asynchronous email deliberation avoids the travel and repeated video calls a group this size would otherwise need.

## What we are working on, and why it matters

Two worlds are meeting in this room.

Software has a carbon footprint. The Software Carbon Intensity (SCI) specification, published as an international standard (ISO/IEC 21031:2024), gives a consistent way to measure it: a rate of carbon emissions per unit of useful work, expressed as **SCI = (E x I + M) / R**.

OpenTelemetry (OTel) is the open standard the software industry uses to observe how systems behave, the traces, metrics and logs that almost every modern platform emits. Its **semantic conventions** are the shared vocabulary that makes all that telemetry mean the same thing everywhere.

Today there is no agreed way to express carbon intensity as native OpenTelemetry telemetry. If there were, carbon could be measured and reported with the same tools teams already use for performance and reliability, instead of being bolted on afterwards. Closing that gap is what this Assembly exists to do.

## Why you, and who else is here

You are one of around 40 practitioners drawn from both communities: people who build and maintain OpenTelemetry, and people who work in software sustainability and carbon measurement. The mix is deliberate. Neither community can answer this alone, and the entire point is to agree something both can stand behind. You are here because your expertise is needed in at least part of this work.

## What we will produce, and where it goes

We will produce a blueprint: an agreed design document setting out how SCI should be represented in OpenTelemetry, capturing the design decisions in enough detail that the formal conventions can be written from it directly. The blueprint is then rendered into draft semantic conventions, which you will be invited to review for fidelity before submission, and the GSF carries them to the OpenTelemetry Semantic Conventions SIG, the group that governs these conventions, as the community's proposed design.

## What taking part involves, in one glance

- About **30 to 45 minutes of your time in an active week.**
- **Everything by email**, answered in your own time within each window.
- **A series of sections**, each tracing one part of the SCI formula, run one at a time.
- **An orientation call** to open, offered in two time-zone slots (attend whichever suits), then a handful of informal drop-ins.

The rest of this document explains each of these in detail. Read on when you need it.

---

# What we ask of you, and what you can expect from us

This Assembly works because a small group of people each do a small amount, reliably. Here is the deal in both directions.

## What we ask of you

- **Bring your expertise, and your disagreement.** You are here as an expert. The most valuable thing you can do is take a clear position and say where you would draw a line, especially when it differs from the room. We would rather have your sharp disagreement than your polite agreement.
- **Stay open past your own domain.** Nobody here spans the whole problem. Contribute where you are strong, and stay genuinely open where someone else is stronger.
- **Respond within the window.** You do not need to answer everything, but a reliable reply each round is what keeps the process moving for everyone. Roughly 30 to 45 minutes in an active week.
- **Disagree constructively.** When you object, say what would need to change, ideally with alternative wording. A flat "no" without a route forward stalls the group; a well-argued objection moves it.
- **Respect the phases.** When a section is open for exploration, explore. When it moves to a decision, decide. Once it closes, it stays closed. Reopening settled ground is the one thing that can unravel the work.

## What you can expect from us

- **Your voice carries equal weight.** Every participant has equal standing, regardless of seniority, organisation or how loudly anyone else writes. The process is built so the quietest, best-argued point can win.
- **Nothing you say is wasted.** Every response is acknowledged, and every synthesis opens by showing what changed because of the group's input. You will see your fingerprint on the outcome.
- **A predictable rhythm.** Clear windows, Anywhere on Earth deadlines, synthesis after each round closes, and a reminder before anything is due. No surprises about what is expected or when.
- **Genuine neutrality.** The facilitator runs the process and never takes a side on the substance. The decisions are yours; the facilitation only ensures everyone gets a fair hearing and no one gets deadlocked.
- **Your candour protected.** Discover responses are private, and nothing is ever published outside the Assembly with your name against it. What is shared within the group stays within the group unless we all agree otherwise, which is what makes honest input safe.

---

# What consensus means here, and what it does not

A section is done when the group has settled every open decision within it and no objections remain unresolved. Consensus does not mean everyone is happy, and it is not a check on whether the conventions will turn out accurate or complete; that is not something a group agreement can promise. What it does guarantee is that every design decision this Assembly is responsible for has been made and agreed, so the work can move forward. We deliberately look for the position the least satisfied person can still accept, rather than one that pleases the majority while quietly leaving someone behind.

# What we need from you: clear positions, especially where you disagree

This is boundary-drawing work. What is in scope and what is out. Which existing OpenTelemetry conventions we reuse and which we do not. Where operational emissions end and embodied carbon begins. Every question we send is trying to locate a line the group can agree on.

The most useful thing you can do is take a clear position and explain where you would draw the line and why, above all when you disagree with others. Disagreement is not friction to be smoothed over; it is the signal that shows us where the real boundary sits.

# What we are doing: mapping the SCI formula onto OpenTelemetry

The SCI specification reduces software carbon intensity to a single formula:

**SCI = (E x I + M) / R**

Our task is to take that formula apart and agree how each component, E, I, M and R, should be represented in OpenTelemetry. Work through every component and the blueprint is complete.

# The shape of the work

The Assembly is organised into a series of sections. Each runs in order, closes fully before the next opens, and does not reopen. Together they trace the SCI formula from end to end.

The exact number of sections and how they are grouped is being finalised, but the territory is fixed by the formula. Expect the work to move through:

- **Scope and use cases** – who the telemetry serves, what decisions it enables, what is explicitly out of scope.
- **Namespace and reuse** – where the conventions live, what we reuse from existing OpenTelemetry conventions, and how we express units.
- **Operational emissions (E and I)** – energy and carbon intensity: instruments, boundaries, provenance, method disclosure.
- **Embodied carbon (M)** – how M is represented and allocated, treated honestly given thin data.
- **Functional unit and composition (R)** – how R is expressed and how the whole SCI computation composes, tested with a worked example.

# How a section works

A section moves through three phases, always in this order: Discover, then Deliberate, then Decide. Each phase is one kind of email, asking for one thing, with the time cost and an Anywhere on Earth deadline stated at the top. You reply above the line. There are no portals and nothing to install.

## Discover: open the questions

You receive a small set of open questions and reply free-form, in as much depth as you like. There is no template. This is where you open the space, so long, unpolished, thinking-out-loud answers are exactly what we want; short answers are the thing to avoid. Each round pairs its core questions with an optional deeper technical one, so you can go as far as your expertise takes you. Your Discover responses are private: only an anonymised synthesis is ever shared back, never your raw words with your name against them. That privacy is deliberate, because it lets you be candid and keeps quieter voices from being drowned out by louder ones.

A practical tip: dictate your Discover responses. Speech-to-text captures rich reasoning far better than typing tends to, and there is no need to tidy it up on our account.

**Your Discover response is your entry ticket for the section.** If you do not take part in Discover, you cannot take part in Deliberate or Decide for that section; you rejoin at the next section. This protects everyone who put the work in from a last-minute block by someone who did not.

## Deliberate: react to the candidates

Deliberate is the one phase that is a visible conversation: you will see who said what and respond to one another directly in the thread, because that is where real deliberation happens. You receive three candidate positions, and you rate each one from 0 to 10 and comment on each. Ratings use shared anchors, so that a 5 means the same thing in Santiago as it does in Tokyo:

- **0** – you would fundamentally object to this.
- **5** – you could probably accept it. It would likely survive a Decide vote.
- **10** – you would fully endorse it.

## Decide: give a verdict

You receive one proposed position and give one of three verdicts:

- **Endorse** – you actively support this. No text needed, though it is welcome.
- **Consent** – you can live with this. No text needed.
- **Object** – this cannot go forward as written. An objection must say specifically what would need to change, ideally with proposed wording. Objecting commits you to helping resolve it.

**Silence is consent.** If you do not respond within a Decide window, you are recorded as consenting. There is no abstention and there is no later round to catch it. If something is wrong, you must object now.

**If someone objects,** it is normal mechanics, not conflict:

- The objection triggers discussion and a revised candidate that takes on the proposed change where one was given, followed by a further Decide round. There are at most three rounds.
- If it is still unresolved after a revision round, it goes to a live resolution session in the next standing slot, with advance notice. Attendance is required for the objector and for someone representing the endorsing position, and optional for everyone else. These sessions are recorded, because they are part of the decision record.
- If objections still persist after three rounds, the outcome is chosen by a published fallback rule over all the votes cast. No single person can stall a section indefinitely.

## The rhythm you can rely on

- Each round has a response window with a clear deadline. Window lengths vary by phase, and a window is sometimes extended so everyone gets a fair chance to respond.
- Deadlines are set **Anywhere on Earth**, and a synthesis follows once the round closes. You always know when the next thing is coming.
- Every response is acknowledged, even briefly. You will not send something into silence.
- You get a reminder before a deadline.

## What you get back each round

- **What changed because of your responses**, opening every synthesis with the anonymised reasoning that actually shifted a candidate.
- **Insight of the round:** one anonymised quote that taught the group something.
- **What surprised us:** one line on where responses diverged from what anyone expected.

## Time commitment

Plan for **30 to 45 minutes in an active week**, though some weeks are lighter. We would rather give you an honest estimate now than have the workload surprise you later.

# How your privacy works

The two scopes work differently, on purpose. Within Deliberate, other participants see your comments, because the debate has to happen somewhere. Outside the Assembly, nothing is ever published with your name against it: only the settled consensus and anonymised synthesis are made public, and the record is made auditable through cryptographic proofs rather than by exposing who said what. You can take part fully even if your organisation restricts public positions.

# Recognition

- **Named contributor credit** in the final report, opt-in. Positions are never attributed to you, but you are credited as a founding contributor to a prospective OpenTelemetry convention.
- **A closing showcase** when the report publishes: an optional celebration where participants can present a section they helped settle.
- **A review before submission.** Once the blueprint is rendered into draft conventions, you will be invited to review them to confirm they faithfully reflect what the group agreed, before they go to the SIG.

# Staying connected: drop-ins

Three optional drop-in calls run across the Assembly. These are for connection, not deliberation.

- 45 minutes, cameras encouraged, no agenda, no minutes, **no recording**.
- Two rotating time slots so no hemisphere always gets the worst one.
- **We do not discuss active candidates on these calls.** Substance stays in the written process so that nobody who missed the call loses influence, and so the record stays complete. Anything substantive is a Discover question, and we will say so on the call.

# Participant directory (opt-in)

Many of you applied partly to meet the rest of you. If you opt in, the directory lists your name, organisation, one line of expertise, and LinkedIn. **[TO CONFIRM: where the directory lives / how to opt in]**

# FAQ

Common questions are answered on a dedicated page: FAQ.

# Your contacts

- **Project Lead:** Sarah Hsu **[TO CONFIRM: contact route]**
- **Facilitator / day-to-day:** **[TO CONFIRM: name + reply-to address]**
- **Drop-in hosts:** **[TO CONFIRM: Pindy + facilitator]**

# Key dates

- **Orientation call (same content, two slots):** Wednesday 22 July, 14:00 to 15:00 GMT, and Thursday 23 July, 08:30 to 09:30 GMT.
- **First section opens:** **[TO CONFIRM]**
- **Drop-ins:** **[TO CONFIRM: three dates]**
- **Standing objection-resolution slots:** **[TO CONFIRM: bi-weekly slot]**
