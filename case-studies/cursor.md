# Case study: Cursor

Cursor matters because it was one of the first products to ship the agency spectrum in a single coherent surface. Tab-complete is suggest mode. Inline edit is review mode. Composer and agent mode are act mode. The user moves between them without leaving the editor. The model is the same. The trust temperature is not.

If you want to see most of the primer's primitives expressed in one product, Cursor is the most legible example we have right now. It does not get everything right. It gets enough right that it is worth deconstructing carefully.

## What Cursor represents

Cursor is a code editor with an agent layer that operates at multiple positions on the agency spectrum, with the user moving freely between them. It is the strongest current example of a product that has accepted that the same user, on the same model, on the same codebase, needs different trust calibrations for different tasks.

It is also, structurally, an answer to the chat-as-default failure mode. The chat panel exists, but it is not the artefact. The artefact is the code, and the editor is the surface. The chat is the conversation about the work. That separation is what makes the product feel like an editor with an assistant rather than a chat with code in it.

## How Cursor expresses the primer's primitives

**Agency spectrum.** Tab-complete is suggest. Inline edit, where the user reviews a diff before accepting, is review. Composer, where the agent works across multiple files and shows a checkpoint, sits between review and act. Agent mode, where the agent runs to completion on a multi-step task, is full act. The user picks which mode matches the task. The mode change is visible.

**Plan visibility.** Agent mode shows the plan before it acts. A list of steps with file-level intent, editable before commit. The user reads in twenty seconds whether the agent understood the task. This is one of the strongest plan visibility implementations in any current agent product.

**Streaming.** Code streams in as the agent writes it. But — and this is important — for structured changes the system shows the diff progressively rather than character-by-character generation. The user sees the file change, not the model typing. The granularity matches the work.

**Tool-use transparency.** When the agent runs a command, edits a file, or searches the codebase, it surfaces the call. Inline. The user sees what was done.

**Undo and reversibility.** Per-file undo with git history. Checkpointing on multi-file changes. Anything destructive sits inside the editor's existing undo stack. The user has familiar paths back. The agent does not invent its own undo system — it inherits the editor's.

**Handoffs.** The handoff between modes is light but real. Tab-complete suggesting something can be expanded into an inline edit. An inline edit can be promoted to a composer session. The state travels. The user doesn't restart their thinking.

## What Cursor gets right

Three things, in order of how much they matter.

**The editor is the artefact.** Most agent products are chat windows with code as the output. Cursor inverts this. The code is the artefact. The chat is the conversation. The product feels like an editor that gained an assistant, not a chat that gained a code box. This single architectural choice carries an enormous amount of design weight.

**The agency spectrum is legible.** A user can tell which mode they are in. The friction of each mode matches its consequence. Tab-complete is free. Inline edit is one click. Composer needs a checkpoint. Agent mode shows a plan. The friction is the system telling the truth about what is about to happen.

**Plan visibility before act mode.** The plan is real, editable, and serves as the contract. The agent does not deviate without re-confirming. This is the move that makes act mode feel safe enough to use, which is the move that lets the product climb the agency spectrum at all.

## What Cursor could improve

Three patterns where the primer points to gaps.

**Confidence and hallucination disclosure within code.** The system rarely surfaces uncertainty about a specific code change. Most edits look equally confident. A user has no fast way to tell whether the agent is sure about a refactor or is guessing. Adding a coarse confidence indicator on diffs — sure, think, verify — would land trust calibration where it currently sits implicit.

**Tool-call inputs and outputs, not just events.** The product shows that a tool was called. It is less consistent about showing exactly what was sent and what came back. For high-trust workflows, the full payload should be available on demand. Right now it is sometimes shown, sometimes implied.

**Long-running and background work.** Cursor's agent mode is excellent for interactive work but less polished for genuinely long tasks. The status page, the notification model, the "come back tomorrow" affordance — these are still less developed than the live interaction. Products like Devin and overnight refactor tools live further along this axis.

## What to steal

For your own product, four patterns from Cursor worth borrowing directly.

The chat-is-the-conversation-not-the-artefact split, applied wherever your product has a real artefact and a conversation about it. The agency spectrum made visible and switchable, applied to any product where users have different trust calibrations for different tasks. Plan visibility before act mode, applied universally. Checkpointing on multi-step changes, applied wherever a sequence of agent actions could fail partway through.

## What this case study opens up

Cursor is a partial answer to the question this whole primer is asking. It is what an agent product looks like when the team designing it has accepted that trust is not a feature, it is a temperature, and that the temperature has to vary with the task.

Other current products are catching up to Cursor on these primitives. By the time this primer is in its second edition, Cursor will look like an early version of a broader pattern. For now, it is the strongest single example, and the one most worth reading carefully through the primer's lens.

If this helps, open Cursor (or a similar product you use) and walk through one of your common workflows with this chapter beside you. Note which primitives are present, which are absent, and which are present but not where you expected. That is your team's reading list for the next month.

---

**Run while reading**
- Primary: `evaluation / output-quality-rubrics` — Deconstructs an existing AI product against the primer's patterns

**Related primer chapters**
- Streaming and partial output
- Tool-use transparency
- Plan visibility before action
