# Gsheets New/Updated Row to Gmail

This n8n workflow monitors a Google Sheet and sends a Gmail notification whenever a row is added or updated.

It is useful for simple lead alerts, form response notifications, record monitoring, or spreadsheet-based workflow triggers.

## What It Does

The workflow has 2 nodes:

1. `Google Sheets Trigger`
2. `Gmail`

Flow:

- n8n checks the connected Google Sheet on a schedule
- A new or updated row is detected
- Data from the row is read
- A Gmail message is sent with the row details

## Trigger Schedule

The workflow is configured to check the sheet:

```text
Every minute
```

## Data Source

The workflow is connected to:

- Google Sheets document
- Sheet: `Sheet1`

The notification message currently uses these columns:

- `Name`
- `Email`

## Email Sent

Current subject:

```text
New Added/Updated Row
```

Current message format:

```text
A new row was added to your Google Sheet:
Name: [Name value]
Email: [Email value]
```

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A Google Sheets account connected to n8n
- Gmail OAuth credentials configured in n8n
- A Google Sheet with the columns you want to monitor
- A recipient Gmail address

## Workflow Details

- Workflow name: `Gsheets New/Updated Row> Gmail`
- Trigger type: `Google Sheets Trigger`
- Delivery method: `Gmail`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Google Sheets Trigger` node.
3. Connect your Google Sheets account.
4. Select your spreadsheet and target sheet.
5. Make sure your sheet contains the columns referenced in the message, such as `Name` and `Email`.
6. Open the `Send a message` node.
7. Connect your Gmail account.
8. Replace the recipient email address with your own.
9. Update the subject or message format if needed.
10. Save and activate the workflow.

## Use Cases

- New lead notifications
- Spreadsheet row monitoring
- CRM-style alerts from Google Sheets
- Team notifications for updated records

## Notes

- The workflow checks for changes every minute.
- The current message assumes your sheet has `Name` and `Email` columns.
- If your column names are different, update the Gmail message expression in n8n.
- The workflow uses Gmail directly instead of SMTP.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace spreadsheet IDs and URLs
- Remove or replace personal email addresses
- Reconnect your own Google Sheets and Gmail credentials after import

## File

Source workflow:

- `Gsheets New_Updated Row_ Gmail.json`
