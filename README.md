## Result

Built and deployed at Ecowoodies. Reduced the marketing team's LinkedIn content production from **2 hours to 5 minutes per carousel** — a 96% reduction. Zero manual steps remain after the workflow runs: GPT-4o writes the content, PDF.co builds the slides, LinkedIn API posts it.

Previously: writer drafts content → designer builds slides → someone schedules the post → 2 hours minimum.
Now: add topic to Google Sheets → workflow runs automatically → posted in 5 minutes.

---

# LinkedIn Carousel Automation — Make.com + GPT-4o


Paste a topic into Google Sheets → get a fully designed carousel PDF
auto-posted to LinkedIn. Zero manual design, zero manual posting.

## The Problem It Solves

Creating LinkedIn carousel content manually means writing slides,
designing PDFs, and posting — easily 2–3 hours per post.
This workflow reduces that to entering one topic in a spreadsheet.

## Pipeline Architecture
Google Sheets (topic added, status = Pending)
↓
GPT-4o mini — generates 8-slide carousel content as structured JSON
↓
GPT-4o mini — generates LinkedIn caption for the post
↓
HTML template built from slide JSON
↓
PDF.co — converts HTML to styled PDF carousel
↓
LinkedIn API — uploads PDF and publishes post
↓
Google Sheets — row marked as "done"
## Tools Used

| Tool | Role |
|------|------|
| Make.com | Workflow orchestration |
| Google Sheets | Content queue and status tracker |
| OpenAI GPT-4o mini | Slide content + caption generation |
| PDF.co | HTML to PDF conversion |
| LinkedIn API | Automated post publishing |

## How to Use

1. Import `Carousel Posting in Linkedin.json` into Make.com
2. Connect your accounts: Google Sheets, OpenAI, PDF.co, LinkedIn
3. Set up your Google Sheet with columns: `Topic` (A), `Status` (B)
4. Set status of any row to `Pending`
5. Run the scenario — carousel appears on LinkedIn within minutes

## Key Design Decisions

- **GPT-4o mini over GPT-4o** — carousel content doesn't need frontier
  reasoning; mini is 10x cheaper with comparable output for structured JSON
- **HTML → PDF over direct image generation** — gives consistent,
  controllable slide layout without needing a design tool or API
- **Status column in Sheets** — prevents re-processing rows already published;
  simple but critical for idempotency

## Credentials Required

- OpenAI API key
- PDF.co API key
- LinkedIn OAuth token (via Make.com connection)
- Google Sheets OAuth (via Make.com connection)

## .env / Secrets

All credentials are stored inside Make.com's connection manager —
no secrets are committed to this repo.
