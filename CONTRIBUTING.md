# Contributing to agent-design-primer

This primer is opinionated and curated. It moves slowly on purpose — every chapter has to earn its place, because a sloppy chapter weakens the whole resource. That said, contributions are welcome and the maintainer wants this thing to grow.

If you have a chapter idea, a case study, an anti-pattern, or a fix, this guide tells you exactly what to do.

## Before you write anything

Three checks first.

**Read the flagship chapter.** Read [`chapters/L4-trust-calibration.md`](./chapters/L4-trust-calibration.md) end-to-end. That's the shape every chapter follows: grenade opening, definition, why it matters now, patterns that work, anti-patterns, worked example, activation close, footer with run-while-reading skill links and related chapters. If your idea doesn't fit that shape, open an issue first to talk it through.

**Check `cross-links.yaml`.** The map at the repo root lists every chapter and its companion skill in [`ai-design-skills`](https://github.com/Owl-Listener/ai-design-skills). If your topic already exists there as a placeholder, pick it up. If it doesn't, that's fine — you'll add an entry as part of your PR.

**Open an issue first for new chapters.** Bug fixes, typos, broken links, and small clarifications can go straight to a PR. New chapters need a 200-word issue first describing the topic, the layer it belongs to, the patterns you'll cover, and the skill it pairs with. This saves you from writing 1,500 words on something we've already decided not to cover.

## How to propose a new chapter

Open an issue using the "New chapter proposal" template (or, if it doesn't exist yet, follow this shape):

1. **Topic name.** What it is in three words.
2. **Layer.** L1 Foundations, L2 Primitives, L3 Behaviour, L4 Trust/Safety/Accessibility, L5 Case study, or Appendix.
3. **Why this chapter belongs here.** One paragraph. What does it cover that the existing chapters don't?
4. **Patterns you'll cover.** Three to five, named.
5. **Companion skill.** Which plugin in `ai-design-skills`, and what skill within it. If no skill exists yet, propose one.
6. **Prior art.** What you've read or built that informs this chapter. Be specific.

The maintainer will respond within a week with one of three answers: yes go write it, not yet (with reasons), or let's reshape this together.

## How to write the chapter

Use [`CHAPTER_TEMPLATE.md`](./CHAPTER_TEMPLATE.md). It mirrors the flagship chapter's structure and includes inline guidance for each section.

A few principles that matter more than the template:

**Write with conviction.** Hedging makes a primer worthless. If you're not sure of a pattern yet, leave it out. Better to have a short chapter that's sharp than a long one that's mushy.

**Use "you" and "we" more than "I".** The reader should feel like they are sitting across the table from the writer. The voice is direct but warm.

**Earn every word.** Aim for 1,000–1,500 words. If you cross 2,000, the chapter is probably two chapters.

**Don't oversimplify.** Readers of this primer are senior enough to handle complexity. Patronising them is worse than confusing them.

**No punching bags.** Critique patterns, not companies. If a product gets something wrong, name the *pattern* and explain the mechanism. Don't make a brand the villain.

**No "just a tool."** This is a primer about agents. Treat them as systems worth taking seriously, not as toys.

## Diagrams and screenshots

Every chapter benefits from one hero image and one or two supporting visuals. Style guide lives in `assets/STYLE.md`.

If you can produce diagrams in the house style, attach them to the PR. If you can't, leave a placeholder comment in the markdown — `<!-- diagram: agency-spectrum -->` — and the maintainer or another contributor will pair on it.

Screenshots of real products are welcome but credit the source and check the licensing. When in doubt, redraw rather than embed.

## The cross-link requirement

Every new chapter must add an entry to `cross-links.yaml` at the repo root. The entry binds your chapter to its primary skill in `ai-design-skills` and lists any related chapters or inclusive-design skills.

This requirement is not optional. The link map is the spine of the loop between this primer and `ai-design-skills`. A chapter without a map entry breaks the loop.

If the skill you'd point to doesn't exist yet, you have two options:
- Open a paired PR in `ai-design-skills` proposing the skill, link them in the description.
- Set the `primary_skill` to `null` in the YAML if the chapter is a pure-reading one (Layer 1 Foundations is the canonical example).

## Submitting the PR

A complete PR includes:

1. The chapter file at `chapters/L[layer]-[slug].md`
2. The `cross-links.yaml` entry
3. At least one diagram or a placeholder for one
4. A description that links to the original issue
5. A confirmation that you read the flagship chapter and follow its shape

The maintainer will review within two weeks. Reviews focus on:
- **Voice and conviction.** Does the chapter sound certain where it should be and honest where it shouldn't?
- **Pattern fit.** Are the patterns specific, general, and honest about trade-offs?
- **Anti-patterns.** Are they real failure modes, not strawmen?
- **Worked example.** Does it ground the patterns in something concrete?
- **Cross-link integrity.** Is the YAML entry correct and the skill it references real?
- **Length.** Is every word earning its place?

Most PRs go through 1–2 rounds of review. That is normal and is the work that keeps this primer good.

## Smaller contributions are welcome

You don't have to write a whole chapter to contribute. The following are valuable and easy to PR:

- Typo and grammar fixes
- Broken link fixes
- New entries in the appendices (heuristics, anti-patterns)
- Translations of the foundations and flagship chapter
- Better diagrams for existing chapters
- Case study additions to existing chapters (one or two paragraphs)

For these, no issue is needed — open the PR directly with a clear description of what changed and why.

## Code of conduct

Be kind. Argue with ideas, never with people. The space we're working in is genuinely uncertain, and that uncertainty is the point. Disagreement is welcome. Vilification is not.

If a comment or PR makes you feel unwelcome, email the maintainer directly. The Owl-Listener norm is "call people in, not out." We'll do the same here.

## Recognition

Every contributor is named in the chapter footer they wrote, and in the repo's `CONTRIBUTORS.md`. If you'd rather be anonymous, say so in the PR and we'll honour that.

## Questions

Open an issue tagged `question` or email the maintainer.

The primer is a small house. Please come in and help us build it.
