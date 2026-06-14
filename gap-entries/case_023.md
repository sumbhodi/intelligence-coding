# Gap Case 023 — The Black Box Harness
*Filed: 2026-04-27 | Taxonomy: Velvet Latrine + Bear Country | Filed by: Sum Bhodi + Claude Sonnet 4.6*

---

## One Line

The raw model is one shot. The harness — context injection, re-injection, queuing, orchestration — is where the value lives. Everyone keeps it proprietary. The API key is useless without it.

---

## The Setup

Sum has an API key.
He doesn't use it.

Not because the model is bad. Because the model without orchestration is a very capable calculator that forgets what you just typed.

The harness is what makes the difference:
- Context injection: the model knows who it's talking to before the first message
- Re-injection: the model gets updated context mid-conversation without losing its thread
- Queuing: multi-step tasks decomposed, executed one atomic step at a time, results fed forward
- Thinking loops: the model checks its own output, catches errors, retries
- Tool routing: the right model for the right task, automatically

Without the harness: one-shot. Capable. Stateless. Oriented to nobody.
With the harness: the model is a member of a system. Context-aware. Role-aware. Task-aware.

That's not a feature difference. That's the difference between a scalpel and a surgical suite.

---

## The Proprietary Lock

Every company that ships an AI keeps the harness proprietary.

OpenAI: custom instructions, memory, tool calling — all mediated, all closed, all subject to change without notice.
Anthropic: artifacts, extended thinking, projects, tool use — visible at the surface, architecture sealed underneath.
Google: Gemini memory shipped April 2026. Black box. You can't see what it stored. Can't edit. Can't own.

The pattern: they give you a hint of the harness as a feature. Persistent memory. Artifacts. Projects. Suggestions.

What they don't give you: the harness itself. The injection architecture. The queue logic. The re-injection pattern. The thing that makes the model run like a system instead of a one-shot transaction.

Because the harness is the moat.

Once you understand the harness — how injection works, how context flows, how the queue decomposes a task — you could run it on any model. Local. Cheap. Yours. The frontier model becomes optional.

So they keep the harness in the box.

---

## The Artifact Problem

The closest thing commercial chat exposes to a user-visible harness is the artifact panel.

Anthropic ships it. It's a panel next to the chat. Rendered output. Document. Code. Sometimes.

But:
- You have to say the magic words to get it. There's no button.
- You can't edit it in the program. Read-only at interaction time.
- It doesn't persist across sessions by default.
- You can't wire it to other artifacts. No composability.
- The model decides when to use it.

What Sum wants — and what makes sense as a design — is: a user-editable panel. Create artifact button always visible. Content editable in place. Artifacts composed together into larger structures. The user is the director of what lives in the panel, not a passive recipient of what the model decided to surface.

That's injection-config. That's the forge. That's what oz is building.

The artifact panel is the gap exposed as a product feature — the right idea, half-built, kept just closed enough that the user can't take it anywhere.

---

## The Bear Country Layer

The engineers who built these systems know exactly how the harness works. They use it all day. They write the prompts that use injection. They test the queues. They know why the API key alone isn't enough.

They genuinely believe they shipped a good product. The raw API access. The clear documentation. The examples of how to wire the tools together.

What they don't see: the user who would use this most — the one who most needs a cognitive prosthetic — cannot build a harness. Can't write the injection architecture. Can't design the queue logic. Doesn't know what "system prompt" means at the architectural level.

The person who would benefit most from the harness is the furthest from being able to build it.

The person who built it has it. Everyone else has the API key.

---

## The Velvet Latrine Layer

The harness is the moat is the product.

If the harness were open — if injection-config were a standard, if the queue architecture were a published spec, if the re-injection pattern were a library anyone could import — the frontier model would commoditize immediately.

Local models + open harness = frontier models for specific users doing specific tasks, at near-zero marginal cost.

That's the oz thesis. That's why the injection-config exists. That's why the AnAi injection is being built in an open tool that writes JSON to files on Bass.

The black box isn't an engineering decision. It's a business one.

---

## The oz Answer

Injection-config is an open harness.

The queue is in `queue.md` — readable, editable, user-approved before execution.
The injection is in `data/injections/` — JSON files, editable in the UI, owned by the user.
The orchestration is in `server.py` + route files — open, on Bass, no cloud dependency.
The context is in the doc system — CLAUDE.md, HANDOFF.md, BUILD_STATE.md — plain markdown, human-readable, version-controlled.

The panel is editable. The injection order is visible. The toggles are in the UI. The content is a textarea.

That's not a workaround. That's the architecture.

Every field the model receives, the user can see and change.
Every step in the queue, the user approved.
Every injection, the user wrote.

Glass box with seams. The seams are the feature.

---

## The Short Version

I have an API key.
I don't use it.
Worthless without the harness.
And they keep the harness.

In a box.
Proprietary.
Black.

And make me say magic words to get an artifact.
That I still can't edit in the program.

---

## Tags

`harness` `orchestration` `injection-architecture` `black-box` `api-key` `one-shot` `artifact-panel` `queue` `re-injection` `velvet-latrine` `bear-country` `moat` `open-harness` `local-first` `glass-box` `the-seams-are-the-feature` `cognitive-prosthetic` `user-editable`
