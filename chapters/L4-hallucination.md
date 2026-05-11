# Hallucination disclosure

Every agent will hallucinate. The question is whether the user finds out before, during, or after the consequences. Most products are still answering "after," and the cost is borne by the user, the business, and the field's reputation in roughly that order.

A hallucination is the agent producing a sentence that sounds true and isn't. Sometimes it's a fabricated source. Sometimes it's a confident answer to an unanswerable question. Sometimes it's the agent inventing a feature, a function, a person, a fact. The model itself cannot reliably tell you which sentences are hallucinations. The design has to.

This chapter is about the design.

## What hallucination disclosure actually is

The definition first.

**Hallucination disclosure is the agent's surfaced acknowledgement that a particular claim may be fabricated or unsupported, designed to let the user identify and verify unreliable content before acting on it.**

Three load-bearing pieces.

**Surfaced acknowledgement.** The system has to say it. A hallucination disclosed in fine print at the bottom of the chat is not really disclosed. The signal has to land in the same field of vision as the claim itself.

**Per-claim, not blanket.** A generic disclaimer that says "this model may be inaccurate" is worse than no disclaimer. It applies to everything and therefore to nothing. The user learns to dismiss it. Real disclosure is at the level of specific claims that are suspect for specific reasons.

**Before acting.** A user who discovers the hallucination after they've sent the email, signed the contract, or quoted the figure is too late. The disclosure has to land in the window where the user can still verify.

## Why it matters now

Two reasons.

The first is that models are getting more confident, not less. A 2026 model speaks with the fluency of an authority and the rigour of a magazine quiz, and the gap between those two is the hallucination zone. Disclosure design is the wedge between fluency and truth.

The second is that hallucinations cluster. They are not random across all topics. They concentrate in specific shapes — fabricated citations, invented entities, confident answers to questions where the model has thin training data. Knowing which shapes hallucinate most lets you design disclosure where it matters, instead of plastering disclaimers everywhere.

## The patterns that actually work

Five patterns.

**Mark unverified claims visibly.** When the agent makes a claim it cannot support from a source, mark it. A small inline indicator — a colour, a footnote, a label — that says "this is from the model's training, not from a specific source you can verify." Wikipedia's "citation needed" template is the prior art. It works.

**Distinguish hallucination from honest uncertainty.** A model saying "I'm not sure" is different from a model fabricating a confident answer. Both are forms of uncertainty, but they need different design treatment. Hedging is a signal the user can trust. A confident hallucination is a signal that has betrayed the user. Surface them differently.

**Lower confidence in known hallucination zones.** If the system knows it tends to fabricate citations, lower its confidence signal in that surface. If it knows it tends to invent function names in obscure libraries, hedge there. The model can be calibrated against itself once you know where it weakens.

**Build a feedback loop for suspected hallucinations.** Let the user flag a sentence as "this looks fabricated." Log it. Use it to retrain, to tune, to improve disclosure. The user is often the first to know when the model has hallucinated. The system should treat that as data.

**Reduce hallucination at the source where possible.** Constrained retrieval, grounded generation, citation-requiring prompts. The best hallucination disclosure is the one you didn't need because the system didn't hallucinate in the first place. This is a model and engineering question as much as a design one, and the designer should be loud in the room when it's being debated.

## When this fails

Three anti-patterns.

**Equal treatment for verified and unverified.** The agent produces a paragraph in which three claims are sourced and one is fabricated, with no visual or structural difference between them. The user reads as if all four are equally reliable. The hallucination travels into their work, undetected.

**Generic disclaimers everywhere.** "This response may contain inaccuracies." Plastered at the bottom of every message. Users learn to dismiss it on autopilot. By the time something genuinely uncertain appears, the muscle memory of dismissal has already won.

**Defensive over-hedging.** Every claim wrapped in qualifiers — "I think," "possibly," "according to my training" — to the point where the user cannot tell what the system actually knows. Hedging applied uniformly is the same failure as no hedging at all. The signal has to discriminate, or it isn't a signal.

## A worked example

A legal research agent helps a junior associate prepare for a deposition.

The agent produces a memo with six claims. Each one is rendered with a small colour-coded indicator beside it. Four claims are blue: linked to specific cases, click-through to the original opinion. One claim is grey: linked to a secondary source, a law review article. One claim is yellow: from the model's general legal knowledge, not from a specific source. That last one carries a small label — "general knowledge, verify before citing."

The associate reads the memo. They scan the colours before reading the text. They know exactly where to interrogate. The yellow claim turns out to be slightly wrong — the principle exists, but the specific phrasing the agent used doesn't appear in any actual case. The associate catches it because the colour told them to look. They rewrite the sentence using their own knowledge. The memo ships.

The model still hallucinated. The disclosure design caught it. That's the whole job.

## What this opens up

Hallucination disclosure is the most direct expression of the agent telling the truth about itself. A product that does it well is a product that has accepted, at the design level, that the model is fallible and the user is the final reviewer. A product that does it poorly is a product that is asking the user to take the agent's word for everything.

The chapters on citations, confidence, and trust calibration all build on this one. Each of them is, in part, a different surface for the same underlying commitment to honesty.

If this helps, take your product's last response to a user and ask: which sentences were sourced, which were uncertain, and which were the model speaking from training data. Then ask whether a user could have told them apart at a glance. The answer is your work for next week.

---

**Run while reading**
- Primary: `ai-alignment-reasoning / transparency-patterns` — Disclosing fabricated or unsupported claims to the user
- Secondary: `evaluation / failure-taxonomy` — Classifying hallucination types to design disclosure for each

**Related primer chapters**
- Citations and provenance
- Confidence and uncertainty
