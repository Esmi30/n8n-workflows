# File Upload Notification

This n8n workflow watches a Google Drive folder and sends a Telegram message whenever a new file is uploaded.

It is useful for team file alerts, shared folder monitoring, content pipeline notifications, or simple Google Drive activity tracking.

## What It Does

The workflow has 2 nodes:

1. `Google Drive Trigger`
2. `Send a text message`

Flow:

- n8n checks a specific Google Drive folder on a schedule
- A new file is detected
- File details are pulled from Google Drive
- A Telegram notification is sent with the file name and link

## Trigger Schedule

The workflow is configured to check the folder:

```text
Every minute
```

## Trigger Event

The workflow is set to watch:

- A specific Google Drive folder
- Event type: `fileCreated`

## Notification Sent

The Telegram message includes:

- File name
- Google Drive file link

Example structure:

```text
A new file has been uploaded to Google Drive Folder:

Name: [File Name]
Link: [Google Drive Link]
```

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A Google Drive account connected to n8n
- Telegram credentials configured in n8n
- Access to the Google Drive folder you want to monitor
- A Telegram chat ID or group ID

## Workflow Details

- Workflow name: `File Upload Notification`
- Trigger type: `Google Drive Trigger`
- Event: `fileCreated`
- Notification method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Google Drive Trigger` node.
3. Connect your Google Drive account.
4. Select the folder you want to monitor.
5. Open the Telegram node.
6. Replace the `chatId` with your own Telegram chat or group ID.
7. Connect your Telegram credentials.
8. Save and activate the workflow.

## Use Cases

- Shared drive upload alerts
- Team collaboration notifications
- Content review workflows
- Asset pipeline monitoring

## Notes

- The workflow checks only one specific folder.
- It currently sends alerts only when a new file is created.
- You can expand it to handle updates, moves, or file-type filtering.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Google Drive folder IDs and URLs
- Remove or replace Telegram chat IDs
- Reconnect your own Google Drive and Telegram credentials after import

## File

Source workflow:

- `File Upload Notification.json`
