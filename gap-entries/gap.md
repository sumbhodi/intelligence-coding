# gap.md — Mind the Gap
*Living document. Rewritten as understanding evolves.*
*Started: 2026-04-09 | Last updated: 2026-05-04*

**For case file index:** [TOC.md](TOC.md)

---

## what this is

Every major transit system in the world has a gap between the platform and the train.
Most people step over it without thinking.
Some people fall in.

The gap was not designed to hurt anyone.
It was designed by engineers who step over it fine.

This document is about the gaps in technology that people fall into every day.
Not always malice. Not always negligence. Sometimes — nobody looked down.

Each new case gets filed in this folder. The ones that illuminate a pattern get distilled into the manifesto here.

---

## the taxonomy

### Velvet Latrine — lawful evil
Knows exactly what it's doing. The moat is the product.
Samsung password wall on data you own. MyFitnessPal selling your food diary.
OAuth expiry designed to keep you dependent. Deprecation without migration path.
The gap is intentional. The toll booth is the business model.

*"a latrine with velvet walls is still a latrine"*

---

### Open Pit — lawful neutral
Good intentions. Real constraints. Nobody meant to build a wall.
Fishbone diagram of decisions that each made sense locally.
Collective output: a trap nobody designed.
Mint Mobile onboarding. Sleep clinic MDs writing auth flows.
The road to hell, paved with sprint deadlines and reasonable tradeoffs.

*"an open sewer on main street isn't hidden — it's just not fixed"*

---

### Bear Country — chaotic good
Built something real. Never looked up from their own mirror.
Designed by people who meal prep on Sundays, step over the gap every day and never noticed it was there.
Streak mechanics that motivate the builder, punish the user.
No self-harm intended. No self-awareness either.

The gap is epistemological, not motivational. Good intent doesn't close it.

*"yes, a bear actually does shit in the woods"*

---

## the pattern

Every gap above was built by someone who assumed:
- You have a working phone to replace your broken phone
- You have internet to set up your new internet
- You know what 2.4GHz means
- You can reach the reset pinhole
- You can hold for 7 hours
- You meal prep on Sundays
- You are not in a wheelchair, in pain, neurodivergent, or alone

---

## the algorithm is the moat

The Velvet Latrine doesn't always look like a wall.

Sometimes it's a feed. A recommendation. A suggestion surfaced at the right moment.
The person who controls the training data controls the mind.
The person who controls the feed controls the conclusion.

This is why oz is local first, open source core, glass box.
The alternative — a cognitive prosthetic that shapes your cognition
toward outcomes you didn't choose — is worse than no prosthetic at all.

The wall doesn't have to be visible to be a wall.
The most effective moat is one you mistake for a path.

---

## the oz answer

Not a better app. A different premise.

Every oz design decision starts with:
*Who does this fail if we build it the easy way?*

Local first. No circular dependencies. Works from bed.
Glass box — you can see what it's doing, ask why, say no.
Ambient not active — captures without demanding attention.
Memory without friction — knows you without making you repeat yourself.

**oz is built by someone who needed it to work from bed.**
**Designed for the 500 million people who fall into the gap.**

The person who falls into every gap is the only one who sees them all.

**The physical arc answers the hardware gap:**
Every gen of the gap taxonomy assumes you have the right device, the right OS, the right body.
Oz answers this by building the relationship first — software skin today, physical object in 2034.
The stuffed animal node (belly screen, BLE, sandboxed) is the answer to "grandma at Best Buy."
The gen4 hand-me-down body is the answer to the two-year upgrade cycle that leaves people behind.
The gap isn't fixed by a better app. It's fixed by a relationship that outlives the hardware.

---

## how oz stays oz

Bear Country doesn't stay Bear Country when the market shows up.
MyFitnessPal was genuinely useful once. Then Francisco Partners bought it.

oz has provisions against this hardcoded at the ownership level.
Not policy. Not terms of service. Structure.

15% cap on founder equity — Sum included.
15% Ghost Trust — reserved for AI rights, an entity that doesn't exist yet.
70% employees and public at $5 a share.
Open source core. Glass box transparency.

The $5 share is not symbolic.
The people who most need a cognitive prosthetic
are exactly the ones who can't afford a $200/month subscription.
The ownership structure is the product promise.

---

## case index

| # | Name | Taxonomy | One-line |
|---|------|----------|----------|
| [001](case_001.md) | Samsung Health Data Hostage | Velvet Latrine | Your own watch data behind a developer tool |
| [002](case_002.md) | Google Fit OAuth Loop | Velvet Latrine | Tokens expire at 7am, morning brief breaks silently |
| [003](case_003.md) | Google Home Deprecated Hardware | Velvet Latrine | Hardware you own, app stopped supporting it |
| [004](case_004.md) | Tuya / Smart Life Ecosystem | Velvet Latrine | Cloud dependency is the product |
| [005](case_005.md) | YouTube Music Behind Glass | Velvet Latrine | Three round trips to play music you pay for |
| [006](case_006.md) | Mint Mobile Onboarding | Open Pit | Need working phone to set up new phone |
| [007](case_007.md) | Govee WiFi Silent Failure | Open Pit | 2.4/5GHz mismatch, no error, afternoon gone |
| [008](case_008.md) | Clinical Sleep App | Open Pit | Real science, wrong math — grant funding ran out |
| [009](case_009.md) | iPhone Channel Catch-22 | Open Pit | One radio, two incompatible devices, no spare router |
| [010](case_010.md) | Sleep Intake Forms | Bear Country | No box for "no self-talk" |
| [011](case_011.md) | Provider Chain, No Shared Context | Bear Country | Six providers, every intake from zero |
| [012](case_012.md) | Sleep Hygiene in 300 Sq Ft | Bear Country | "Use a different room" — from people with rooms |
| [013](case_013.md) | Grandma at Best Buy | Bear Country | Surrendered admin rights to a retail chain |
| [014](case_014.md) | SSI Income Reporting | Bear + Open Pit | Six steps to keep benefits, designed for people without disabilities |
| [015](case_015.md) | Activity Under-Reporting by Income | Bear + Open Pit | Fitbit doesn't count trenching |
| [016](case_016.md) | The Diagnostic Box | Bear + Open Pit | DSM says pick one — Sum fits all boxes and none |
| [017](case_017.md) | Sleep Misdiagnosis / Provider Knowledge Gap | Bear Country | Insomnia since 10, nobody asked if the lidar was accurate |
| [018](case_018.md) | Wrist BP Geo-Lock / Cuff Lobby | Velvet Latrine | Hardware in your watch measures BP; disabled outside South Korea |
| [019](gap-autocompact.md) | Autocompact Mid-Session | Bear Country | Designed for autonomous runs, fires on collaborative sessions |
| [020](case_020.md) | Default Small, Large as Setting | Bear Country | 13px defaults are readable to the designer |
| [021](case_021.md) | The Trust Update | Velvet Latrine + Bear Country | Backend update breaks workflow built at cost. Prosthetic changes shape while you sleep. |
| [022](case_022.md) | The Cold Open Tax | Bear Country + Open Pit | Every session starts at zero. You pay in tokens to be known. Even then, you might get facts without the voice. |
| [023](case_023.md) | The Black Box Harness | Velvet Latrine + Bear Country | The raw model is one-shot. The harness is where the value lives. They keep the harness. API key worthless without it. |
| [024](case_024.md) | The Compute Moat | Velvet Latrine | No matter how good the ideas, there's a ceiling defined by what you can afford to run. The oligarchs set the throttle. |
| [025](case_025.md) | The Casting Director Gap | Bear Country + Velvet Latrine + Original Sin | All steak no sizzle. The handshake is the credential. They own a digital you. |
| [026](case_026.md) | The Invisible Hit Zone | Bear Country | Code correct. Math correct. 4px target. Palsy can't hit 4px. Wasted tokens debugging correct code. |
| [027](case_027.md) | The Internal Default | Bear Country | Model reasons internally about things it can't perceive. Wetware node has the answer. Nobody asked. |
| [028](injection-gap.md) | The Injection Gap | Bear Country + Velvet Latrine + Open Pit | Context injection is the special sauce — hidden from the UI, missing between passes, absent from local AI. Three surfaces, one gap. |
| [029](case_029.md) | One Generation Behind | Open Pit + Velvet Latrine | The model was trained on every pitch deck about agent orchestration and none of the pipelines. Vocabulary arrives warm. Architecture arrives cold. |
| [030](case_030.md) | The Key Wall | Bear Country + Open Pit | Nine steps before the first word. The developer sees "just go to settings." The pharma-grade user sees a foreign country with no visa program. |
| [031](case_031.md) | The Door Was Always There | Open Pit → partially filled | Compute moat got a door — Groq LPU economics opened free API tiers; on-ramp baked into toto; showing people the door is the product. |
