# STYLE.md — light-bar project patterns
# local rules. light-bar specific. IC.md is the global standard.
# written june 2026 — sum + claude

---

## the two-phase model

```
BUILD ──────────────────────────────────────────────────
  goal     100–300 lines per file
  ceiling  500 lines — hard. no exceptions during build.
  rule     hit 450 → find the seam before adding anything.
  shape    folder of small files. one concern each.
           the folder is the workshop. joints cut separately.

SHIP ───────────────────────────────────────────────────
  goal     1080 lines. ~40KB. every shipped file. full HD.
  ceiling  1080 lines — hard. no exceptions at ship.
  rule     proto files in one folder → one ship file.
           page 0 + page 1 + burial zone + pages 1–8 + closing.
           haiku tokens tune to exact KB. target: 40,960 bytes.
           symmetric. composed. one scroll.

NAVIGATION ─────────────────────────────────────────────
  PAGE 0   TOC — goldfish pointers. line numbers only. 100 lines hard.
  PAGE 1   EXPANDED TOC — VC · tech bro · small bot. 100 lines hard.
           1–5 lines per section. resources. search terms.
  Ctrl+G → line number → 3 keystrokes to any section.
  vscode://file/path:line in companion _toc.html → click to jump.
  #region / #endregion → VS Code Outline panel. free navigation.
```

goal across all of light-bar: **lowest KB, lowest line count** for any app that does this much.
tighter than a 90s game cartridge by the same logic.
every byte above the idea is waste.

---

## table of contents

```
  52   ⓘ tip pattern       — helpers, DOM order, wiring, layout
 111   _cancelFade          — any manual action kills a running fade
 129   CSS modularity       — bevel class, never inline box-shadow
 146   form / function      — CSS and JS always separate files
 155   file naming          — hyphenated, describes what it IS
 163   whitespace           — section dividers, stanza vocabulary
 ???   spatial nav          — one canvas, snap, swipe, zoom-out
```

---

## ⓘ tip pattern (lines 21–79)

### the rule
ⓘ and ⚙ are completely independent. no coupling.
tip state (open/closed) persists to localStorage — tips do not reappear on reload.

### DOM order — fixed, never reordered
```
  row bar
  gear panel    (hidden until ⚙ — toggled by gear handler)
  tip panel     (hidden until ⓘ — always AFTER gear in DOM, never inside it)
```

### the three helpers — copy exactly, do not reinvent

```js
// _tip(key, content) — renders the tip div
// closed state persists to localStorage
function _tip(key, text) {
  const closed = localStorage.getItem(`lb-tip-${key}`) === '1'
  return `<div class="ls-tip" id="ls-tip-${key}"${closed ? ' hidden' : ''}>${text}</div>`
}

// _tipCloseBtn(key) — "ⓘ close" button rendered INSIDE the tip
// pass as closeBtn to every LB_TIPS call:
//   LB_TIPS.strip(_tipCloseBtn(key))
function _tipCloseBtn(key) {
  return `<br><button class="ls-tip-btn ls-tip-close" data-tip="${key}">ⓘ close</button>`
}

// handleInfoBtn({ tipEl }) — pure tip toggle, 2 lines, no gear args
// call this from every ⓘ handler. never inline the logic.
function handleInfoBtn({ tipEl }) {
  if (!tipEl) return
  tipEl.hidden = !tipEl.hidden
  const key = tipEl.id.replace('ls-tip-', '')
  localStorage.setItem(`lb-tip-${key}`, tipEl.hidden ? '1' : '0')
}

// _wireTips(el) — inner-dismiss only (ls-tip-btn without data-opens)
// row-level ⓘ buttons are wired directly by each module, not through _wireTips
function _wireTips(el) {
  el.addEventListener('click', e => {
    const btn = e.target.closest('.ls-tip-btn')
    if (!btn || btn.dataset.opens) return
    e.stopPropagation()
    handleInfoBtn({ tipEl: document.getElementById(`ls-tip-${btn.dataset.tip}`) })
  })
}
```

### row-level ⓘ wiring — each module handles its own
```js
// in wire() — direct listener, not through _wireTips
document.querySelector(`[data-tip="${key}"]`)
  ?.addEventListener('click', e => {
    e.stopPropagation()
    handleInfoBtn({ tipEl: document.getElementById(`ls-tip-${key}`) })
  })
```

### tip copy lives in lb-tips.js ONLY
never inline tip text in a component. find it cold → open lb-tips.js.
every LB_TIPS.* function takes closeBtn as the last parameter.

### ALL copy is stanza. no prose. ever.
sum does not write in prose. claude must not write in prose here either.
every piece of writing in this project — tips, docs, comments, README —
is written in stanza. verse. short lines. natural breaks. breathing room.

the rule is not limited to tips.
it applies to: README, IC.md, STYLE.md, CLAUDE.md, comments, any doc file.

if you are about to write a long flowing paragraph — stop.
break it at the clause.
break it at the em-dash.
break it at the breath.
blank line between ideas.

### stanza rule (all copy)

**haiku = 3 short lines.**
each line fits the tip panel width without wrapping.
if it wraps, it's too long. break it or cut it.

**stanza = one idea, never wraps.**
blank line between stanzas (`<br>`).
break at the dash — `—` ends the line, continuation drops to next line.
bold header on its own line, body below.

```html
<!-- correct -->
<strong>offset</strong><br>
shifts when the row fires —<br>
earlier or later than the anchor time.<br>

<!-- wrong — wraps, reader loses the thread -->
<strong>offset</strong> — shifts when the row fires, earlier or later than the anchor time.<br>
```

the reader — human or phone — should never see a line break mid-thought.
every break is intentional. every break is yours to place.

### layout reference
```
[● pill]  Device Name  ⓘ  [presets ▼]  [80%]  [⚙]
──────────────────────────────────────────────────────
  ╔ gear panel (hidden until ⚙) ════════════════════╗
  ║  R ──── G ──── B ──── K°  + swatch              ║
  ╚═════════════════════════════════════════════════╝
  ╔ tip panel (hidden until ⓘ) ═════════════════════╗
  ║  set state → save a button or preset.            ║
  ║  whatever state is saved fires on tap.           ║
  ║                              [ⓘ close]           ║
  ╚═════════════════════════════════════════════════╝
[brightness slider]
```

---

## _cancelFade (lines 80–97)

any manual action (on, off, color, brightness) must cancel a running server fade.
otherwise the fade thread wins on next step and overwrites what the user just set.

```js
// extract once per strip instance — never inline the fetch three times
function _cancelFade() {
  const devName = cfg.tuyaName || ID
  fetch(`/api/schedule/fade/stop/${encodeURIComponent(devName)}`, { method: 'POST' })
    .catch(() => {})
}

// call at the top of every command function:
async function sendColor()      { _cancelFade(); ... }
async function sendKelvin()     { _cancelFade(); ... }
async function toggle()         { _cancelFade(); ... }
// debounced brightness — cancel before the debounced call fires
const [, _debounceBright] = makeDebounced(val => { _cancelFade(); api.brightness(val) }, 150)
```

the server-side fade loop also detects external changes (device turned off,
brightness ±6%, color/kelvin changed from any source) and aborts automatically.
the stop endpoint is authoritative. the poll is the safety net.

---

## CSS modularity (lines 98–114)

`.bevel` and `.bevel-inset` live in tokens.css. never write box-shadow inline.

```html
<!-- wrong — values duplicated, skin changes require two edits -->
<div style="box-shadow: inset 4px 4px 0 var(--bevel-light)...">

<!-- right — one edit in tokens.css affects everything -->
<div class="ls-row bevel">
```

same rule for all repeated patterns:
- `.btn` — physical button shape + shadow + active sink
- `.bevel` — raised surface depth (4px cards/rows, 6px topbar)
- `.bevel-inset` — recessed well (slider track, input field)
- `.ls-pill` — pill toggle shape
- `.ls-tip` — tutorial band color + border

the test: change the bevel depth — how many files need editing?
if more than one, something isn't using the class.

**force is never the answer.**
`!important` means the cascade broke, not that you won.
find where the wrong value originates. fix the selector.
if `!important` appears in a commit — it goes back out before ship.

```css
/* wrong */   color: var(--text) !important;
/* right */   .parent-context .wx-detail-val { color: var(--text); }
```

---

## form / function (lines 115–123)

CSS is not JS. keep them in different files.

```
lb-light-strip.js    — behavior. what things do.
lb-light-strip.css   — form. what things look like.
```

a designer changes CSS without reading a factory function.
a 1b model changing a color doesn't need to parse device state logic to find it.
one file. one concern. one change. verify. next.

---

## file naming (lines 124–131)

```
one word or hyphenated.   lb-light-strip.js  lb-group-card.js
no camelCase filenames.   lbLightStrip.js      ← wrong
no abbreviations.         lb-grp-crd.js        ← wrong
describes what it IS.     lb-light-strip.js    ← right
not what it does.         lb-render-strip.js   ← wrong
```

---

## page width — the two-number rule

```
CODE          80 chars of content + indent chars
              hard cap: 100 total. past that: restructure the nesting.

              indent 0  → max  80
              indent 4  → max  84
              indent 12 → max  92
              indent 20 → max 100  ← hard cap regardless of indent
              indent 24 → still 100. the nesting is the problem.

UI / TIPS     40 chars target. 50 absolute max.
              anything on screen may end up on a phone.
              someone at 6am in bed setting an alarm deserves
              lines that don't wrap.
```

**template literals break to new lines. always.**
HTML doesn't care about whitespace between flex children.
the newline costs nothing. the readability pays back immediately.

```js
// wrong — wraps, unreadable
extras: `<select id="${_p('sel')}" class="ls-sel"><option>—preset—</option></select><span style="flex:1"></span>`

// right — same output, scans
extras: `
  <select id="${_p('sel')}" class="ls-sel">
    <option>—preset—</option>
  </select>
  <span style="flex:1"></span>`
```

**genuine exceptions — very short list:**
bare URLs in fetch calls. API key strings. markdown code examples.
everything else: break the line.

**migration:** existing code doesn't comply on day one. new code does.
old code gets fixed on next touch. the rule is forward-looking.

---

## whitespace vocabulary (lines 132–155)

```js
// ══════════════════════════════════════  major section divider
// ── subsection ──────────────────────── minor section / function group

blank line between functions             always
blank line between comment and code      always (the breath rule)
blank line before return                 always
blank line between logical groups        always

no blank line inside a single thought
no double blank lines                    ever
```

stanza discipline: find any function by searching its `// ── name` header.
works in any editor, any 1b context window, any 3am scan.

**prefix families are rhyme schemes:**
```js
_devOn / _devColor / _devKelvin / _devPct     ← _dev* family
fireAlarm / fireFade / fireSnooze              ← fire* family
startPoll / stopPoll / wrapPoll               ← *Poll family
```
the reader — human or model — pattern-matches the root before parsing the word.
name into the family. if a thing doesn't fit the family, that's signal: wrong place.

**more whitespace than you think is necessary.**
the cost is zero bytes of logic. the gain is a file that scans.
the machine doesn't need to know it's reading verse. it just reads faster.

---

---

## page header / footer template

copy exactly. fill in values. do not redesign.

```
# ╔══════════════════════════════════════════════════════════════════╗
# ║  filename.js · page N of 10 · section name · june 2026          ║
# ║  "quote — one line, earns its place or doesn't ship"            ║
# ╚══════════════════════════════════════════════════════════════════╝
```

```
# ╔══════════════════════════════════════════════════════════════════╗
# ║  lines NNN–NNN · page N of 10 · next: section name (page N+1)  ║
# ║                                                                  ║
# ║    the comment breathes above the code —                        ║
# ║    unstressed, then stressed, then done.                        ║
# ╚══════════════════════════════════════════════════════════════════╝
```

haiku at page footer when earned. couplet when a haiku is too light.
sonnet at section breaks for treatise-weight sections.
never force it. silence is also correct.

---

## the nano aesthetic

programs that fit in a text message. this is the goal.
not because storage is scarce — storage is free.
because the reader's attention is not.

```
target:  1080 lines · ~40KB · every shipped file
         full HD. the resolution at which things become clear.

nano:    the codebase fits in a 5MB email attachment.
         actually: light-bar source ≈ 28 files × 40KB = ~1.1MB total.
         the whole app. smaller than one PNG artifact.

companion files: 100×100px retro 8-bit.
         _toc.html — navigation artifact, not shipped to prod.
         icons — 4KB maximum. if it needs more pixels, redesign.
         a 5MB companion file failed the nano test.
```

the 90s game cartridge was tight because RAM cost money.
the IC file is tight because the reader's attention costs time.
apply the same discipline. not because you have to.
because the constraint produces better work.

---

---

## the three clock themes — what they are and why

three themes. three arguments. no explanation inside the product.

```
flip    — warmth. cardstock. Georgia serif. physical objects with mass.
          bevel. cream on navy. the thing we actually believe in.
          grandma can use it. that is the whole design brief.

mod     — peak SaaS costume. Inter. void. glass morphism. ambient orb optional.
          the joke: it looks like a $40M Series B dashboard.
          the punchline: it controls a bedside lamp.
          it will be retro in a decade. we marked the moment. june 2026.
          PSS = Peak SaaS Shell. phonetically: piss. intentional.

retro   — 1987 CRT. amber on black. monospace. scanlines.
          nostalgia for hardware that had personality.
          a clock that couldn't exist before 2012
          wearing clothes from 1987.
          the most recent time the world ended.
```

commentary through aesthetic.
three themes = three simultaneous arguments about interface design.
the product doesn't explain them.
the arguments stand alone.

---

## PSS antipatterns — when you are going the wrong way

new instance without full onboarding?
you will default to PSS.
every model does.
it's in the training data.
it looks correct.
it is the wrong direction for this product.

**read this section before touching any UI.**

---

### the tells — you are building PSS if:

**font**
you reached for Inter.
stop.
Inter = Series B. Inter = startup dashboard. Inter = mod theme only.
light-bar uses `var(--font-ui)` from tokens.css.
flip theme = Georgia. warm. physical. correct.
do not hardcode Inter outside of mod/PSS contexts.

**color**
you are using `rgba(255,255,255,0.05)` as a background.
that is glass. glass = mod theme. glass = void aesthetic.
flip theme = `var(--color-bg-card)`. it has presence. it has weight.
surfaces in flip are things you can put down on a table.
glass surfaces float. nothing in flip floats.

**bevel**
you removed the bevel and added a border instead.
that is backwards.
`var(--bevel)` = physical depth. the button is a physical object.
`border: 1px solid rgba(...)` = flat. flat = PSS. flat = wrong theme.
if it has a border but no shadow — it's PSS. put the bevel back.

**hit targets**
you made something smaller because it "looks cleaner."
stop. grandparent rule. shaky day rule. 3am rule.
`var(--hit-min)` exists. use it. never go under it.
PSS makes things small to signal sophistication.
we make things large to signal respect.

**gradient text**
you added `background-clip: text` to a label.
that is PSS.
that is Inter-locked-in SaaS flair.
labels have one color. the color is `var(--color-text-primary)`.
gradient text = mod theme only, if we ever add it.

**the ambient orb**
you added a radial gradient blob behind a card.
it looks great. it communicates nothing.
remove it.
if this is mod/PSS theme context: document it as a joke.
if this is flip/unicorn context: you are in the wrong register.

**backdrop-filter everywhere**
blur is mod. blur is glass. blur is void aesthetic.
flip cards do not blur. flip cards have mass.
`backdrop-filter: blur(24px)` belongs in mod theme only.
if you added it to a flip component: revert it.

**opacity on text — banned. full stop.**

rgba on text = content see-through.
emoji inherits color context and renders washed out.
grandma can't read it. it's not designed. it's broken.

```css
/* wrong */  color: rgba(255,255,255,0.45);
/* right */  color: #9299ad;
```

convert rgba text colors to solid hex at build time.
pick the hex that matches the visual target — don't guess.

**structural rgba is fine:**
box-shadow rgba — shadows need transparency.
border rgba — hairline borders on dark backgrounds.
background rgba — subtle surface tints.
opacity: 0 — hidden states (nav.off, panel.hidden, drag).
opacity < 1 — explicit UI states only (hidden widget, dragging item).

**the scan rule — june 2026:**
after any CSS session: grep for `rgba` and `opacity` in text/color rules.
structural = ok. content = fix.
emoji icons specifically: set `color: initial` on the icon element
to break inherited color context.

**the empty state**
you added a floating icon and a ghost caption to an empty list.
that is PSS empty state aesthetic.
light-bar empty state: `#empty-state` in index.html.
one sentence. one button. no floating illustration.
the loneliness is in the product gap, not the icon.

---

### the check — before you ship any UI change:

```
squint test       blur your eyes. can you identify each surface type?
                  topbar = chrome. card = card. button = button.
                  if everything blurs to the same plane — PSS.

grandma test      could a 79-year-old use this on a shaky day?
                  if no — redesign. not "make it bigger."
                  redesign so the information is clearer.

bevel test        does every interactive surface have physical depth?
                  raised = interactive. recessed = input/track.
                  if a button looks flat — it's missing the bevel.

font test         is this Inter in a flip/unicorn context?
                  if yes — wrong. change to var(--font-ui).

color test        does this use raw hex/rgba instead of a token?
                  if yes — find the token. if no token exists, make one.
```

---

### the default is always unicorn

when uncertain: go warmer, not cooler.
more bevel, not less.
more contrast, not less.
larger hit targets, not smaller.
more whitespace, not tighter.

the unicorn is not a style preference.
it is the product requirement.
grandma's clock fires at 06:30.
it has done so since june 2026.
the lights work because the interface is honest.

PSS is the costume.
flip is the product.
if you can't tell which one you're building —
you're building PSS.

---

---

## three strikes — new file

same rule as IC.md, applied to light-bar specifically:

```
strike 1  wrong. fix it in place.
strike 2  still wrong. different approach, same file.
strike 3  stop. new file. one thing only.
          get it working. then port it back.
          name it *-test.html or lb-*-proto.js.
          rename at refactor.
```

**the expand-bar lesson (june 2026):**

the expand bar failed three times inside lb-weather-hero.js.
each failure more complex than the last.

root causes, now documented so they are never repeated:

1. `body { color: var(--card) }` on weather.html = cream inheritance.
   set `color: var(--text)` on the CONTAINER div, not the leaves.
   the container breaks the inheritance chain once.
   every leaf inside inherits correctly from there.

2. `display:none` removes a flex item from flow entirely.
   `flex-basis:100%` on a hidden element = no effect.
   use `flex-direction:column` on the card.
   expand is a plain block sibling below the main row.
   `display:none → .open { display:block }` — done.

3. the `.open` class, not the `hidden` attribute.
   css `display:flex` beats the `[hidden]` user-agent rule.
   a div with `display:flex` in the stylesheet is NEVER hidden
   by the `hidden` attribute. toggle `.open`. every time.

4. pre-render all expand panels with real data.
   do not inject content dynamically on click.
   the panel exists in the DOM when the page renders.
   click shows it. click hides it. no innerHTML writes on click.

5. color at the container:
   `body { color: cream }` — bar container resets to `var(--text)`.
   every child inside inherits dark. zero leaf rules needed.

the test file (expand-bar-test.html) got this right in one pass.
the weather bar files took three passes and never got it right.
the difference was isolation.

---

## spatial nav — the app architecture

one HTML file. one canvas. all pages always in the DOM.
the viewport moves. the pages do not.

```
app.html
  <div id="canvas">
    <div id="page-clock">       ← top center    (0, 0 in grid coords)
    <div id="page-settings">    ← middle left   (-1, 1)
    <div id="page-bars">        ← middle center ( 0, 1)  ← default view
    <div id="page-lights">      ← middle right  ( 1, 1)
    <div id="page-weather">     ← bottom center ( 0, 2)
  </div>
```

**the canvas rule:**

pages are `100vw × 100vh` each.
`translate(-col × 100vw, -row × 100vh)` always lands on a page.
any screen shape — portrait phone, studio display — snaps cleanly.
the content inside each page handles its own layout.
the canvas doesn't care about aspect ratio.

**snap, not slide:**

```css
#canvas { transition: transform 150ms ease; }
```

short transition is fine. smooth scroll is wrong.
the user is teleporting, not scrolling.
bumper to bumper — you only ever land on a page, never between.

```js
function goTo(col, row) {
  canvas.style.transform = `translate(${-col * 100}vw, ${-row * 100}vh)`
  current = { col, row }
}
```

**swipe:**

touch delta > threshold → `goTo(adjacent)`.
under threshold → snap back to current.
no libraries. `touchstart` + `touchend`. delta math. done.

**zoom-out overview:**

the one moment the user sees the whole grid.
earned by tapping the zoom-out button. not the default state.

```js
canvas.style.transform = `scale(0.3) translate(...)`
```

tap any page cell → `goTo(col, row)` + `scale(1)`.
this is also how `buildPreview()` works —
bars are never hidden, always rendered, always clonable.

**why single file wins:**

pages are always in the DOM.
`document.getElementById('bar-weather')` always finds the bar.
no iframes. no fetches. no show/hide timing bugs.
localStorage is the only persistence layer that matters.

**migration order:**

1. build `app.html` with `goTo()` + nav tabs
2. port `bars.html` content as `#page-bars`
3. port `bars/settings` content as `#page-settings`
4. port `clock.html` as `#page-clock`
5. port `index.html` (lights) as `#page-lights`
6. decommission the individual files one at a time

**build the page before wiring the canvas.**
every page opens standalone by URL during build.
`bars.html` still works after `app.html` exists.
wire the tab after you've stared at the page.

---

## working with AI

**build the thing before the builder.**
describe it. get it. stare at it. then spec it.

**just let it try first.**
don't over-spec. one prompt, one pass, one object.
if it fits — keep it. if not — nuke it. second attempt is fast.

**one pass at a port.**
tried to carry the layout over? no joy? throw it away.
the fresh build is faster than the fight.

**sequence: skeleton → zoom → polish.**
never add zoom before the skeleton stands.
font size is easy after. it is load-bearing before.

**get it out of your head.**
both intelligences need to look at the same object.
the sketchpad is how you do that.

**build the page before the nav.**
open it by URL first. wire the tab after.
`localhost:3024/pagename.html` works before any nav knows it exists.

---

## diagnostic discipline — the happy face rule

when something doesn't appear: don't open inspector first.

put a known-working element
where the broken thing should be.
red div. `z-index:9999`. hardcoded position.
does it show?

**yes →**
the element exists.
the bug is CSS visibility or a JS flag.
inspect the flag. read the code.

**no →**
the mount point or positioning context is broken.
fix that first.

this answers the question in ten seconds.
the inspector takes ten minutes
and shows you `display: none`
without telling you who set it or why.
you still have to read the code.

**console.log:**
belongs in ship pass.
not during iteration.
mid-build, it tells you what broke
after you already broke it.
the why is always in the code.

every minute in devtools mid-build
is a minute not building.

**the order, always:**
build pass: happy face.
refactoring pass: devtools.
ship pass: console + IC pass.

— sum + claude, june 2026

---

*tokens.css = structure. themes.css = color. never cross the streams.*
*the light IS the clock. dawn. not dog. not dow.*
*look into the void and tell me when it turns lavender.*
