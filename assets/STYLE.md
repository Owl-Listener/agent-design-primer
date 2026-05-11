# Diagram and asset style guide

This is a placeholder. The v0.2 release will populate it with the primer's full visual style.

For contributors producing diagrams in the interim, here is the working direction.

## Working principles

**Calm, not loud.** The primer is a reference document. Diagrams should support the reading, not interrupt it. Muted palette, generous whitespace, type-led.

**Sketch-friendly.** Diagrams should read at the level of a smart whiteboard sketch, not a marketing illustration. They are explaining something, not selling it.

**Owl-Listener visual identity.** The primer sits alongside `designpowers`, `ai-design-skills`, and `inclusive-design-skills`. Diagrams should feel like part of that family.

**Accessible by default.** No colour-only meaning. All diagrams need alt text. Type sizes generous. Contrast checked against WCAG AA.

## Format guidance

**SVG preferred** for diagrams that benefit from scaling and accessibility. Inline `<title>` and `<desc>` elements for assistive technology.

**PNG acceptable** for screenshots from real products in the case studies. Light annotation in the primer's visual style overlaid where useful.

**Maximum width** of 1200px in source. Render at the size that fits the reading column.

## Diagram inventory needed for v0.2

The following diagrams will land in v0.2.

- The agency spectrum (Layer 1) — a horizontal scale showing suggest → review → act → autonomous with annotated cost-of-trust
- The L2 primitives map — a single visual showing the eight primitives and how they relate
- The trust calibration model (Layer 4, flagship) — over-trust and under-trust as two failure poles with calibrated trust as the middle
- The plan-progress-handoff chain (Layer 3) — showing how the three patterns chain together
- The five mental models (Layer 1) — tool, assistant, colleague, oracle, wizard, each with a quick visual cue

Contributors who want to produce one or more of these are welcome. Open a PR with the SVG and matching alt text.

## Until v0.2 ships

Where a chapter would benefit from a diagram, contributors should leave a placeholder comment in the markdown:

```
<!-- diagram: agency-spectrum-l1 -->
```

The maintainer or another contributor will pair on producing the visual. The primer is fully readable without the diagrams; they enhance, not enable.
