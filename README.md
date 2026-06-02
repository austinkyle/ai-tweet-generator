# Daily AI Tweet Generator

An n8n workflow that runs on a daily schedule, generates 10 ready-to-post X (Twitter) posts on user-defined topics using an LLM, and delivers them to a Google Sheet for review and scheduling.

---

## What It Does

Maintaining a consistent X presence requires daily content creation — time most business owners and creators don't have. This workflow generates a full day's worth of posts automatically every morning, dropping them into a Google Sheet where they can be reviewed, edited, and scheduled at your convenience.

**Input:** User-defined topics configured in the workflow
**Output:** 10 post variations per run, logged to Google Sheets with date and topic

---

## Pipeline Flow

```
Schedule Trigger (daily)
        ↓
Load user-defined topics
        ↓
LLM — Generate 10 X posts per topic
        ↓
Google Sheets — Append posts with date, topic, and content
        ↓
Ready for human review and scheduling
```

---

## Key Features

- **Fully automated** — runs daily without any manual trigger
- **User-defined topics** — configure your own topic list to match your niche and voice
- **10 posts per run** — gives you options to choose from rather than locking you into one output
- **Google Sheets output** — clean, reviewable log with date and topic columns
- **Non-destructive** — posts are never auto-published, always human-reviewed first

---

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration and scheduling |
| LLM (Claude / OpenAI) | Post generation |
| Google Sheets API | Output storage and review interface |

---

## Environment Variables

```
CLAUDE_API_KEY=your_claude_api_key
GOOGLE_SHEETS_CLIENT_ID=your_client_id
GOOGLE_SHEETS_CLIENT_SECRET=your_client_secret
GOOGLE_SHEETS_REFRESH_TOKEN=your_refresh_token
GOOGLE_SHEETS_ID=your_spreadsheet_id
```

---

## Setup

1. Import `ai-tweet-generator.json` into your n8n instance
2. Add Google Sheets OAuth2 credentials in n8n's Credentials manager
3. Add your Claude or OpenAI API key
4. Define your topics in the workflow configuration node
5. Set your preferred daily schedule time
6. Activate the workflow

---

## Google Sheets Output Format

| Date | Topic | Post | Status |
|---|---|---|---|
| 2026-06-02 | AI automation | Your generated post here... | Review |

---

## Roadmap

- [x] Daily scheduled generation
- [x] User-defined topic configuration
- [x] Google Sheets delivery
- [ ] Tone/voice customization per topic
- [ ] Direct Buffer or Typefully integration for one-click scheduling
- [ ] Engagement scoring to prioritize top posts
