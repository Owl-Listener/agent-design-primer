# [Topic name]

[**The grenade.** Three to five short paragraphs. Open with the thing every designer working on this already feels but hasn't said out loud. Be declarative. Don't hedge. The point is to make the reader nod once, hard, and lean in.]

[Then ground them. Why is this idea harder than people think? What's the failure mode if you ignore it? End the opening section with a one-line transition into the definition.]

This chapter is about how.

## What [the topic] actually is

[A short definition, then expand it.]

**[Topic] is [one-sentence operational definition that someone could quote without reading the rest of the chapter].**

[Two or three short paragraphs that unpack the definition. If the definition has 2–3 load-bearing words, name them and expand each. Keep it concrete.]

[If there is real prior art — academic, industry, foundational — name it here. Don't pretend ideas appeared in a vacuum.]

## Why it matters now

[Why this matters in 2026, specifically. What's changed in the model capabilities, the product surfaces, or the user expectations that make this a live question. Two or three short paragraphs.]

[Optional second paragraph here on user variation. Most agent UX problems get worse when you remember users are not a monolith.]

## The patterns that actually work

[Three to five named patterns. Each one is a bold heading sentence followed by 2–4 sentences of explanation. The patterns should be:]

[- Specific enough that a designer could leave this chapter and start applying them]
[- General enough that they aren't tied to one product]
[- Honest about trade-offs, not just best-cases]

**Pattern one.** [Two to four sentences.]

**Pattern two.** [Two to four sentences.]

**Pattern three.** [Two to four sentences.]

[Optional pattern four and five if the topic warrants it. If you have more than five, the chapter is probably two chapters.]

## When this fails

[Two to four anti-patterns, each with a name and 2–3 sentences. These are usually well-intentioned mistakes, not malicious ones. Be specific about why each fails — the mechanism, not just the outcome.]

**Anti-pattern one.** [Two to three sentences explaining what it is, why designers reach for it, and why it harms.]

**Anti-pattern two.** [Same shape.]

**Anti-pattern three.** [Same shape.]

## A worked example

[One concrete product or scenario. Real if you can, hypothetical if you must. Walk through how the patterns would apply to a specific case. Include at least two different user types if user variation matters here.]

[About 150–250 words. Long enough to feel real, short enough to not become its own chapter.]

## What this opens up

[Two to four short paragraphs that zoom out. What does this chapter unlock for the reader? What conversation should it spark inside their team?]

[Close with activation. The reader should leave needing to talk to someone — a colleague, an engineer, a PM, the designer making this exact mistake right now. Don't give them a tidy conclusion. Give them a reason to act.]

---

**Run while reading**
- Primary: `[plugin] / [skill]` — [one-line description of what running it produces]
- Secondary: `[plugin] / [skill]` — [one-line description, optional]

**Related primer chapters**
- [Chapter title] — [one-line on why this connects]
- [Chapter title] — [one-line on why this connects]

**From `inclusive-design-skills`** *(if applicable)*
- `[skill]` — [what it does for inclusive UX in this domain]

**Reference** *(if applicable)*
- [Author, Year. Title. Source.]

---

## Notes for the writer (delete before publishing)

**Length target.** 1,000–1,500 words. The flagship chapter is a good north star. Shorter is fine if the topic is sharp. Longer means it's probably two chapters.

**Voice.** Write with conviction. Use "you" and "we" more than "I". Prefer narrative paragraphs over bullets. Use coarse signals over false precision (don't say "87% of teams" if you don't have a real source). Don't oversimplify — readers can handle complexity if you earn their trust first.

**Things the primer never does.**
- Never use a brand or person as a punching bag. Critique patterns, not companies.
- Never write something you can't stand behind. If you don't have an answer yet, leave the chapter in drafts.
- Never use ALL CAPS or italics for emphasis. Use bold sparingly.
- Never frame AI as "just a tool." This is a primer about *agents* — write as if the agent is a system worth taking seriously.

**Cross-link requirement.** Every chapter must register in `cross-links.yaml` at the repo root. Add an entry there in the same PR that adds your chapter file. The entry binds your chapter to its primary skill in `ai-design-skills` (or `null` if it's a pure-reading chapter).

**Diagrams and screenshots.** One hero image at minimum, ideally near the top of the chapter or right after the definition. Style guide is in `assets/STYLE.md`. If you can't produce one, leave a placeholder comment and we'll pair on it.

**Filename.** `chapters/L[layer-number]-[short-slug].md`. Examples: `chapters/L2-citations.md`, `chapters/L4-trust-calibration.md`.
