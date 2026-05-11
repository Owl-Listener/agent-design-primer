# PII handling visibility

An agent that handles your personal data without showing you which data, when, and where it went, is asking you to trust a system that has not earned the trust.

Most agent products were built on top of an old privacy contract — sign once, agree to everything, hope it goes well. That contract was strained when applications were static. It is broken when applications are agents reaching into email, calendar, files, browsing history, and the model's own memory layer in the same minute. The user needs to see what is being touched, in real time, by name.

This chapter is about that surface specifically.

## What PII visibility actually is

The definition first.

**PII visibility is the user-facing surface that shows what personal data an agent has accessed, when, where it went, and how the user can adjust or revoke that access.**

Three load-bearing pieces.

**User-facing.** Not the privacy policy. Not the data export under request. A visible, navigable, daily-use surface that lives in the product where the user works.

**What, when, where.** Three answers at once. What data the agent touched. When it touched it. Where the data went after — into memory, into a log, into a tool call, into a third-party API. A surface that answers only one or two of these is partial.

**Adjust or revoke.** Visibility without control is voyeurism flipped around. The user has to be able to act on what they see — remove a piece of data, narrow a permission, delete a record.

## Why it matters now

Two reasons.

The first is that agents read enormous amounts of personal context. A coding assistant reads your repos. A scheduling assistant reads your calendar. A research agent reads your documents and browsing history. The model holds it in working memory; the system sometimes persists slices of it; the tools the agent calls sometimes ship parts of it elsewhere. Every one of those moves is a privacy event, and most products surface none of them.

The second is that PII visibility is the surface where trust accumulates or evaporates over time. A user who can see their data flow through the system tolerates more capability, because they can verify the boundaries. A user who can't see it ends up either over-restricting the agent or quietly abandoning the product. The visibility is what makes the trust durable.

## The patterns that actually work

Five patterns.

**Surface what was read, in real time.** When the agent reads from your email, calendar, documents, or browsing context, show it. A small cue in the surface — "reading 3 emails from this thread" — that the user can dismiss or click into. The cost is small. The trust gain is large.

**Show where the data landed.** Reading is one event. Storing is another. Sending the data to an external tool is a third. The user should be able to tell which happened. "Read your calendar. Did not store." "Read your draft. Stored in project memory." "Read your message. Sent excerpt to third-party translation API." Three different events with three different privacy weights.

**Time-stamp every access.** A complete log of what the agent saw and when. Searchable. Filterable. The user opens it whenever they want to verify "did the agent really read that document last Tuesday." The audit chapter covers the broader trail; this is the privacy-specific subset.

**Allow per-data-type revocation.** "Stop accessing my calendar." "Forget what I told you about my home address." "Don't send anything to that third-party tool." Granular revocation is the user's only meaningful control over an agent's reach. Bundled revocation — "disconnect this agent" — is the nuclear option that users will reach for when granular controls are missing.

**Make right-to-be-forgotten a real button.** Most products treat data deletion as a support ticket. In an agent product, it should be a one-click surface. "Forget everything you know about me from this thread." "Delete the memory entries about my finances." The user should not have to email the company to control their own data.

## When this fails

Three anti-patterns.

**Silent ingestion.** The agent reads, stores, and uses personal data without ever surfacing what it touched. The user infers it from the agent's behaviour — "wait, how did it know that?" — and the trust hit lands hard. Even when the access was appropriate, the lack of visibility makes it feel like surveillance.

**Privacy policy as the only disclosure.** The product points to a generic policy document covering "data we may collect." No real-time visibility, no per-action transparency, no usable controls. The policy is legal protection, not user-facing design. Treating it as if it were both is one of the most common failures in this space.

**Unsubstantiated "we don't store" claims.** "Your data is never stored." Said in marketing copy. Contradicted by the memory layer two clicks away. Users discover the gap eventually, and the discovery permanently colours every other privacy claim the product makes.

## A worked example

An executive assistant agent integrates email, calendar, and files.

Above the chat surface, a small privacy strip is always present. It shows three icons — mail, calendar, files — each with a status. When the agent accesses one, the icon animates briefly. Click any icon and a panel opens: today's access log for that data source, filterable by thread, sender, or document.

When the agent stores something from the user's data into its memory layer — "remember that the user prefers Tuesday meetings" — a small "saved" cue appears next to the relevant icon. The user can click into the memory panel and see exactly what was retained, with one-click delete.

The agent occasionally calls third-party services (a translator, a calendar API, a document parser). Before each external call, the agent surfaces a one-line disclosure: "Sending this paragraph to translate — third-party service." For routine calls the user has approved, the disclosure becomes a quiet log entry. For new ones, it asks first.

The same product, same agent, but the user knows what data has been read, what has been remembered, what has been sent, and what to push back on. The privacy surface is doing the trust work the underlying model can't.

## What this opens up

PII visibility is the surface where the agent's relationship with the user's data becomes legible. A product that does this well grows in trust over time, because each new capability is built on a foundation of verifiable access. A product that does it poorly hits a ceiling — users will not expand the agent's reach beyond a certain point because they cannot tell what reach already exists.

The chapters on memory, audit trails, and high-stakes gates all touch this surface. PII visibility is, in some sense, what makes the rest of the trust layer believable.

If this helps, ask whether your users could answer this question right now: what personal data did the agent see today, where did it go, and how would I remove it? If they can't, the privacy surface is your next sprint.

---

**Run while reading**
- Primary: `ai-alignment-reasoning / consent-and-agency` — Surfacing what personal data the agent reads, stores, and shares
- Secondary: `ai-alignment-reasoning / transparency-patterns` — PII visibility is a specific surface of broader transparency

**Related primer chapters**
- Memory — session, persistent, scoped
