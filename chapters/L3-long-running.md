# Long-running tasks and latency masking

We learned to design for tasks that take seconds. We are now designing for tasks that take hours. The interface for an hour-long task is not a longer spinner. It is a different surface entirely.

When an agent's work spans minutes, the user can sit and watch. When it spans an hour, they have to walk away. When it spans a day, they need a way to find their way back. Each of those modes carries different design requirements, and most products are still applying the spinner pattern to all three.

This chapter is about the surfaces a long task actually needs.

## What long-running design actually is

The definition first.

**Long-running task design is the surface and behaviour of an agent task that exceeds the user's willingness or ability to wait at the screen, designed to let the user leave, return, intervene, and trust the result without supervising the entire process.**

Three load-bearing pieces.

**Exceeds willingness or ability to wait.** The threshold is not fixed. For some users and some tasks, two minutes is too long. For others, an overnight job is normal. The design has to accommodate both.

**Let the user leave.** A long task that requires the user's attention the entire time is not a long task. It is a short task you ran badly. The whole point is that the user can leave.

**Return, intervene, trust the result.** The path back is as important as the path forward. The user has to be able to find the task again, see what's happened, adjust if needed, and accept the output with the same confidence they would have if they had watched the whole thing.

## Why it matters now

Two reasons.

The first is that the long-running surface is where agents start to feel less like chat partners and more like colleagues. A colleague doesn't ask you to sit and watch them while they work for two hours. They start the work, give you a sense of when it'll be done, and find you when it's ready. The products that nail this feel adult. The ones that don't feel like demos.

The second is that long-running work is where cost, time, and risk all compound. A bad task that takes ten seconds is a non-event. A bad task that takes ten hours is a real loss. The design has to make the user feel in control across the full duration, not just at the start and the end.

## The patterns that actually work

Five patterns.

**Decide foreground or background, explicitly.** Some tasks need the user's tab open. Most don't. The strong move is to ask the user which mode they want, or to default to background and tell them how to find the task again. Tasks that quietly require the tab to stay open are the most common cause of lost work in long-running products.

**Signal cost before commitment.** "This will take about thirty minutes" or "this is likely to run overnight" or "this consumed two dollars of compute on average for similar tasks." Whatever the relevant cost is — time, money, attention — surface it before the user commits. The user can decide whether to proceed, schedule for later, or scope down.

**Notify when state changes meaningfully.** Not for every step. Notify when the task completes, when it fails, when it needs the user's input, when it discovered something unexpected. The notification surface — push, email, in-app, ambient — should match the user's relationship with the product. A coding agent might notify via the IDE; a research agent might email. Match the channel to the workflow.

**Build a status page and make it findable.** Long-running tasks need a home. A place where the user can return any time and see where their tasks are. Running, queued, completed, failed. Most products skip this because their early tasks were short. As tasks get longer, the lack of a status page becomes acute.

**Allow mid-flight intervention.** The user should be able to come back during the task and adjust scope, cancel, or pause without losing what's been done. This is harder than it sounds because it requires the agent to checkpoint along the way. But it is the move that converts a long task from a black box into a real collaboration.

## When this fails

Three anti-patterns.

**The hostage UI.** The user is locked into the tab while the task runs. They can't navigate away, can't close the browser, can't sleep their laptop. The system was not built to survive disconnection, and so it imposes that constraint on the user. This is the single most common failure in early agentic products.

**The amnesiac restart.** The user closes the tab, comes back, and the task is gone. No record, no result, no way to find it. The system never had a persistent representation of the work. Trust collapses on first occurrence.

**The silent overrun.** The system said thirty minutes. It has been ninety. No update, no notification, no signal that anything is wrong. The user is left to wonder whether to wait, cancel, or restart. Long-running tasks need explicit signalling when they exceed their expected time.

## A worked example

A code-refactor agent is asked to migrate a legacy module to a new API. The agent estimates the work at four hours.

Before starting, the agent surfaces the cost: "Estimated four hours. About $12 of compute. Affects 47 files. I'll create a draft pull request when done. You'll get a Slack notification, and you can check the status at any time at /tasks/3284."

The user kicks it off at 5pm and closes their laptop. At 8am, they wake to a Slack notification: "Refactor complete. Draft PR ready for review. 47 files changed. Six tests previously passing now fail, with suggested fixes attached." They open the PR, review the changes, accept the suggestions on the failing tests, and merge.

At any point during the night, the user could have opened the status page and seen exactly which file the agent was working on, paused the task, or scoped it down. They didn't need to. The fact that they could is what made closing the laptop feel safe.

Same model, same task. The long-running design is the difference between "this works" and "I trust this."

## What this opens up

Long-running task design is the surface where agentic products grow up. It is where they stop feeling like demos and start feeling like infrastructure. The chapters on error recovery, audit trails, and handoffs all compound here, because a long task touches all three concerns within its lifetime.

If this helps, identify the longest task your product currently runs. Ask whether the user can walk away from it, return to it, and trust the result. If any of those three is a "not really," that's the next sprint.

---

**Run while reading**
- Primary: `design-agent-orchestration / state-management` — Persisting agent state so the user can leave and return
- Secondary: `design-agent-orchestration / observability-design` — Status pages and notifications for tasks that span time

**Related primer chapters**
- Step-tracking and progress
