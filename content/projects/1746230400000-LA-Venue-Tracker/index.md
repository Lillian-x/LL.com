---
title: "Learning Analytics Venue Tracker"
date: 2026-05-02
draft: true   # kept in repo for future use; not published. Flip to false to publish.
description: "Interactive Gantt + Excel tracker for paper deadlines, conference dates, and journal special issues across the Learning Analytics community and adjacent education-tech venues."
tags: ["learning analytics", "research planning", "tools", "data visualization"]
---

A community-maintained tracker for paper submission deadlines, conference dates, workshops, and journal special issues across the Learning Analytics, Educational Data Mining, and adjacent learning sciences / education-technology research community.

**18 venues tracked · 150 deadline entries · 12-month rolling Gantt view**

## What's tracked

- **Core LA conferences:** LAK · AIED · EDM · L@S
- **Learning Sciences conferences:** ISLS Annual Meeting (CSCL + ICLS) · ITS · EC-TEL
- **Big-tent venues that accept LA papers:** AERA · CHI · HICSS · ICLR
- **Journals (rolling submission):** JLA · JEDM · BJET · CAE / CAEAI / CAEO / CAE:XR · IEEE TLT · B&IT · C&I

For each venue we track main deadlines (paper, abstract, notification, camera-ready), sub-track deadlines (DC, posters, workshops, late-breaking, industry, blue-sky), workshop list per cycle, scope, official URLs, and historical deadline pattern for projection.

## Interactive Gantt visualization

The interactive view below auto-scrolls a 12-month rolling window starting from the current month. Diamond markers are color-coded by status — 🔴 upcoming (≤60 days), 🟣 confirmed, 🟠 projected (estimated from historical pattern), ⚫ past — and 📢 marks each conference date. Bar colors indicate the venue category.

<iframe src="/la-venue-tracker/gantt.html"
        title="Learning Analytics Venue Tracker — Interactive Gantt"
        style="width:100%; height:780px; border:1px solid #ddd; border-radius:6px;"
        loading="lazy"></iframe>

> If the embed feels cramped, **[open the full-screen Gantt in a new tab →](/la-venue-tracker/gantt.html)**

## Download the data

The canonical dataset lives in a single Excel workbook with 10 sheets (`All_Deadlines`, `Venue_Profiles`, `Journals`, `Special_Issues`, `Sub_Tracks`, `Workshops_2026`, `HICSS_Minitracks`, `Historical_Pattern`, `Sources`, README).

📥 **[Download `tracker.xlsx`](/la-venue-tracker/tracker.xlsx)** (≈45 KB)

## Why this exists

PhD researchers working in Learning Analytics juggle 10+ submission cycles a year across overlapping venues — and "the LAK deadline" or "is HICSS still open?" gets asked over and over in lab Slacks. Existing trackers (WikiCFP, conference RSS feeds) miss the special-issue and sub-track signal that actually drives planning. This is my hand-curated, single-page answer to "what should I be working on next?"

## How it's built

- **Source of truth:** a single Python file (`build_tracker.py`) regenerates the entire Excel workbook
- **Visualization:** self-contained HTML (`gantt.html`) — no CDN, no build step, works offline
- **Auto-research tool:** an LLM-assisted script (`add_venue.py`, Kimi K2 + DuckDuckGo web search) takes a venue name, fetches the CFP data, patches both files, and rebuilds the Excel
- **Verification log:** every deadline change is appended to `docs/data_sources.md` with the official URL

## Caveats

This tracker is maintained by hand. **Always verify the deadline at the official venue page before submitting.** "Projected" deadlines (orange diamonds) are extrapolations from past cycles and have not been officially announced.

## Color scheme

Bar colors adapted from the *Science* journal Indian Ocean dengue figure (Chen et al.):

| Category | Bar color |
|---|---|
| 🟥 Core LA | terracotta `#b85441` |
| 🟩 Learning Sciences | forest green `#297645` |
| 🟦 Big-tent | ocean blue `#4695be` |
| 🟨 Journals | mustard yellow `#d8b03c` |

## License & contributions

MIT-licensed; data is community-contributed and provided as-is for research planning. Issues and pull requests welcome on the [project repository](https://github.com/Lillian-x/la-venue-tracker) *(repo URL pending — please reach out via email if you'd like to contribute before that's public)*.
