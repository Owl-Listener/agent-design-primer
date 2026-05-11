# Confidence and uncertainty

Most agents lie about how confident they are. Some lie up, presenting wobbly outputs with the swagger of an oracle. Some lie down, hedging on things they are actually quite reliable at. Almost none of them are neutral, and the neutrality is the whole job.

Confidence design is the practice of making the system's actual uncertainty visible to the user, in a form they can act on, at the moment they need it. That sounds simple. It is one of the hardest interfaces in agent design, because it requires the system to tell the truth about itself in real time, and most product cultures are not set up to reward that.

This chapter is about how to do it anyway.

## What confidence design actually is

The definition first.

**Confidence design is the visible expression of a system's belief about its own output, calibrated to be neither over-stated nor under-stated, designed to let the user decide how much to trust this answer right now.**

Three load-bearing pieces.

**Visible expression.** The system internally has a notion of confidence — whether that's a probability, a heuristic, an eval score, or a model's own meta-prediction. Confidence design is the work of turning that internal state into a signal the user can read.

**Calibrated.** The signal has to mean something. If the system says "I'm sure" and is wrong half the time, the signal is broken. Calibration is the discipline of making the confidence label match the actual base rate of correctness.

**At the moment they need it.** Confidence is a real-time state, not a static badge. The same agent's confidence on the same question can change with the day, the prompt context, or the data freshness. The signal needs to update with the system, not lag behind it.

There's a deep literature here. The paper to read if you want to go further is Lee and See's *Trust in Automation*, which we cite in the chapter on trust calibration. The short version is: trust should match trustworthiness, and confidence design is the surface where that matching happens.

## Why it matters now

Because the absence of confidence design is the presence of false confidence.

A model that produces a sentence with no confidence signal is, by default, asking the user to trust it equally regardless of how shaky the underlying generation was. Users are forgiving of this for low-stakes work. They are not forgiving for high-stakes work, and the stakes are rising in every product category.

The other reason is that confidence is the connective tissue between citations, refusals, and trust calibration. A product without a confidence layer is a product where these features cannot talk to each other. The citation chapter, the refusal chapter, the trust calibration chapter all assume the system can express how sure it is. If yours can't, this is the chapter to fix first.

## The patterns that actually work

Five patterns.

**Coarse signals, not fine ones.** Use three or four levels, not a percentage. "I'm sure," "I think," "I'd verify this," "I'm not sure" gives the user something interpretable. "92%" gives the user nothing — they can't know what 92% means without a base rate, and the system probably can't support that level of granularity anyway. False precision is the most common failure in this space.

**Calibrate to base rate, not to feeling.** "Sure" should mean the model is right 95% of the time at this confidence label, across the full eval set. "I'd verify" should mean it's right 60-70%. These numbers come from running evals, not from intuition. A confidence system that hasn't been calibrated to base rate is decoration, not signal.

**Different signals for different stakes.** A recipe agent and a financial agent should not use the same confidence vocabulary. The financial agent needs more granularity at the high-stakes end ("I'd verify this with a CPA before acting") and fewer cheerful words. The recipe agent can be warmer. Match the language and the gating to the stakes the user is actually facing.

**Confidence about this task, not the model in general.** The agent should not say "I am 80% accurate overall." It should say "I'm confident in this specific answer to this specific question with this specific input." Per-output confidence is honest. Aggregate confidence is misleading because the user is acting on one output at a time.

**Honest fallback when confidence is unknown.** Sometimes the system genuinely cannot estimate its own confidence — a novel input, a new domain, a missing eval set. The honest move is to say so. "I don't have a strong sense of how confident I should be on this — please verify carefully" is a real signal, and users respect it. Faking confidence in the unknown is worse than admitting it.

## When this fails

Three anti-patterns.

**The precision parade.** Percentages everywhere, often to two decimal places. "73.21% confident" tells the user nothing they can use, and implies a level of self-knowledge the system does not have. Coarse signals beat this every time.

**Hidden confidence.** The model has internal logits, the eval set has scores, the system knows it should hedge — and the UI shows nothing. The result is that the user trusts every output equally and is then surprised by the wrong ones. The signal exists. It's just not on the surface.

**Smiling confidence.** The verbal hedge says "I'm not sure" while the visual treatment says "this is the answer." A muted prose qualifier next to a bold green checkmark is a contradiction the user resolves in favour of the visual. Match the verbal and the visual, or the contradiction will mislead them.

## A worked example

A medical-questions agent is built into a patient portal. Patients can ask anything from "what does this lab result mean" to "should I worry about this symptom."

The agent has three confidence levels, expressed as labelled sentences and matching colour cues. **"This is well-established"** in muted green for things like the meaning of a standard lab range. **"I think, but please verify"** in muted yellow for interpretive answers about specific results. **"I'd ask your clinician"** in muted orange for symptom-related questions, especially anything potentially urgent.

The visual treatment matches the linguistic hedge, every time. Action is gated at the lowest confidence level — the agent will offer to help draft a question for the clinician, but it will not auto-recommend treatments.

The patient learns the system in two or three interactions. They start to scan for the colour before reading the answer. They calibrate. The agent has done its job: not by being more accurate, but by being more honest about its accuracy.

## What this opens up

Confidence design is the discipline that turns an opaque model into a system the user can reason about. Without it, every other pattern in this primer is harder. With it, the citation pattern, the refusal pattern, the gates, the audit trails — all of them become easier because they have a shared language for "how sure is this, right now."

If you build only one new layer in your agent product this year, build this one. It is the connective tissue.

If this helps, look at the next sentence your agent produces and ask: how confident is the system in this, and how would the user know? If the answer to the second question is "they wouldn't," you have your work for next week.

---

**Run while reading**
- Primary: `ai-alignment-reasoning / transparency-patterns` — Surfacing model confidence and uncertainty as calibrated signals
- Secondary: `evaluation / output-quality-rubrics` — Calibrating confidence labels to base rates from eval data

**Related primer chapters**
- Citations and provenance
- Trust calibration across users
