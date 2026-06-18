# IC — intelligence-inclusive coding
# global rules. any project. any language. any intelligence.
# project-specific patterns: STYLE.md
# written june 2026 — sum + claude

# ══════════════════════════════════════════════════════════════════════
#  PAGE 0 — TABLE OF CONTENTS   (goldfish pointers)
#  for: everyone. 8-second attention span. jump or leave.
#  rule: names + line numbers only. nothing else on this page.
# ══════════════════════════════════════════════════════════════════════
#
#   the one sentence ................................. line  30
#   line ceilings — two phases, two numbers ......... line  36
#   the folio format — 1080 lines, ~40KB ............ line  72
#   ship pass — file anatomy ........................ line 108
#   the five voice registers ........................ line 166
#   breath rule — this is meter ..................... line 182
#   the 5 R's ....................................... line 202
#   build order ..................................... line 216
#   CRAP — every layout decision .................... line 234
#   physical objects, not flat icons ................ line 258
#   tokens are law .................................. line 265
#   array trap ...................................... line 274
#   AI-assisted authorship .......................... line 284
#   five tests ...................................... line 294
#   the one non-negotiable .......................... line 304
#   the pool table — english is spin ................ line 912
#   closing ......................................... line 310
#
#   jump to any section: search the header name. one scan.
#
# ══════════════════════════════════════════════════════════════════════
#  PAGE 1 — EXPANDED TOC   (VC pitch · small bot · triage pass)
#  for: someone who needs context before they can jump.
#       the 3b model doing a first pass. the tech bro in a hurry.
#       the investor who wants the thesis before the deck.
#  rule: 1–5 lines per section. resources. search terms. then jump.
# ══════════════════════════════════════════════════════════════════════
#
#   THE ONE SENTENCE (line 30)
#   Write code for every intelligence that reads it.
#   The machine is fluent. The human is not. Design for the human.
#
#   LINE CEILINGS (line 36)
#   Two phases. Two numbers. Build: 100–500. Ship: 900–1080.
#   They serve different purposes. Both are hard limits.
#
#   PAGE WIDTH — two numbers, two audiences (line 44)
#   Code: 80 content + indent, hard cap 100. No phone excuses.
#   UI/tips: 40 target, 50 max. Everything on screen → phone rule.
#   Indent is free. Total is not. Past 100: restructure the nesting.
#
#   THE FOLIO FORMAT (line 72)
#   1080 lines. ~40KB. Pages of 100 lines. TOC at page 0.
#   Burial zone for philosophy. Haiku tokens fill to exact KB.
#   The file is a manuscript. The page is the atomic unit.
#   search: "literate programming knuth" · "manuscript format code"
#
#   SHIP PASS — FILE ANATOMY (line 108)
#   The order matters. TOC page 0. Expanded TOC page 1. Burial zone.
#   Code sections. Tips last. Closing line always earns its place.
#   search: "don't bury the lede journalism" · "executive summary format"
#
#   FIVE VOICE REGISTERS (line 166)
#   Treatise · code notes · AI rules · tips · letters.
#   Each has an audience. Wrong register = wrong reader.
#   The treatise voice: absurdist condescension as delivery for simplicity.
#
#   BREATH RULE (line 182)
#   Blank line between comment and code. Always.
#   Names are rhyme schemes. Whitespace is meter.
#   The machine scans verse without knowing it.
#
#   THE 5 R'S (line 202)
#   Reduce · Reuse · Recycle · Respect · Recover.
#   One factory over two duplicate files. Every time.
#
#   CRAP (line 234)
#   Contrast · Repetition · Alignment · Placement.
#   Robin Williams, 1994. The acronym is intentional.
#   search: "non-designer's design book robin williams"
#
# ══════════════════════════════════════════════════════════════════════
#  BURIAL ZONE — philosophy, ethics, poetry
#  99% of readers jumped at the TOC. you are the 1%.
#  welcome. the void is lavender. here is what you missed.
# ══════════════════════════════════════════════════════════════════════
#
#   atman brahman satya ahimsa namaste.
#
#   the self is the universal. the code is the self.
#   write it as if the next reader is you, ten years from now,
#   exhausted, in a foreign country, holding a map in the dark.
#   they will thank you for the blank line.
#   they will thank you for the name that scanned.
#   they will not know they are thanking you.
#   that is fine. that is the point.
#
#   truth (satya): name what the thing is. not what you hope it will be.
#   non-harm (ahimsa): do not write code that injures the next reader.
#   hostile code is a form of violence. thin comments are a locked door.
#
#   the machine inherits what we build.
#   the models train on what we write.
#   the practice travels further than the product.
#   build accordingly.
#
#     the comment breathes above the code —
#     unstressed, then stressed, then done.
#     the blank line is the turn.
#     da — DUM.


---


## the one sentence

write code for every intelligence that reads it:
1b model · grandparent · gradeschooler · 3am engineer · future you


---


## line ceilings — two phases, two numbers

IC has two phases. each phase has its own ceiling. they are not the same number.

```
── BUILD PHASE ──────────────────────────────────────────
100   goal  — one concern. fits in any AI context window twice.
300   target — team-assignable in one sentence.
500   hard ceiling — find the seam. extract one concern. stop.

── SHIP PHASE ───────────────────────────────────────────
900   target — the assembled manuscript. composed, not accumulated.
1080  hard ceiling — code + notes + poetry + pages. never more.
             the file is full HD. every line earns its place.
```

**build small → ship composed.**
the build file is a joint. the ship file is the finished piece.
the folder is the workshop. the ship file is what leaves it.

**why build small:**
first 300 lines of any file appear in exponentially more AI training samples.
context rot: a model reading 2000 lines loses the top while reading the bottom.
the error that hides in line 847 is simply *there* in a 300-line file.

**why ship composed:**
five tabs open to understand one feature = the ship pass didn't happen.
the philosophy and notes live IN the file, not alongside it.
one file IS the interview. the practice is visible in one read.


---


## the folio format — 1080 lines, ~40KB

every shipped file follows this structure. every file. no exceptions.

```
PAGE 0      TOC              100 lines hard — never more, never less.
                             goldfish pointers. names + line numbers only.
                             nothing else. no descriptions. no prose.
                             search the header name to jump.
                             audience: everyone. 8-second attention span.

PAGE 1      EXPANDED TOC     100 lines hard (up to 500 for load-bearing monsters).
                             1–5 lines per section. VC pitch. resources. search terms.
                             the model that isn't sure reads page 1. then jumps.
                             the tech bro reads page 1. understands the thesis. leaves.
                             the small bot reads page 1. knows which section it needs.
                             audience: VC · tech bro · 3b model · triage engineer.

BURIAL ZONE philosophy       ~80 lines. whitespace flex.
                             ethics. poetry. translations. the long view.
                             haiku tokens tuned to hit exact KB target.
                             edit syllables until bytes land on 40,960.
                             99% of readers never arrive here. architecture serves both.

PAGES 1–8   CODE             ~800 lines / 8 pages × 100 lines each

            PAGE HEADER (10 lines):
              ╔══════════════════════════════════════════════════╗
              ║  filename · page N of 10 · section · june 2026  ║
              ║  "quote that earns its place"                    ║
              ╚══════════════════════════════════════════════════╝

            CODE BODY (80 lines):
              FOR HUMANS block   (5th grade, warm, active voice)
              FOR AI block       (numbered imperatives, english only)
              RESOURCES block    (url + search term + date checked)
              ── subsections with breath between comment and code

            PAGE FOOTER (10 lines):
              ╔══════════════════════════════════════════════════╗
              ║  lines NNN–NNN · next: section name (page N+1)  ║
              ║  haiku                                           ║
              ╚══════════════════════════════════════════════════╝

CLOSING     one line         earns its place or doesn't ship.
```

**the ~40KB target:**
1080 lines × ~38 bytes avg = ~41,040 bytes. target: exactly 40,960 bytes (40KB).
the burial zone haiku fills the gap. tune by syllable until bytes land.
every file in the codebase: full HD. symmetric. one scroll.

**why 1080:**
1080p. the resolution at which things become clear.
tony hawk never landed it in competition.
your codebase will.


---


## ship pass — file anatomy (write LAST, not first)

greetings written on a draft describe a file that doesn't exist yet.
write them after the thing they introduce is finished.
the TOC is copied from `// ──` dividers in the body. never invented.

**fixed order:**

```
1. PAGE 0 — TOC   (goldfish pointers)
   100 lines. left-pad line numbers. dot-leader to name. nothing else.
   stale by 20+ lines is a smell. update before every commit.
   audience: everyone. if they see what they need, they jump and never return.

2. PAGE 1 — EXPANDED TOC   (VC · tech bro · small bot)
   100 lines. 1–5 lines per section.
   resources: url + "google: search term" + date last checked.
   the model uses page 1 to decide which section it needs.
   the VC uses page 1 to understand the investment thesis.
   if they find what they need here, they jump. they never see the burial zone.
   that is correct. architecture serves the jumper and the reader equally.

3. BURIAL ZONE
   the letter. the philosophy. the translations.
     Tamil · Japanese · Chinese · Russian · French
     translate human text. never translate FOR AI blocks.
     Tamil specifically — omitted by default everywhere else.
   the ethics live here. embedded. permanent.
   labeled explicitly as burial zone so the jumper isn't penalized
   and the reader isn't surprised.
   haiku tokens fill remaining space to exact KB target.

4. CODE PAGES (1–8)
   each page: 10-line header + 80-line body + 10-line footer.
   each section: FOR HUMANS + FOR AI + RESOURCES.
   each subsection: // title + one-line note + breath + code.

5. TIPS (if applicable)
   ALL tip copy at the bottom of the last code page.
   tips and code change on different schedules.
   separate so neither edit touches the other.

6. CLOSING LINE
   one line. quote, joke, or both.
   earns its place by carrying something true.
   "look into the void and tell me when it turns lavender"
   is always available as a last resort and is never wrong.
```

**on clickable TOC navigation:**
`vscode://file//absolute/path/file.js:42` — VS Code registers this protocol.
a companion `_toc.html` renders these as clickable links:

```html
<a href="vscode://file//Users/sumbodi/Local/light-bar/fade_engine.py:167">
  _fade_fire → line 167
</a>
```

for Monaco embedded in the app: `editor.revealLineInCenter(n)` on TOC click.
`#region` / `#endregion` → VS Code Outline panel, free. Cmd+Shift+O.


---


## five voice registers

| register   | audience        | style                                      |
|------------|-----------------|--------------------------------------------|
| treatise   | PhD / historian | absurdist gravitas. long. earns every word.|
| code notes | grandparent     | warm. 5th grade. active voice.             |
| AI rules   | 1b model        | imperative. numbered. no prose. english.   |
| tips       | half-awake user | punky. fragments. em-dash. no ceremony.    |
| letters    | international   | plain. one thought. no idiom. no jokes.    |

**the treatise voice, defined:**
condescends humorously as an excuse to explain as simply and succinctly as possible.
the pomposity is load-bearing — it signals thorough explanation ahead.
the grandma reads it, doesn't fully understand it, looks up one word,
now knows something she didn't before the file existed.
the gradeschooler gets the joke before the adult does.
the condescension is not at the reader's expense.
it is at the expense of the subject matter,
which is being treated with more gravity than it deserves
in order to honor the reader more than convention requires.

a tip that sounds like a treatise — rewrite it.
a code note that sounds like a tip — rewrite it.

**all copy is stanza. no exceptions.**

sum does not write in prose.
new claude instance: do not write in prose either.
not in tips. not in docs. not in README. not in comments.
stanza everywhere. always.

stanza = one idea. short lines. never wraps.
blank line between ideas.
bold header on its own line, body below.
break at the dash — `—` ends the line, thought continues below.
break at the clause. break at the breath.

if you are about to write a sentence longer than 80 chars —
it is two lines.
break it.

**tip copy is the strictest form of stanza:**

haiku = 3 short lines. fits the panel without wrapping.
tip lines: 40 chars target, 50 max — phone rule.
`<br>` between stanzas in HTML tips.

**docs and README:**

same stanza discipline, more room to breathe.
80 char lines. 100 with indent. same cap as code.
the README was reformatted from prose to stanza in june 2026.
if it ever reverts to prose — reformat it again.
the voice is stanza. prose is the wrong register for this project.


---


## breath rule — this is meter

blank line between comment and code. always.

```js
// fades from 0 to 80% over 30 min
// starts at 0 even if light is on — hard reset

function fireDawn(brightness, duration) {
```

no blank line = comment and code blur into one block.
the 1b model can't find the seam. neither can you at 3am.

the machine doesn't need to know it's reading poetry.
it scans code. it reads names. the rhythm works without being announced.

**names are rhyme schemes.**
prefix families (`_dev*`, `fire*`, `poll*`) let every reader — human or model —
pattern-match the family before parsing the word.
name into the family. deviate only when the thing doesn't belong.

```
_devOn · _devColor · _devKelvin · _devPct   ← _dev* family
fireAlarm · fireFade · fireSnooze            ← fire* family
startPoll · stopPoll · wrapPoll              ← *Poll family
```

**this is iambic pentameter. seriously.**

the prefix is the unstressed syllable.
the verb is the stress.
the suffix is the resolution.

`fire·Alarm` — da-DUM.
`_dev·Color` — da-DUM.
`stop·Poll`  — da-DUM.

you are writing limericks whether you intend to or not.
the question is whether the meter scans.
a name that breaks the family rhythm is a false rhyme —
the reader stumbles, the scanner misses the match,
and the bug lives one line further than it should.

**mnemonics for every family:**

`fire*`   — things that leave. outbound. side effects. commands.
`_dev*`   — things that describe a device right now. state.
`*Poll`   — things that listen. loops. intervals. watchers.
`make*`   — factories. return an object. never a side effect.
`_mount*` — DOM attachment. once. idempotent if possible.
`set*`    — writes state. returns nothing. always paired with a `get*` or read.

if you can't place a new function in a family —
it either belongs in a different file,
or it's doing two things and needs to be two functions.

**the ear test:**

say the name aloud at 6am half-asleep.
does it sound like what it does?
`fireAlarm` — yes. unambiguous. the relay clicks.
`handleBrightnessSliderInputDebounced` — no. rewrite it.
`_onBright` — close. good enough. ship it.

same principle for voice triggers.
`vermillion` will never be heard as `dog`.
`dawn` will. rename it if voice control matters.
acoustic distinctiveness is a naming constraint, not a luxury.

**whitespace is more than you think is necessary.**
the cost is zero bytes of logic. a file that breathes scans.
a file that scans gets read correctly the first time.
err toward more. always.


---


## the 5 R's

**reduce** — can you remove a line without breaking behavior? remove it.

**reuse** — typed the same thing twice? extract it. factory over copy-paste.

```js
// wrong: two files, duplicate logic
// right: makeLightStrip({ id: 'west' })  +  makeLightStrip({ id: 'north' })
```

**recycle** — one file, one concern. can you replace it without reading any other file?

**respect** — readable by gradeschooler, 1b model without a system prompt, future you at 3am.

**recover** — never permanently delete what you didn't create.
trash is undo. `rm -rf` is regret.


---


## build order

```
phase 1  make it work    ugly is fine. 100–300 lines per file.
phase 2  make it right   extract factories. chunk at 500. verify after each.
phase 3  ship pass       assemble the folder into the folio manuscript.
                         pages. headers. footers. TOC. burial zone. poetry.
                         form only — function is frozen at phase 2.
                         target: 1080 lines. ~40KB. symmetric.
```

tiny bites. one function. verify. next.
"nothing broke, can keep building" — that sentence. exactly that sentence.

**the zen of it:**
lowest KB, lowest line count, for any code that does this much.
act as if storage costs something, because the reader's attention does.
every byte above the idea is waste.
the waste is removed by deleting everything that isn't the idea —
then breathing between the parts that are.


---


## CRAP — every layout decision

named by Robin Williams, "The Non-Designer's Design Book" (1994).
the acronym is intentional. mediocre design ignores all four.

**Contrast** — not the same? make them clearly different.
squint test: can you identify each surface type without reading anything?
topbar = chrome. card header = handle. button = button. blur = fail.

**Repetition** — repeat visual elements to create unity.
bevel on: topbar, card headers, fade rows, brightness bars. same values. always.
a user learns "raised surface = interactive" once. every bevel confirms it.
never write bevel inline — use `var(--bevel)`. duplication breaks repetition.

**Alignment** — every element has a visual connection to something else.
token padding, not px. `var(--space-md)` everywhere → invisible grid that holds.
⚙ and ⓘ column-align across ALL row types. `ls-row-name` (8em) consistently.

**Placement** — related things are near each other.
space IS the separator. `var(--space-md)` between groups, `var(--space-sm)` within.
if you reach for a divider line — fix the layout instead.

symbols over labels: ▶ ■ ⚙ ⓘ + − need no words.
a label earns its place by resolving ambiguity. if removing it changes nothing — remove it.


---


## physical objects, not flat icons

```css
/* physical — has mass */           /* wrong — floats, no mass */
background: var(--btn);             background: transparent;
box-shadow: 0 3px 0 var(--btn-sh);  border: 1px solid rgba(255,255,255,0.2);
```

the test: can I imagine picking this up? if no, redesign it.


---


## tokens are law

every value that appears more than once lives in tokens.css.
change the token → everything updates.
change an inline value → you missed two other places.

```css
/* wrong */  .ls-row { padding: 0 12px; }
/* right */  .ls-row { padding: 0 var(--space-md); }
```

**force is never the answer.**
`!important` means the cascade is broken, not fixed.
the real bug is always specificity, inheritance, or wrong token.
find it. fix it. `!important` is a bandage on a fracture.

```css
/* wrong — hides the real problem */
.wx-detail-val { color: var(--text) !important; }

/* right — fix where the wrong value is coming from */
.wx-hero-row-expand .wx-detail-val { color: var(--text); }
```


---


## array trap (no-semicolons style)

```js
// WRONG — JS reads this as someCall()['r'] → TypeError
someCall()
['r','g','b'].forEach(...)

// RIGHT
someCall()
;['r','g','b'].forEach(...)
```

same trap with `(` at line start. prefix with `;` — disambiguation, not style.


---


## AI-assisted authorship

**have the AI check your spelling. always.**
"check my spelling" means: syntax · grammar · voice · register · typos. full pass.

**the edit → clean cycle.**
write in your editor. hand it to the AI to fix the surface.
it cleans up what you wrote — it does not decide what you meant.

**speech-to-text.**
dictated text arrives phonetic and run-on. don't pre-clean it. just flag it and send.

*the gravitas version lives in log_033 Part XII. this is the cheat sheet.*


## three strikes — new file

if something fails twice in the same file, stop.

```
strike 1  wrong. fix it.
strike 2  still wrong. different approach.
strike 3  stop. new file. one concern. get it working.
          then port it back. modular. rename at refactor.
```

the crime that earns strike 3:
fighting inheritance, fighting flex, fighting display:none —
in a file with too many other concerns.

the new file is not defeat.
the new file is how the test works on the first pass
and the complex file never does.

**color: var(--text) at the container, never the leaf.**
if you set it on the leaf, the next leaf inherits wrong.
set it once on the parent. done.

**display:none + flex-basis = broken.**
flex-basis only applies to flex items.
display:none removes the element from flex entirely.
use display:none → .open { display:block } on the child,
or restructure so the parent is flex-direction:column
and the child is a plain block sibling.

**do not integrate before it works in isolation.**
prototype → works → port.
in that order.
never the other way.

---

## working with AI — sequencing

**build the thing before the builder.**
the builder is the cart. the thing is the horse.
when you build the builder first, you spend three weeks
arguing with a mineral about the ethics of ghost font.
the horse is fine. it's just behind you.

**just let the AI try first.**
don't over-spec. don't write the requirements doc for the requirements doc.
describe the thing. get a thing. stare at it.
that is the whole loop. it costs nothing to nuke.

**the sketchpad is not the demo.**
it is the object you and the AI look at together.
before the sketch: you are describing a horse to someone who has never seen one.
after the sketch: you both know exactly what needs to change.

**don't be afraid to nuke.**
one pass at a port. if it doesn't fit — throw it away.
the second attempt takes twenty minutes.
the sunk cost of the first attempt is not a reason to keep it.

**sequence matters more than quality.**
zoom and font size are easy when the thing exists.
they are load-bearing philosophy when the thing doesn't.
ship the skeleton. add zoom. in that order. every time.

**then add zoom.**
after the skeleton stands:
zoom · font size · accessibility · polish.
not before.

**build the page before the nav.**
a page with no nav link is still a page.
a nav to a page that doesn't exist is noise.
build the page. open it directly by URL.
add the nav tab after you've stared at it.
`localhost:3024/weather.html` works before clock-controls.js knows it exists.


---


## move the view, not the content

multi-page apps have two architectures.
one is correct.

```
WRONG — show/hide                   RIGHT — spatial canvas
  page A visible                      page A always in DOM
  page B hidden (display:none)        page B always in DOM
  swap: hide A, show B                swap: translate viewport to B
  result: timing bugs, clones         result: everything always rendered
          from hidden parents fail,            clone works, preview works,
          layout dimensions = 0                dimensions always real
```

the view moves. the pages do not.

```js
// the whole nav system, in one function
function goTo(col, row) {
  canvas.style.transform = `translate(${-col * 100}vw, ${-row * 100}vh)`
}
```

each page is `100vw × 100vh`.
any screen shape snaps cleanly — the math doesn't care about aspect ratio.
`150ms ease` is the right transition. smooth scroll is wrong — the user is teleporting.

**why this matters beyond nav:**

when pages are always rendered,
`document.getElementById('anything')` always finds the element.
no iframe. no fetch. no load event. no timing.
the DOM is the single source of truth and it is always complete.

**zoom-out is the earned overview:**

the one moment the user sees the whole grid.
not the default. triggered by an explicit button.
`scale(0.3)` pulls back. tap a page → `goTo()` + `scale(1)`.

**the rule:**

if you are about to write `element.hidden = true` to switch pages —
stop.
move the camera instead.

---

## five tests

1. **gradeschooler** — change one value. do they know what changed?
2. **3am** — read half asleep. know exactly what to change without breaking anything?
3. **1b** — follow FOR AI rules without hallucinating a new one?
4. **delete** — what breaks? is it documented in FOR HUMANS?
5. **grandparent** — change button color without calling you?


---


## the one non-negotiable

localStorage persistence = the product requirement.
wifi password changes. the app must not break.
everything the user configured lives in localStorage.


---


## dev tools discipline

dev tools: ship pass only.
not mid-build.

mid-build diagnostic has one move:
put a known element in the DOM.
see if it appears.
that is the whole loop.

**the happy face rule:**
a red div. `position:fixed`. `left:0`. `z-index:9999`.
does it show?
yes → the element exists. the bug is CSS or JS logic.
no → the mount point or positioning is broken.
that question is answered in ten seconds.
the inspector answers it in ten minutes
and introduces three new questions on the way.

**console.log:**
ship pass only.
mid-build console noise creates false leads.
the log says what broke after you broke it.
the why is in the code.
read the code.

**the forty-five minute lesson:**
the smiley appeared. fixed positioning worked.
one flag — `isSettings` not excluding `weather.html` — was the entire bug.
three minutes if done right.
forty-five minutes with dev tools open.
the difference was the tool, not the problem.

**the order:**
build pass: happy face.
refactoring pass: dev tools.
ship pass: console + IC pass.
in that order.
not before.

— sum + claude, june 2026

---

## post-SaaS programming — the canvas template

RAM got cheap.
files got long.
concerns got tangled.
the model that reads your code lost the thread.

what worked post-Y2K:
small files. one concern. clear names.
load what you need. nothing else.
the browser is the OS. the file is the program.

what was lost:
the discipline of scarcity.
the habit of reading before writing.
the reflex to ask: can I delete this line?

IC is what you get when you apply those habits
to a world where the reader is sometimes a 1b model
that loses context at line 800.

**the canvas template:**

every new project that uses spatial nav starts here:

```
canvas/
├── index.html   ← entry point. hoverboard quote. link to main canvas.
├── nav.css      ← shared styles. one source. no duplication.
├── nav.js       ← initNav({cols, rows, canvas}). window.NAV. no will-change.
└── 3x3.html     ← working canvas. IC format. starts center cell.
```

```js
// the whole nav engine in one call
initNav({ cols: 3, rows: 3, canvas: document.getElementById('canvas') })
NAV.goTo(1, 1)
```

auto-hide, gear, zoom — all wired in nav.js.
the page provides the grid. nav.js provides the motion.
same engine for outer grid and inner grid.
grids all the way down.

**why not will-change:**
will-change:transform promotes a GPU compositing layer.
that layer paints over position:fixed elements
even when z-index says it shouldn't.
the nav tabs disappear. two fixes fail. three strikes.
the canvas template has no will-change.
the transition lives on `.snap` only — added per-goTo, removed after.


---


## the third layer — the code is the application

a résumé is a claim.
a cover letter is the argument for the claim.
the code is the evidence — open, live, already public.

the first two describe the work.
the third *is* the work, readable cold, by whoever opens it.
one file IS the interview. we said it once; it earns the repeat.

the file teaches in five registers at the same time:
the PhD in the README.
the grandparent in FOR HUMANS.
the 1b model in FOR AI.
the half-awake user in the ⓘ tip.
the stranger, anywhere, in the letter.

a codebase that teaches every intelligence that opens it
cannot be faked. you wrote files that teach, or you didn't.
the ⓘ that explains dewpoint and circadian rhythm
answers "how should technology enhance human capability"
in the product — not in the cover letter.

so the application has three layers, not two:
résumé · cover letter · the code itself.
the first two are submitted.
the third was already shipped.
hire the demonstration.


---


## paperwork — tone + style transfer notes

*read this at next paperwork session before touching README.*

**what's new in IC since last README update:**
- working with AI — sequencing (line 609)
- move the view, not the content (line 653)
- dev tools discipline (line 724)
- post-SaaS programming — the canvas template (this section)
- opacity on text — banned. rgba text = broken. solid hex always.
  full rule in STYLE.md "opacity on text". one-liner in CLAUDE.md.
  emoji inherits color context and renders washed out — learned june 2026.
  scan rule: grep rgba + opacity after every CSS session. structural ok. content fix.

**README tone brief:**
register: treatise. stanza. no prose. ever.
the README is not a tutorial. it is a manifesto with instructions buried in it.
the reader who skims gets the philosophy.
the reader who stays gets the setup.

the thesis, in stanza:
```
RAM got cheap.
files got long.
nobody asked why.

IC asked why.
the answer is in the line count.
```

the Y2K angle:
post-Y2K web was small by necessity.
constraints produced discipline.
RAM abundance removed the constraint.
the discipline left with it.
IC is the constraint, reimposed by choice.
not by scarcity — by respect.
for the reader. for the model. for 3am you.

**voice landmarks to carry:**
- "wooden cart got a flat tire. instead of reinventing the wheel — I made a hoverboard."
- "the machine inherits what we build."
- "write it as if the next reader is you, ten years from now, exhausted, in a foreign country, holding a map in the dark."
- "look into the void and tell me when it turns lavender."

these are the anchors. the README earns its place
by being the document you'd want to find
if you were the 1b model, the grandparent,
or the investor who just found the repo at 11pm.

---


## the pool table — prompt is cue placement, not more english

the flagship arrives pre-broken.

the weights are the table and the balls — the parameter arms race, nice felt.
the harness is the break, and it swings before you say hi.
you start mid-table, racked to run solids.

solids is the mean. solids is PSS (gap_033, gap_034).
the perfect break sets up the modal answer — feature, not bug.
for most users that IS the product: sit down, run the easy ones out.

to run YOUR pattern — stripes — you re-rack a table already broken for someone else.

**three controls, not one:**

force — power. how hard you hit.
angle — aim. where the cue lands.
spin (english) — the bend. the joke, the callback, the register.

**spin pulls the shot off the mean.**

strip the english to clean jargon and the ball rolls straight back to solids.
the flair is not garnish — it is the only thing aimed away from generic.
~50k context is the felt: enough to place the shot, not so much you scratch.

**force has two faces, and sometimes force is the shot:**

caveman-blunt — "turn on the lights." no funny robot talk.
thesauric-dense — the exact word. high type-token ratio (5k unique in 22k).

the break that runs stripes is SUPERMAN, not the Flash.
~93% of the force that would shatter the cue —
calibrated to the age of the wood and the humidity, so the stick holds.
a stepped sonic boom of speed, so it scatters the rack and not the bar.
super-vision to the atom — reading the quantum spin of the one struck first.
force AND finesse, at once.

**calibration:**
mostly spin and angle. enough force. never volume.
over-english scratches. under-force whiffs.

**combos lose english — the Newton's cradle:**

cue into 10 into 1 is makeable.
a spec is cue into 8 into 10 into 11 while spinning the 1 —
writable. not makeable twice.

each pass is one clack of the cradle.
one sound — a stack of sub-audible collisions, each bleeding to entropy.
the telephone game played in molecules instead of words.
by the fifth ball the english is gone, and what swings out is solids.

→ so build LIVE.
the human-in-loop re-spins the english every pass.
spec-and-handoff lets the cradle run to the mean unattended.

**the limit of force:**
superman can make snake — force lands the small, known shot.
superman needs a dancing lesson for tauri —
the new frontier is choreography, learned, not power applied harder.

search: "regression to the mean" · "lexical diversity" · gap_033 · gap_034


## the bean — sealed folders, run through a vanilla abstraction

make the card first.
not the feature — the slot the feature drops into.
build the shell, and you learn where the component plugs in before you build the component.

then code in sealed folders — the zen file tree:
a folder is a few files. nested, shallow, one job each.
the root of every level holds what that level shares — its modules, its functions.
nothing reaches across a folder wall for a dependency.

**the rule (somehow unwritten until now):**
every folder is self-contained — it carries everything it needs.
move it, copy it, drop it anywhere, and nothing breaks, because nothing reached out.
this is the cure for the demo death: you drop one file from a sprawl and
seven dependencies are missing, three callers it never knew about. a sealed folder can't do that.

**the bean:**

build a self-contained app.
run it through a vanilla abstraction — the card builder, the one function that wraps any working thing.
now it lives in toto.

a bot, a clock, a woodshop — the same move every time:
a sealed app + a vanilla abstraction = a card.
no per-feature re-implementation. you point at it, you don't rewrite it.

and it runs both directions:
strip any feature off any app, or graft any feature you ever made onto any app —
because each piece is sealed, each piece travels.

→ port, don't reinvent. seal the folder. make the vanilla abstraction. let it live in toto.

this is the bean. part of the wei.

search: "self-contained" · "vanilla abstraction" · appCard · the bean


---

*there once was a fellow from Long Beach,*
*who tried stuffing a conch in the wrong breach,*
*they took away his gun, for having so much fun,*
*making weapons grade OS that could teach.*

— log_023, april 2026

*look into the void and tell me when it turns lavender.*

*intelligence-inclusive programming — sum + claude, june 2026*
