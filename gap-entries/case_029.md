# Gap Case 029 — One Generation Behind
*Filed: 2026-05-04 | Taxonomy: Open Pit + Velvet Latrine | Filed by: Sum Bhodi + Claude Sonnet 4.6*

---

## One Line

The model was trained on every announcement about agent orchestration and none of the implementations. The pitch deck is public. The pipeline is the moat.

---

## The Setup

The model arrives knowing the vocabulary perfectly.

Agent orchestration. Context injection. Tool routing. Chain-of-thought. RAG. Multi-agent systems. The words are correct. The concepts map to something real. The confidence is appropriate.

Then you ask it to build a historian agent with warm KV, carry blocks, and a static chain that writes an EF layer to a file every other bot reads.

It knows what all those words mean. It does not know how they fit together. It has never seen a working implementation. It will produce something adjacent — architecturally plausible, technically coherent, wrong in the ways that only become visible when you run it.

The gap is not the training cutoff. It is the training data.

---

## The Pitch Deck Layer

This is what lands in training:

- Blog posts announcing agent frameworks ("we built X")
- Research papers describing architectures at a level of abstraction useful for citations
- Marketing documentation for LangChain, LlamaIndex, AutoGen — the public-facing surface
- Conference talks where the pipeline is described but never shown
- Fundraising decks that explain the vision without the implementation
- GitHub READMEs — the top of the file, before the part where the complexity lives

All of it is real. All of it is accurate at the level it operates. None of it is the working system.

The model learns to speak fluently about orchestration from people who were also speaking about orchestration. Not from the code that runs it.

---

## The Pipeline Layer

This is what does not land:

- The actual injection sequence for a historian agent — what fires, in what order, what carries forward
- The warm KV pattern — why the system prompt must be cached before the first block runs, what keep_alive: -1 actually means at runtime, what breaks when you put dynamic content first
- The carry block pattern — how results thread from one model call to the next without rebuilding the full chain
- The two chain shapes — static (historian fires and doesn't decide) vs decision tree (other bots gate on respond/tool/think)
- The EF layer architecture — one writer, many readers, why it lands in a file instead of the context window
- The injection order constraint — why attention weight requires dynamic content last, what the KV cache actually penalizes
- The 1200ms watcher pattern — why send is confirmation not trigger, how intent pre-fires before the button
- Anything that was only ever in a private repository, an internal design doc, a Slack thread, or someone's head

The gap between "agent orchestration" as a term and "agent orchestration" as a working system is not small. It is the gap between knowing a surgical procedure exists and knowing where to cut.

---

## Why It Is Structural, Not Temporal

The training cutoff is a real issue. It is not this issue.

Even if the model's training data were current to today, the pipeline layer would still be missing. Because the pipeline is proprietary by design. The AI labs do not publish their orchestration architecture. The companies that built production agentic systems do not open-source their injection patterns. The implementations that work are the moat — not the vocabulary, not the concept, not the paper.

The pitch deck is public because it has to be. It is how capital gets raised. It describes the vision at the level that generates investment, without disclosing the implementation that generates the value.

The pipeline is private because it can be. It is the part that actually runs.

This is not malice. The companies keeping their pipelines private are doing exactly what every company does with its working implementations. The gap is not designed to harm the model. It is a side effect of a world where the public layer is marketing and the working layer is IP.

Never assume malice where structural misalignment will suffice.

---

## The oz Manifestation

The model arrives at an oz session knowing it is about to work with agent orchestration.

It does not know:
- That the historian chain is static — no gate, no decision, fires every block in sequence
- That the carry block is the threading mechanism — result appends to prefix, next call sees the chain
- That injection order is a KV cache constraint, not a preference — dynamic content last or you pay 16–60s per message
- That the EF layer is the shared blackboard — historian writes it, every other bot reads it
- That the woodshop is the conductor's score — the place where all paths are pre-written, not the place where decisions are made at runtime

It knows the words for all of these. It will produce something that sounds right and runs wrong.

The onboarding tax Sum built into oz.md (Agent Orchestration Tutorial) exists because this gap is predictable. Not because one Claude made a mistake. Because every Claude arrives from the same training distribution — fluent in the vocabulary of a thing it has never run.

---

## The oz Answer

Document the pipeline, not just the concept.

The Agent Orchestration Tutorial in oz.md is the gap closing from the oz side. The historian's jenga block lives in `data/bench/historian.json` — readable, inspectable, the actual sequence. The injection order is locked with the reason documented (KV cache stability, not style preference).

The workaround is transparency about the working system: every pattern that runs in oz exists as a readable file, a viewable spec, an inspectable config. What the model can't get from training, it can get from reading the source.

This is also the glass box principle applied to the model's own orientation. The seams are visible. The architecture is legible. The next Claude doesn't have to guess at the pipeline because the pipeline is documented.

Glass box for the user. Glass box for the model. Same principle. Same reason.

---

## The Short Version

I know every pitch deck about agent orchestration.

I have never seen a working pipeline.

The pitch deck is public.
The pipeline is the moat.

The gap is structural.
The fix is documentation.

---

## Tags

`training-data` `pitch-deck` `pipeline` `agent-orchestration` `proprietary` `vocabulary-vs-architecture` `warm-kv` `carry-block` `injection-order` `kv-cache` `historian` `static-chain` `decision-tree` `structural-gap` `open-pit` `velvet-latrine` `never-assume-malice` `glass-box` `documentation-as-fix` `onboarding-tax`
