# Lead Capture System

This n8n workflow receives lead submissions from Tally, saves them to Google Sheets, creates a ClickUp task, and sends a Telegram notification.

It is useful for client inquiry pipelines, service lead capture, and lightweight CRM automation.

## What It Does

The workflow has 4 nodes:

1. `Receive Lead`
2. `Save to Sheets`
3. `Create Task`
4. `Notify via Telegram`

Flow:

- A lead submits a Tally form
- Lead details are saved into Google Sheets
- A new ClickUp task is created for follow-up
- A Telegram alert is sent with the lead information

## Lead Data Captured

The workflow maps these fields:

- Full Name
- Email
- Phone
- Service
- Budget
- Date

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A Tally form connected to n8n
- Google Sheets credentials configured in n8n
- ClickUp credentials configured in n8n
- Telegram credentials configured in n8n

## Workflow Details

- Workflow name: `Lead Capture System`
- Trigger type: `Tally Trigger`
- Storage: `Google Sheets`
- Task management: `ClickUp`
- Notification method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Receive Lead` node and connect your Tally account.
3. Make sure your form field mappings match the workflow expressions.
4. Open the `Save to Sheets` node and connect your Google Sheets account.
5. Select your spreadsheet and target sheet.
6. Open the `Create Task` node and connect your ClickUp account.
7. Set the correct team, space, and list.
8. Open the Telegram node and replace the destination `chatId` if needed.
9. Save and activate the workflow.

## Use Cases

- Service inquiry capture
- Sales pipeline automation
- Team lead notifications
- Spreadsheet plus task tracker workflows

## Notes

- The workflow depends on Tally question IDs, so changes to the form may require expression updates.
- ClickUp task content includes the lead details for follow-up.
- The exported JSON appears to contain encoded emoji characters in the Telegram message, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Tally form IDs
- Remove or replace spreadsheet IDs and URLs
- Remove or replace Telegram chat IDs
- Reconnect your own Tally, Google Sheets, ClickUp, and Telegram credentials after import

## File

Source workflow:

- `Lead Capture System.json`
