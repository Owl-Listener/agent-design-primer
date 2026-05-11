# Memory

An agent that forgets feels like an amnesiac roommate. An agent that remembers wrong feels like a stalker. The middle is what design has to find, and the middle is harder than it looks.

Memory is the most personal surface in any agent product. What the system retains about a user shapes what it can do for them, what it can offend them with, and what it can be trusted with over time. Get it right and the user feels known. Get it wrong and they feel surveilled, or worse, misremembered.

This chapter is about getting it right.

## What memory actually is

The definition first.

**Memory is the agent's stored representation of past interactions, user-stated preferences, and observed patterns, designed to make future interactions more useful without making them feel intrusive.**

Three load-bearing pieces.

**Stored representation.** Memory is not the agent's ability to read context in the current turn. That's just attention. Memory is what persists across turns, across sessions, sometimes across years.

**More useful.** The whole purpose of memory is utility. A memory that doesn't make future interactions better is a privacy debt with no return. Every piece of stored information has to earn its place by changing what the agent can do.

**Without intrusion.** Memory has to feel like the system knowing you, not the system watching you. The line between the two is largely about transparency and control. Users tolerate enormous amounts of memory when they can see it and edit it. They tolerate almost none when they can't.

## Why it matters now

Two reasons.

The first is that long-running agent products are starting to ship. ChatGPT remembers across sessions. Claude has projects. Cursor has rules. Every coding assistant, every personal assistant, every customer agent is heading toward persistent memory because the utility is real. Without memory, the user has to teach the agent every time. With memory, the agent learns and improves. That difference is the difference between a product the user keeps and a product the user abandons.

The second is that memory is the surface where privacy, dignity, and trust collide. A misremembered fact, a forgotten promise, a surfaced detail from six months ago — these are not technical errors. They are relational ones. A product that gets memory wrong is a product that has hurt the user in a way the user remembers far longer than a bad answer.

## The patterns that actually work

Five patterns.

**Tiered memory.** Not all memory is the same. *Session memory* lasts for the current conversation. *Project memory* persists across sessions for a specific scope — a codebase, a document, a topic. *Persistent memory* lasts across everything the user does with the agent. Each tier has different rules for what's stored, how long it lives, and how it surfaces. Conflating the tiers is the most common mistake. The user thought it was session, the system stored it persistent, and now the agent is using a passing comment as a fixed preference.

**Memory the user can see.** A memory the user cannot inspect is a memory the user cannot trust. The strongest pattern is a memory panel — a place the user can open and read what the agent thinks it knows about them. The panel doesn't have to be in their face. It just has to be findable.

**Memory the user can edit.** Visibility without editability is voyeurism in reverse. Once the user can see what's stored, they need to be able to change it, correct it, or delete it. One click to remove. One click to edit. No friction. No "are you sure" wall.

**Memory that surfaces when it activates.** When the agent uses a piece of memory in its current response, it should say so. A small cue — "remembering: you prefer concise summaries" — that the user can dismiss or override. This is the difference between memory that helps and memory that surprises.

**Default to forgetting unless explicitly remembered.** The strong default for new information is to let it pass. Only the things the user explicitly asks the agent to remember, or that the system has high-confidence learned over many sessions, should persist. The opposite default — remember everything by default — is how products end up with bloated, untrustworthy memory layers full of one-off comments treated as fixed facts.

## When this fails

Three anti-patterns.

**Silent memory.** The agent uses what it remembers without surfacing it. The user gets a personalised response that feels uncanny. They can't tell what the system used or how it knew. Even when the memory is correct, the lack of transparency erodes trust faster than a wrong answer would.

**Sticky memory.** The user has asked the system to forget something, and it keeps coming up. Sometimes a UI bug, often an architectural one — the memory was written in multiple places and only some of them got deleted. The user feels powerless. They were promised control and didn't get it.

**Drift memory.** The system accumulates without bound. Every casual comment becomes a stored preference. Three months in, the agent's model of the user is a tangled mess of context that no longer reflects them. The user can either spend an hour cleaning it or abandon the product. Most abandon.

## A worked example

A coding assistant remembers project context across sessions.

The user opens a project they haven't touched in a month. The assistant greets them with a small cue: "Remembering: this project uses TypeScript strict mode, prefers functional components, has tests in Vitest, and you wanted me to ask before suggesting any new dependencies." The user nods and starts coding.

Halfway through a refactor, the assistant suggests a new dependency. Before it does, a chip appears: "Suggesting `zod` — okay? You asked me to check before this." The user approves once. The assistant remembers that they're now okay with `zod` specifically, not new dependencies in general.

In the sidebar, there's a memory panel. The user can open it any time and see four sections: *project conventions*, *coding style*, *standing instructions*, *recent decisions*. Each item has a small edit pencil and a small trash icon. The panel doesn't follow them around. It's just there when they want it.

The user does not feel watched. They feel known. Same memory architecture, but with the transparency and control built in, the experience inverts entirely.

## What this opens up

Memory is the surface where the agent's relationship with the user accumulates. Done well, it compounds — the agent gets more useful every week. Done poorly, it decays — the user trusts the agent less every week because each interaction surfaces another misremembered or unwanted retention.

The chapters on PII handling, trust calibration, and audit trails all build on memory. Each of them is, in part, about what the system retains and what it does with what it retains.

If this helps, open your product's memory layer and read it through the eyes of the user. Anything you wouldn't want a colleague to know about you, after a week of working together, is something the memory layer probably shouldn't have stored either.

---

**Run while reading**
- Primary: `design-agent-orchestration / state-management` — Designing tiered memory with user-visible scope and controls
- Secondary: `ai-alignment-reasoning / consent-and-agency` — Memory as a consent and control surface for the user

**Related primer chapters**
- PII handling visibility
