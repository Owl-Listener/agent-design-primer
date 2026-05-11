# Plan visibility before action

An agent that doesn't show its plan is asking you to trust the conclusion without seeing the work. We have spent decades teaching users not to do that, and we are now asking them to do it constantly, several times an hour, often for tasks that matter.

The plan is the contract. It is the agent telling the user "this is what I think you asked for, this is how I'll go about it, here's where you can intervene." When that contract is invisible, every step the agent takes is happening behind a curtain. When it is visible, the user becomes a collaborator instead of a hostage.

This chapter is about the curtain.

## What plan visibility actually is

The definition first.

**Plan visibility is the agent's commitment to surfacing, before it acts, the structure and intent of the work it is about to do, in a form the user can read, adjust, and approve.**

Three load-bearing pieces.

**Before it acts.** Showing the plan after the work is done is not plan visibility. It is a receipt. The whole point is to give the user the option to redirect before any side effects land.

**Structure and intent.** The plan has to communicate both. The structure is the steps. The intent is why those steps add up to what the user asked for. A list of steps with no intent reads like a procedure. A list of intents with no steps reads like a vision document. The plan is the bridge.

**Read, adjust, and approve.** The plan is interactive, not decorative. The user has to be able to see it, change it, and confirm before the agent commits. Anything less is a one-way display.

## Why it matters now

Two reasons.

The first is that agentic work spans more steps than chat-style work, often by an order of magnitude. The user cannot keep the plan in their head if the system doesn't surface it. The longer the chain, the more catastrophic a misinterpretation becomes.

The second is that the plan is where the user gets to be a designer of their own work. Without it, they are reduced to either accepting whatever the agent produces or rerunning the whole task with a different prompt. The plan is the steering wheel. Without it, you can only choose the destination, not the route.

## The patterns that actually work

Five patterns.

**Show the plan before the work starts.** A short, structured preview. Three to seven steps, named clearly, with a one-line description each. The user reads it in ten seconds and either nods or adjusts. This is the move that turns an opaque process into a transparent one.

**Make the plan editable, not just visible.** The user should be able to add a step, remove a step, reorder, or rewrite. The plan that they approve is the plan the agent commits to. Plans that look editable but aren't are worse than ones that don't pretend.

**Update the plan as the agent learns.** Sometimes the agent discovers, halfway through, that the original plan won't work. The strong move is to pause, show the user the revised plan, and ask for re-approval before continuing. Silent plan revision is one of the most disorienting patterns in agentic UX.

**Treat the plan as the contract.** Whatever appears in the plan is what the agent will do. Whatever does not appear in the plan is what the agent will not do. This sounds obvious. It is routinely violated. Agents take side actions, fetch extra sources, modify adjacent files. If the plan didn't promise it, the user didn't approve it.

**Re-confirm before major deviation.** If the agent needs to step outside the plan — escalate scope, touch a system the plan didn't mention, ask for new permissions — pause and ask. The cost of asking is a few seconds. The cost of not asking is the user discovering an unrequested action after the fact.

## When this fails

Three anti-patterns.

**The reveal-after-the-fact.** The agent shows a plan, but only after the work is done. "Here's what I did." The user has no opportunity to adjust. The plan is a transcript, not a contract.

**The frozen plan.** The plan is visible but cannot be edited. The user can see what the agent intends but has no way to change it without restarting from scratch. This is the most common failure in early agent products, often because editability was complex to build.

**The decorative plan.** A plan appears, the user approves it, and then the agent does something different. Whether through model drift or design negligence, the agent's behaviour and the displayed plan diverge. Once users notice, they stop trusting any plan the system shows.

## A worked example

A research agent helps a journalist gather sources for an article on housing policy.

The agent reads the journalist's request and produces a four-step plan: *search recent academic papers on US housing policy 2024–2026; search city-level policy news from three cities the journalist named; pull data from federal housing statistics; produce a summary with at least eight sources, prioritising primary documents.*

The journalist reads the plan in fifteen seconds. They adjust two things: they add "include UK comparisons" as a new step three, and they tighten step four to "at least twelve sources, with city-level coverage balanced across the three cities." They approve.

The agent works. Halfway through, it discovers that the federal statistics database is unreachable. It pauses, surfaces a revised plan: "skipping federal statistics, will use HUD data instead, expected output unchanged." The journalist nods. The agent continues.

When the work completes, the result matches the plan the journalist actually approved. Not the plan the agent originally proposed. The journalist never had to wonder what the agent did or why.

## What this opens up

Plan visibility is the single most leveraged pattern in agentic UX. It compounds with everything else in this primer. With it, every other pattern — progress, error recovery, handoffs, undo — has a structure to live inside. Without it, every other pattern has to compensate for a missing spine.

The case studies in Layer 5 deconstruct several products through this lens. Cursor's agent mode is one of the few products that shipped plan visibility well at launch. Most others are catching up.

If this helps, look at the next time your product takes more than three actions in a row on a user's behalf. If the user can't see the plan before those actions, that's the next sprint.

---

**Run while reading**
- Primary: `design-agent-orchestration / observability-design` — Making the agent's plan and intent legible before action
- Secondary: `design-agent-orchestration / task-decomposition` — Breaking work into steps the plan can show

**Related primer chapters**
- Step-tracking and progress
- Handoffs — agent→user, agent→agent
