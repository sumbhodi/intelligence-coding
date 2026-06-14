# Case 002 — Google Fit OAuth Loop
*Filed: 2026-04-09 | Velvet Latrine*

**What failed:** Google Fit MCP OAuth tokens expire every ~13 hours. Re-auth requires terminal, browser flow, copy-paste. Health data pipeline breaks silently overnight. Root cause: app is in Google's "testing" mode, which caps refresh token lifetime.

**Human cost:** Wake up, morning brief broken, no sleep data, no idea why.

**Who it fails:** Anyone who can't run terminal commands at 7am. Anyone with state-dependent memory who can't reconstruct the fix under stress.

**oz feature:** Auto-refresh silently. Permanent fix: publish the OAuth app out of testing mode. One-time step.

**Classification:** *Velvet Latrine* — the testing mode cap is a structural incentive to stay dependent on Google's cloud stack. The fix exists. They chose not to make it default.
