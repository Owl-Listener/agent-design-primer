# Streaming and partial output

Watch a user wait for an agent. Watch the moment the first token appears. That moment is doing more emotional work than your entire interface, and you probably haven't designed it.

Streaming feels like a delivery mechanism. It is actually a contract. The agent is telling the user, in real time, that something is happening, that the work is shaped a certain way, that the user can intervene if they want, that the system is alive. Every one of those signals is a design decision. Most products make it by accident.

This chapter is about making it on purpose.

## What streaming actually is

A short definition first.

**Streaming is the progressive reveal of agent output as it is produced, designed to communicate work-in-progress to the user without blocking on completion.**

Three things in that sentence are doing the work.

**Progressive reveal**, because streaming is not just "show the answer faster." It is showing the answer in pieces, in an order, with structure. A token-by-token reveal is a choice. A chunked reveal of structured fields is a different choice. Both are streaming. Neither is automatic.

**Work-in-progress**, because the user is watching the system think. That is a vulnerable state for both sides. A good stream tells the user the system is fine. A bad stream tells them it is broken, or worse, makes them feel the system is performing thinking it isn't actually doing.

**Without blocking**, because the alternative is the spinner. The spinner is the absence of design. The spinner is what you ship when you have not made any of the decisions this chapter is about.

## Why it matters now

Two reasons.

The first is that latency is no longer a fixed cost. Models vary, tools vary, prompt complexity varies. The same query can take two seconds or two minutes. A product that doesn't design for this variance ships either an over-eager interface that flickers, or a leaden one that feels broken. Neither is acceptable when users are doing real work.

The second is that streaming is one of the only places where the agent can express its plan, its uncertainty, and its progress in the same gesture. Done well, it is the densest signal in your product. Done badly, it is noise that obscures what's happening.

## The patterns that actually work

Five patterns, layered.

**Choose the granularity that matches the work.** Token-by-token streaming is correct for prose. It is wrong for structured data, where the user needs to see the whole shape before any field. Chunked streaming, where the agent emits one structured field at a time, is correct for forms and reports. Buffered streaming, where the agent works silently and reveals on completion, is correct for anything where partial output would mislead. Most products pick one mode and apply it everywhere. The strong ones pick per-task.

**Show the structure before the content.** A user who sees "Summary: ... Sources: ... Recommendation: ..." appearing as headers immediately knows what the answer is going to look like. They orient. They start preparing to read. Then the content fills in. This is a small move that changes everything about how a long stream feels.

**Mask latency honestly.** When the system is genuinely working but nothing is appearing yet, fill the time with truthful signals. "Searching three sources." "Reading the document." "Drafting." Not generic spinners. Not fake typing animations on content that's already cached. The user can tell when you are stalling and when you are working, and the trust cost of the former is high.

**Make abort visible at all times.** A stream the user cannot stop is a stream the user cannot trust. The abort button should be present from the first frame and large enough to hit while the eye is reading. This is a safety feature, not a convenience feature.

**Decide what persists after the stream finishes.** The transcript of a stream is not always the artefact the user wants to keep. Sometimes the stream collapses into a finished document. Sometimes it remains as a record. Sometimes parts of it disappear and parts stay. The product that handles this thoughtfully feels considered. The product that doesn't feels like a chatroom that accidentally swallowed the user's real work.

## When this fails

Three anti-patterns.

**The performative stream.** Token-by-token animation on content that's already in memory. The system has the answer, it is showing it letter by letter to feel "AI-ish." Users notice within a week. Trust drops permanently after that.

**The unstoppable stream.** No abort, or an abort buried three menus deep. Especially common in voice products and embedded chat widgets. The user is held hostage to whatever the agent is producing, including bad output they can already see going wrong.

**The mismatched surface.** Streaming structured data, like a spreadsheet or a calendar update, into a chat window character by character. The user gets neither the speed of streaming nor the legibility of structure. The stream undermines its own value.

## A worked example

A user asks an agent to draft a follow-up email to a client after a meeting.

The agent does three things in the first second: it shows a one-line preview ("Drafting a polite, slightly formal follow-up to Maria"), it surfaces the structural skeleton ("Subject: ... Body: 3 paragraphs ... Closing: ..."), and it begins streaming the body.

The skeleton is a chip the user can interact with. If they want a casual tone instead of formal, they tap "tone" and the stream restarts with a new tone, no need to wait for the bad version to finish. The abort button is in the corner the whole time.

When the draft finishes, it doesn't sit in the chat. It collapses out of the transcript and into the user's email composer, ready to send or edit. The transcript shows "Drafted email" as a single line, not the full text. The artefact has migrated to the surface where it belongs.

Same model, same prompt. The streaming pattern is what makes it feel like working with a colleague rather than waiting for a server.

## What this opens up

Streaming is the first surface most users encounter when they meet your agent. The thirty seconds between "I asked" and "I got an answer" set the emotional tone for the whole product. We treat that window as transit time. It is actually the entire first impression.

The chapters on progress, citations, and tool-use transparency all build on streaming. Each of them is, in some sense, a richer form of stream.

If this helps, watch your own product through a slow connection for a day. Most of what you'll want to fix is here.

---

**Run while reading**
- Primary: `model-interaction-design / progressive-disclosure` — Patterns for revealing agent output incrementally with structure and pacing
- Secondary: `model-interaction-design / generative-ui` — Companion for streams that produce interactive surfaces

**Related primer chapters**
- Step-tracking and progress

**From `inclusive-design-skills`**
- `accessible-streaming-output`
