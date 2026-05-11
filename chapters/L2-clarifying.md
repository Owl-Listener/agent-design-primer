# Clarifying questions vs assuming

Most agents either ask too many questions or none. The middle is rare, and the middle is the whole skill.

The pattern shows up everywhere. A user asks for "a meeting next week" and the agent either fires off six questions about date, time, attendees, duration, location, and topic, or it picks all six defaults silently and books something the user has to undo. Either failure mode kills the value of the interaction. The first one feels like an interrogation. The second one feels like a stalker who made plans for you.

There is a small kingdom of design work between those two failure modes. This chapter is about how to live in it.

## What clarifying actually is

A definition first.

**A clarifying question is the agent's request for the minimum information it needs to act well, asked at the moment it can change the outcome and not before, with as few questions as the situation honestly requires.**

Three load-bearing pieces.

**Minimum information.** The agent should ask only for what it cannot reasonably infer. Everything it can default to, it should. Asking for things you could have guessed is the most common failure here.

**At the moment it can change the outcome.** A question asked too early feels like paperwork. A question asked too late feels like the agent already started the wrong thing. The right moment is just before the agent commits to an action that the user would want to influence.

**As few as the situation honestly requires.** Honestly is doing work in that sentence. Sometimes the situation requires zero questions. Sometimes it requires three. Hiding that count to seem efficient is dishonest. Inflating it to seem thorough is wasteful.

## Why it matters now

Because the difference between an agent that helps and an agent that hinders is mostly in this design surface.

A user comes to an agent with a partial intention. The agent has to decide whether the partial intention is enough to act on, whether to ask, and how much to ask. Get that decision right and the user feels understood. Get it wrong and the user does the work twice — once to ask, once to fix what the agent produced.

The other reason is that this surface is where the agent's mental model of the user becomes visible. An agent that asks a good question is signalling "I think you care about this dimension." An agent that doesn't ask is signalling "I think I know what you want, and here's what I'll do unless you stop me." Both signals shape trust. Both are design choices, even when they look like defaults.

## The patterns that actually work

Five patterns.

**Ask early, ask once.** If you need a piece of information to do good work, ask for it before you start, not after the user has waited. A clarifying question two seconds in is a small friction. A clarifying question two minutes in is a wasted journey. And never ask twice — if the user already gave you something, use it.

**Ask the question that changes the answer.** Not all dimensions matter equally. For a flight booking, dates change the answer. Seat preference rarely does. Ask about the dates, default the seat. The skill is knowing which dimensions are pivotal and which are housekeeping, and only surfacing the pivotal ones.

**Show your defaults, let the user override.** Instead of asking, declare. "I'll book economy, direct flights, between 9am and 5pm. Tap any of these to change them before I search." This converts five questions into five chips. The user can scan in two seconds and override what they care about, ignore the rest. This is the move that separates intermediate agent design from advanced.

**Let the user see what you assumed.** Even when you didn't ask, surface the assumptions you made. "Searching based on your home airport and your travel history." A user who sees the assumptions has the option to correct them. A user who doesn't see them has to discover them through the wrong output. The first feels collaborative. The second feels like a mistake to fix.

**Choose multi-turn or upfront based on the work.** For exploratory, conversational work, ask one question at a time and let the dialogue shape the path. For transactional, high-stakes work, ask everything upfront in a structured form. Mixing the two is a common failure. A travel booking is not a brainstorm. A brainstorm is not a form.

## When this fails

Three anti-patterns.

**The interrogation.** Six questions in a row before any work happens. Often the result of an agent that has not been taught to default. Users hate it because every question is a vote of no-confidence in their original message. They gave you the prompt for a reason.

**The silent assumption.** Zero questions, all defaults, often wrong. The user gets a result that's close to what they wanted but off in one or two ways that matter, and now has to debug what the agent assumed. This is the most common failure in chat-based products.

**The decoration question.** Asking something that doesn't actually change what the agent will do. "What's the purpose of this meeting?" before scheduling. The agent will book the same slot regardless. The question wastes the user's time and signals that the design hasn't thought about what to ask versus what to skip.

## A worked example

A travel-booking agent. The user types: "Book me a flight to my parents next weekend."

The agent infers, defaults, and shows its work. "Searching SFO to Chicago O'Hare, departing Friday morning, returning Sunday evening. Economy, direct flights, under $400 if possible. Three quick choices below — tap any to adjust before I search."

The "quick choices" are three chips: *dates*, *budget*, *non-stop only*. The user taps *dates* because they actually wanted Saturday to Tuesday, not Friday to Sunday. The chip opens a small date picker. The user adjusts. They tap "search."

In that one exchange, the agent asked zero questions but made every assumption visible, made every assumption editable, and waited for the user to confirm before committing. Same intent, no interrogation, no wrong booking. The user feels like the agent understood them. The agent did not understand them — it surfaced its assumptions and let the user correct the one that mattered.

That's the whole skill.

## What this opens up

The decision of when to ask is one of the most consequential design choices in any agent product. It shapes the feeling of the whole interaction. An agent that asks well feels like a colleague. An agent that asks poorly feels like a bureaucrat. An agent that doesn't ask at all feels like a careless friend who keeps making your plans for you.

The chapters on memory, plan visibility, and tool-use transparency all build on this one. Each of them is, in part, a different way of letting the user see what the agent is going to do before it does it, so that the clarifying question is implicit in the surface rather than imposed on the conversation.

If this helps, audit the last ten clarifying questions your product asked. For each one, ask: did the answer actually change what the agent did? If the answer is no, that question is decoration.

---

**Run while reading**
- Primary: `model-interaction-design / mixed-initiative-flow` — Deciding when the agent asks vs assumes vs surfaces its assumptions
- Secondary: `prompt-architecture / system-prompt-structure` — Encoding clarification behaviour in the system prompt
