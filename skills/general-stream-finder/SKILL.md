---
name: general-stream-finder
description: Find live streams about the page's niche ranked by concurrent viewers. Use when the user asks who is streaming now, wants live moments to clip, or before general-live-mode.
---

# Stream finder

Run:

`python "${CLAUDE_PLUGIN_ROOT}/scripts/generalStreams.py"`

The query and Twitch category come from `queries[0]` and `twitch_categories[0]` in `niche.json`. Override with `--query` and `--game`.

Then:

1. Show the top 10 live streams: channel, title, concurrent viewers, link.
2. Skip streams that are clearly leaks, early-access tricks or pirated copies. Say why in one line.
3. Recommend 1 to 3 streams. Prefer official channels and creators who allow sharing.
4. Offer the next step: `general-live-mode <url> --minutes 60` to record and clip chat spikes, or `general-moment-finder` on a finished VOD.

Viewer counts are what the script returns at that moment. Do not guess or round them up.
