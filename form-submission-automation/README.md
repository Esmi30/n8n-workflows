# Form Submission Automation

This n8n workflow collects form submissions, stores them in Google Sheets, and sends a Gmail notification for each new entry.

It is useful for simple lead capture, contact forms, sign-up forms, or internal request collection workflows.

## What It Does

The workflow has 3 nodes:

1. `On form submission`
2. `Append row in sheet`
3. `Send a message`

Flow:

- A user submits the n8n form
- The submitted name and email are captured
- A new row is appended to Google Sheets
- A Gmail notification is sent with the submitted details

## Form Fields

The current form includes:

- `What is your name`
- `What is your email`

## Data Storage

The workflow appends submissions to a Google Sheet with these columns:

- `Name`
- `Email`

## Email Sent

Current subject:

```text
New Form Submission from {{ Name }}
```

Current message format:

```text
Name: {{ Name }}
Email: {{ Email }}
```

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A Google Sheets account connected to n8n
- A Gmail account connected to n8n
- A target Google Sheet with matching columns

## Workflow Details

- Workflow name: `Form Submission Automation`
- Trigger type: `Form Trigger`
- Storage: `Google Sheets`
- Notification method: `Gmail`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `On form submission` node and customize the form title or fields if needed.
3. Open the `Append row in sheet` node.
4. Connect your Google Sheets account.
5. Select your spreadsheet and sheet.
6. Make sure the sheet contains the columns `Name` and `Email`, or update the mappings.
7. Open the `Send a message` node.
8. Connect your Gmail account.
9. Replace the recipient email address with your own.
10. Save and activate the workflow.

## Use Cases

- Contact form automation
- Lead capture workflows
- Event registration forms
- Internal intake forms

## Notes

- The workflow is designed for simple two-field submissions.
- You can add more fields to the form and map them into Google Sheets and Gmail.
- The Google Sheet and Gmail account should be replaced with your own before publishing or reuse.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace spreadsheet IDs and URLs
- Remove or replace personal email addresses
- Reconnect your own Google Sheets and Gmail credentials after import

## File

Source workflow:

- `Form Submission Automation.json`
