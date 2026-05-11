# Step-tracking and progress

Progress bars in agent products are the most common lie in the field right now. They jump in arbitrary chunks, get stuck at ninety percent for forty seconds, and finish at a moment that has nothing to do with the underlying work. They were borrowed from file-download interfaces, where the percentage actually meant something. In agentic work, they almost never do.

A real progress signal is not about percentages. It is about visibility — what the agent has done, what it is doing now, and what is left to do. The user needs to know where they are, not how much they have endured.

This chapter is about replacing the lie with something honest.

## What progress actually is

The definition first.

**Progress is the visible state of the agent's work-in-progress against the plan it committed to, designed to keep the user oriented without overstating certainty.**

Three load-bearing pieces.

**Against the plan it committed to.** Progress without a plan is just a spinner with extra steps. The plan is the reference frame. The progress signal tells the user where they are within it.

**Visible state.** The user should be able to tell, at a glance, what's done, what's running, and what's next. The signal has to be richer than a single bar and simpler than a debugger.

**Without overstating certainty.** A progress signal that pretends to know how long things will take is a signal that will be wrong, and the user will notice. Coarse pacing — done, running, queued — is more honest and more useful than precise percentages the system cannot support.

## Why it matters now

Two reasons.

The first is that agentic work has variable duration. The same task can take ten seconds or ten minutes depending on the route the agent takes. Users staring at an opaque progress bar will assume the system is broken long before it actually is. They will abort tasks that were a few seconds from completing. They will lose work, and they will lose trust.

The second is that progress is the surface where the agent's plan and behaviour stay in sync, or stop being in sync. If the progress signal still says "step 2 of 4" while the agent is actually deep in a step the plan never named, the user has lost their map. They cannot intervene meaningfully because they no longer know where the agent is.

## The patterns that actually work

Five patterns.

**Show progress against the plan, not against a percentage.** A list of steps with each one in a clear state — done, running, queued, blocked — is almost always better than a horizontal bar. The user can see exactly what's happening and what's coming. They can intervene at the boundary of a step. The plan and the progress are the same surface.

**Surface what is happening right now.** The currently-running step needs more than a label. It needs a small status: "searching three sources, found two so far," "running test suite, 17 of 24 passing." Just enough information that the user knows the agent isn't stuck. Just little enough that the surface stays readable.

**Reveal partial results as they land.** When a step produces a result that's meaningful on its own — a citation, a draft section, a data point — surface it in the moment, not at the end. The user has something to look at, something to feel progress in, something to react to before the whole task completes.

**Allow interruption at the step boundary.** Users should be able to stop the agent between steps without losing what's been done so far. This is harder than it sounds, because it requires the agent to handle partial completion gracefully. But it converts an all-or-nothing journey into a real collaboration.

**Pace the signal honestly.** If the agent is fast, let the signal be fast. If it is slow, let the signal be slow. Don't fake animation when nothing is happening. Don't hide bursts of speed under artificial pacing. Users can tell when the system is theatrical, and the theatricality drains trust.

## When this fails

Three anti-patterns.

**The fake percentage.** A bar that jumps from 30% to 70% to 95% based on unknowable internal milestones. The user has no information they can act on. The percentage is decorative, and once they figure that out, it's worse than no bar at all.

**The eternal spinner.** A single indeterminate animation for the whole task. The user has no idea whether the system is one second from completion or fifteen minutes. They wait, they wait more, they give up. Especially common in chat-based products that haven't built proper step tracking.

**The unstoppable advance.** The agent does its work, the user can see the progress, but there is no way to interrupt. They can only stop the whole task and restart, losing any progress so far. Progress without interruptability is a fancy waiting room.

## A worked example

A coding assistant is asked to refactor a function across three files and write tests for it.

The plan was approved with five steps: *read the existing function and its callers; refactor to the new pattern; update each call site; write tests; run the test suite.*

The user sees the plan as a vertical checklist. Step one completes in two seconds and ticks. Step two takes longer; the user sees "refactoring — function now returns a typed object instead of a tuple." Step three runs across three files; the user sees each call site update as it happens, with a small diff link. Step four produces tests; one of them looks wrong to the user. They tap "pause" between step four and step five, edit the test, then tap "continue." The agent runs the suite. All twelve tests pass.

The user did not have to ask the agent what was happening. The progress signal said it. They were able to intervene at exactly the moment they needed to, on exactly the step they wanted to. The agent did not have to guess at their intent because the structure was on the surface.

## What this opens up

Progress is the surface where plan visibility becomes a felt experience. The plan tells the user what will happen. The progress tells them what is happening. Together they convert agentic work from a black box into a collaborative one.

The chapters on long-running tasks, error recovery, and tool-use transparency all build on this one. Each of them is, in part, about giving the user the right view at the right moment.

If this helps, watch one of your agent's longer tasks run without intervening. Note every moment you wanted to stop, or check something, or know what was happening. Those moments are the next set of design fixes.

---

**Run while reading**
- Primary: `design-agent-orchestration / observability-design` — Surfacing in-flight state of agent work to the user
- Secondary: `design-agent-orchestration / task-decomposition` — Progress hangs on the structure of the decomposed task

**Related primer chapters**
- Long-running tasks and latency masking
