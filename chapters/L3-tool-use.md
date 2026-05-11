# Tool-use transparency

An agent is a model plus a set of tools it can use. Most products show only the model. The tools are where the real work and the real risk live, and hiding them is the most common way a smart-looking agent becomes a dangerous one.

When the user sees "the agent did the research," they are imagining the model thinking. What actually happened is that the agent searched the web four times, queried a database, called an internal API, and sent an email. Each of those is a real action with real consequences, and each of them is invisible by default.

This chapter is about making them visible.

## What tool-use transparency actually is

The definition first.

**Tool-use transparency is the agent's visible disclosure of the external actions it takes during its work, including which tools were called, with what inputs, with what outputs, and under what authority.**

Three load-bearing pieces.

**Visible disclosure.** Tool use happens whether or not the user sees it. The question is whether they can. A system that calls tools silently is making decisions on the user's behalf without their consent or knowledge.

**Which, with what, with what, under what.** Four pieces of information: the tool identity, the inputs, the outputs, and the authority. All four matter. A tool name without inputs is a vague claim. A tool with inputs but no outputs is a leak. A tool with all three but no authority context is a side door.

**During its work.** Transparency in the moment is far stronger than transparency after the fact. The user should see the tool calls as they happen, with the option to dig in further, not have to reconstruct them from a log they didn't know existed.

## Why it matters now

Two reasons.

The first is that tool use is the surface where agents take real-world actions. Reads are increasingly fine. Writes are increasingly consequential. Sending emails, modifying records, transferring money, deploying code — every one of these flows through a tool call. Hiding that call is the design equivalent of hiding a signature.

The second is that tool use is where the line between assistant and agent actually lives. A model that only generates text is an assistant. A model that calls tools is an agent, because it can affect the world. Treating tool use as an implementation detail rather than a design surface is what makes the boundary feel arbitrary to users — they don't know which actions they should have approved.

## The patterns that actually work

Five patterns.

**Surface tool calls as they happen.** In the agent's progress display, show each tool call as a discrete event with a short, human-readable description. "Searching the web for housing policy 2024." "Querying customer database for account 1284." "Sending email to billing@acme.com." The user reads in real time what the agent is doing in the world.

**Show inputs and outputs on demand.** The agent's surface display can be summary-level. But the user should be able to click into any tool call and see exactly what was sent and what came back. This converts a vague claim into an auditable fact. Especially important for any tool that touches user data.

**Differentiate read tools from write tools, visually and in permissions.** Reads inform the agent. Writes change the world. The user's mental model of the difference is critical, and the design should reinforce it. A read can pass quietly. A write should announce itself, and possibly ask permission, depending on its consequence.

**Treat tool calls as citations.** When the agent produces a claim that came from a tool, link the claim back to the call. "Your account has three open tickets" should link to the database query that returned that count. This closes the loop between the agent's output and the tools that supported it.

**Allow per-tool permissions.** The user should be able to say "you can read my email, you can summarise documents, but ask before you send anything." Granular tool permissions match real user intent. Bundled permissions — "trust this agent with everything" — are the source of almost every overreach story.

## When this fails

Three anti-patterns.

**Invisible tool use.** The agent calls a tool, the user has no idea. They see only the output, which they interpret as the model's knowledge. When the tool was wrong, or the call was inappropriate, the user has no way to diagnose because they didn't know the call happened.

**Bundled permissions.** One initial consent grants the agent access to all available tools, with no ongoing visibility or per-action authority. The user said yes once, weeks ago, and is now surprised by what the agent is willing to do.

**Tool theatre.** The agent surfaces tool use that didn't happen, or shows tool calls that don't correspond to its actual behaviour. Sometimes a bug, sometimes a copy-writing choice to make the agent feel more thorough. Users discover the gap quickly, and trust drops.

## A worked example

A research agent helps a strategist prepare a competitive analysis.

The agent's plan was approved with four steps. As it runs each step, the user sees the tool calls inline.

Step 1: *"Searching the web — 'Acme Corp pricing 2026'"* and *"Searching the web — 'Acme Corp product comparison'"*. Each search has a small expandable section showing the top results.

Step 2: *"Reading three internal strategy docs — STRATEGY-2024, COMP-Q3, COMP-Q4"*. Each document name is clickable. The user can confirm the agent read the right ones.

Step 3: *"Calling the pricing database — query: SELECT * FROM competitor_prices WHERE updated > '2026-01-01'"*. The query is visible. The result count is visible. The user knows the agent used real, fresh data.

Step 4: *"Drafting summary. Sending to no external recipient."* The agent makes explicit that no email or external action will fire from this step.

The output the agent produces is a competitive analysis with inline citations that link back to the specific tool call that supported each claim. The strategist trusts the result not because the agent feels authoritative but because the work is visible.

## What this opens up

Tool-use transparency is the surface where the agent stops being a black box and starts being a colleague. Once the user can see what the agent is doing, they can trust it, correct it, and extend its authority intentionally. The chapters on plan visibility, citations, and high-stakes gates all build on this one — each is, in part, about making more of the agent's internal behaviour visible to the user.

If this helps, list every tool your agent can call. Then ask: for each one, can the user see when it's called, what was sent, what came back, and which ones they've granted permission for. The gaps are the next layer of work.

---

**Run while reading**
- Primary: `ai-alignment-reasoning / transparency-patterns` — Surfacing tool calls, inputs, outputs, and authority to the user
- Secondary: `prompt-architecture / constraint-specification` — Specifying when and how the agent uses each tool
