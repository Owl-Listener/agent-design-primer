# Undo and reversibility

Every action an agent takes has a reversibility tier. Most products treat them all the same, and that is where harm starts. An agent that uses the same one-click confirmation for moving a file and for sending an email and for transferring money is an agent that has not done the work of understanding what its actions actually cost.

Reversibility is not a feature you bolt on at the end. It is a property of every single thing the system can do, and the design has to make that property visible to the user before they commit, not after they regret.

This chapter is about how.

## What undo actually is

The definition first.

**Undo is the agent's design commitment to making each action's reversibility visible, achievable, and proportionate to the cost of the action, so the user can recover from any agent decision they did not actually want.**

Three load-bearing pieces.

**Visible.** Reversibility has to be evident before the action, not after. A user about to delete a file has the right to know whether the file is recoverable in five seconds, twenty-four hours, or never. The visibility of that fact shapes the decision more than the gate around it.

**Achievable.** A reversibility that requires the user to file a support ticket is not really reversibility. The path back has to be at least as easy as the path forward.

**Proportionate.** Not every action needs a full undo. A casual save can be a quiet checkpoint. A production deploy needs an explicit rollback flow. Matching the reversibility design to the action's cost is the discipline.

## Why it matters now

Two reasons.

The first is that agents are taking more autonomous actions, and the gap between "user asked" and "agent did" is widening. With each step the agent takes alone, the surface area for unwanted actions grows. Undo is the design counterweight to that drift.

The second is that the cost of an unwanted action varies wildly. Most product cultures default to "everything is reversible" or "everything is final," depending on engineering convenience. Both defaults are wrong. The user's experience is shaped by how well the system distinguishes between the two.

## The patterns that actually work

Five patterns.

**Tier the actions by reversibility cost.** Three tiers is enough for most products. *Free* — actions that can be undone instantly with no consequence. Drafts, search history, tentative reads. *Costly* — actions that can be undone but with friction or visible side effects. Sending a message, editing a shared document, modifying a database. *Irreversible* — actions that cannot meaningfully be undone, only mitigated. Deleting permanently, transferring money, sending a legally binding contract. Every action in your product should be tagged with one of these tiers.

**Match the gate to the tier.** Free actions get no gate. Costly actions get a single confirmation, with a clear preview of what will change. Irreversible actions get a hard gate — a confirmation that requires a specific kind of input, like typing a word or waiting through a cooldown. Treating every gate the same trains users to dismiss them all.

**Show reversibility before the action, not after.** A button that reads "Delete (recoverable for 30 days)" is doing real work. A button that reads "Delete" and then a banner that says "actually it's permanent" is doing harm. Surface the reversibility status in the affordance itself.

**Preserve a meaningful undo window.** For costly actions, hold the action in a recoverable state for a real amount of time — long enough for the user to notice and reverse. A five-second toast is theatre. A twenty-four-hour soft-delete is a feature. Match the window to how long the user might need to realise they didn't want it.

**Surface what would be reverted, not just the verb.** "Undo" is a vague promise. "Undo the change to your subscription plan" is a clear one. Especially in multi-step agent work, the undo affordance has to tell the user exactly which thing it will reverse. A blanket undo at the end of a complex chain is rarely what the user wants.

## When this fails

Three anti-patterns.

**Silent irreversibility.** The agent takes an action that cannot be undone, without warning the user that this was the irreversible step. The user discovers it when they go to undo and find no path. This is the most damaging failure because it converts an active mistake into a permanent loss, and the user has no recourse.

**Undo theatre.** A button labelled "undo" that doesn't actually restore the prior state. Sometimes a system bug, more often a design choice to make a destructive action feel softer than it is. Users learn the difference within two or three interactions, and trust collapses.

**Cold-water gate.** Confirmation dialogues on every action, including trivial ones. Users learn to dismiss them on autopilot. By the time the system shows a confirmation that actually mattered, the muscle memory of dismissal has already won.

## A worked example

A coding assistant that can edit files, run scripts, and deploy code.

Single-file edits land in the editor with a per-file undo. No confirmation needed. The user sees the diff, they can revert with one click, they can keep working without friction. Free tier.

Multi-file refactors get checkpointed. Before the agent commits a set of related changes, it creates a named restore point. The change happens. A small banner says "checkpoint saved — revert this whole refactor with one click for the next thirty minutes." Costly tier.

Deletions are soft for twenty-four hours. The file appears to be gone, but is recoverable from a trash folder. The agent surfaces this in the moment: "Moved to trash. Permanent in 24 hours." Costly tier with a clear window.

Deploys to production go through a hard gate. The user has to type the name of the environment to confirm. After the deploy, there is a one-click rollback for the next thirty minutes, after which rollback requires a more involved process. The agent makes the irreversibility tier explicit at the moment of choice.

Same agent. Four different reversibility designs. The user can move fast on cheap actions and slow on expensive ones, and the system tells the truth about which is which every time.

## What this opens up

Reversibility design is the surface where the agent expresses respect for the user's time and judgment. A system with thoughtful undo is a system that has accepted it will sometimes be wrong, and has built the recovery in from the start. A system without thoughtful undo is a system that assumes the user will always want what the agent does, which is the most expensive assumption in product design.

The chapters on high-stakes gates and audit trails build directly on this one. Each of them is a different expression of the same idea: that the system is honest about what it is doing, and the user has a real path to change course.

If this helps, list the ten most common actions your agent takes and tag each one as free, costly, or irreversible. You will probably find at least one action tagged the wrong way. That's the next thing to fix.

---

**Run while reading**
- Primary: `ai-alignment-reasoning / consent-and-agency` — Reversibility as an expression of user agency over agent actions
- Secondary: `design-agent-orchestration / failure-recovery` — Undo as one branch of the broader recovery design

**Related primer chapters**
- High-stakes decision gates
