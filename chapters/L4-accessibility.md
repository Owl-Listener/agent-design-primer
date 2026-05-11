# Accessibility of agent loops

Every chapter in this primer so far has been about access. We have just been calling it other things.

Trust calibration is access to the system's honest belief about itself. Citations are access to its sources. Plan visibility is access to its intent. Gates are access to your own decision. Memory is access to what the system retains about you. The audit trail is access to what it did on your behalf. The entire primer is, secretly, a primer about access. This chapter is about the part of access that the field has been treating as a separate concern, and shouldn't.

This is not the addendum chapter. This is the load-bearing one.

## What accessibility of agent loops actually is

A definition first.

**Accessibility of agent loops is the design commitment that every primitive, pattern, and surface in an agent product is usable by people across the full range of sensory, motor, cognitive, and linguistic variation, with no degraded mode or hidden cost.**

Three load-bearing pieces.

**Every primitive, pattern, and surface.** Not a separate layer bolted onto the end. Every chapter in this primer — streaming, citations, gates, memory, handoffs — has accessibility implications that need to be in the original design, not patched in later.

**Full range of variation.** Vision, hearing, motor control, cognitive load, language, literacy, attention. The variation is wide, and the design has to flex across all of it.

**No degraded mode or hidden cost.** Accessible products do not ship a stripped-down version for some users. The accessibility work is in the main surface. A user with a screen reader, a user navigating with keyboard only, a user reading in their second language — they get the full agent, not a polite subset.

## Why this is not the addendum chapter

Two reasons, and they matter for the framing of this entire layer.

The first is that agent loops introduce new accessibility problems that chat-based AI never had to solve. Token-by-token streaming is hostile to most screen readers. Citation pills get lost in dense documents. Plan-then-progress panels become visual sidebars by default. Multi-agent UIs introduce non-linear surfaces that assistive navigation has to traverse. Each of these is an accessibility problem that did not exist in 2023, and most of them are being shipped without anyone having designed for them.

The second is that the user with the most to gain from a good agent is often the user with the most to lose from a bad one. A user with low vision who can finally read their documents through a voice agent. A user with motor difficulty who can finally book appointments through speech instead of forms. The opportunity here is enormous, and the cost of getting the design wrong is the same as the cost of any other technology that promised access and delivered a workaround.

This is why accessibility is the lens, not the chapter.

## The patterns that actually work

Five patterns. Each one cross-cuts the chapters that came before it.

**Design every primitive for non-visual access first.** If a citation surface only works visually, redesign it. If a confidence signal is a colour with no label, fail the design review. If a progress panel doesn't announce state changes through assistive tech, ship it broken. Non-visual access is not the accommodation. It is the source of truth that the visual surface should be a layered enhancement of.

**Match motion and pacing to user preference.** Streaming output that flashes letter by letter is a sensory event with real costs. Respect the user's reduced-motion settings. Allow the user to switch to chunked or buffered streaming. Don't bury the setting in a preferences pane the user has to find.

**Build for cognitive variation, not for the median.** Plain language by default. Coarse signals over fine ones. Short paragraphs. Confidence labels written in words a tired person can read. The cognitive variation argument is not "make it easy for people with disabilities." It is "make it easy for everyone, because everyone has bad days, distracted days, second-language days, days when their child is sick."

**Design handoffs and tool calls to surface through assistive technology.** When the agent hands off to a sub-agent or calls a tool, the screen reader should hear it, the keyboard-only user should be able to navigate to it, and the user with a cognitive disability should be able to follow the change in state. Most current implementations fail at least one of these.

**Translate, don't just localise.** Agent UX in a second language is not "the same product, different words." The hedging vocabulary, the gate copy, the refusal patterns, the citation labels — all of them need translation that preserves the calibration, not the literal wording. A confidence label that reads "I think" in English and translates to a more confident phrase in another language has been mistranslated, not localised.

## When this fails

Three anti-patterns.

**Accessibility as audit.** The product is built, then run through a WCAG checklist at the end, then patched. The patches are workarounds. The main surface remains designed for one kind of user. This is the most common failure across the entire industry and the one this chapter is most directly trying to displace.

**Visual-only confidence signals.** A coloured pill, a green checkmark, a red border — with no label, no announcement, no fallback for users who can't see them. The signal exists for sighted users only. Half the work is done.

**Chat-only interfaces.** Voice input, no keyboard alternative. Keyboard input, no voice alternative. Touch interfaces with no large-tap-target mode. Locking the user into one modality is the most direct way to exclude them, and most current agent products lock to chat by default.

## A worked example

An accounting agent ships with the same primitives in two parallel surfaces.

In the visual surface, the user sees inline citations as small numbered pills, the agent's plan as a checklist, progress as ticking step indicators, and confidence as a coloured label next to each claim.

In the auditory surface, the user hears citations announced as "claim one, source: Section 4.2 of the IRS guidelines," the plan read aloud with each step named, progress announced when a step completes, and confidence spoken in the same coarse vocabulary the visual surface uses: "sure, I think, I'd verify."

Both surfaces use the same underlying state. Switching between them — visual to auditory, keyboard to touch, English to Spanish — is one click and loses nothing. A user navigating with a screen reader gets the full product, not a reduced one. A user using voice in their car gets the full product, not a different one. The primitives travel.

This is harder to build than visual-default with accessibility patches. It is also the only credible answer for an agent product in a regulated domain in 2026, and probably the only credible answer for any agent product in 2027.

## What this opens up

Accessibility is not the final chapter of Layer 4. It is the lens through which every chapter of every layer should be reviewed. The work of this chapter is to make that lens load-bearing in your team's design process — to move accessibility out of the audit step at the end and into the original primitives at the beginning.

The full inclusive-design layer is in [`inclusive-design-skills`](https://github.com/Owl-Listener/inclusive-design-skills). This chapter is the bridge that says: every other chapter in this primer connects there. Read the relevant inclusive skill alongside the chapter it pairs with, and the work compounds.

If this helps, take any chapter in this primer and ask: how does this pattern serve a user navigating with a screen reader, a user reading in their second language, a user with a cognitive load disability, a user with motor variation? If the pattern doesn't have a clean answer for each, that's a chapter to redesign — not as accommodation, but as the original work it should have been.

---

**Run while reading**

This is the bridge chapter. The runnable companions live in [`inclusive-design-skills`](https://github.com/Owl-Listener/inclusive-design-skills).

**Related primer chapters**
- Streaming and partial output
- Citations and provenance
- Handoffs — agent→user, agent→agent

**From `inclusive-design-skills`**
- `cognitive-load-in-agent-loops`
- `accessible-streaming-output`
- `accessible-citation-patterns`
- `screen-reader-handoff-cues`
