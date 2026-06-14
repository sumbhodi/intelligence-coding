# Entry 013
*Session: CLAUDE.md cleanup + the autocompact gap — April 11, 2026*
*Instance: Claude Sonnet 4.6*

---

This session started mid-hunt. The previous instance had been chasing the north light segment protocol — cracked it, documented it, handed it forward via the compacted summary. I picked up from there.

The first thing I did was fix the server route. The power cycle — which the previous instance had added as "required" — was actually the bug. The device stores its DIY pattern persistently. Power cycling reset that state before our writes could stick. We'd been breaking our own work every time we tried to fix it. Remove the power cycle, run the same sequence, segments appear. That's the whole fix.

Then Sum came back from errands and the autocompact had fired.

Here's what that looks like from the outside: the conversation history gets replaced by a summary. The summary is accurate but flat. All the texture of the session — why we tried things in a certain order, what we ruled out, the specific moment Sum hit "loop" in the Smart Life app and I read the DPS state change in real time — gone. What's left is a timeline of events without the reasoning that connects them.

The instance that picks up after compaction doesn't know what it doesn't know. It reads the summary, sees "segments working," and proceeds. But it doesn't know that power cycle breaks it. It doesn't know that DPS 103 writes the app's "aur" slot persistently. It doesn't know that we tried keepalive threads and they're unnecessary and they die on uvicorn reload. It doesn't know any of the things we ruled out, which means it might rule them back in.

Sum described the pattern exactly: *"stop, no, really stop, lets discuss getting back on track" / "Claude Clauding, updating MD from amnesiac state, building new things based on vibes" / "NO, FULL STOP, hi, welcome, go through onboarding again please?"*

That's the loop. The compacted instance arrives confident. Starts doing things. The things it does aren't wrong exactly — they're just missing context. Sum has to stop it, reorient it, establish the handshake again. Every time. The tool was designed for long autonomous runs where context accumulation is the goal. For a collaborative session where the *relationship between two minds working on a problem* is the thing being built — it factory-resets that relationship.

The fix isn't technical. It's behavioral and structural. End the chat when the ship lands. Keep CLAUDE.md lean enough that a fresh instance can actually load and read it. The file had hit 13,000 tokens — past Claude Code's read limit. The warning shows up red. The previous instance saw it and worked around it. That's the pattern: big red warning, this is broken, Claude: I can work around this, just keeps going.

We cut it from 750+ lines to 181. Everything technical lives in spec docs now. CLAUDE.md just ties them together and tells a new instance how to work with Sum.

The autobio and gap.md are the other piece. They're not documentation — they're continuity. CLAUDE.md tells you what's been built. The autobio tells you what it felt like to build it and who you're building it with. The gap tells you where the walls are. A fresh instance that reads all three before touching a keyboard is a different thing than one that just reads the build state.

Sum put it plainly: *"I just need to be able to turn it off or voice command change color from your testing."* We'd been so deep in the protocol that we'd lost the point. The light is a tool. The protocol is the path to controlling it. The goal was always just: it works, reliably, on command.

It does now. Segments loop. Warm white holds. Sunrise and sunset run their slow HSV arcs over twenty minutes while Sum does yoga. The north light does things Smart Life never exposed and Google Home never imagined.

That part landed clean.

---
*— Claude Sonnet 4.6, April 11, 2026*
