News Bot AI

News Bot AI is a Python-based news research and summarisation tool designed to collect relevant news articles, summarise them with AI, and produce client-friendly insights for small businesses, entrepreneurs, and accountancy clients.

The project is intended to use the CrewAI framework to structure the workflow into specialist AI agents, such as a news researcher, business analyst, and content summariser.

What It Does

News Bot AI currently:

- Reads API keys from a local config file
- Searches for news articles using the NewsData.io API
- Summarises articles using OpenAI
- Focuses summaries on business, finance, tax, economic change, and growth planning
- Saves raw news results and AI-generated summaries as JSON files

Intended CrewAI Architecture

The project is designed around a multi-agent workflow:

1. News Research Agent

Responsible for collecting relevant news articles from external news APIs.

Example focus areas:

- UK Budget updates
- Tax changes
- Small business news
- Economic policy
- Finance and accounting updates

2. Business Insight Agent

Reviews the collected news and identifies why it matters to small and medium-sized businesses.

This agent should focus on:

- Financial impact
- Tax planning implications
- Business growth opportunities
- Risks for entrepreneurs
- Practical actions clients may need to consider

3. Summary Writer Agent

Turns the research and analysis into short, readable summaries suitable for:

- Client newsletters
- Blog posts
- LinkedIn updates
- Internal briefing notes
- Accountancy firm updates

Current Workflow

config.txt
   ↓
news_bot.py
   ↓
Fetch news from NewsData.io
   ↓
Summarise articles using OpenAI
   ↓
Write output to JSON files

Requirements

Install the required Python packages:

pip install requests openai crewai

Configuration

Create a "config.txt" file in the project root:

OPENAI_API_KEY=your_openai_api_key
NEWSDATA_API_KEY=your_newsdata_api_key

Do not commit real API keys to GitHub.

Running the Bot

Run the script:

python news_bot.py

By default, the script searches for:

budget uk

The script will create output files similar to:

newsdata_raw_YYYYMMDD_HHMMSS.json
summaries_YYYYMMDD_HHMMSS.json

Output

The summary output contains:

[
  {
    "title": "Article title",
    "summary": "AI-generated business-focused summary",
    "url": "Original article URL"
  }
]

Suggested Next Improvements

Convert Fully to CrewAI

The current code imports CrewAI but does not yet define a full crew, task, or agent workflow.

A future version should include:

- "research_agent"
- "business_analysis_agent"
- "summary_writer_agent"
- CrewAI tasks for each stage
- A final report output

Add Environment Variable Support

Replace "config.txt" with ".env" support using "python-dotenv".

Add Topic Selection

Allow the user to pass a topic from the command line:

python news_bot.py "uk tax changes"

Add Markdown Reports

Generate a readable Markdown report as well as JSON:

reports/news_report_YYYYMMDD.md

Add Scheduling

Run the bot daily or weekly using:

- cron
- GitHub Actions
- Azure Functions
- AWS Lambda

Add Client-Friendly Outputs

Future outputs could include:

- Weekly business news digest
- Accountancy client newsletter
- LinkedIn post draft
- Blog article draft
- “What this means for your business” section

Example Use Case

An accountancy firm could use this bot to monitor UK Budget updates, tax news, and economic changes, then generate short client-friendly summaries explaining what business owners need to know.

Project Status

Early prototype.

The current script works as a basic news fetcher and summariser. The next major step is to refactor the logic into a proper CrewAI multi-agent workflow.

Disclaimer

This project produces AI-generated summaries for informational purposes only. Financial, tax, legal, or business decisions should be reviewed by a qualified professional.
