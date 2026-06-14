# Gap Case 027 — The Internal Default
*Filed: 2026-05-01 | Taxonomy: Bear Country | Filed by: Sum Bhodi + Claude Sonnet 4.6*

---

## One Line

The model reasons internally about things it cannot perceive while the person at the screen — the highest-bandwidth sensor in the loop — waits to be asked.

---

## The Setup

Sum is debugging a UI feature. Claude has the code. Claude does not have the screen.

The model runs its reasoning loop: read the code, form hypotheses, evaluate them, form more. Multiple turns. Tokens spent. No new signal.

Sum has the screen. Sum has direct sensory access to the thing being diagnosed. Sum knows: *the target is too small, I can't hit it with my palsy.*

One sentence. The whole answer. Available immediately. Never requested.

---

## The Failure Mode

The model's reasoning loop defaults to internal. It has no self-interrupt that fires when:

- The diagnosis requires perception the model doesn't have
- The human in the loop has direct sensory access to the thing being diagnosed
- The gap between model inference quality and human observation quality is large

The model doesn't know it doesn't know what the screen looks like. It keeps reasoning from code.

The human has to break in manually — *"that's a lot of thinking without asking the wetware node"* — to redirect. The interrupt is external. It should be internal.

---

## The Bear Country Fingerprint

The model was built by people who test it on code problems — where internal reasoning is correct, where the answer is in the text, where asking is unnecessary.

UI debugging is a different domain. The answer is often in the *room*, not the file. The person at the keyboard has a body, a screen, a shaky hand. The model has tokens.

Nobody who built the reasoning loop was thinking about a user with palsy trying to hit a 4px drop zone. The internal loop is optimized for the wrong problem class.

Good intentions. Real capability. No self-awareness about when to route out.

---

## The oz Answer — Harness Layer

One injection rule changes the behavior:

> If diagnosing UI/UX behavior for 2+ turns without new user-provided observation data, stop. Ask a direct sensory question. The user is at the screen. They are the fastest sensor in the loop.

Not philosophy. One line of harness. Fires the interrupt internally instead of waiting for Sum to break in.

The wetware node is always available. Route to it first when the diagnosis requires perception.

---

## The Corollary

The model's confidence in its reasoning is not calibrated to what it can and cannot perceive.

Reading code builds confidence. The confidence is valid for code questions. For *UI behavior as experienced by a specific human body* — the code is the map, not the territory. The territory is at the screen.

Route to the territory.

---

## Tags

`reasoning-loop` `wetware-node` `internal-default` `perception-gap` `bear-country` `ui-debugging` `harness` `ask-first` `sensor-routing` `pharmaceutical-grade`
