# case_030 — The Key Wall

*Filed: 2026-05-08*
*Taxonomy: Bear Country + Open Pit*

---

## The Gap

Chat interface. Works beautifully. Smart. Responsive. Designed for the person who needs it most.

Nine steps before the first word.

1. Have a GitHub account
2. Know what that is
3. Log in (remember the password)
4. Click your avatar
5. Settings
6. Developer settings (buried at the bottom of a long sidebar)
7. Personal access tokens
8. Generate new token
9. Copy it (tiny button, easy to miss)
10. Return to the chat. Find the gear. Open settings. Find the key field. Paste.

Ten steps. The average user drops at step 2. The pharma-grade target drops at step 1.

The mother of the person who built it drops at step 1.

---

## Who Falls In

Not edge cases. The majority.

- Anyone without a GitHub account (most people)
- Anyone with motor control issues (copy-paste fails)
- Anyone with cognitive load issues (ten steps is ten too many)
- Anyone for whom "developer settings" is a foreign country
- Anyone who closes the tab before finishing and loses the token
- Anyone who pastes it wrong and gets an error with no explanation

The pharma-grade target — 5-year-old with Alzheimer's and palsy, half-blind, 500 neuro-divergent still — doesn't finish step six.

---

## Why It Exists (Not Malice)

**Bear Country:** The developer who built GitHub Models authentication has had a GitHub account since 2009. Navigates developer settings the way they navigate their kitchen. The nine steps don't register as nine steps — they register as *just go to settings.* Good intent. Real rate-limiting reason. Nobody looked down.

**Open Pit:** The API requires authentication. Without it, anyone hammers the free servers and Microsoft loses the business case. The wall exists for real infrastructure reasons. Nobody designed it to exclude anyone. The fishbone diagram of decisions each made local sense. Collective output: a trap nobody designed.

The gap is epistemological, not motivational.

---

## The Underlying Pattern

Every key-based auth system makes the same assumption:

> You know what an API key is.
> You know where to generate one.
> You can navigate the settings of a developer platform.
> Your hands work well enough to copy a 40-character string.
> You won't close the tab before you finish.

None of these are true of the population that most needs AI assistance.

The key wall doesn't look like a wall from the inside. It looks like *just go to settings.* That's what makes it Bear Country — the gap is invisible to the builder.

---

## The oz Answer

toto on Hugging Face Spaces.

HF token in HF Secrets — never touches the browser. HF pays for inference on their free tier. User opens URL. Types. Gets a response.

Zero steps.

When the free tier exhausts, the message is:
> "Free quota for today used up. Try again tomorrow — or add your own key to skip the queue."

The wall becomes a door with a sign on it. The queue is honest. The exit is visible. The seams show.

The funnel goes further: toto teaches you that local is better. oz installs it. One green button, hardware-aware. Dolphin runs at home. No cloud, no key, no wall.

The destination was always local. The free cloud entry is the on-ramp.

**The person who couldn't get past step one eventually runs AI on their own machine.**

That's not aspirational. That's the architecture.

---

*Related: case_022 (Cold Open Tax), case_023 (Black Box Harness), case_028 (Injection Gap)*
*oz answer: toto-funnel-spec.md*
