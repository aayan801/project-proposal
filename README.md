# CurbCut

*Real-time campus accessibility navigation — built by and for the people who hit the barriers every day.*

## Team

- Aayan — [aayan801](#) 
- Abdullah — [GitHub profile](#) *(add GitHub profile link)*
- Gillani — [GitHub profile](#) *(add GitHub profile link)*

## What and Why?

**What:** CurbCut is a mobile-first web app that turns campus accessibility from tribal knowledge into a live, shared map. Anyone can report a broken elevator, a blocked ramp, a jammed automatic door, or a construction detour in under 15 seconds. Everyone else sees those reports instantly on a map and can get walking directions that route around stairs-only paths and any currently active hazards.

**Why:** Every campus is full of accessibility barriers that are completely invisible until you personally run into one. An elevator goes down in a dorm or classroom building, and the only people who find out are the ones already standing in front of the closed doors. A ramp gets fenced off for construction with no sign pointing to a detour that's three buildings out of the way. Someone always knows about the problem — it just never gets collected or shared with the people about to walk into it.

For most students that's a mild annoyance. For a student with a mobility disability, someone on crutches after an injury, or a parent with a stroller, it can mean genuinely being unable to get to class, a shift, or an exam on time — with no way to find out in advance and reroute. Campuses have facilities offices that log outages, but that information rarely reaches the people who need it in the moment, and there's no channel at all for the barriers facilities doesn't even know about yet (a snow drift over a curb cut, a bike locked across a ramp, a door that's supposed to be automatic but hasn't worked in a week).

This mirrors what's sometimes called the "curb cut effect" — accessibility features built for people with disabilities usually end up helping far more people than expected. The same reports that help a wheelchair user avoid a broken elevator also help a delivery worker pushing a cart, a band member hauling equipment, or anyone dragging a suitcase to the airport shuttle. CurbCut is cheap to build and cheap to use, and the data it collects — which entrances, ramps, and elevators actually work, and how reliably — is exactly what a facilities office needs to prioritize repairs, but doesn't currently have in one place.

## For Whom?

Our initial, real users are people on our own campus:

- **Students, faculty, and staff with mobility disabilities or temporary injuries** — the people directly affected every time a ramp or elevator goes down. We have classmates who use canes, crutches, or wheelchairs who've agreed to try early versions and tell us what's actually useful versus what's just noise.
- **Parents, visitors, and campus tour groups with strollers**, and **facilities or delivery staff moving carts and equipment** — people who hit the exact same barriers even though they'd never describe themselves as "accessibility app users."
- **The campus accessibility/disability services office and facilities management** — a natural long-term partner. They already track some of this manually; a timestamped, crowd-confirmed feed of real, current barriers is more useful to them than what they currently have.

We're deliberately starting narrow — our own campus, people we can actually talk to and watch use the app — rather than designing for an abstract "everyone." That's also what makes it realistic to validate within a semester.

## How?

From an end user's perspective, CurbCut works like this:

1. **Open it, no install needed.** CurbCut is a mobile web app — open a link, optionally "add to home screen," and you're looking at a live map centered on your location. No app store, no account required just to look around or report something.
2. **Report a barrier in seconds.** Tap "Report," pick a category (elevator out, ramp blocked, door broken, construction detour, ice/snow, other), confirm the auto-detected pin location (or drag it), optionally attach a photo, and submit. The flow is designed to take under 15 seconds, because the people who most need to report something usually have the least patience for a slow form.
3. **See what's happening around you.** The map shows active reports as icons, color-coded by how recently they were confirmed. Anyone can tap a report to "confirm — still there" or "mark resolved," so stale reports fade out and the map stays trustworthy without needing a moderator watching it constantly.
4. **Get an accessible route, not just a route.** Enter a destination (building or room), tap "Accessible route," and get walking directions that avoid stairs-only paths and any currently reported hazards, with a plain-language heads-up along the way (e.g., "Ramp near the library is blocked until Friday — rerouting via the east path").
5. **Follow the places you actually care about.** Subscribe to a building or a regular route (dorm → first class) and get a notification the moment something changes — a new issue reported, or your issue marked fixed.
6. **(Stretch) A simple dashboard for facilities.** A lightweight view where the accessibility/facilities office can see open reports, mark them in progress or resolved, and export a log — turning scattered word-of-mouth into something they can act on and measure.

## Scope

This is sized well for a team of 4–6 over one semester because the hard parts are bounded and the rest is well-understood web app work:

- **We're not building a routing engine from scratch.** We layer hazard data and an "avoid stairs" preference on top of an existing mapping SDK's walking-directions API (e.g., Mapbox or Google Maps, plus OpenStreetMap accessibility tags), rather than writing pathfinding ourselves. That keeps the hardest algorithmic piece off our plate while still requiring real, meaningful integration work.
- **The rest splits cleanly across a team:** a map/reporting UI (1–2 people), a backend and database for reports and confirmations (1–2 people), geolocation and push notifications via a service worker (1 person), and UX/data — walking the campus to seed the initial accessible-entrance and elevator dataset, and interviewing real users (1 person).
- **It's not trivial, either.** Live crowdsourced data with confirmation and decay logic, geolocation-driven UX, offline-friendly behavior, and notification delivery are all genuinely non-trivial pieces that touch most of what a mobile web app course wants a team to practice — without requiring anything exotic like custom machine learning or native mobile code.
- **Clear stretch goals if we're ahead of schedule:** the facilities dashboard, lightweight photo moderation, recognition for helpful reporters, and — longer term — exporting our accessibility dataset to open map data like OpenStreetMap so it outlives the semester.
