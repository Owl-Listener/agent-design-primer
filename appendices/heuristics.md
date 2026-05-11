# Appendix: Heuristics for agent UX

Heuristics are not laws. They are pressure-tested guidelines that hold up across most cases and tell you, in a sentence, what to prioritise when you have to choose. Nielsen's ten heuristics did this for interface design in the nineties. This appendix is the agent-UX analogue, drawn from the patterns throughout the primer.

Use them as a review checklist. Use them in design crits. Use them as the seed for an org-wide language about what good agent UX is.

Fifteen heuristics, in the order most teams will encounter them.

---

**1. Trust is calibrated, not maximised.**
The goal is for users to trust the system exactly as much as the system deserves to be trusted, on this task, in this moment. Under-trust kills value. Over-trust causes harm. The middle is the work.
*Example:* A medical-questions agent labels claims as "well-established," "I think," or "ask your clinician," with each label visually matched and behaviour-gated.

**2. The plan is the contract.**
What appears in the plan is what the agent will do. What does not appear is what it will not do. Plans that the agent quietly deviates from are not plans.
*Example:* An agent's plan to refactor three files cannot, mid-run, also modify a fourth file without pausing and re-confirming.

**3. Show structure before content.**
When the agent produces a substantial output, show the shape first, then fill it in. A user who knows what is coming reads better, intervenes earlier, and trusts more.
*Example:* An agent's response begins with the headers ("Summary, Sources, Recommendation") before streaming the body of each section.

**4. Sources are required for verifiable claims.**
A claim that can be sourced should be. A claim that cannot be sourced should be marked as such. The default assumption — that the user trusts the agent on faith — is the wrong one.
*Example:* Inline numbered pills on each substantive claim, with click-through to the actual document.

**5. Confidence signals are coarse, not fine.**
"Sure / I think / I'd verify" beats "82% confident" every time. False precision is dishonesty disguised as rigour.
*Example:* Three coarse labels with calibrated base rates, applied consistently across the product.

**6. Refusals carry reasons and paths forward.**
A refusal without a reason feels arbitrary. A refusal without a redirect feels like a wall. The strong refusal carries both.
*Example:* "I can't approve this refund above $100, but I've prepared everything for the support team and they'll be in touch within four hours."

**7. The artefact is not the chat.**
When the agent produces something substantial, it should live in its own surface. The chat is the conversation about the work. The artefact is the work.
*Example:* Code lives in the editor, documents live in their own panel, drafted emails land in the composer — not in the transcript.

**8. Reversibility is proportional to consequence.**
Match the gate to the stakes. Free actions get no friction. Costly actions get a confirmation. Irreversible actions get a hard gate.
*Example:* Drafting a message has no gate. Sending it has a one-click confirm. Deleting an entire conversation has a type-to-confirm.

**9. Memory is visible and editable.**
The user should be able to see what the agent remembers about them and change or delete any entry. Memory the user cannot see or control is a privacy debt.
*Example:* A memory panel accessible from a sidebar, with per-entry edit and delete affordances.

**10. Tool use is surfaced.**
When the agent calls an external tool, the user should be able to tell — including what was sent, what came back, and under what authority.
*Example:* Inline cues during the agent's work — "searching the web," "querying the database," "sending an email" — with click-through to the call details.

**11. Handoffs preserve context, intent, and place.**
Whether the handoff is to another agent or to a human, the full state should travel. The receiving collaborator should not need to ask the user to restart.
*Example:* When an agent escalates to a human, the human sees the conversation, the user's intent, what the agent tried, and the user's emotional state.

**12. Failure is legible.**
When the agent fails, the user should know what failed, why, and what to do next. Silent retries teach over-trust. Failure made visible builds trust.
*Example:* "Payment was rejected by the airline. The card is valid on our end. Retry now, try a different card, or save and try later."

**13. Long tasks survive the user leaving.**
Tasks that take more than a few minutes need to persist across closed tabs, with a way for the user to return and check in.
*Example:* A status page showing all running and recent tasks, accessible at any time, with notifications when state changes.

**14. Multi-agent work shows the team.**
When more than one agent is involved, surface who is doing what, what each step costs, and how disagreements are resolved.
*Example:* A sidebar showing the named sub-agents, their current state, and a running cost meter.

**15. Accessibility is the lens, not the addendum.**
Every primitive in this primer has to work across sensory, motor, cognitive, and linguistic variation, in the main surface, not in a separate accessibility mode.
*Example:* Confidence signals are spoken and visual. Citations announce themselves to screen readers. Streaming respects reduced-motion settings.

---

**Run while reading**
- Primary: `evaluation / output-quality-rubrics` — A heuristic evaluation rubric tuned for agentic products
