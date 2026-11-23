---
name: general-twitch-reaction
description: Watch the biggest live streamer in the page's niche and make reaction clips: face on top, content below, big title. Use when the user wants streamer reaction clips, "face on top" clips, Twitch clips, or asks who is streaming now.
---

# Twitch reaction clips

Face on top, content below, a big title on the seam. The format of most viral streamer clips.

## 1. Find the streamer (no Twitch account or key needed)

`python "${CLAUDE_PLUGIN_ROOT}/scripts/generalStreams.py"` lists the top live streams in the page's niche on Twitch and YouTube, ranked by viewers (`queries[0]` and `twitch_categories[0]` from `niche.json`). Pick a streamer who runs a clipping campaign (check `campaigns.md`), or one whose clips you have permission to post.

## 2. Get the moment

- Live: `python "${CLAUDE_PLUGIN_ROOT}/scripts/generalLive.py" https://twitch.tv/<login> --minutes 60` records the stream, reads Twitch chat anonymously and cuts a clip every time chat explodes.
- After the fact: `python "${CLAUDE_PLUGIN_ROOT}/scripts/generalMoments.py" <twitch VOD or clip URL> --top 8` scores the VOD and writes `candidates.md`.

## 3. Cut the reaction clip

```
python "${CLAUDE_PLUGIN_ROOT}/scripts/generalCut.py" jobs/<id> --pick 1 --layout react --cam auto \
  --title "They REALIZED why it took 13 YEARS" --title-style box --captions bubble
```

- `--cam auto` finds the streamer's webcam itself (face detection plus the webcam frame around it). It prints where it found the cam. If it finds no stable face it falls back to the blur layout and says so. Check the first frame once; if the crop is wrong, pass `--cam x:y:w:h` fractions.
- `--title-style box`: white band with bold black text on the seam. `--title-style outline`: white text with a thick black outline across the top of the content, for short titles ("FINAL BOSS in one try").
- `--captions bubble`: white speech bubble ("Oh my god!"). `word`: word-by-word captions. `none`: title only.
- Write the title with `general-hook-writer` (reaction titles section).

## Rules

- Clip a streamer only inside their campaign or with permission. Credit them in the post caption, not on the video.
- Titles describe what happened. Never invent a quote or an opinion.
- Run `general-rule-check` before posting. No spoilers in the title during launch week.
