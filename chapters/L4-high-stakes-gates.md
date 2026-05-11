# High-stakes decision gates

A gate is friction. A gate is also the difference between a hallucinated decision and a deliberate one. Most products treat all gates the same, which trains users to dismiss them all, which means the gate that mattered didn't catch what it was supposed to catch.

The work of gate design is not about adding obstacles. It is about matching the cost of an action to the deliberateness of the moment that approves it. A small, reversible action gets a small gate or no gate. A large, irreversible action gets a large gate, and the largeness of the gate is itself information — it tells the user "what you are about to do is consequential."

This chapter is about building gates that mean something.

## What a gate actually is

The definition first.

**A gate is a deliberate friction designed to make an action's commitment moment more conscious than the action's request moment, scaled to the consequence of the action.**

Three load-bearing pieces.

**Deliberate friction.** A gate is, on purpose, harder than the path to it. Friction without purpose is bad UX. Friction with purpose is safety.

**Commitment moment.** Gates are about the transition from "I would like this to happen" to "this is now happening." The two moments are different, and the gate lives between them.

**Scaled to consequence.** Not all actions deserve the same gate. The single most important design move in this whole topic is calibrating gate strength to action stakes.

## Why it matters now

Two reasons.

The first is that agents are starting to take actions whose consequences exceed the user's ability to recover. Send money, sign contracts, deploy code, send communications under the user's name. The gate is often the last meaningful checkpoint before an irreversible commitment.

The second is gate fatigue. Most products have inherited a gate culture from the desktop era — confirm everything, ask are-you-sure to anything that touches data. Users have learned to dismiss without reading. When the gate that finally matters appears, the muscle memory of dismissal swallows it. Gate design has to fight this directly.

## The patterns that actually work

Five patterns.

**Match gate strength to action stakes.** A reversible action gets a one-click confirmation or none at all. A costly action gets a short confirmation with a preview of the change. An irreversible action gets a hard gate — typing a confirmation phrase, a brief cooldown, a second click after a delay. The user feels the difference. The feeling is part of the design.

**Type-to-confirm for irreversible.** For actions that cannot be undone — deleting an account, transferring funds, deploying to production — require the user to type something specific. The name of the resource. The amount. The word "delete." The friction is small but precise. It cannot be dismissed by autopilot.

**Cooldown for major changes.** Some decisions benefit from a forced pause. A request to permanently delete a workspace might land in a "scheduled for deletion in 24 hours" state, with a clear undo. A large agent-initiated change might wait two minutes before executing, with a "cancel" button on screen. The pause turns "I clicked yes" into "I had time to reconsider and didn't."

**Dual control for shared accounts.** When an action affects more than one user, route the gate through more than one. A team budget change requires approval from a second admin. A shared document deletion requires a second confirmation from the original owner. This is heavyweight and should be rare, but for the right actions it is the right call.

**Preview the action, specifically.** A gate that says "delete this?" is weaker than a gate that says "delete these 47 files in /project-alpha/?" The second one tells the user what they're about to do, in their own terms. A surprising number of mistakes are caught at the preview-the-specifics moment.

## When this fails

Three anti-patterns.

**Gate everywhere.** Confirmation dialogues on every action, including trivial ones. Users learn to dismiss on autopilot. By the time a gate that matters appears, it gets dismissed too. This is the most common failure in legacy desktop products that have migrated agents into them.

**No gate.** A silent commit of a high-stakes action. The agent decides, the agent acts, the user discovers it later. Especially common in early agentic products that haven't yet built a gate vocabulary for irreversible work.

**Soft gate for a hard action.** A one-click "Confirm?" for something that cannot be undone. The interface treats the action like a routine save when it is in fact a permanent deletion. Users approve in seconds and regret in days. Match the gate to the stakes, every time.

## A worked example

An accounting agent processes invoices and can move money on the company's behalf.

For a draft invoice — no gate. The agent generates, the user reviews. Free tier.

For sending an invoice to a customer — a one-click confirmation with a preview of the email and the amount. "Send invoice #2841 for $4,200 to billing@acme.com." Costly tier with explicit preview.

For approving a vendor payment under $1,000 — a one-click confirmation, similar preview. Costly tier.

For approving a vendor payment over $10,000 — a type-to-confirm. "To approve a payment of $14,200 to Acme Corp, type the amount and the vendor name below." Hard gate. The friction is intentional. The user has to slow down.

For changing a tax setting or modifying the chart of accounts — a 24-hour cooldown, with an email to all admins and a clear "cancel before deadline" affordance. Reversible during the window, irreversible after.

The same product, the same agent, five different gate strengths. Users encounter friction proportional to consequence, and the gates that matter are the ones they actually read.

## What this opens up

Gate design is the surface where the agent's respect for the user's authority becomes visible. A system that gates well is a system that has understood the asymmetry of an irreversible action and built the design to honour it. A system that gates poorly is a system that has either over-trusted itself or under-trusted the user, and both errors are corrosive.

The chapters on undo, audit trails, and refusal patterns all chain with this one. A gate is one of several mechanisms a careful product uses to make the moment of commitment a deliberate one.

If this helps, take the five highest-stakes actions in your product and look at the gates in front of them. If any of them is dismissable in a half-second of autopilot, that's the gate that will fail you when it matters.

---

**Run while reading**
- Primary: `ai-alignment-reasoning / escalation-design` — Designing confirmation, dual-control, and review for irreversible actions
- Secondary: `ai-alignment-reasoning / guardrail-design` — Gates and guardrails are two sides of the same decision

**Related primer chapters**
- Undo and reversibility
