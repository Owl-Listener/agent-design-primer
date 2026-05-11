# Citations and provenance

A claim without a source is a guess pretending to be a fact. Most AI products are full of guesses pretending to be facts. We have built a generation of agents that speak with the confidence of an encyclopedia and the rigour of a magazine quiz, and the citation pattern is where that gap shows most clearly.

The work of citation design is not decoration. It is the visible scaffolding that lets a user decide whether to trust a sentence. When the scaffolding is missing, the user has to assume. They will assume too much, or too little, and either choice is a design failure.

This chapter is about getting the scaffolding right.

## What citations actually are

A short definition.

**A citation is a visible connection between an agent's claim and the source the claim was drawn from, designed to let the user verify or doubt the claim with the smallest possible amount of friction.**

Three load-bearing words.

**Visible.** A citation that exists in the system but isn't surfaced to the user is not a citation. It is metadata. The whole point is the user being able to see, at a glance, whether a claim is grounded.

**Connection.** A citation has to actually link the specific claim to the specific source. A list of references at the bottom of a document is not a citation system. It is a bibliography pretending to be one.

**Smallest possible friction.** Verification is only useful if the user actually does it. A citation that takes seven clicks to open is a citation no one opens. Frictionless verification is the whole game.

The pattern has a long history outside AI. Wikipedia's footnote system is one of the most successful citation patterns ever shipped. Perplexity inherited it. Most other AI products are still figuring it out.

## Why it matters now

Because the alternative to citation is fabrication.

Every agent that synthesises information will, eventually, generate a sentence that sounds plausible and is not true. A citation system is the only honest way for the agent to expose that risk to the user. Without one, the system is implicitly claiming "everything I say is true." With one, the system is saying "here is what I'm claiming, and here is what it rests on. Look for yourself."

The second message is harder to ship and infinitely more trustworthy. As stakes rise — legal, medical, financial, scientific — the gap between the two becomes the difference between a product that helps and a product that harms.

## The patterns that actually work

Five patterns.

**Inline pills, not end-of-document blocks.** A claim and its source should be visible together. Footnotes that require scrolling break the connection. The strongest pattern is a small inline marker (a pill, a number, a dot) that opens a source preview on hover or tap, with the full source one click away. Perplexity is the canonical example.

**Show source quality, not just source presence.** A peer-reviewed paper is not the same as a personal blog. A primary document is not the same as an aggregator. Surface that difference. A coloured pill, an icon, a tier label — anything that lets the user know in half a second what kind of evidence they're looking at.

**Make "I don't have a source for this" a first-class state.** Some claims come from the model's training data, not from a specific document. The honest move is to label them. "Based on general knowledge, not a specific source" is a sentence every agent should be able to render. A product that hides this is not citation-aware. It is citation-cosmetic.

**Pair citation density with claim risk.** A casual summary doesn't need a citation per sentence. A medical recommendation might. A good system varies citation density with the stakes of the claim. A great system lets the user adjust the density themselves, like a microscope's focus.

**Make sources openable, not decorative.** A citation that doesn't actually open the source is theatre. Every pill, marker, and label has to lead somewhere reachable, in one click. The source itself should land in a side panel, not a new tab, so the user keeps their place in the agent's output.

## When this fails

Three anti-patterns.

**Decorative citations.** Pills that look like sources but don't open, or that open a 404, or that point to a paywalled paper without preview. These actively erode trust because the user thinks the system is grounded and discovers later that it isn't. Worse than no citation at all.

**Citation overload.** Every clause linked, every word footnoted, the page becoming visually noisy. Users stop reading the citations because there are too many to scan. The signal collapses into noise.

**Phantom citations.** A citation that does open, but the source doesn't actually support the claim. The agent picked the source for plausibility, not relevance. This is the most damaging failure mode because it looks legitimate at every level except the actual content.

## A worked example

A legal research agent helps an associate prepare a brief on a specific tort question.

Each citation in the agent's output is a small numbered pill, hoverable for a one-line source summary, clickable for a side-panel view of the actual statute or case. Statutes are coloured blue. Court cases are coloured purple. Secondary sources, like law review articles, are grey. Claims drawn from the model's general legal knowledge, with no specific source, are tagged "general — verify before citing in court," in a muted yellow.

At the top of the brief, the agent shows a citation density bar — a thin strip across the document indicating where claims are well-sourced and where they're thin. The associate scans the bar before reading. Where the bar is grey-yellow, they know to interrogate harder.

The associate finishes their work in forty minutes instead of three hours, and trusts the result enough to file. Same model, same query. The citation system is the difference.

## What this opens up

Citations are the most visible expression of a deeper question, which is whether your agent is willing to be checked. A product that hides its sources is a product that wants to be trusted without earning it. A product that surfaces them, prominently and honestly, is a product that has accepted the asymmetry: the user is the final authority, the agent is the helpful subordinate.

That stance, played out at scale, is what builds the kind of trust that survives a hallucination. Without citations, one bad answer collapses the relationship. With them, one bad answer is something the user can identify, correct, and move past.

If this helps, audit your own product right now. Find one claim. Try to verify it. Time how long it takes. The number you get is your citation system's grade.

---

**Run while reading**
- Primary: `ai-alignment-reasoning / transparency-patterns` — Surfacing the agent's sources, reasoning, and provenance to the user
- Secondary: `evaluation / output-quality-rubrics` — Rubrics for evaluating whether claims are well-sourced

**Related primer chapters**
- Confidence and uncertainty
- Hallucination disclosure

**From `inclusive-design-skills`**
- `accessible-citation-patterns`
