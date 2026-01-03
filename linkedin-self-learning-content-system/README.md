# LinkedIn Self-Learning Content System

# LinkedIn Self-Learning Content System

A closed-loop LinkedIn content engine that **generates posts, tracks real performance, and adapts its writing rules automatically** — built with n8n, Google Sheets, and free APIs.

This is **not** a generic “AI post generator”.
It is a **rule-driven system that improves over time based on real LinkedIn views**.

---

## What This System Does

- Generates LinkedIn posts from your ideas
- Uses web search for context (no scraping)
- Writes opinionated, human-sounding posts
- Tracks LinkedIn post views via email notifications
- Learns weekly by updating writing rules
- Improves future posts automatically

You still post manually on LinkedIn (safe & compliant).

---

## How Learning Works (Simple Explanation)
- LinkedIn sends view counts by email
- Views are logged automatically
- Weekly workflow analyses performance
- Writing rules are updated
- Next post follows the new rules

No paid APIs. No black-box ML.

---

## Tech Stack

- **n8n** (local, npm)
- **Google Sheet**
- **Gmail (LinkedIn notifications)**
- **LLM of your choice** (OpenAI / Gemini / OpenRouter / Ollama)

---

## Prerequisites (Required)

You need:

- Node.js installed
- A Google account
- Gmail with LinkedIn email notifications enabled

No coding required.

## Step 1 — Install n8n Locally

Run in terminal/command prompt:
npm install -g n8n
n8n

##Step 2 — Import the Workflows

- Import these files from this folder:

  01_content_generator.json
  02_performance_tracker.json
  03_rules_learner.json

##Step 3 — Download the Excel Sheet and open it in Google Sheets

 -Usage
   Sheet 1:
    Add ideas in Topic
    Set Status = To Do
    Automation fills Content

  Sheet 2 — PostPerformance:
    Used by the learning workflow.

  Sheet 3 — WritingRules (IMPORTANT)
     ⚠️ Do NOT change ID = 1
      This row is updated automatically

## Automation Schedule (How & When It Runs)

This system runs on fixed, predictable schedules:

- **Content Generator**
  - Runs automatically **every Sunday at 12:00 AM**
  - Fills the `Content` column in Google Sheets for all rows with `Status = To Do`

- **Performance Tracker (Gmail Trigger)**
  - Runs **instantly** whenever a LinkedIn email arrives
  - Listens for impression notifications
  - Logs post views to the `PostPerformance` sheet

- **Rules Learner**
  - Runs **every Sunday at 11:00 PM**
  - Analyzes recent performance
  - Updates writing rules if performance trends change

This ensures:
- Content is prepared first
- Performance is collected continuously
- Learning happens after a full week of data


