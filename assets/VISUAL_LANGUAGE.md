# Owl-Listener visual language

This is the reference for visual work under the Owl-Listener brand — diagrams, illustrations, deck templates, repo assets, social graphics, anything that needs to feel like part of the family.

When asked to produce a visual artefact for Owl-Listener, this doc is the source of truth. Pull from it.

---

## The synthesis in one sentence

**Geometric clarity in deliberate colour, with visible hand quality.**

The visual language sits between two ends of MC's own work:

- The **MC Dean Percolates Substack cover** — sage and ink, illustrated, intimate, Studio Ghibli / Adrian Tomine register. Geometric underneath the warmth. Display type is heavy and characterful.
- **Jessie and Katey murals** (a reference MC pulls from, not her own work) — saturated geometric pattern, hard-edge, Bauhaus crossed with seventies pop and Op Art. Composed but loud.

The Owl-Listener identity lives between them: warmer than a wireframe, more composed than a mural, geometric like both.

---

## What it is

- Type-led, geometry-led, not illustration-decorative
- Multi-colour by default, never single-ink minimalism
- Composed — even when bold, every element has a place
- Hand-quality permitted and welcomed (not performed)
- Accessible by default (high contrast, no colour-only meaning, screen-reader-ready)
- Confident — opinionated where it sits, never tentative

## What it is not

- Calm Japanese minimalism in single ink (that was a wrong early read)
- Sketch-thin wireframe with restrained whitespace
- Tech-bro neon or AI-cliché gradient
- Decorative illustration without structural purpose
- Sci-fi or robot iconography for anything agent-related

---

## Palette

A six-colour palette pulled from across the cover and the murals. Use four to six in any single composition. Cream is always the ground.

| Role | Name | Hex | Notes |
|------|------|-----|-------|
| Ground | Cream | `#f4eede` | Warm off-white. Background of everything. Not pure white. |
| Primary mark | Ink | `#1a1a1a` | Near-black for type and dominant forms. Not pure black. |
| Calm accent | Sage | `#a0b196` | From the Substack cover. Quiet, conversational. |
| Structural accent | Teal | `#2e9ba8` | From the murals. Cooler, grounded, conveys structure. |
| Hot accent | Magenta | `#d44569` | From the murals. Use for emphasis, "this matters". |
| Warm accent | Yellow | `#e6b637` | From the murals. Use for warmth, progress, attention. |

**Palette rules.**

- Cream is the default ground. Reach for white only if cream genuinely breaks the surrounding context.
- Use ink as the primary mark colour. Other colours are zones, not text.
- Two-tone compositions: ink + one accent on cream. Good for restrained artefacts.
- Multi-tone compositions: ink + three to four accents on cream. Good for diagrams and infographics.
- Saturated mode: ink + five colours, geometric blocks, mural register. Reserved for hero artefacts.
- Never use accent colours for body text. They're for fields, marks, and emphasis.

---

## Geometric vocabulary

Five primitives. Used as the information layer, not as decoration.

- **Stripes** (vertical, horizontal, diagonal) — varied density and orientation. Carry intensity, pace, depth.
- **Half-circles and full circles** — soft anchors. Communicate friendliness, completeness, focus.
- **Hard-edge rectangles and blocks** — confident, structural. Hold colour fields, carry type.
- **Triangles** — directional, signal, arrow-like.
- **Nested forms** (concentric circles, layered semicircles) — depth, memory, accumulation.

**Composition rules.**

- Hard edges where shapes meet. No soft gradients between shape boundaries.
- Geometric forms can vary in size dramatically — small marks next to large fields is correct, not chaotic.
- Hand quality lives in slight imperfection: lines not perfectly aligned, weight variation in strokes, edges that wobble a degree or two.
- Each composition has at least one "still point" where the eye rests.

---

## Typography

**Body and reading type.** Inter, IBM Plex Sans, or another humanist sans. Reserved, generous, accessible. Weight 400–500.

**Display type.** A heavier, more characterful sans. Söhne Breit, GT America (especially Mono or Extended), Founders Grotesk, or similar. The display face is where personality lands. Weight 600–800.

**Pairing rule.** One characterful display face + one quiet body face. Never two characterful faces. Never a serif unless deliberately for an essay surface.

**Setting.**

- Body: 16–18px on screen, line-height ~1.5, generous paragraph breaks
- Display: 28–60px depending on surface, tight line-height (1.0–1.1)
- Captions: 12–14px, all-caps with letter-spacing of about 1.5–2px, used sparingly

---

## Density and spacing

- Generous whitespace as a default. If a composition feels balanced, push the whitespace further before pulling back.
- Eight-point grid for spacing. All margins, gutters, and offsets snap to multiples of 8.
- Diagrams sit on the eight-point grid where possible.
- Hand quality lives in the elements, not in the grid. The grid is rigid; the marks are loose.

---

## Application notes by surface

**Diagrams (information artefacts).** Use cream ground, three to four colours, geometric vocabulary as the information layer. Type in ink at body or display weight depending on diagram scale. Always include `<title>` and `<desc>` in SVG. See `agent-design-primer/assets/diagrams/` for the v0.2 reference set.

**Social graphics (LinkedIn, Substack covers).** Higher saturation acceptable. Closer to the mural end of the spectrum. Display type front-and-centre. Keep the geometric vocabulary disciplined — even a loud graphic should be composed.

**Decks and slides.** Cream ground, ink and one accent per slide as default. Reserve multi-colour for hero slides. Type at the larger end of the display range. Geometric marks as section dividers.

**Repo READMEs.** Mostly type-led with a single hero diagram. Restraint here lets the content carry. Body type in standard markdown rendering.

**Long-form essays (Substack).** Closest to the cover register. Sage and ink as primary, occasional pop of one other accent. Generous whitespace. Display heading once at the top, body type throughout.

---

## Reference designers and projects

Look at when stuck.

- **Jessie and Katey** — for mural-scale geometric pattern, palette, hand-painted texture
- **Adrian Tomine** — for line quality and kitchen-table intimacy
- **Studio Ghibli backgrounds** — for the cover-register warmth
- **Paula Scher** (especially the Public Theater work) — for confident display type, environmental scale
- **Bruno Munari** — for playful imperfection within structure
- **Stefanie Posavec** — for hand-drawn information design at this register
- **Mariana Castilho** — for warm, story-led data visualisation
- **Kenya Hara** — for restraint when restraint is the right answer

---

## Accessibility constraints (load-bearing, not afterthought)

- WCAG AA contrast as the minimum floor for all type
- No colour-only meaning — every colour-coded signal also carries a shape, label, or pattern
- Alt text and `<desc>` on every SVG
- Type sizes generous; minimum body 16px
- Reduced-motion respected in any animated artefact
- High-contrast and dark mode variants of any hero artefact

---

## What changes between v0.2 and v0.3

The diagrams in v0.2 (currently in the primer's `assets/diagrams/`) are SVG, system-font, no hand texture. They are correct in palette and geometry but flat in materiality. The v0.3 redraw moves them into Figma or Procreate, swaps system font for the characterful display face, adds subtle paper-grain texture, and brings the hand-quality the language is asking for.

---

## How to use this doc in future sessions

When MC asks for a visual artefact under the Owl-Listener brand, open this file first. Use the palette as given. Stay inside the geometric vocabulary. Match the density and typography rules. Push back if a request would violate the "what it is not" list.

When in doubt, ask: *would this sit next to the Substack cover and the Jessie-and-Katey murals and feel like part of the same world?*

If yes, ship it. If no, redraw.
