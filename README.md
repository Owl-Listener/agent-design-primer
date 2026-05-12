# agent-design-primer

A primer for **designing AI agents** — written for a discipline that's still forming as I ship this.

Five layers, contributable, opinionated, free. About 30,000 words of patterns, anti-patterns, and case studies, written for product designers now responsible for shipping agentic experiences and looking for more than another blog post. You can also feed it to your favourite AI work partner and they can run you through it, absorb it and guide you through. It is specifically structured to make this easy for them.

This primer is about the *experience users have with agents*: the calibration of trust, the visibility of plans, the design of refusals, the texture of citations. It is not about *agentic design patterns* in the engineering sense (ReAct, reflection, planning loops, tool use, multi-agent orchestration). Those patterns are well documented elsewhere — see Microsoft's [`ai-agents-for-beginners`](https://github.com/microsoft/ai-agents-for-beginners) or Antonio Gulli's *Agentic Design Patterns*. This is the design twin: how the human and the agent meet on the surface.

---

## What's in the primer

**Layer 1 — Foundations** *(inline below)*
What an agent is, the agency spectrum, the mental models users bring, why "chat" is rarely the right surface.

**Layer 2 — Core interaction primitives**
The vocabulary every agent design uses.
- [Streaming and partial output](./chapters/L2-streaming.md)
- [Citations and provenance](./chapters/L2-citations.md)
- [Confidence and uncertainty](./chapters/L2-confidence.md)
- [Refusal patterns](./chapters/L2-refusal.md)
- [Clarifying questions vs assuming](./chapters/L2-clarifying.md)
- [Memory](./chapters/L2-memory.md)
- [Undo and reversibility](./chapters/L2-undo.md)
- [Handoffs](./chapters/L2-handoff.md)

**Layer 3 — Behaviour patterns**
How agents should act.
- [Plan visibility before action](./chapters/L3-plan-visibility.md)
- [Step-tracking and progress](./chapters/L3-progress.md)
- [Error recovery and graceful degradation](./chapters/L3-error-recovery.md)
- [Long-running tasks and latency masking](./chapters/L3-long-running.md)
- [Tool-use transparency](./chapters/L3-tool-use.md)
- [Multi-agent orchestration UX](./chapters/L3-multi-agent.md)

**Layer 4 — Trust, safety, accessibility**
Where the inclusive lens becomes load-bearing.
- [Trust calibration across users](./chapters/L4-trust-calibration.md) — the flagship chapter
- [Hallucination disclosure](./chapters/L4-hallucination.md)
- [High-stakes decision gates](./chapters/L4-high-stakes-gates.md)
- [Audit trails and reversibility tiers](./chapters/L4-audit-trails.md)
- [PII handling visibility](./chapters/L4-pii-handling.md)
- [Accessibility of agent loops](./chapters/L4-accessibility.md) — the lens, not the addendum

**Layer 5 — Case studies**
Real products deconstructed through the primer's lens.
- [Cursor](./case-studies/cursor.md)
- [Claude (artifacts and Computer Use)](./case-studies/claude.md)
- [Perplexity](./case-studies/perplexity.md)

**Appendices**
- [Heuristics for agent UX](./appendices/heuristics.md) — fifteen heuristics, print-and-stick-to-the-wall
- [Anti-patterns](./appendices/anti-patterns.md) — fourteen failure modes with fixes

---

## Who this is for

Three concentric audiences, biggest to smallest.

Product designers asked to design agentic features and unsure where to start. Design engineers and AI PMs who need shared vocabulary with their design partners. Senior designers building org-wide agent UX guidelines.

The primer makes sense end-to-end on first read. Skip around if you already have a specific problem. If you only have an hour, read Layer 1 below and the chapter on [trust calibration](./chapters/L4-trust-calibration.md).

---

## Layer 1 — Foundations

There is no shared definition of "AI agent" yet. We are eighteen months into the wave that brought us tab-complete-that-codes, browsers-that-shop, assistants-that-book-flights, and the word "agent" is doing a different job in every product. So before we go anywhere else, we name what we mean. This vocabulary work is load-bearing for everything that follows.

### What an agent is, and what it isn't

An agent is a system that takes actions in the world, on behalf of a user, to accomplish a goal. It perceives, it decides, it acts, it observes the result, and it loops. That loop, however small, is what makes it an agent rather than a generator.

A model that writes a sentence is not an agent. A model that writes a sentence and then sends it to your boss is. The difference is action, and the consequence that follows.

Almost every difficult design question in this primer changes shape depending on whether you are working with a generator or an agent. A misplaced apostrophe is a typo. A misplaced email is a phone call to HR. The patterns we cover later live in that gap.

### The agency spectrum

Most products do not pick a single point on this spectrum. They pick a range and let the user move through it.

**Suggest.** The agent proposes. The user does the work. Autocomplete is the canonical case. The agent's footprint is small, the user's authority is total. Trust is cheap, because nothing happens without an explicit act of will.

**Review.** The agent drafts. The user approves before any action lands. Most chat-based AI lives here today. The agent does the heavy lifting, the user is the gate. Trust costs more, because the user has to know enough to spot a bad draft.

**Act.** The agent performs the work. The user can intervene during, or correct after. This is where Cursor's agent mode lives, where Devin lives, where most "computer use" demos live. Trust is expensive, because the user is no longer between the agent and the action.

**Autonomous.** The agent runs to completion. The user reviews the result after the fact, sometimes hours or days later. Background research, scheduled writing, overnight code refactors. Trust is paid in advance, when you define the scope and design the rollbacks.

The same product can carry the same model across all four positions, and the design has to stretch with it. A product that ships in "review" mode and quietly slides into "act" mode without changing its UX has just changed its safety profile and not told the user.

### The mental models users bring

People do not arrive at your agent as blank slates. They arrive with a metaphor already loaded, and the metaphor decides what they expect, what they forgive, and what makes them angry.

The five most common metaphors are:

**Tool.** A hammer. Predictable, reliable, doesn't surprise you. Users with this model do not forgive errors. They expect determinism.

**Assistant.** An intern. Useful, eager, makes mistakes you can correct. Users with this model forgive a lot but become impatient at slow learning.

**Colleague.** A peer. Has its own taste, can push back, contributes ideas. Users with this model expect dialogue and feel patronised by templating.

**Oracle.** An authority. Knows things you don't. Users with this model over-trust the output and rarely check it. This is the most dangerous mental model in any high-stakes product.

**Wizard.** Magic. Inscrutable, occasionally miraculous, occasionally broken. Users with this model are delighted by surprise and frustrated by failure they cannot explain.

A well-designed product picks the metaphor it wants to cultivate and reinforces it through the surface, the language, and the failure mode. A poorly designed product picks none, and users land on whichever metaphor first feels right, which is often the one that hurts them most.

### Why "chat" is rarely the right surface

Chat is the default for almost every agent product right now. It shouldn't be.

Chat works for messaging. It works because the metaphor is *transcript*, a record of two people talking. Most agentic work is not a transcript. It is a structured task, a long-running process, a multi-modal artefact, a thing you should be able to scrub through and rewind.

When we put agentic work inside a chat surface, three things happen. The user loses the ability to see the work as a whole. The agent loses the ability to surface its plan and its progress in a structured way. And the conversation itself becomes the artefact, which is rarely what either side actually wanted.

Better metaphors are emerging. **Workspace**, where the agent has a panel and the artefact has another. **Instrument**, where the agent has a control surface tuned for the task. **Environment**, where the agent and the user share a space they both modify.

You will see all three appear in the case studies in Layer 5. For now, hold this loosely. Chat is the default because it was the easiest thing to ship in 2023. Not because it is the right surface for what you are designing in 2026.

### Where to go from here

Now you have the vocabulary. Layers 2 through 4 cover the patterns designers reach for once they know what kind of agent they are building, what level of agency it operates at, what mental model they are cultivating, and what surface they are using. Layer 5 deconstructs three real products through this lens.

If you only have an hour, read this Foundations section and the chapter on [trust calibration](./chapters/L4-trust-calibration.md). Those two together will reorient most of the design decisions you are making this week.

---

## How this primer works with `ai-design-skills`

`agent-design-primer` is a textbook. [`ai-design-skills`](https://github.com/Owl-Listener/ai-design-skills) is a toolbox. They are designed to be used together.

Read a chapter to understand **why** a pattern exists and **when** to apply it. Run the linked skill to **produce a draft** of that pattern for your specific product.

Every chapter ends with a *Run while reading* block pointing at the relevant skill. Every skill in `ai-design-skills` carries a back-pointer to its primer chapter, so the loop closes inside your IDE and on GitHub.

The full mapping lives in [`cross-links.yaml`](./cross-links.yaml) — a single source of truth, machine-readable, editable in one place when skill names change.

### Which repo do I open first?

| Your goal | Start here |
|---|---|
| *Use* AI more effectively as a designer | [`ai-design-skills`](https://github.com/Owl-Listener/ai-design-skills) |
| *Design* AI experiences for your users | this repo |
| Both | this repo, with `ai-design-skills` installed — your agent will load the right skill as you go |

---

## How this primer works with the rest of Owl-Listener

This primer is the human-readable spine. The rest of the constellation:

- **[`designpowers`](https://github.com/Owl-Listener/designpowers)** — the agent design team (10 agents) you point at any of these chapters in practice
- **[`ai-design-skills`](https://github.com/Owl-Listener/ai-design-skills)** — runnable skills paired with primer chapters
- **[`inclusive-design-skills`](https://github.com/Owl-Listener/inclusive-design-skills)** — the inclusive lens; Layer 4 of this primer links here
- **[`designer-skills`](https://github.com/Owl-Listener/designer-skills)** — broader design practice (research, systems, UI) for non-AI work
- **[`agent-ready`](https://github.com/Owl-Listener/agent-ready)** — Figma plugin scoring whether your design files can be read by an agent

If you're new to the ecosystem, start with this primer's Layer 1 above and the `ai-design-skills` quickstart in parallel.

---

## Status

**v0.1** — full spine written, twenty chapters across five layers, three case studies, two appendices. Diagrams are placeholders in v0.1 and will be redrawn in the Owl-Listener visual language for v0.2.

This primer is maintained in public. Patterns will be added as the field surfaces new ones. Case studies will be refreshed quarterly with a dated *last validated* footer. Cross-links will be re-checked as `ai-design-skills` evolves. The version of this primer that exists in 2027 will look different from the one you're reading now — that's deliberate, not a flaw.

Contributions welcome (see [CONTRIBUTING.md](./CONTRIBUTING.md)).

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to propose a new chapter, submit a case study, or contribute an anti-pattern. The [chapter template](./CHAPTER_TEMPLATE.md) shows the structure every chapter follows.

---

## License

This primer is released under [Creative Commons Attribution 4.0](./LICENSE). Quote it, adapt it, translate it, teach with it. Attribution to Owl-Listener appreciated.

---

## A note from the maintainer

We are at a moment when the practice of design is being rewritten. The role of the product designer is shifting to the person who designs the *relationship* between a human and a new kind of intelligence.

This primer will be wrong about some things and right about others, and it will keep evolvingnt. That is the point. The work is to keep moving, in public.

If this helps you, send it to a designer who needs it.
