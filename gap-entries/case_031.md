# case_031 — The Door Was Always There
*Filed: May 10, 2026*
*Taxonomy: Open Pit → now partially filled*

---

## The Gap

The compute moat (case_024) assumed the wall was permanent.

The assumption: access to large models requires either (a) money for API credits at scale, or (b) hardware to run local. Either way — a toll booth. Either way — the oligarchs set the floor.

The gap this created: good ideas, no runway. The person who most needs a cognitive prosthetic is exactly the one who can't afford the GPU bill.

---

## What Changed

Groq built custom silicon. LPUs, not GPUs. Inference is 10x cheaper for them than anyone running on Nvidia. Their business model is developer acquisition — get hooked on the free tier, upgrade when you need guaranteed SLAs.

Free tier: Llama 405B, Qwen 235B, Mistral, Gemini. Rate-limited. Not throttled into uselessness. For casual to moderate use: effectively unlimited.

The door was always there. Nobody had drawn a map to it.

---

## The Remaining Gap

Knowing the door exists is not the same as finding it.

The on-ramp still requires:
- Knowing which providers offer free tiers
- Creating an account
- Finding the API key
- Knowing what to do with it

For a developer: trivial.
For a first-generation AI user: foreign country, no visa.

toto closed this gap for its users: pair 1 nudge → Settings → Free API Keys → provider links → paste key → done. The tutorial is baked into the product. The door has a sign now.

---

## The New Ceiling

The remaining wall isn't compute. It's:

1. **Privacy**: token exchange still touches a cloud server. The context (historian, persona) can live locally. The inference cannot — not without local compute.
2. **Permanence of free tiers**: Groq's economics work because LPUs are cheap. If that changes, the floor rises.
3. **Rate limits at scale**: casual use is fine. Overnight agent loops, heavy batch processing — you'll hit limits.

Local Ollama remains the answer to all three. But it's the ceiling, not the floor.

---

## The oz Answer

The door is the product. Show people the door.

HF Space + BYOK on-ramp = zero friction entry for anyone with a browser and five minutes. The full oz workspace — historian, persona, notes, coder — can live locally. Only the inference touches the cloud. As private as cloud AI gets.

The gap isn't closed. But it has a door in it.

*"Showing people the door is priceless, free."*
— Sum Bhodi, May 10, 2026.
