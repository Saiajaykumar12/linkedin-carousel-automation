Built this to solve a real problem at Ecowoodies: content creation was taking 2 hours per carousel. After deploying this pipeline, the marketing team's production time dropped to under 5 minutes per post — a 96% reduction. Zero manual steps remain in the workflow.

# LinkedIn Carousel Automation

Auto-generates and posts LinkedIn carousel PDFs using Make.com

## How It Works
1. Reads a topic from Google Sheets (status = Pending)
2. GPT-4o mini generates 8-slide carousel content as JSON
3. GPT-4o mini generates a LinkedIn caption
4. HTML is built from the slides and converted to PDF via PDF.co
5. PDF is uploaded and posted to LinkedIn
6. Row is marked as "done" in Google Sheets

## Tools Used
- Make.com
- Google Sheets
- OpenAI GPT-4o mini
- PDF.co
- LinkedIn API

## Setup
1. Import `scenario.json` into Make.com
2. Add your own API keys and tokens
3. Set up your Google Sheet with columns: Topic (A), Status (B)
4. Run the scenario
