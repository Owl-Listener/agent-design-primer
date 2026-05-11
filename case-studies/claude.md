# Case study: Claude (artifacts and Computer Use)

Claude matters because it ships two strong, opposite expressions of agentic UX inside the same product. Artifacts is a careful step away from chat as the artefact. Computer Use is a careful step into full act mode on the user's own machine. Each one is a different bet about what agentic work should feel like, and reading them together is more instructive than reading either alone.

This case study deconstructs both, through the primer's lens.

## What Claude represents

Two surfaces, two design philosophies.

**Artifacts** is the move that says: when the model produces something substantial, it should not live inside the chat transcript. It should have its own panel. It should be editable, persistent, and addressable. The chat becomes the conversation about the work. The artefact becomes the work.

**Computer Use** is the move that says: when the user wants the agent to take real action in the world, the agent should be able to see what the user sees and act on the user's behalf. It is the most direct expression of full act mode in any current consumer product. It is also the one that exposes the most unfinished design problems in the field.

Both are research previews, and both are improving. The patterns they ship are worth reading even when the implementations are still rough.

## How Claude expresses the primer's primitives

**Artifacts — the architecture as a primitive.** The split between chat and artefact is itself a design pattern. The chat handles the conversation. The artefact holds the persistent output. The user can edit either. The model can update either. The two surfaces stay in sync without forcing the user to scroll a transcript looking for the actual work.

**Artifacts — versioning.** Artefacts have version history. The user can compare versions. This is a quiet but important application of audit and reversibility within a conversational product.

**Computer Use — plan visibility.** Before acting, the agent describes what it intends to do. The user can interrupt. This is plan visibility in a more difficult setting than Cursor's, because the agent is about to operate the user's mouse and keyboard, and the consequences are immediate.

**Computer Use — tool transparency.** Each action — clicking, typing, scrolling, opening — is visible as it happens. The user can watch the agent work. This is the strongest expression of "the work is on the surface" in any consumer product.

**Computer Use — gates.** Destructive actions trigger explicit confirmation. The agent does not silently install software, delete files, or make purchases without checking. The gate vocabulary is still under development, but the principle is there.

**Memory — Projects.** Project-scoped memory lets the user have persistent context for a topic without leaking it into other conversations. The tiering of session, project, and persistent memory matches the primer's recommendation closely.

## What Claude gets right

Three things, in order of importance.

**Artifacts is a structural answer to "chat is rarely the right surface."** The product accepted that the chat metaphor was not enough for substantial outputs and shipped a second surface that the chat orbits around. This is, on its own, one of the most consequential design moves any chat-based AI product has made.

**Computer Use exposes the work.** When the agent acts on the user's machine, the user can see it happening. The agent does not retreat into a black box and emerge with a result. The screen is the surface. The user is the witness. This is more transparent than most enterprise automation tools.

**Memory is tiered and visible.** Projects, conversations, and the broader memory layer are distinct, and the user can see what is stored where. The visibility is imperfect — finding specific memory entries can be harder than it should be — but the tiered architecture is correct.

## What Claude could improve

Three patterns where the primer points to gaps.

**Streaming inside chat for long structured outputs.** Even with artefacts, much of the agent's output streams as text in the chat. For genuinely long, structured outputs, the streaming experience could move from "letters appearing" to "structural sections arriving." Cursor's diff-progressive pattern is a relevant comparison.

**Computer Use's confidence and disclosure.** When the agent operates on the user's screen, the user wants to know how confident the agent is about what it is about to click. Right now this is mostly implicit. A coarse confidence label on planned actions — sure, think, verify — would land trust calibration in real time, when it matters most.

**Audit trails for the user, not just the conversation.** A user who has had hundreds of conversations with Claude has no easy way to ask "what did the agent do for me last month." Conversations are searchable. Actions across conversations are less so. As the product scales, a user-facing audit layer becomes more valuable.

## What to steal

For your own product, four patterns from Claude worth borrowing directly.

The chat-orbits-artefact pattern, applied wherever your product produces a substantial output that the user will iterate on. Tiered, named memory with visible scope. Per-action visibility when the agent operates externally. Versioning on any user-editable agent output.

## A note on the tension between the two surfaces

Artifacts and Computer Use are opposite bets. Artifacts says: the agent's work should be carefully separated from the conversation, and the user is in control of editing it. Computer Use says: the agent should operate the user's environment directly, with the user watching.

Both can be right. The strongest agent products of the next few years will probably ship both — careful, structured output for substantive work, plus the ability to act in the world for ephemeral tasks. The skill is knowing which mode applies to which task and making the boundary clear.

## What this case study opens up

Claude is two case studies in one. Read alongside Cursor, the contrast is instructive. Cursor is a single editor with an agent layered through it. Claude is a chat with two different agent expressions on either side. Both succeed. Neither fully answers the design question. Both push the field forward.

If this helps, open both Artifacts and Computer Use and run the same task through each. Note which feels safer, which feels faster, which feels more honest about what is happening. That comparison is your team's read on the agency spectrum debate.

---

**Run while reading**
- Primary: `evaluation / output-quality-rubrics` — Deconstructs an existing AI product against the primer's patterns

**Related primer chapters**
- Plan visibility before action
- High-stakes decision gates
- Memory — session, persistent, scoped
