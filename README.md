# general-from-claude-code

A faceless clipping desk that works for any niche. It finds recent videos and live streams, picks the strongest moments, cuts captioned 1080x1920 clips, checks them against your rules, and learns from the numbers. You approve every post; nothing is uploaded automatically.

The GTA 6 plugin is the same pipeline with a fixed preset. This one reads the niche from `niche.json` in your page folder.

## First run

```
Use general-from-claude-code. Set up my clip page, ask me the setup questions in one message,
write niche.json, then find today's trending videos for my niche, pick the best moments in the top one,
and cut my first 3 clips with hooks.
```

`general-setup` asks for the niche label, search queries, platforms, Twitch categories, subreddits, sources, caption language, banned topics and hashtags. It writes them to `niche.json` and builds the page folder.

## niche.json

Only the fields the scripts read:

```json
{
  "label": "your niche",
  "queries": ["search phrase", "second phrase"],
  "twitch_categories": ["Twitch category name"],
  "subreddits": ["subreddit"],
  "title_template": "HOW TO {topic}",
  "banned_terms": ["leak", "piracy"],
  "hype_words": ["no way", "insane"],
  "hashtags": ["#example"],
  "caption_language": "en",
  "sources": ["official source site"]
}
```

A missing field falls back to a safe default: no query means the scripts ask for `--query`, and an empty banned list uses the built-in one. A missing `niche.json` is not an error; it just means no defaults.

## Skills

| Skill | What it does |
|---|---|
| `general-setup` | Installs tools, asks the niche questions, writes `niche.json` and the page folder |
| `general-campaign-finder` | Finds live clipping campaigns and records rate, budget and rules |
| `general-trend-radar` | Recent videos ranked by views per hour |
| `general-stream-finder` | Live streams ranked by concurrent viewers |
| `general-moment-finder` | Best 15 to 40 s moments from a video or VOD |
| `general-live-mode` | Records a live stream and clips chat spikes |
| `general-twitch-reaction` | Face on top, content below, big title on the seam |
| `general-clip-cutter` | 1080x1920 clip with word-by-word captions and a hook box |
| `general-hook-writer` | Three hook options per clip |
| `general-rule-check` | Length, format, hashtags and banned terms before posting |
| `general-multilang` | One clip in several languages with translated captions |
| `general-questions-to-posts` | Repeated fan questions turned into HOW TO drafts |
| `general-secrets-map` | Verified hidden spots and tips database with timestamps and credit |
| `general-cheat-codes` | GTA 6 cheat-code reference (preset; skip it for other niches) |
| `general-playbook` | Daily routine and 7-day kickoff from the generic playbook |
| `general-learning-loop` | Scoreboard, tests and payouts from real numbers only |

## Scripts

```
pip install -r requirements.txt
python scripts/generalTrends.py
python scripts/generalStreams.py
python scripts/generalMoments.py "https://www.youtube.com/watch?v=..."
python scripts/generalCut.py jobs/<id> --pick 2 --layout facecam --hook "Nobody noticed this"
python scripts/generalCheck.py jobs/<id>/edits/clip_2.mp4 --campaign campaigns.md
python scripts/generalLive.py "https://www.youtube.com/watch?v=<live>" --minutes 60
```

Set `CLIP_DESK_HOME` to the page folder if you run the scripts from somewhere else.

Windows, macOS or Linux, Python 3.10+. MIT license.
