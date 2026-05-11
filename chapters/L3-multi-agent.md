# Multi-agent orchestration UX

Most multi-agent products treat the user as if they're working with one big agent. They're not. They're working with a team, and the team needs a manager. The design of that manager — the layer that shows who's doing what, who's accountable, where the costs are landing — is one of the most underdeveloped surfaces in the field.

When you have one agent, the UX problem is "how does the user collaborate with this thing." When you have ten, the problem becomes "how does the user collaborate with a team, while still knowing which agent did what, who to redirect, and what it all cost." The leap is not linear. It is qualitative.

This chapter is about designing the team, not the individual.

## What multi-agent UX actually is

The definition first.

**Multi-agent orchestration UX is the surface that lets a user direct, observe, and intervene in the coordinated work of multiple agents, with visibility into who is doing what, why, and at what cost.**

Three load-bearing pieces.

**Direct, observe, intervene.** The user should be able to delegate, watch, and step in. Most multi-agent products only support delegation. Observation and intervention are usually missing.

**Coordinated work.** The agents are not independent. Their outputs depend on each other, their work runs in parallel or sequence, they sometimes disagree. The coordination itself is part of the experience.

**Who, why, cost.** Three pieces of information. Who is the sub-agent currently working. Why was it chosen for this slice of work. What is it costing — in time, money, compute, or attention. Without these three, the user has no way to make sense of the activity in front of them.

## Why it matters now

Two reasons.

The first is that multi-agent products are no longer rare. Cursor, Devin, Manus, every "deep research" feature, every coding agent that orchestrates sub-agents. The pattern is becoming the norm, and the UX hasn't caught up. Most products show the result and hide the team.

The second is that multi-agent products carry a new failure mode the field has not really named yet. Sub-agents can drift from the user's intent in ways the orchestrator doesn't catch. They can disagree with each other in ways that confuse the output. They can rack up costs the user did not expect. These failures are different from single-agent failures, and they require their own design moves.

## The patterns that actually work

Five patterns.

**Show the team.** The user should be able to see, at any moment, which sub-agents exist, which are active, and what each one is doing. A small panel or sidebar is usually enough. "Researcher — searching 4 sources. Summariser — idle. Writer — waiting for researcher." This converts opacity into legibility.

**Surface coordination, not just output.** When the work flows between sub-agents, show the seams. "Researcher passed 12 sources to Summariser. Summariser produced 3 themes. Writer is drafting around theme 2." The user understands the pipeline, not just the result.

**Signal cost per sub-agent.** Each agent's time, compute, or money cost should be visible. Aggregate it at the top, break it down by sub-agent below. "This task used $4.20 — researcher $2.80, summariser $0.40, writer $1.00." Without this, multi-agent products are pricing surprises waiting to happen.

**Handle disagreement, deliberately.** Sometimes sub-agents reach contradictory conclusions. The orchestration layer should not paper over this — it should surface it. "Researcher found three sources supporting X, two supporting Y. Writer is currently using Y. Want to switch?" The user gets the conflict as data, not as confusion.

**Single throat to choke, optionally.** Even in a multi-agent system, the user should be able to talk to "the agent" as if it were one. The orchestrator handles routing to sub-agents internally. But the user can dig in to a specific sub-agent when they want to. Both surfaces matter. Forcing the user to think in agent-team terms all the time is exhausting.

## When this fails

Three anti-patterns.

**The opaque crowd.** The user knows there are multiple agents — the product page said so — but they cannot see which is doing what. The system feels powerful and unaccountable in equal measure. When something goes wrong, the user cannot tell which agent to blame, which means they blame the whole product.

**The parallel mob.** Sub-agents run in parallel without visible coordination. The user sees a frenzy of activity, finds the result acceptable, and has no idea whether the activity was efficient or wasteful. The cost of running ten agents in parallel when two would have done becomes the user's problem, often invisibly.

**The cost surprise.** The bill at the end is bigger than the user expected because each sub-agent's calls were not surfaced in real time. Especially common in deep-research products where the system fans out to many tools and many model calls. The honest move is to show cost as it accumulates, not after.

## A worked example

A research and writing system helps an analyst produce a market report.

The orchestrator is the surface the user talks to. Behind it, three named sub-agents work in coordination: a Researcher, a Summariser, and a Writer. The user can see all three in a sidebar with their current state.

The user asks: "Produce a five-page report on the European EV charging market." The orchestrator shows the plan. The Researcher runs first — twelve searches across four databases, surfacing fifty-two sources. The Summariser distils them into eight themes, with confidence levels on each. The Writer drafts around the themes, producing a structured report.

At each step, the user can dig in. They can see exactly what the Researcher searched for. They can adjust the themes the Summariser found before the Writer starts. They can pause the Writer mid-paragraph if the tone is wrong.

At the top of the screen, a cost meter ticks up: $0.43 so far, mostly the Researcher's database calls. The user sees they're on track for about $3 total. They keep going.

When the report is done, the analyst trusts it — not because the multi-agent system feels intelligent, but because every step of the work was legible. The orchestration UX did the trust-building, not the model.

## What this opens up

Multi-agent orchestration is the surface where agent products grow from individual tools into systems. The chapters on plan visibility, handoffs, and tool-use transparency all compound here. Multi-agent work is, in some sense, the test that everything else in this primer has been preparing the reader for.

The discipline is young. Most products will redesign their orchestration UX two or three times in the next eighteen months as the patterns settle. If your product is shipping a multi-agent surface now, design for the surfaces in this chapter, not the ones you've seen in current products. Most current products are placeholders.

If this helps, watch your product's next multi-agent task run. Can the user see the team, the coordination, the cost, the disagreement, and the option to dig into any sub-agent? If even one of those is missing, that's the next sprint.

---

**Run while reading**
- Primary: `design-agent-orchestration / agent-role-design` — Designing the roles, boundaries, and visibility of sub-agents
- Secondary: `design-agent-orchestration / task-decomposition` — Routing work to the right sub-agent

**Related primer chapters**
- Handoffs — agent→user, agent→agent
- Plan visibility before action
