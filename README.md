# Daily AI Tweet Generator

An n8n workflow that runs every night, reads today's top AI news headlines, and uses an LLM to draft 12 ready-to-post X (Twitter) posts about AI — logged to a Google Sheet for human review, never auto-published.

---

## What It Does

Maintaining a consistent X presence requires daily content creation — time most business owners and creators don't have. This workflow pulls today's trending AI headlines and turns them into a batch of on-voice, aphoristic tweets each night, dropping them into a Google Sheet where they can be reviewed, edited, and scheduled at your convenience.

**Input:** Top AI headlines from Google News (via RSS), fetched automatically each run
**Output:** 12 tweets per run — spread across categories (fine detail, high-level, optimistic, pessimistic, philosophical, contrarian, news-inspired) — logged to Google Sheets

---

## Pipeline Flow

```
Schedule Trigger (daily, 10 PM)
        ↓
Fetch AI News — Google News RSS search for "artificial intelligence"
        ↓
Keep top 8 headlines
        ↓
Format headlines + build prompt
        ↓
OpenAI (gpt-4o) — generate 12 tweets across fixed tone categories
        ↓
Parse response JSON
        ↓
Google Sheets — append each tweet with date, topic, and content
        ↓
Ready for human review and scheduling
```

---

## Key Features

- **Fully automated** — runs nightly without any manual trigger
- **News-driven** — pulls real, current AI headlines instead of a static topic list
- **12 posts per run** — spread across a fixed mix of tones (fine-detail, big-picture, optimistic, pessimistic, philosophical, contrarian, and news-inspired) so you have real variety to choose from
- **Voice-constrained prompt** — hard rules baked into the prompt (280-char limit, no hashtags/emojis/links, punchline-driven, varied openers)
- **Google Sheets output** — clean, reviewable log with date, topic, and content
- **Non-destructive** — posts are never auto-published, always human-reviewed first

---

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration and scheduling |
| Google News RSS | Source of daily AI headlines |
| OpenAI (gpt-4o) | Tweet generation |
| Google Sheets API | Output storage and review interface |

---

## Setup

1. Import `Daily AI Tweet Generator n8n Workflow.json` into your n8n instance
2. Add an OpenAI API credential in n8n's Credentials manager
3. Add Google Sheets OAuth2 credentials and point the workflow at your own spreadsheet
4. Adjust the RSS search query or schedule time if desired
5. Activate the workflow

---

## Google Sheets Output Format

| Date | Headline / Topic | Post | Category |
|---|---|---|---|
| 2026-06-02 | (source headline or null) | Your generated tweet text... | Contrarian |

---

## Roadmap

- [x] Nightly scheduled generation
- [x] Live AI news sourcing via RSS
- [x] Google Sheets delivery
- [ ] Tone/voice customization per run
- [ ] Direct Buffer or Typefully integration for one-click scheduling
- [ ] Engagement scoring to prioritize top posts
