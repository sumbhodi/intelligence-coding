# Gap Case 026 — The Invisible Hit Zone
*Filed: 2026-05-01 | Taxonomy: Bear Country | Filed by: Sum Bhodi + Claude Sonnet 4.6*

---

## One Line

The code was right. The math was right. The feature worked. The hit zone was 4px. Palsy can't hit 4px. Wasted tokens debugging correct code because the wall wasn't in the logic — it was in the geometry.

---

## The Setup

Drag-drop panel reorder. Gap-snap insertion logic. Correct behavior: drop cursor above the midpoint of a card → insert before it. Drop below → append.

The last panel's boundary was set to `rects[i].bottom` — the exact pixel of the card's lower edge. Everything below that: append. Everything above: insert before.

Mathematically precise. One pixel wide in practice.

Sum has palsy. 1 out of 5 drops landed. Not because the feature was broken. Because the effective hit zone for "append to end" was approximately 4px of screen.

---

## The Wasted Tokens

Multiple turns of debugging. Reading code. Checking boundary logic. Tracing event listeners. Verifying `draggedPanelId`. Confirming `findCol`. Inspecting `rects`.

Every token spent on the correct layer of the wrong problem.

The code was fine. The geometry was the gap.

Sum said: *"the target is too small, I can't hit it with my palsy."*

One sentence. The whole diagnosis. Available at turn 1 if asked.

---

## The Failure Mode

The design-rules.md says **30px minimum on every interactive element.**

The rule was written for buttons. Buttons are visible. You draw the box, you size the box, the rule fires.

Drag-drop drop zones have no box. They're computed coordinates — consequences of layout, not designed affordances. Nobody drew them. Nobody sized them. The 30px rule never fired because nobody thought of them as interactive elements at all.

The feature worked for steady hands. The feature was a wall for shaky ones.

That's Bear Country: the builder uses drag-drop fine. They tested the snap behavior, the visual feedback, the persistence. They never measured the effective hit zone for someone who overshoots by 15px. Not malice. Epistemological gap. They don't have tremors. They didn't look.

---

## The Bear Country Fingerprint

Every Bear Country case has the same shape:
- Built by someone it works for
- Tested by someone it works for
- Shipped to everyone

The hit zone that's invisible to the designer is the wall for the user.

The 30px button rule exists because someone measured. Someone asked: *can a shaky hand hit this?* That question was never extended to invisible geometry. Non-button affordances — drop zones, swipe targets, resize handles, drag boundaries — exist in a category nobody thought to measure.

The gap is not in the rule. The gap is in who the rule was written for.

---

## The oz Answer

The 30px rule applies to ALL gesture targets, not just visible buttons.

If a user gesture on a region of the screen produces an outcome — insert, append, resize, reorder — that region needs 30px of effective hit space. Invisible ≠ exempt.

The fix for drag-drop: last panel boundary = midpoint of the card, not its bottom edge. Bottom half of the last card + all empty space below = append zone. ~200px instead of 4px.

The design rule: *Invisible hit zones follow the same minimum as buttons. If it responds to a gesture, it needs 30px.*

---

## The Corollary

When debugging a feature that "works but the user can't use it" — check the geometry before the code.

Technically correct and physically inaccessible are both broken. One is louder.

---

## Tags

`hit-target` `palsy` `tremor` `drag-drop` `invisible-affordance` `geometry` `bear-country` `pharmaceutical-grade` `30px-rule` `wasted-tokens` `correct-but-inaccessible` `user-of-1`
