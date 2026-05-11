# Appendix: Anti-patterns

Anti-patterns are the failure modes the rest of this primer is trying to prevent. Most of them are not malicious. They are reasonable design choices that produced the wrong outcome, often because the team didn't have the primitive-level vocabulary to name what was actually going wrong.

This appendix names them. Each one has the same shape: the pattern's name, the mechanism by which it fails, and the chapter to read for the fix.

Fourteen anti-patterns, grouped by the layer they most often appear in.

---

## Trust and confidence

**The smiling assistant.** A persona so warm and confident that the user cannot tell when the system is guessing. The verbal hedge says "I think" while the visual treatment says "this is the answer." Users default to the visual, every time.
*Fix:* L4 — Trust calibration, L2 — Confidence and uncertainty.

**False precision.** Confidence shown as a percentage to multiple decimal places. The system cannot support that level of self-knowledge. Users round it to "the computer says it's right."
*Fix:* L2 — Confidence and uncertainty.

**Hidden confidence.** The model has internal signals, the eval set has scores, the system knows it should hedge — and the UI shows nothing. The user trusts every output equally and is surprised by the wrong ones.
*Fix:* L2 — Confidence and uncertainty.

**Generic disclaimers.** "This response may contain inaccuracies." Plastered at the bottom of every message. Users learn to dismiss on autopilot. By the time something genuinely uncertain appears, the muscle memory of dismissal has already won.
*Fix:* L4 — Hallucination disclosure.

---

## Citations and provenance

**Decorative citations.** Pills that look like sources but don't open, or that open a 404, or point to a paywalled paper with no preview. Worse than no citation, because the user thinks the system is grounded.
*Fix:* L2 — Citations and provenance.

**Phantom citations.** The citation opens, but the source does not actually support the claim. The agent picked the source for plausibility, not relevance. The most damaging citation failure because it looks legitimate at every level except the actual content.
*Fix:* L2 — Citations and provenance, L4 — Hallucination disclosure.

---

## Behaviour and progress

**Silent retry.** The system tries three times, succeeds on the third, shows the user only the success. The user develops an inflated sense of reliability. When they hit a real failure, the surprise is total.
*Fix:* L3 — Error recovery.

**The reveal-after-the-fact.** A plan is shown, but only after the work is done. The user has no opportunity to adjust. The plan is a receipt, not a contract.
*Fix:* L3 — Plan visibility before action.

**The fake percentage.** A progress bar that jumps in arbitrary chunks, gets stuck at 95%, finishes at a moment unrelated to the underlying work. Progress as theatre rather than signal.
*Fix:* L3 — Step-tracking and progress.

**The hostage UI.** Long-running tasks that require the user's tab to stay open. The user closes the laptop, the work is lost. The system imposes its limitations on the user instead of designing around them.
*Fix:* L3 — Long-running tasks.

---

## Refusals and gates

**The cold wall.** "I can't do that." Full stop. No reason, no redirect. The user feels stonewalled and either gives up or starts adversarially rephrasing until the system says yes to something it shouldn't.
*Fix:* L2 — Refusal patterns.

**The fake refusal.** The agent says "I can't help with that" and then helps with it anyway, or says no and silently does a degraded version. The user can't tell what the system actually did.
*Fix:* L2 — Refusal patterns.

**Gate everywhere.** Confirmation dialogues on every action. Users learn to dismiss them on autopilot. By the time a gate that matters appears, it gets dismissed too.
*Fix:* L4 — High-stakes decision gates.

**Soft gate for a hard action.** A one-click "confirm?" for something that cannot be undone. The interface treats the action as routine when it is in fact permanent.
*Fix:* L4 — High-stakes decision gates.

---

## Memory, privacy, and multi-agent

**Silent ingestion.** The agent reads, stores, and uses personal data without surfacing what it touched. The user infers from behaviour — "wait, how did it know that?" — and the trust hit lands hard.
*Fix:* L2 — Memory, L4 — PII handling visibility.

**Sticky memory.** The user asked the system to forget something, and it keeps coming up. Sometimes a bug, often architectural — the memory was written in multiple places and only some got deleted. The user feels powerless.
*Fix:* L2 — Memory.

**The opaque crowd.** The user knows there are multiple agents — the product page said so — but they cannot see which is doing what. The system feels powerful and unaccountable in equal measure.
*Fix:* L3 — Multi-agent orchestration.

**Cost surprise.** The bill at the end is bigger than the user expected because each sub-agent's calls were not surfaced in real time. The user blames the whole product, even when the individual calls were appropriate.
*Fix:* L3 — Multi-agent orchestration, L3 — Long-running tasks.

---

## Accessibility

**Accessibility as audit.** The product is built, then run through a WCAG checklist at the end, then patched. The patches are workarounds. The main surface remains designed for one kind of user.
*Fix:* L4 — Accessibility of agent loops. Every chapter in the primer, with the lens this chapter applies.

**Visual-only confidence signals.** A coloured pill, a green checkmark, a red border — with no label, no announcement, no fallback. Half the work is done.
*Fix:* L2 — Confidence and uncertainty, L4 — Accessibility of agent loops.

---

**Run while reading**
- Primary: `evaluation / failure-taxonomy` — A catalogue of agent UX anti-patterns and their failure mechanisms
- Secondary: `ai-alignment-reasoning / guardrail-design` — Many anti-patterns hide in refusal and gate UX
