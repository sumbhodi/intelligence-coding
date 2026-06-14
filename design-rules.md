---
name: design-rules
description: Hard UI constraints. Global. Read before every build or tweak. No exceptions.
last-updated: 2026-04-30
---

# Design Rules — Hard Constraints

These are not preferences. Not guidelines. Not things to revisit.
They exist because the person who needs oz most can't use it if they're wrong.

**If you're about to ship something and haven't checked every line below — stop.**

---

## Design Tokens — One Source of Truth

**Every value that appears more than once is a token. No exceptions.**

- Sizing, spacing, color, border-width, shadow: defined at `:root` as CSS custom properties.
- JS constants that repeat across files: defined once in a shared config or at the top of the owning file.
- **The test:** if you change a font size token, does everything that uses it update? If not, you have hardcoded duplicates. Hunt them.

**Example — settings font size slider:**
```css
/* wrong: 20 files each hardcode 28px */
font-size: 28px;

/* right: one token, one change */
:root { --fs-body: 28px; }
font-size: var(--fs-body);
```

**Derived tokens are first-class:**
```css
/* slider/handle thickness scales with font — change --fs-body, slider updates too */
:root {
  --slider-h: calc(var(--fs-body) * 0.5);
}
```

**The rule for new code:** if you're about to type a pixel value that matches an existing token, use the token. If no token exists for it and it'll appear twice: make one.

**The rule for combined modules:** when combining files, pull all duplicate values to `:root` tokens first. Then replace. Don't combine and leave the duplicates.

---

## No Redundant Logic

**Logic that appears twice gets a function. The second copy is the bug.**

- Card header collapse/expand: one function, called everywhere. Not inlined slightly differently per card.
- Toggle pill add/remove: one function. Not hand-rolled in three card files.
- API fetch pattern: one wrapper. Not copy-pasted with minor variations.

**As we build going forward:** write functions first, inline last. When you notice you're writing something you wrote last week: stop, find the first copy, extract it, use it.

**The compaction risk:** hardcoded duplication is invisible until it breaks — always in one place but not the other. Functions break loud. Duplicates break quiet.

---

## File Size

- **Target: 500 lines.** Hard ceiling: **800 lines.**
- Hit 600+ mid-session? Stop. Split. Continue.
- Final pass (Opus/future model) can combine up to 10 files.
- Build modular first. Combine last.

---

## Typography — Locked Defaults

| Use | Size | Token |
|-----|------|-------|
| Body / item text | **28px** | `--fs-body` |
| Column / section labels | **20px** | `--fs-label` |
| Card titles / `.ph-title` | **30px** | `--fs-title` |
| Tab / header chrome | **18px** | `--fs-tab` |

- **Large print is the default.** Smaller is a setting. Larger is never needed.
- **No ghost text.** If it's on screen, it's readable. `#3A1808` is a background tint, not a text color.
- Every label, status, header: readable at arm's length in ambient light.

---

## Hit Targets — Palsy Rule

- **Minimum 30px** on every interactive element. No exceptions.
- Whole card header (`.ph`) is the drag zone — no dedicated drag icon needed.
- Resize handles: `⇕` vertical, `⇔` horizontal. Left-aligned, no box, bold contrast.
- If your finger can miss it on a shaky day, it's too small.

**Invisible hit zones follow the same rule.**
The 30px minimum applies to ALL gesture targets — not just visible buttons. Drop zones, drag boundaries, resize regions, swipe targets: any area where a user gesture produces an outcome needs 30px of effective hit space. Invisible ≠ exempt.

The failure mode: drag-drop append zone was mathematically correct at 1px. Feature worked. User of 1 couldn't hit it. Technically right is not the same as accessible. *See gap case_026.*

**The test:** can someone with a tremor hit this on a bad day? If not, make the zone bigger.

---

## Skins Are the Product Roadmap

**Every skin you build is a rehearsal for a physical object that will exist.**

Software skin today → physical product in 2034.
The beach card is a future wearable concept. The forge is the desk surface. Neo is the terminal chassis.
Design every card like someone will manufacture it.

When you're spec'ing a new skin: *what IS this as an object? what material? what weight?*
The answer shapes every design decision — color, depth, texture, shadow, sound.

→ canonical examples in `oz.md` (canonical build examples section)

---

## Physical Objects — Not Flat Icons

**Buttons and controls should feel like objects you can pick up off a surface.**

- Colored background + `box-shadow: 0 3px 0 [darker shade]` = raised from surface = physical
- Flat SVG on dark background = corporate dark mode = wrong every time
- The test: *can I imagine picking this up?* If no, it's wrong
- Size ≠ physical. A 40px flat gray button is still a ghost.

**What physical looks like:**
- Beach card wave handle: textured, has weight
- Forge jenga blocks: wood grain, shadow, drag-able mass
- Brain nav buttons: green/red/gold/brown backgrounds, `0 3px 0` bottom shadow, Courier monospace label
- A real cooler, a real brain, a real axe — not a flat outline SVG

**What kills it:**
- Blue icon on blue background (color on same-hue bg = invisible)
- SVG outline icon with no fill, no shadow, no background
- `opacity: 0.6` on anything interactive
- Monochrome icon set — everything same weight, same color, same depth (none)

**The anti-pattern to name:** *Corporate dark mode* — everything float-dark, hairline borders, flat icons, no depth, no color, no mass. Looks like a developer built it for other developers and doesn't use it. That's the failure mode. When you notice yourself building in that direction: stop, add a background color, add a shadow, make it land.

**SVGs are fine for:** topology (the oz logo, layout toggle, the gear). They're wrong for: navigation objects, tool launchers, anything that should feel like a physical verb.

---

## No × Buttons

**Zero × close/remove buttons on blocks, cards, or items.** Removal is a gesture, not a button.

- Drag to kindling (waste bin) = the remove path. Always.
- × buttons clutter the block surface, cover label text, and conflict with the drag surface.
- They also imply "dismiss" rather than "this goes somewhere" — wrong mental model for a forge.
- If something needs a quick-remove affordance: make the gesture clearer, not add a button.

**The rule:** oz has exactly 0 × buttons on blocks. Keep it that way.

---

## Glass Box — Show the Machine Language

**The human sees the YAML. The human sees the JSON. The seams are visible. That's the feature.**

- Do NOT abstract machine language behind friendly forms, toggles, or wizards.
- The forge editor IS the YAML — no translation layer between what the user writes and what the model receives.
- AI helps with syntax errors in place — corrects and returns the source. Never replaces it with a black box equivalent.
- The matrix streaming is real code. Render it that way.

**The distinction:**
- Black box: user configures → system translates → model receives something user never saw
- Glass box: user edits directly → AI corrects syntax → model receives exactly what user sees

One builds dependency. One builds fluency. Oz builds fluency.

See also: [gap case_022](../gap-entries/case_022.md) — Human Never Sees JSON.

---

## Nothing Decorative — Everything Functional

**If you can see it, you can click it. If clicking it does nothing, remove it.**

- Every visible element on screen has a function. No exceptions.
- No visual elements for "making it feel richer."
- If it's not actionable, it's noise — and noise costs EF.
- Applies to icons, labels, borders, lines, badges, and indicators.

---

## No Decorative Geometry

**Arrows, chevrons, triangles = functional only.** If it's there, it does something. If it doesn't do something, remove it.

- No decorative `▸` `▾` `›` floated in corners or headers with no click handler.
- No corner accent shapes for visual interest.
- This keeps getting added back. It is always wrong.

---

## Topbar / Header Space

- Empty topbar/header space = **click to expand/collapse**, **hold to drag**.
- Never dead space. Never decoration.
- Not a branding zone. A functional zone.

## Topbar Button Conventions

**oz topbar layout (left → right):**
```
[ logo ]  [ layout icons ]  [ brain ]  [ gear ]
```
- Logo: left anchor, fixed
- Layout icons center: home · 1col · 2col · 3col · +top-row · +bottom-row (PNGs from Sum)
- Brain: right of center — back lot / immutable desktop
- Gear: rightmost — settings
- Portrait/landscape toggle: **removed**. Superseded by layout icons.

**Button PNG pipeline:**
- Sum generates at: 620×620 px source, 25px inset (4%), 43px feather (7%), 560×560 output bbox
- Drop in `/Volumes/Bass/oz/oz4.2/assets/` — Claude wires in with one `background-image` line
- All topbar icon buttons: 44px hit target minimum, physical depth treatment (background + shadow), not flat SVG on dark

---

## Column Layout

- **No resize sliders between columns.** Each zone scrolls independently.
- `overflow: hidden` on zones + `overflow-y: auto` on columns — expanding one column cannot shift another.
- `html, body { height: 100%; overflow: hidden; }` — page does not scroll. Columns do.
- No `align-items: flex-start` on `.zones` — causes layout bleed.

---

## Panel Standard (oz4 pattern — applies to all dashboards)

- **Panel header (`.ph`):** 42px height minimum. `cursor: grab`. The **whole header** is the drag zone — no dedicated drag icon needed or allowed.
- **Panel title:** 30px (`--fs-title`). Status/badge text: 18px (`--fs-tab`).
- **Panel collapse:** `panel:not(.open) .pb { display: none }` — body hidden, not shrunk.
- **Corner brackets** (`::before` top-left, `::after` bottom-right): oz4 panel aesthetic. Structural feel. Use in bot/doc panels. **Do not use in workshop/jenga blocks** — different design language.
- **Border width:** `--bw: 5px` — oz4 standard. Don't use 1px hairlines on primary structure.

---

## Resize Handles

- **Vertical resize (height):** `⇕` — left-aligned, no box, bold contrast, `cursor: ns-resize`, minimum **30px** hit target.
- **Horizontal divider (column):** `⇔` — centered in the divider bar, `cursor: col-resize`, minimum **30px** wide.
- Both: keyboard-visible symbols only. No custom SVGs. No decorative arrows.

---

## Bot Output vs. Shared Space

- oz shares space — notes, todos, and context columns are collaborative by design. Do not segregate human and AI into separate zones.
- **Bot chat output** (message bubbles): visually distinct from input. Dark backgrounds (`#020c14` in oz4) on AI turns. Not because they're machine territory — because readability requires contrast between turns.
- **Shared content** (notes, todos, docs): no visual marker of authorship. If Sum wrote it or oz wrote it, it lives in the same space with the same weight.

---

## No "AI Made This" Tells

- No loading spinners with bounce animations.
- No empty state copy with emoji: "Nothing here yet! 🎉"
- No modals with `border-radius: 16px`.
- No glassmorphism. No gradient blue-purple overuse — blue-purple is fine in topbar and logo; it's the wellness app smear across every surface that's wrong. Save it for effect.

The benchmark: *gamified marketing that sells your data — Angry Birds, Jewel, Tetris.* Pharmaceutical grade UI. Weapons grade OS.
If it looks like a wellness app, something went wrong.

---

## Opacity — Locked Box. Ask Before Touching.

**The opacity slider has a locked plastic box over it.**

- Do NOT use `opacity` on text, labels, or UI elements to suggest hierarchy.
- Do NOT use it to "soften" secondary content. If it's on screen, it's readable. If it shouldn't be readable, don't show it.
- **Ghost font = wrong. Every time. No exceptions.**

**When opacity IS allowed (ask permission first):**
- Intentional 3D depth layering — foreground/background Z-axis effect (e.g. wall layer receding behind bench stack)
- Glass box / blue-on-blue effects — with explicit permission, sparingly
- Never for text. Never for labels. Never to fake hierarchy.

**Rule:** If you're reaching for opacity to make something "feel secondary" — use size, position, or just remove it instead.

---

## The Asset Ladder

Every UI element climbs this ladder. Stop at the first rung that works.

1. **Mock up** — concept sketch, placeholder, get the shape right
2. **Emoji** — if it reads correctly and has enough mass, ship it. `🧠` is the reference.
3. **CSS illustration** — when emoji falls short. colored, weighted, depth, shadow. casting call bots are the reference.
4. **PNG** — when CSS falls short. user generates the image, bot advises on composition. one line to wire it in.

When Sum says **"CSS"** — he means rung 3. Draw it, don't describe it.

Emoji is not failure. It's a valid rung. CSS is not always better — it's the next rung when emoji isn't enough.

---

## Real Images Over CSS Fabrication — But Try CSS First

**CSS owns: geometry, structure, dark bezels, gradients, scan lines, color palettes, silhouettes.**
**Image gen owns: material texture, atmospheric depth, real surfaces (wood grain, concrete, fabric).**

- Try CSS first. One failed tweak → ask for an image. Don't spend sessions fabricating what a photo does in seconds.
- CSS gradients ≠ wood grain. CSS noise ≠ painted concrete. SVG turbulence ≠ real surface.
- When a visual needs to look like a real material with depth: **ask for an image.**
- PNG workflow: user drops image in folder, you reference it. One line. Done.
- Future: wall, floor, and window are separate swappable files. User customizes their view.
- The miter joint experiment is the canonical example of what not to do.

**The handoff:** Sum generates or photographs the asset. Claude wires it in. Division of labor.

---

## Lean Code — The Goal Is Fewer Lines

**The measure of oz is how few lines of code does everything mac, android, and pc can do.**

- Open source libraries (monaco, TipTap, etc.) will be the largest KB in oz. That is correct and intentional.
- oz's own code should be as thin as possible — layout engine, card utils, routes, skins.
- Every function written is a liability. Every reused function is an asset.
- If it already exists in oz, use it. If it exists in open source under MIT/Apache 2.0, import it. Build only what doesn't exist.

**Open source rule:** MIT or Apache 2.0 (do-as-thou-wilt licenses). GPL is a dependency trap. Commercial is a moat. Only MIT/Apache. Any bot can research the best available library — that's not Claude's job. Claude's job is to evaluate, strip to essentials, skin it, and plug it in.

**The lean test:** if you're building something that an open source library does, stop. Find the library. Import it. Skin it. That's the whole job.

---

## Mockup Workflow — Hardcode First, Port Second

**Never prototype in the live oz build. Mockups go in `specs/mockups/`.**

1. Static HTML — no server, no routes, hardcoded data. Shape + interaction only.
2. Design validation — screenshot, test in a separate session (Gemini/Grok/image gen — different token purse).
3. Port to oz4.2 — wire routes, live data, real models, follow all rules.
4. Delete the mockup or archive it.

**The token purse rule:** design work (vibe, skin direction, library choice, layout exploration) happens in other tools. Claude's job in the build workflow is: check the work, strip excess, modularize, plug in cleanly. Not design. Integration.

---

## Skin ≠ Bot — Hard Separation

**A skin owns zero bot knowledge. No model string. No system prompt. No hardcoded persona.**

- Skin = chrome: layout, colors, resize handles, input tray, send button, skin-specific UI
- Bot = role + harness: model, persona, injection stack — lives in `data/roles/` + `data/bots/`
- Wiring: `oz.buildCard({ skinId, roleSlug, ... })` — on power-on fetches `/api/injection/preview/{roleSlug}`

**The test:** can you swap the bot without touching the skin JS? If not, something leaked.

New skin → call `oz.buildCard()`, keep skin JS to: HTML mount + skin-specific UI (handles, toggles, buttons) + input wiring. Nothing else.

---

## Card Chrome Contracts — What Each Category Always Has

Cards are one of four types. The type defines what controls are always present. Skin handles visual. Content handles logic.

**Bot cards** — power toggle · jewels · permission tier · persona drawer · HIL btn · stop btn · `.oz-msg-u`/`.oz-msg-bot` output · input field · `oz.buildCard()` call
**Doc cards** — tab bar · rollback controls · save indicator · (optional) bot context inject
**Tool cards** — run/stop · parameter inputs · log/output area · no message bubbles
**Monitor cards** — data display · refresh state · (optional) context inject button

When building a new card, identify its category first. Wire the chrome contract before the skin.
