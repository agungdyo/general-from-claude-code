---
name: general-trend-radar
description: Rank recent videos for the page's niche by views per hour to see what is trending now. Use when the user asks what is hot, what to clip today, or wants fresh source videos.
---

# Trend radar

Run:

`python "${CLAUDE_PLUGIN_ROOT}/scripts/generalTrends.py" --hours 24 --limit 30`

The query comes from `queries[0]` in `niche.json`. Override `--query` for another angle, and `--hours` for a wider window.

Then:

1. Show the top 10 as a short table: title, channel, views, views per hour, age, link.
2. Pick 3 that fit the page's niche angle. Prefer official sources and creators who allow sharing.
3. Flag any that look like leaks or "play early": drop them and say so.
4. Offer the next step for the picks: `general-moment-finder <url> --top 8`.

If the script errors, show the last error line and fix the cause (missing yt-dlp, network). Do not invent a list.
