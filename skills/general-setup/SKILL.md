---
name: general-setup
description: First-run setup for the clip desk in any niche. Use when the user installs the plugin, says "set up", "start", or when ffmpeg, yt-dlp or faster-whisper are missing, or when the page folder has no niche.json.
---

# Setup

Do the work yourself. Ask the human only what is listed here.

## 1. Install tools (no questions)

Check each with `ffmpeg -version`, `yt-dlp --version`, `python -c "import faster_whisper, numpy"`. Install only what is missing:

- ffmpeg. Windows: `winget install --id Gyan.FFmpeg -e --source winget`. macOS: `brew install ffmpeg`. Linux: `sudo apt install -y ffmpeg`
- Python packages, all systems: `python -m pip install -U -r "${CLAUDE_PLUGIN_ROOT}/requirements.txt"` (faster-whisper, numpy, requests and a fresh yt-dlp; the scripts prefer the pip yt-dlp, because an old yt-dlp gets HTTP 403 from YouTube)
- Re-run the pip line once a week: YouTube changes often and yt-dlp updates follow.

If a winget/brew/apt install needs a new terminal for PATH, say so in one line and re-check. Never spend money or add a card.

## 2. Ask at most 7 questions, in ONE numbered message

1. Page name and handle (@).
2. Niche label, in the words the audience searches (for example "anime edits", "home cooking", "football highlights").
3. Platforms (for example X, Instagram Reels, TikTok, YouTube Shorts).
4. 1 to 3 search queries for YouTube. The niche label is usually the first.
5. Twitch category names to watch, if any.
6. Subreddits and official sources to check, if any.
7. Caption language, banned topics and 1 to 5 hashtags.

If the human already gave an answer, do not ask it again. Skip the message if everything is known.

## 3. Show the plan, ask ONE "yes"

List the folder and files you will create, then ask for a single "yes". After the yes, create in the current directory a folder named after the page, with `niche.json` in it:

```json
{
  "label": "anime edits",
  "queries": ["anime edit", "anime scene"],
  "twitch_categories": ["Just Chatting"],
  "subreddits": ["anime"],
  "title_template": "HOW TO {topic}",
  "banned_terms": ["leak", "piracy", "free download"],
  "hype_words": ["no way", "insane", "clip that"],
  "hashtags": ["#anime"],
  "caption_language": "en",
  "sources": ["animenewsnetwork.com"]
}
```

Replace the example values with the answers. Use exactly these keys. Leave a list empty when the answer is none; the scripts then fall back to their defaults or ask for a flag. `{topic}` in `title_template` is replaced by the question topic.

## 4. Build the page folder

- `playbook.md` (copy from `${CLAUDE_PLUGIN_ROOT}/skills/general-playbook/references/playbook.md` and fill the [BRACKETED] fields from the answers)
- `facts.md` (verified facts only, each with an official source link)
- `idea-bank.md`, `watchlist.md`, `log.md`
- `scoreboard.csv` with this header line only:
  `post_id,date,time,platform,pillar,format,hook,length_sec,credit,views_12h,views_24h,views_72h,likes,reposts_or_shares,replies_or_comments,saves_or_bookmarks,followers_at_read,test_name,notes`
- `learning.md` with headings Wins, Losses, Current Rules
- `takedowns.md`
- `campaigns.md` (title line and an empty table: name, platform, rate per 1K views, budget left, rules, link, checked on)
- `payouts.csv` with header `date,campaign,platform,post_url,views,rate_per_1k,est_payout,status` (managed by `scripts/generalPayouts.py`)
- folders `media/official`, `media/raw`, `media/edits`

## 5. Finish

Tell the human, in 3 lines: what was installed, where the folder is, and the next step (`general-campaign-finder`, then `general-trend-radar`). Remind them that they approve every post and that nothing is uploaded automatically.
