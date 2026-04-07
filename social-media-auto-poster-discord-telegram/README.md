# Social Media Auto Poster (Discord / Telegram)

This n8n workflow reads new content from Google Sheets and automatically posts it to either Discord or Telegram, then marks the row as posted.

It is useful for simple content scheduling, social post queues, and spreadsheet-driven publishing workflows.

## What It Does

The workflow has 6 nodes:

1. `Google Sheets Trigger`
2. `If`
3. `Switch`
4. `Discord`
5. `Send a text message`
6. `Update row in sheet`

Flow:

- A new row is added in Google Sheets
- The workflow checks whether the row has not been posted yet
- The `Platform` field determines whether the content goes to Discord or Telegram
- The post content is sent to the selected platform
- The source row is updated to mark it as posted

## Trigger Schedule

The workflow is configured to check the sheet:

```text
Every minute
```

## Spreadsheet Logic

The workflow expects fields such as:

- `Post`
- `Platform`
- `Posted`
- `Date Posted`

Current platform routing:

- `Discord` -> Discord webhook
- `Telegram` -> Telegram message

Rows are updated after posting with:

- `Posted = Yes`
- `Date Posted = current time`

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A Google Sheets account connected to n8n
- A Discord webhook configured in n8n
- Telegram credentials configured in n8n
- A spreadsheet with the expected columns

## Workflow Details

- Workflow name: `Social Media Auto Poster (Discord / Telegram)`
- Trigger type: `Google Sheets Trigger`
- Delivery channels: `Discord` and `Telegram`
- Data source: `Google Sheets`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Google Sheets Trigger` node and connect your Google Sheets account.
3. Select your spreadsheet and sheet.
4. Make sure your sheet includes the columns `Post`, `Platform`, `Posted`, and `Date Posted`.
5. Open the Discord node and connect your webhook credentials.
6. Open the Telegram node and replace the `chatId` with your own.
7. Review the `If` and `Switch` nodes if you want different posting rules or platform names.
8. Save and activate the workflow.

## Use Cases

- Spreadsheet-based content scheduling
- Cross-platform posting automation
- Team-managed content queues
- Basic social media publishing workflows

## Notes

- The workflow currently posts only when `Posted` is `No`.
- Routing depends on exact platform values in the sheet.
- The update step matches rows using the `Platform` column, so you may want to switch to a more unique row identifier for more reliable updates.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace spreadsheet IDs and URLs
- Remove or replace Telegram chat IDs
- Reconnect your own Google Sheets, Discord, and Telegram credentials after import

## File

Source workflow:

- `Social Media Auto Poster (Discord _ Telegram).json`
