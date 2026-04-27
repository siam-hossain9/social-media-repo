# Multi-Platform Social Media Content Engine 🚀

This repository contains an autonomous n8n workflow that monitors trending topics, generates a targeted weekly content calendar using artificial intelligence, creates platform-specific posts, and schedules them for publication.

## 🖼️ Workflow Overview

![n8n Workflow diagram](workflow.png)

*(Note: Please ensure the provided workflow image is saved as `workflow.png` in this repository)*

## ⚙️ How It Works

This n8n workflow operates essentially as a fully automated Social Media Manager. Here's a breakdown of its components:

1. **Scheduled Trigger:** The workflow wakes up on a weekly schedule (via Cron).
2. **Trend Analysis:** It fetches the latest queries from Google Trends and currently trending topics from Twitter.
3. **Information Parsing:** Custom Javascript nodes extract and combine the popular themes (specifically targeting Technology, AI, and Automation niches).
4. **AI Generation (OpenAI):** 
   - A single week content calendar is first created.
   - For each content idea, individual AI agents generate optimized text specifically tailored for Twitter, LinkedIn, and Instagram.
   - DALL-E generates a matching, high-quality professional image based on the generated content.
5. **Data Enrichment & Packaging:** The image URL and textual combinations are compiled into a strict schema, and an optimal scheduling date/time is calculated.
6. **Information Storage:** The content pieces and their metadata are backed up into Google Sheets and an Airtable CRM platform.
7. **Automated Publishing via Buffer:** The constructed posts (text + image) are scheduled via Buffer API to go live on Twitter, LinkedIn, and Instagram at their calculated optimal times.
8. **Slack Notification:** A summary report of the scheduled week is pushed to a Slack channel alerting the team.
9. **Analytics Repurposing Loop:** The workflow implements a 7-day Wait node to monitor performance. Afterward, it automatically analyzes post engagement and utilizes a secondary AI logic to decide if top-performing content should be repurposed, sending a weekly report via Email. 

## 🚀 Setup Instructions

1. Import `Multi-Platform Social Media Content Engine.json` into your n8n workspace.
2. Ensure you have activated credentials for:
   - OpenAI
   - Buffer (Twitter, LinkedIn, Instagram profiles)
   - Google Sheets
   - Airtable
   - Slack (Webhook)
3. Activate the workflow and adjust the cron expression if needed.
