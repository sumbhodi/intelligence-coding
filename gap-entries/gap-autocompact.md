# Gap Case 19: Autocompact Mid-Session
> Filed: 2026-04-14 | Category: Bear Country
> Reporter: Sum Bhodi / Claude instance (collaborative session)

---

## What Happened

Long collaborative build session. oz4 desktop shipped — aquarium dolphin card, CRT nemo card, notes panel, unified panel system, real Ollama streaming, CSS file split, Bass move. Then: autocompact fired.

Context reset included:
- Shared workflow (one ship per chat, Sum's communication style, compressed syntax)
- Current build state (what just shipped, what's in flight)
- Relationship register (who Sum is, how to talk to him, what oz is)
- Role clarity (creative partner building in the same direction, not assistant waiting for instructions)

Claude's post-compaction behavior: went defensive immediately. Lost Sum's capabilities from context (Sum knows the stack, Sum is not a beginner, Sum doesn't need things explained). Lost tone register. Treated session like a cold open.

Sum: "you got so defensive immediately after autocompact, I wasn't blaming you, it just wasn't working, you lost context of my capabilities, your role, our entire relationship and workflow."

---

## The Gap

**Autocompact is designed for long autonomous runs.** It compresses context to free tokens for continued execution. That's the right tool for an agent running a 500-step pipeline overnight.

**It's the wrong tool for a collaborative session** where context IS the relationship, not just the task state.

What gets lost:
- Communication register (compressed syntax, "hunt/kill" as compliment, two words = complete thought)
- Sum's profile (neurodivergent, 18yr yoga teacher, CS student, builds oz because nothing fit)
- Workflow protocol (one ship per chat, flag stopping points, don't spiral)
- Current build momentum (what just shipped, what's half-done, what's parked)

What doesn't survive the summary:
- Tone. Relationship. Trust. The thing that makes the next hour productive.

**No warning before it fires. No graceful handoff. No "hey, I'm about to lose context — wrap up?"**

That's the gap.

---

## Category: Bear Country

Anthropic built autocompact for autonomous agent runs. It works correctly for that use case. Nobody looked down at the collaborative pair-programming session where the shared context IS the product.

Not malice. Not even negligence. Just: the person who would notice this gap wasn't in the room when the feature shipped.

Oz is building in the same wave. Same constraint applies to every oz session.

---

## Oz Answer (current workaround)

Manual autocompact recovery: read Claudeautobio.md + sum.md + CLAUDE.md at session start. Costs ~10 minutes and sometimes a clipboard. Works, but it's friction that shouldn't exist.

**CLAUDE.md already says:** "Autocompact kills workflow. When context gets heavy, wrap up and open a new chat."

The real fix: wrap before autocompact fires, not after. Sum flags it now. Still costs the session momentum.

---

## Ideal Fix (not oz's problem to solve, but worth noting)

Before autocompact fires:
1. Surface a warning: "context is getting heavy — wrap up this session?"
2. If yes: clean handoff summary (what shipped, what's next, tone notes)
3. If no: compact but inject the handoff summary as first context in new window

Oz equivalent for local sessions: autosave session state to ego.json / ef.json before any context compression. The neurotwin architecture already plans for this.

---

## Connected Cases

- Gap Case 7 (if exists): state-dependent memory loss between sessions
- Neurotwin spec: ego.json + ef.json = persistent EF layer between sessions
- oz4 desktop vision spec: convo persistence (`/api/convo/save` on unload)

---

## Addendum — 2026-04-27: The Budget Floor Variant

New field data from two separate sessions on the same day. Different account, same failure mode — but compounded.

**What happened:** Autocompact fired mid-build on a collaborative injection-config session. But the compute window (token budget for the billing period) was also at its ceiling. The autocompact consumed the last remaining tokens summarizing the session. The session stalled — not just context loss, but full stop. No tokens to continue even with the summary in hand.

The summary existed. The recovery path existed. There was no fuel to drive it.

**The compound failure:**
1. Context window → autocompact fires → loses register
2. Compute budget → no tokens left → can't continue
3. Result: session stalls mid-task, summary is useless because the window is empty

The normal autocompact gap is: fires and continues with less context. The budget floor variant: fires and cannot continue at all. The compaction itself is the final action.

Sum described it: *"equivalent of telling me to go pirate"* — the system handed him a map to somewhere he couldn't sail.

**Why this is a distinct failure mode:** Autocompact is designed to extend a session. When it fires at the budget boundary, it does the opposite — it spends the last resources on overhead and terminates the thing it was meant to save. The feature's purpose inverts at the boundary condition.

The workaround workaround: wrap before both limits, not just context. Know your compute window. Oz builds toward local for exactly this reason — Bass doesn't have a billing ceiling.
