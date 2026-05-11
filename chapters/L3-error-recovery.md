# Error recovery and graceful degradation

Most agents handle errors by retrying silently. Silent retry teaches users that errors don't happen — until they do, and then the user has no idea what went wrong, what was tried, or what to do next.

Error handling is not a defensive layer at the bottom of an agent product. It is one of the primary surfaces. How an agent fails, how it recovers, and how it explains itself in the failure are visible to the user almost every day. A well-designed failure builds trust. A badly designed one collapses it.

This chapter is about designing for the moment things go wrong.

## What error recovery actually is

The definition first.

**Error recovery is the agent's response to a failure in its own work, designed to make the failure legible to the user, preserve what was already done, and offer a path forward.**

Three load-bearing pieces.

**Legible failure.** The user has to know that something went wrong, what it was, and which step it affected. A failure the user cannot see is a failure they cannot work with.

**Preserve what was done.** A failure on step four should not erase steps one, two, and three. Most users have been burned at least once by a system that lost their work because of a partial failure. The strong move is to checkpoint along the way, so a failure costs only the step it actually affected.

**Offer a path forward.** Retry the same way, try a different way, hand off to a human, abandon and start over. The user should never be stranded.

## Why it matters now

Two reasons.

The first is that agentic systems compose tools, and tools fail. Every external API, every model call, every file system operation is a potential failure point. The more capable the agent, the more failure surfaces it touches. Pretending those surfaces don't fail is one way to ship. Designing for when they do is the better way.

The second is that the failure is where the user's mental model of the agent gets revised, hard. A user who experiences a graceful failure leaves with more trust, because the system told the truth and helped them past it. A user who experiences a hidden or messy failure leaves with less, because the system either lied or panicked.

## The patterns that actually work

Five patterns.

**Surface the failure when it happens.** A failure that the user discovers later is a betrayal. The agent should say, as soon as it knows, that something went wrong and which step it was. Even if the agent can retry, even if it can recover, the user benefits from knowing the wobble happened.

**Distinguish recoverable from terminal.** Not all failures are the same. A network timeout is recoverable with a retry. A permission denial is recoverable with a different approach. A model refusal on safety grounds is probably terminal for this attempt. Label them differently, treat them differently, and tell the user which kind they're dealing with.

**Offer a real menu of paths forward.** "Retry," "Try a different approach," "Ask a human," "Stop here and let me handle it." Not a single button that says "retry" and hopes for the best. The user has more context than the agent does about what they actually want to do next.

**Preserve user work across the failure.** Whatever has already been completed should remain. The user should not have to redo step one because step four failed. This requires checkpointing, which requires plan visibility, which is why these patterns chain together.

**Make failure a useful data point.** Logged failures, with the context that caused them, are gold for improving the system. They are also useful to the user retrospectively — "this agent fails on this kind of task" is a meaningful signal for whether to trust it next time. Surfacing failure rates is one of the strongest trust moves a product can make.

## When this fails

Three anti-patterns.

**The silent retry.** The agent tries, fails, tries again, succeeds, shows only the success. The user never sees the wobble. They develop an inflated sense of the system's reliability. When they eventually hit a failure that doesn't recover, the surprise is total.

**The generic failure.** "Something went wrong." No information about what step, what failed, what to do. The user cannot diagnose, cannot decide, cannot recover. This is the most common failure mode in chat-based products because the system was not designed to surface internal state.

**The forget-and-restart.** A failure occurs, and the system loses the entire conversation or task and pushes the user back to start. Everything done so far is gone. The cost of a recoverable error becomes the cost of a complete redo.

## A worked example

A travel-booking agent is mid-task: it has found three flight options and is now trying to book the chosen one when the airline's payment system returns an error.

The agent does not silently retry. It pauses, shows the user a clear message: "The airline's booking system rejected the payment. The card looks fine on our end. This sometimes happens during peak booking times." The agent then offers three paths: retry now, try a different card, save the flight selection and try again later. The flight choice and traveller details are preserved. The user picks "retry now." The booking goes through on the second attempt.

If the second attempt had also failed, the agent would have surfaced a fourth option: connect with the airline's support team, with the flight details and the failure history packaged into the handoff. The user would not have had to restart anything.

Same underlying problem, four possible paths forward, the user never lost their work, and the failure became a moment of trust rather than a moment of frustration.

## What this opens up

Error recovery is the surface where the agent's character under stress becomes visible. A system that fails gracefully is a system the user keeps. A system that fails noisily, opaquely, or destructively is one they replace at the first opportunity.

The chapters on long-running tasks, high-stakes gates, and audit trails all depend on this pattern. Each of them assumes failure is a normal event the system handles well, not an exceptional one that breaks the model.

If this helps, deliberately cause a failure in your product right now — pull the network, hit a rate limit, send a bad input. Watch what your users would see. If you cringe, that's the next thing to fix.

---

**Run while reading**
- Primary: `design-agent-orchestration / failure-recovery` — Designing retry, fallback, and human-handoff for agent failure modes
- Secondary: `system-behavior-shaping / error-personality` — How the agent communicates failure with its voice and tone
