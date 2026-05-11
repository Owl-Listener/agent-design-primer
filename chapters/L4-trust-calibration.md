# Trust calibration across users

Most users either trust your AI too much or not enough. There is almost no middle. That is a design problem, not a user problem.

We have been telling ourselves a story for two years now. The story is that the work of an AI designer is to build trust. Add a logo. Soften the copy. Make the agent reliable enough and the trust will take care of itself.

It doesn't.

A user who trusts your agent too much will accept a hallucinated invoice, sign a contract it drafted, take a wrong dose. A user who trusts it too little will check every line, ignore the parts that are actually useful, and eventually stop using it altogether. Both of those are failure. The middle, where the user trusts the system exactly as much as the system deserves to be trusted in this moment, on this task, is where the value lives. That middle is not a personality trait. It is a thing you design for.

This chapter is about how.

## What trust calibration actually is

A short definition, then we expand it.

**Trust calibration is the alignment between a user's level of trust and the system's actual trustworthiness for a given task at a given moment.**

Three words in that sentence are doing the work.

**Alignment**, because the goal is to match the trust to the moment, not to grow it. A perfectly calibrated user trusts a well-cited answer to a routine question and double-checks an uncertain answer to a high-stakes one. Same person, same agent, two different temperatures.

**This task**, because trust is not global. A model that is excellent at summarising documents is not therefore excellent at financial advice. Users need different defaults for different surfaces, and the design should help them switch.

**This moment**, because models drift. The system that was right yesterday may be wrong today. Trust is a living thing. It grows and contracts the way an organism does, and the design has to give it room to breathe.

This echoes a much older idea from Lee and See's HCI work. Trust between humans and automation should be calibrated, not maximised. That paper is from 2004, and we have spent two decades building products that ignore it.

## Why it matters now

Because the stakes have moved.

When the worst your software could do was crash, miscalibrated trust meant a frustrated user. When the worst your software could do is autonomously transfer money, send an email under your name, write code that ships to production, or describe a tumour, miscalibrated trust is harm. Every product moving towards an agent surface is moving towards higher stakes, and most of them are doing it without designing for the difference.

The other reason is that users are not a monolith.

The new junior employee using your agent for the first time needs strong calibration signals because they have no internal model of when to doubt. The senior expert needs weaker, more elegant signals because they already know which outputs to interrogate. Designing for one of them and not the other is how you end up with a product that feels patronising to power users and dangerous to novices, and you ship it anyway because the average user seems happy. The average user is a fiction.

## The patterns that actually work

There are five patterns that do the heavy lifting. Most agent products use one or two. The well-designed ones use all five, layered.

**Confidence display, calibrated to base rate.** Not a percentage. Percentages are precise where the system is not. Use coarse, honest signals: "I'm sure," "I think," "I'd verify this." The more granular your confidence display, the more you imply you can support that granularity. You usually can't.

**Provenance and sources, surfaced by default.** Users learn to trust an agent when they can see what it learned from. They learn to doubt it when sources are missing or thin. Both lessons are useful. Both should be visible without effort.

**Asymmetric defaults for asymmetric stakes.** Reversible action gets one click. Irreversible action gets a gate, a confirmation, a cooldown. The user's trust should not be the only thing protecting them from a bad outcome. This is not friction. It is the system telling the truth about what it is doing.

**Demonstrated track record, surfaced over time.** Users calibrate by experience. If your agent has been wrong about your spreadsheets twice, the user should be able to see that without leaving the surface they're working in. Most products hide this. Hiding it does not protect trust. It just delays the correction.

**Failure visibility, designed in.** When the system fails, show it failing. Most products go quiet on failure or paper over it with a graceful retry. Both teach the user that failures don't happen. They do, and the user will eventually find one. They will find it without the calibration signal you could have given them, and the trust will collapse all at once instead of softening gradually.

## When this fails

Three anti-patterns to watch for, all of them well-intentioned.

**The smiling assistant.** A persona so warm and confident that the user can't tell when it is guessing. This is the most common failure mode in chat-based products. The fix is rarely a copy change. It is an architecture change. The persona should be capable of unsmiling honesty when the underlying confidence drops.

**False precision.** The "87% confident" label that no human can interpret and no system can support. Users round it to "the computer says it's right." Coarse signals, not fine ones.

**Silent retries.** The system tries three times, succeeds on the third, and shows the user only the success. This is the engineer's instinct, and it teaches over-trust. Show the retry. Show the wobble. Let the user see the work.

## A worked example

Imagine you are designing the AI assistant for a healthcare scheduling app. The model is good at parsing emails into appointments, mediocre at handling cancellations, weak at insurance billing.

Three users, three calibrations, one product.

The new front-desk hire needs strong scaffolding. The agent surfaces its confidence in plain language. It refuses to act on insurance billing unsupervised. It shows sources for every appointment it creates and asks for review on the first ten until the user dismisses the prompt.

The seasoned office manager has earned faster defaults. The agent moves through routine appointments without confirmation but still flags low-confidence cancellations. Her interface shows confidence as a quiet colour cue, not a sentence.

The clinic owner sees a weekly trust report. The agent's accuracy on insurance billing is at 64% over the last month. She uses that to decide whether to expand the agent's autonomy or pull it back.

Same agent. Same model. Three completely different trust temperatures, all calibrated honestly.

## What this opens up

We have spent a decade learning to design for engagement. Now we are learning to design for trust, and we are going to spend the next decade learning to design for *calibrated* trust. The first asks "do they like this." The second asks "do they understand it well enough to live alongside it."

That second question is the work of this whole primer. This chapter is one face of it.

If this helps, send it to the designer on your team who is right now adding a smiling assistant to a high-stakes flow, and tell them the smile is the problem.

---

**Run while reading**
- Primary: `evaluation / user-satisfaction-signals` — Measuring whether users trust the agent appropriately for their tasks
- Secondary: `ai-alignment-reasoning / transparency-patterns` — Transparency is the lever that calibrates trust

**Related primer chapters**
- Confidence and uncertainty
- Hallucination disclosure

**From `inclusive-design-skills`**
- `inclusive-trust-signals`
