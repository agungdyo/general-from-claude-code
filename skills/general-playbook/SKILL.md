---
name: general-playbook
description: Run the daily page routine from the full playbook. Use when the user says "daily routine", "what do I do today", "run the page", asks about the 7-day kickoff, launch day, content pillars, posting slots, or safety rules.
---

# Playbook

1. Read `${CLAUDE_PLUGIN_ROOT}/skills/general-playbook/references/playbook.md`. If the page folder has its own `playbook.md`, read that one instead (it is the customized copy).
2. If the page folder does not exist, run the `general-setup` skill first.
3. Find where the page is: the kickoff day (section 17) or the normal daily schedule (section 9). Check `log.md` and `scoreboard.csv`.
4. Run the day:
   - Official sources first (section 5). Record each verified fact with its link in `facts.md`.
   - Find material: `general-trend-radar`, `general-stream-finder`, `general-campaign-finder`.
   - Cut clips: `general-moment-finder`, then `general-clip-cutter`, with hooks from `general-hook-writer`.
   - Gate every clip with `general-rule-check`.
   - Log and learn with `general-learning-loop`.
5. Send the human ONE message with the exact caption, media path and credit for each post. They reply "yes" to approve. They post it themselves or schedule it. Never auto-upload.
6. End the day with the short report (section 16): what posted, top post with numbers, one lesson, tomorrow's test.

Hard rules: no leaks, no "early access" tricks, no piracy, no game exploits or fake accounts, no invented facts or numbers, credit every creator, no earnings promises. Anything outside the normal mix needs the human's yes first.
