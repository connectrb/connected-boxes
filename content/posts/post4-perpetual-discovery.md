---
title: "Post4: Archaeology of Enterprises"
date: 2026-04-07T00:15:48+10:00
# bookComments: false
# bookSearchExclude: false
# bookPostThumbnail: thumbnail.*
---

I can't remember how many times I have faced the same dilemma every time I have started working on a new program -
 - How do I quickly understand what has been built so far?
 - How do I know which systems are talking to each other?

> Knowing what exists today so that we can design a better future is always one of the biggest hurdles of any project.

## The mystery of perpetual discovery

It has alluded me all throughout my career: **how can any organisation have the right amount of information about Technology Systems?** It's not that tools don't exist to capture this information, but then, keeping those tools updated is a challenge. Understanding which teams use which tools for delivering which processes is easy to capture when it all starts, but much harder to keep up to date as time progresses and multiple projects get delivered.

> Documentation is always a snapshot. And snapshots get stale the moment the camera clicks.

## The Archaeology (aka Discovery) Phase

I call this phase, The Archaeology, not because I'm being dramatic (well, just a little), but because that's exactly what it feels like.

The archaeology always starts with looking at existing documentation. It's finally time to make use of the expensive Configuration Management Databases (CMDBs), assuming they will solve the mystery of current state. I don't have any statistics to prove it except in my experience: I have never been able to rely on information in CMDBs.

They offer a starting point beyond which it always turns into a scavenger hunt for that one person who has been in the company for 10 years and "knows where the bodies are buried." Documentation is mostly a snapshot in time. Human knowledge is the only thing to rely upon, and is often the most fragile part of the system.

The Archaeology Phase is consistently a one-time tax we pay at the start of a project. In my experience, this one-time tax ranges between 10-20% depending upon the size and complexity of the program.

> One-time tax to find out what we have built so far so that we can change it again for another future archaeologist to discover.

---

## The Agile Paradox: Helper and Hindrance
Agile was supposed to solve the "Big Upfront Planning" problem, but it has created a different problem.

When you're sprinting with velocity, documentation is the first thing sacrificed. Not because teams are lazy. But because there's always another story waiting. Another feature. Another Release.

The result? High-velocity feature factories leaving trails of undocumented ruins behind them.

## The Afterlife: Making Documentation Survive
How do we stop documentation from becoming a static tombstone the moment the project team disbands?

* **Shift from 'Authoring' to 'Curating':** Documentation shouldn't be a project deliverable; it should be an operational requirement.
* **Living Maps:** Documentation must live where the work happens—in the code, in the READMEs, or linked directly to the monitoring tools.
* **The 'Kind Ancestor' Rule:** We need to leave the site better than we found it. If the documentation doesn't survive the "handover," the project isn't actually finished.

## The Veteran’s Lens: Discovery after 25 Years
After 25 years in the trenches, my approach to discovery has shifted from **gathering data** to **developing intuition.**

1. **Interview the 'Keepers of the Flame':** Every org has someone who remembers *why* a weird workaround was implemented in 2012. Find them. Their stories are worth more than any CMDB.
2. **Expect Entropy:** Start every project assuming the "source of truth" is actually a "source of half-truths."
3. **Listen for the Silences:** Often, the biggest risks are in the systems that "just work" and haven't been touched in five years. Those are the most dangerous ruins to disturb.
4. **Trust the traffic:** Diagrams may lie, but logs don't. If possible, access real-time telemetry from systems.

## The archaeology continues
Here's what I've accepted after a long time of doing this: you will never fully know what you have built. And that's okay.

The goal isn't to eliminate discovery, but to get better at it. Learn to discover and leave better breadcrumbs. Be the kind ancestor for next person digging through your ruins.

The system will keep growing, more boxes will keep connecting. The documentation will keep lagging. The mystery will persist.

![Whiteboard](/connected-boxes/images/posts/archaeology.png)
*Gemini Banana thinks this is representation of my post*
