# Handoffs

Most agent-to-human and agent-to-agent handoffs are silent. The information that mattered most disappears in the handoff, and the user has to start over. That's the moment where almost every agent product feels broken, and it is one of the most under-designed surfaces in the whole field.

A handoff is the seam between two collaborators. It is the place where context, intent, and progress have to travel cleanly from one to another, or the value of all the prior work is lost. The handoff itself is the design problem. The two collaborators are the easy part.

This chapter is about getting the seam right.

## What a handoff actually is

The definition first.

**A handoff is the transfer of an in-progress task from one collaborator to another, designed to preserve the context, the intent, and the user's place, with visibility into the transfer itself.**

Three load-bearing pieces.

**Transfer of an in-progress task.** A handoff is not just a routing decision. It is a movement of state. Whatever has happened so far has to travel with the task. The receiving collaborator needs everything the sending one had.

**Preserve context, intent, and place.** Context is the data. Intent is the user's goal. Place is where the user is in the journey. All three have to survive the handoff. Losing any one of them means the user has to teach the new collaborator from scratch, and that's the failure that makes handoffs feel like restarts.

**Visibility into the transfer.** A handoff the user can't see is a handoff that feels like a bug. The strongest pattern is to make the handoff itself a visible moment, with a clear who and a clear why.

## Why it matters now

Two reasons.

The first is that multi-agent systems are everywhere now. Background sub-agents, specialised tool-using agents, escalation paths to humans. Every one of these is a handoff design problem, and most of them are still solved badly. The receiving agent often gets a thin slice of the context the previous one had. The user pays for that thinness in repeated explanation.

The second is that human-in-the-loop products live or die on the handoff to the human. When the agent escalates and the human gets nothing — no transcript, no summary, no diagnosis — the user gets to feel the cost of the handoff personally. They have to relive the conversation. They blame the system, but the failure is the seam.

## The patterns that actually work

Five patterns.

**Define the handoff payload.** What information travels with the task at the moment of handoff. The original user request. The conversation transcript or relevant subset. The agent's interpretation of the user's intent. What the agent has already tried. What it concluded or partially concluded. The user's current emotional state, if it matters for tone (an escalation from a frustrated user needs a different opening than one from a curious user). A handoff with no payload is just a routing decision wearing the word "handoff."

**Define the handoff trigger.** When the system decides to hand off, not when the user has to demand it. Triggers might be: agent confidence drops below a threshold; user expresses frustration repeatedly; task crosses a policy boundary; another collaborator has specialised capability. Make the triggers explicit, log when they fire, and tune them with real data.

**Define the re-entry point.** Where the user picks up. After a handoff to a human, can the user come back to the agent layer for follow-up questions? After a handoff to a sub-agent, does the user see the result inline or does it land somewhere else? The re-entry shapes whether the handoff feels like a continuation or a fork in the road.

**Make the handoff visible.** Show the user the handoff is happening. A small cue at the moment of transition. "Connecting you with Marisol from the billing team, who has the full conversation so far." This three things at once: it acknowledges the transfer, it names the new collaborator, and it implicitly promises that the context travelled. Users feel met.

**Allow bidirectional handoffs.** The strongest products let the user pull a task back from a sub-agent or a human, or move it forward to a different one. The handoff is not a one-way door. It is a switching surface the user has some authority over.

## When this fails

Three anti-patterns.

**The cold handoff.** The new collaborator gets nothing. The user has to repeat everything. This is the most common failure in human-in-the-loop products, and it is the most damaging because the user experiences it as the agent having wasted their time on a conversation that didn't count.

**The stealth handoff.** The handoff happened, but the user doesn't know. They were talking to one agent and now they're talking to another, or to a human, or to a different model, and nobody told them. The break in tone or behaviour is something they feel before they understand, and it erodes trust faster than a clear handoff ever would.

**The one-way handoff.** The user can be moved between collaborators only by the system. They cannot pull back. They cannot reroute. They cannot return to the original agent for a follow-up. This frustrates power users especially, who often want to use the agent layer to ask quick clarifying questions even after a human has taken over the main thread.

## A worked example

A customer support agent handles billing inquiries for a SaaS company.

The user asks about a refund. The agent works through it, gathers the relevant details, attempts to process the refund, hits a policy threshold above its authority. The agent shifts.

Visible handoff cue appears: "I've prepared everything for Marisol on the billing team. She has the full conversation, your account details, and what I've tried so far. She'll be in touch within four hours, and you'll get an email with case number C-2841." The user knows what happened and what to expect.

Marisol opens the case. She sees a structured summary: the user's request, the agent's interpretation, the policy threshold that was hit, the data the agent already gathered, the user's tone over the course of the conversation. She doesn't have to ask the user anything they've already explained.

When Marisol responds, the user has two surfaces. They can reply to Marisol directly. They can also still ask the agent quick follow-up questions ("what was my case number again?") that don't need Marisol's involvement. The handoff is real but not exclusive.

Same case, same model, completely different experience because the seam was designed.

## What this opens up

Handoffs are where collaborative work either compounds or collapses. The handoff carries everything that was built, or it loses it. The chapters on plan visibility, multi-agent orchestration, and audit trails all depend on the handoff design being solid. Each of them is, in part, about making the seam between collaborators visible and traversable.

The deeper truth here is that multi-agent and human-in-the-loop products are made or broken by their seams, not by their nodes. We spend most of our design attention on the individual agents and the individual humans. We should be spending much more on the moments between them.

If this helps, look at the next handoff your product performs. List what the receiving side knows when they pick it up. If the list is missing the original user intent, the agent's attempts, or the user's emotional state, that's your next sprint.

---

**Run while reading**
- Primary: `design-agent-orchestration / handoff-protocols` — Designing the payload, trigger, and re-entry points for handoffs
- Secondary: `design-agent-orchestration / state-management` — Keeping context intact across handoffs

**Related primer chapters**
- Multi-agent orchestration UX
- Plan visibility before action
