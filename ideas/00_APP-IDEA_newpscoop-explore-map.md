---
ssot_type: APP_IDEA
id: app-newpscoop-explore-map
version: 0.3.0
status: draft
owner: "moez salhi"
created_at: 2025-10-18
last_updated: 2025-10-18
current_phase: prototyping
tags: [hospitality, map, poi, events, csv-simple, wix, google-maps, ttv]
---

# 0. Executive Snapshot (Context Rescue)
Goal: A single-file, configurable “Local Explorer” that shows nearby POIs and events around a venue, driven by a **single simple Google Sheet** (published CSV).  
Users: hotel guests/staff first; easily verticalized for campuses, coworking, retail.  
Success: ≤1 day to first embed; <2.5s render; ≤1h content refresh via republish.

# 1. Initial Requirement (Single Source of Truth)
Problem: Guests need an up-to-date local guide; staff need non-technical updates.  
In-scope: Google Maps + Places, clustering, filters, distance rings, directions, search.  
Data: One Google Sheet → published CSV with a **single, simple schema**.  
Out-of-scope now: ML personalization, e-commerce, auth, multi-language (Phase 2+).  
Acceptance v0: Works on Wix; CSV → pins/cards; filters & chips; a11y & responsive.

# 2. Client Starting-Point Example (Mapped A/B/C)
**Sections and subcategories (canonical):**
- **A. Upcoming Events** (`type=event`)
  - Subsections: Film & Entertainment; Live Music & Performances; Food & Drink; Art & Culture; Tours & Activities; Weeklies
- **B. Our Favorites** (`type in {poi, post}`)
  - Subsections (examples): Activities; Eats & Treats; Lobster Roll; Parking & EV Charger; Ride On; Kidventure
- **C. Complete Guide** (`type=poi`)
  - Subsections (examples): Historic Mansions & Architecture; Landmarks & Sightseeing; Sailing, Tours & Harbor; Beaches & Waterfront; Events & Entertainment; Outdoor & Sports; Farms & Orchards; Food & Drink; Romantic & Relaxation

**Note:** “Blog-style” lists (e.g., Lobster Roll) use `type=post` (no map pin) and render as informational cards with links.

# 3. CSV/Sheet Schema (minimal, user-friendly)
Columns:  
`type,section,subsection,title,description,address,lat,lng,city,url,tags,date_start,date_end,repeat,repeat_days,price,image_url,featured,pin_priority`  
- Editors only add rows; data-validations provide dropdowns for `type/section/subsection/repeat`.  
- Weekly events: `repeat=weekly`, `repeat_days=Mon;Wed;Sat`.

# 4. Solution Direction (Provisional)
Client HTML app reads the CSV, normalizes rows, renders:  
- `event` → filtered by date chips (today → +7) + Weeklies logic  
- `poi` → pins, clustering, distance chips, directions  
- `post` → list cards only  
Search: matches `title|tags|address`.  
Future: optional thin API `/pois` `/events` to aggregate from multiple sources.

# 5. Phase Plan (TTV)
Prototype (1–2d): pins from hardcoded rows; filters; chips.  
POC (3–5d): Sheet CSV ingest + MarkerClusterer + Autocomplete temp pin.  
MVP (7–10d): Full A/B/C mapping + `post` cards + fallback + a11y polish.

# 6. Decision Log
- 2025-10-18 — Adopted **single-sheet** CSV with A/B/C baked in; `post` type for blog-style items.
- 2025-10-18 — Chose weekly recurrence via `repeat` + `repeat_days` (simple, human-editable).

# 7. Change Log
- v0.1.0 — Initial draft  
- v0.2.0 — Added API layer vision, verticalization  
- v0.3.0 — Embedded A/B/C mapping + one-sheet CSV simplification

# 8. Glossary
POI — map pin with location; POST — informational card without a pin; WEEKLIES — repeating weekly events with chosen weekdays.
