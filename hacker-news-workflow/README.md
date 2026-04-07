# Hacker News Workflow

This n8n workflow searches Hacker News for posts related to a specific keyword.

It is a simple manual workflow for testing the Hacker News node, exploring search results, or building a starting point for content monitoring workflows.

## What It Does

The workflow has 2 nodes:

1. `Manual Trigger`
2. `Hacker News`

Flow:

- You manually run the workflow in n8n
- The Hacker News node searches for stories
- Results are returned based on the configured keyword

## Search Configuration

Current setup:

- Resource: `all`
- Limit: `10`
- Keyword: `automation`

This means the workflow fetches up to 10 Hacker News results related to the keyword `automation`.

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Access to the Hacker News node in n8n

No external credentials are required for this basic setup.

## Workflow Details

- Workflow name: `Hacker News Workflow`
- Trigger type: `Manual Trigger`
- Action: `Search Hacker News`
- Result limit: `10`
- Status: `Inactive`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Hacker News` node.
3. Change the keyword if you want to search a different topic.
4. Adjust the result limit if needed.
5. Save the workflow.
6. Click `Execute workflow` to run it manually.

## Use Cases

- Quick Hacker News topic searches
- Content research
- Testing the n8n Hacker News node
- Building a future monitoring workflow

## Notes

- This workflow runs only when triggered manually.
- It does not currently send, store, or transform the search results.
- You can extend it by adding nodes for Telegram, Gmail, Google Sheets, Notion, or databases.

## Possible Extensions

- Send results to Telegram
- Email top matches daily
- Save stories to Google Sheets
- Filter results further with a Code node
- Turn it into a scheduled monitoring workflow

## File

Source workflow:

- `Hacker News Workflow.json`
