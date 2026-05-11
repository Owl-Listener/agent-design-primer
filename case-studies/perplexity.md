# Case study: Perplexity

Perplexity matters because it solved one primitive better than almost anyone else: citations. The entire product is organised around the conviction that a claim without a source is not worth showing the user. Whatever else you think of the product, the citation pattern it shipped has become the reference implementation for the field, and the primer's whole citations chapter borrows from it.

It is also a study in what happens when you nail one primitive and have to figure out the others.

## What Perplexity represents

Perplexity is a search and answer engine that treats citations as the central design surface. Every claim it produces is sourced. Every source is openable. The entire visual system orbits around making the connection between claim and source as small a friction as possible.

It is also a useful case study in primitive prioritisation. Some products try to be excellent at everything from launch. Perplexity made a bet on one primitive and built outward from there. The bet paid off. The cost of the bet is visible in primitives the product is still catching up on.

## How Perplexity expresses the primer's primitives

**Citations.** Inline numbered pills next to claims. Hover to preview, click to open in side panel. Source quality differentiated by domain type (academic, news, blog, official). The pattern is the strongest in the field.

**Streaming.** The answer streams while citations populate in real time alongside it. The user sees both the prose and the sourcing emerge together. This is a sophisticated form of streaming where structure and content reveal in parallel.

**Confidence and uncertainty.** Implicit, mostly. Citation density does some of the work — heavily-cited paragraphs feel sturdier than lightly-cited ones. But the product rarely surfaces explicit confidence labels. A user has to infer.

**Hallucination disclosure.** The product reduces hallucination at the source through retrieval grounding. Almost every claim has a source. The cases where it doesn't are not always marked, which is the residual gap.

**Multi-agent orchestration.** Pro features hint at multi-step research and sub-agent behaviour. The visibility into these flows is still developing.

**Memory.** Limited. Conversation history exists. Persistent personalisation is light by comparison to Claude or ChatGPT. This is intentional for a search-style product but worth flagging.

## What Perplexity gets right

Three things, in order of importance.

**The citation pattern is now the field standard.** Inline pills, hoverable preview, click-through to source in a side panel. This is the implementation other products are catching up to. The pattern is small but its design weight is large — it is the surface where the product earned its early trust.

**Source quality is differentiated, not just present.** Domains are coloured or grouped to give the user a sense of whether they're reading academic, news, or aggregator content. The signal is coarse but useful.

**Streaming and citations reveal in parallel.** Most products either stream answers without citations and patch them in later, or hold the citations until the end. Perplexity reveals them together. The user sees the source emerge as the claim emerges.

## What Perplexity could improve

Three patterns where the primer points to gaps.

**Explicit confidence and uncertainty.** A coarse confidence signal — sure, think, verify — would complement the citation density. Right now the product asks the user to do the inference work themselves. For complex queries with mixed-quality sources, an explicit hedge would be honest.

**Plan visibility for Pro multi-step queries.** When the product takes on a longer research task, it could show its plan upfront — what searches it intends to run, what tools it will use, what it will summarise. Some of this is visible. The pattern could be sharper.

**Handling claims without a source.** Some claims come from the model's general knowledge rather than retrieved sources. The product does not always mark these distinctly. The chapter on hallucination disclosure argues that "I don't have a source for this" should be a first-class state. Perplexity has the surface to make it one.

## What to steal

For your own product, four patterns from Perplexity worth borrowing directly.

The inline citation pill pattern, applied wherever your product makes claims that could be sourced. The side-panel source preview, applied wherever you want the user to verify without losing their place. Differentiated source quality, applied to any retrieval-based system. Parallel reveal of answer and citation, applied wherever streaming output includes provenance.

## A note on primitive prioritisation

Perplexity is a useful argument for picking your primitive. The product did not try to be excellent at memory, multi-agent orchestration, computer use, or persistent context. It picked citations and went deep. The cost is visible — competitors with broader feature sets have caught up on other primitives — but the strategy worked. The product earned a place in the field by being the best at one thing.

This is a useful question for any team designing an agent product. Which primitive in this primer is the one your product is most clearly built around? If you can't answer, you may be designing a product that is good at everything and excellent at nothing.

## What this case study opens up

Perplexity is the citation primitive in isolation. Cursor is the agency spectrum. Claude is the chat-as-conversation-not-artefact split, plus computer use. Each of the three case studies is, in some sense, a different primitive showing what it can do when it is treated as load-bearing rather than secondary.

If this helps, ask which primitive your product is built around. Then read the corresponding chapter in this primer alongside the case study above, and look at the gap between where Perplexity, Cursor, or Claude has gone with that primitive and where your product has gone. The gap is your roadmap.

---

**Run while reading**
- Primary: `evaluation / output-quality-rubrics` — Deconstructs an existing AI product against the primer's patterns

**Related primer chapters**
- Citations and provenance
- Hallucination disclosure
