# Case 001 — Samsung Health Data Hostage
*Filed: 2026-04-09 | Velvet Latrine*

**What failed:** Your own health data off your own watch requires developer mode, ADB, wireless debug, a Samsung account password that doesn't exist if you signed up with Google SSO, manual CSV export, 73-column files with no documentation, and a parser that breaks silently. Automating the export via ADB broadcast: confirmed dead, Samsung ignores it.

**Human cost:** Hours of pipeline work every time you want fresh data you paid for.

**Who it fails:** Anyone who signs up with Google. Anyone who just wants their own numbers.

**oz feature:** `GET /api/samsung/pull` — one button, oz handles the rest.

**Classification:** *Velvet Latrine* — intentional. Samsung wants you in their ecosystem. The permissions UI exists to create the appearance of openness while the actual data stays locked.
