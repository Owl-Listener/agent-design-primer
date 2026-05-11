# Diagram briefs for v0.2

This document is for you (the designer redrawing these) and for any contributor producing visuals. Each brief says *what the diagram has to communicate*, *what to emphasise*, and *what would break the design*. The starter SVGs in this folder are conceptual sketches, not finished art. You will redraw all of them.

The visual language across all five diagrams should be calm, sketch-friendly, type-led, accessible by default. See [`STYLE.md`](./STYLE.md) for the working principles.

---

## 1. The agency spectrum

**Lives in:** `README.md` Layer 1, near the agency spectrum section.

**Communicates:** that "AI agent" is not a single thing. It is a spectrum of four positions, and most products span a range of those positions rather than picking one. The cost of trust rises as you move right.

**Must include:**
- Four labelled positions along a horizontal axis: **Suggest, Review, Act, Autonomous**
- A one-line example product anchored to each position (Autocomplete, ChatGPT, Cursor agent, Devin / overnight refactor)
- A signal of trust cost rising from left to right (could be a thickening line, a colour ramp, an explicit label)
- An indication that products span a range, not a single point (e.g., a bracket or band across multiple positions)

**Emphasise:** the spectrum nature. The eye should travel left-to-right and feel the increase in cost.

**Avoid:** treating the positions as four discrete categories with no relationship. Avoid sci-fi or robot iconography for autonomous.

**Starter SVG:** `agency-spectrum.svg`

---

## 2. The L2 primitives map

**Lives in:** Layer 2 chapters, possibly inline in the README as the L2 overview image.

**Communicates:** that the eight Layer 2 primitives are not a flat list. They cluster into thematic groups, and the clusters reveal what each primitive is really about.

**Must include:**
- All eight primitives named: **Streaming, Citations, Confidence, Refusals, Clarifying, Memory, Undo, Handoffs**
- A visual grouping that reveals relationship. Suggested clustering:
  - *Output surface:* Streaming, Citations, Confidence (how the agent communicates results)
  - *Authority surface:* Refusals, Undo, Handoffs (where authority lives between user and agent)
  - *Conversation surface:* Clarifying, Memory (how the relationship accumulates)
- Cluster labels visible but quiet

**Emphasise:** the clusters, not the individual primitives. The reader should walk away thinking "these are the three faces of Layer 2," not "there are eight things."

**Avoid:** a forced symmetry. The clusters are uneven (3-3-2) and that's accurate; do not pad them to balance.

**Starter SVG:** `l2-primitives-map.svg`

---

## 3. The trust calibration model

**Lives in:** `chapters/L4-trust-calibration.md`, near the top.

**Communicates:** that calibrated trust is the middle, not the goal of "more trust." Both poles are failure. Different users sit at different default positions and the design has to flex.

**Must include:**
- A horizontal axis with three named regions: **Under-trust** (left), **Calibrated trust** (middle), **Over-trust** (right)
- Indication that both poles are failure modes (e.g., short labels: "User ignores correct output" left, "User accepts wrong output" right)
- The middle is named as the goal, not as a default state
- Optionally: a marker showing different user types (novice, expert) sitting at different starting positions

**Emphasise:** that "calibrated" is the goal. The middle is wide and earned, not a thin sweet spot.

**Avoid:** drawing this as a bell curve. It is not a distribution. It is a continuum where the middle is the design target.

**Starter SVG:** `trust-calibration-model.svg`

---

## 4. The plan-progress-handoff chain

**Lives in:** Layer 3 chapters, ideally inline once in `L3-plan-visibility.md`.

**Communicates:** that three of Layer 3's patterns are not independent. They chain. The plan creates the structure that the progress display tracks against. The progress state is the thing that travels in handoffs.

**Must include:**
- Three labelled boxes in sequence: **Plan, Progress, Handoff**
- Arrows showing the chain (not just adjacency)
- A note on each arrow saying what travels between the stages. Plan → Progress: "the structure." Progress → Handoff: "the live state."
- A loop back from Handoff → Plan, lightly, to show that handoffs to new collaborators often start with a fresh plan

**Emphasise:** the chain, not the boxes. The reader should understand these as a system.

**Avoid:** making this look like an org-chart flowchart. It is a continuous handoff between three design surfaces, not a series of approval steps.

**Starter SVG:** `plan-progress-handoff-chain.svg`

---

## 5. The five mental models

**Lives in:** `README.md` Layer 1, in the mental models section.

**Communicates:** the five metaphors users bring (tool, assistant, colleague, oracle, wizard) shape what they expect and what makes them angry. The metaphor decides the design problem.

**Must include:**
- All five named: **Tool, Assistant, Colleague, Oracle, Wizard**
- For each: a short label of "what users expect" and a one-line label of "what makes them angry" (or "failure mode")
- Visual differentiation that makes the five feel distinct (not five identical boxes)

**Emphasise:** that these are real, recognisable, and different. The reader should be able to look at the diagram and recognise their own users' mental model in one of the five.

**Avoid:** using literal images of the things (a hammer for "tool," a crystal ball for "oracle"). The diagrams should be type-led and conceptual, not literal-illustrative.

**Starter SVG:** `mental-models.svg`

---

## What good v0.2 looks like

When you have redrawn all five in the Owl-Listener visual language:

- All five are accessible: alt text, screen-reader-readable structure, sufficient contrast, no colour-only meaning
- All five are translatable: any text can be swapped without breaking the layout
- All five are licensable: source files (Figma, SVG) committed alongside the rendered versions
- All five feel like part of the same family, not five different visual styles
- All five can stand alone outside the primer (e.g., as LinkedIn graphics) without losing meaning

The starter SVGs in this folder satisfy none of these criteria fully. They are conceptual sketches. The redraw is the work.
