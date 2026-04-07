# RSS News Bot

This n8n workflow monitors an RSS feed and sends new articles to Telegram automatically.

It is built for simple news delivery: when a new item appears in the feed, the workflow sends a formatted message to a Telegram chat or group.

## What It Does

The workflow has 2 nodes:

1. `RSS Feed Trigger`
2. `Telegram`

Flow:

- n8n checks the RSS feed on a schedule
- A new article is detected
- The article title, link, and publish date are pulled from the feed item
- A Telegram message is sent to the configured chat

## Feed Source

Current RSS feed:

```text
https://technology.inquirer.net/feed
```

## Trigger Schedule

The workflow is configured to check the feed:

```text
Every minute
```

## Message Format

The Telegram message includes:

- News source label
- Article title
- Article link
- Publication date

Example structure:

```text
Inquirer Tech

[Article Title]

Read more:
[Article Link]

[Publication Date]
```

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A Telegram bot
- Telegram credentials configured in n8n
- A Telegram chat ID or group ID
- A valid RSS feed URL

## Workflow Details

- Workflow name: `RSS News Bot`
- Trigger type: `RSS Feed Trigger`
- Feed URL: `https://technology.inquirer.net/feed`
- Delivery channel: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `RSS Feed Trigger` node.
3. Replace the feed URL if you want a different news source.
4. Open the `Send a text message` node.
5. Connect your own Telegram credentials if needed.
6. Replace the `chatId` with your own Telegram chat or group ID.
7. Save and activate the workflow.

## Use Cases

- Personal news alerts
- Tech news monitoring
- Telegram channel auto-posting
- Feed-to-chat automation

## Notes

- The workflow currently checks only one RSS feed.
- Messages are sent to a fixed Telegram chat ID.
- You can customize the Telegram message format in the Telegram node.
- You can duplicate the flow for multiple feeds if needed.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace real chat IDs
- Reconnect your own Telegram credentials after import
- Review the message format before publishing screenshots or exports

## File

Source workflow:

- `RSS News Bot.json`
