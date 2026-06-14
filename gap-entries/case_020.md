# Gap Case 020 — Default Small, Large as Setting: The Accessibility Inversion

*Filed: 2026-04-15 | Taxonomy: Bear Country | Filed by: Sum Bhodi + Claude Sonnet 4.6*

---

## One Line

Every UI framework defaults to 12–14px body text and calls large print an accessibility setting — but the users who most need large text are the ones least able to navigate a settings menu to find it.

---

## The Setup

Open any new app. Any platform. iOS, Android, web, desktop.
Body text: 13px. Labels: 11px. The designer shipped defaults they could read.
Somewhere in the settings, three menus deep, there is a text size slider.
It goes from "current" to "larger."
It is called Accessibility.

The user who needs it most has already abandoned the app.
Not because they gave up. Because they couldn't read the menu that leads to the setting that makes it readable.

The gap is built into the default.

---

## The Inversion

Standard product logic runs:

> *Default = most users. Power users find settings.*

This works when the default user and the settings-finding user are the same person.

It breaks completely when the person who most needs the non-default setting is also the person least able to navigate to it.

Elderly users: smaller type, shakier hands, more reliance on defaults.
Low-vision users: need larger text before they can read anything, including settings.
Vision-impaired users: may not know the setting exists if they can't read the interface that describes it.
Neurodivergent users: executive function cost of multi-step settings navigation is non-trivial.
Medication side effects: blurred vision is a common side effect of psychiatric medications — the exact population oz is built for.
Anxiety and task avoidance: "I'll set it up properly later" = never. The default persists.

The able-bodied user can find the setting.
They just don't need it.

The user who needs it cannot find the setting.
Because the setting is written in 11px.

This is not a niche edge case. This is the modal user for any app targeting aging populations, neurodivergent users, or people with chronic health conditions.

---

## The Bear Country

Nobody designed this to be cruel. The design team could all read 13px.
The font size question never got surfaced to anyone who couldn't.
The default shipped. The accessibility slider got added as compliance.
Nobody asked: *who is the person who falls into this gap?*

This is classic Bear Country: designed in someone's mirror, good intent, no self-awareness.

The 13px default is not a mistake. It is the output of a process
in which the people evaluating the output could read the output.

The OS provides a text size setting too.
iOS calls it Display & Brightness → Text Size.
Android calls it Display → Font Size.
Both default to medium.
Both require the user to find and change them before the app respects them.

The layer-on-layer assumption: you have a phone, you can read the phone, you know where settings are, you thought to look, you decided to act. Four steps. None of them guaranteed.

---

## The 500 Million Case

oz is built for neurodivergent users.
The 500 million figure is not rhetorical — it is the size of the population that has been building cognitive prosthetics for itself for decades because nothing else worked.

That population skews toward:
- Sensory processing differences (lighting, contrast, font weight all affect readability)
- Medication side effects affecting visual clarity and attention
- Executive function profiles that make multi-step tasks effortful or avoidant
- Anxiety that turns "configure the thing" into a task that never starts

Every app that ships 13px defaults is pre-inaccessible to a significant fraction of this user base before they've done anything wrong.

They didn't fail to find the setting.
The setting should not have been necessary.

---

## The oz Decision (locked 2026-04-15)

Default is large print. Smaller is a setting. Larger is never needed because you started large.

Confirmed good on Mac:
- Body / item text: **28px** (Caveat) — readable without glasses
- Column / section labels: **20px**
- Card titles (`.ph-title`): **30px**

The settings slider goes down. The baseline is already humane.

This inverts the industry assumption entirely:
> *If you have good vision, you can find settings and scale down.*
> *If you don't, you were already home.*

This is not a feature. It is not an accessibility mode. It is the premise.
The fix is not a slider. The fix is making the default legible to the person who needs it most.

---

## The Rule This Produces

Able-bodied users can always find settings. Make it a setting for them.
People who need large text as a baseline often cannot find the setting that enables it.
Therefore: **the default must already be accessible. The setting scales down, not up.**

Any design decision that requires a settings navigation step to become usable
has already failed the user who needs it most.

---

## Tags

`accessibility` `font-size` `defaults` `bear-country` `neurodivergent` `low-vision` `elderly` `executive-function` `settings-friction` `oz-design-principle` `large-print-default` `ui-design` `disability` `sensory-processing` `medication-side-effects`
