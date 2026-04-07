# Gmail Reminder

This n8n workflow sends a daily reminder email on a fixed schedule.

It is useful for personal reminders, lightweight daily notifications, or simple recurring email automation.

## What It Does

The workflow has 3 nodes:

1. `Schedule Trigger`
2. `Send an Email`
3. `Code in JavaScript`

Flow:

- The schedule trigger runs once per day
- n8n sends an email using SMTP
- A JavaScript code node runs after the email step

## Schedule

The workflow is configured to trigger at:

```text
8:00
```

## Email Details

Current configuration:

- From: `esmyriade@gmail.com`
- To: `esmyriade@gmail.com`
- Subject: `Daily Reminder`
- Message: `Good morning! This is your n8n reminder.`

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- SMTP credentials configured in n8n
- A valid sender email address
- A recipient email address

## Workflow Details

- Workflow name: `Gmail Reminder`
- Trigger type: `Schedule Trigger`
- Delivery method: `SMTP / Email`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Schedule Trigger` node and adjust the trigger time if needed.
3. Open the `Send an Email` node.
4. Replace the sender and recipient email addresses with your own.
5. Connect your SMTP credentials.
6. Customize the subject and message.
7. Save and activate the workflow.

## Use Cases

- Daily self-reminders
- Morning routine notifications
- Follow-up prompts
- Basic scheduled email automation

## About the Code Node

The workflow includes a `Code in JavaScript` node after the email step.

At the moment, it only returns:

```javascript
return [
  {
    json: {
      message: $json.message
    }
  }
];
```

This means it does not add much value unless you plan to extend the workflow further. You can keep it for future logic or remove it if you want a simpler version.

## Notes

- The workflow is currently configured as a fixed daily reminder.
- It uses SMTP credentials, even though the workflow name references Gmail.
- If you are using Gmail SMTP, make sure your account and app-password setup are configured correctly.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace personal email addresses
- Reconnect your own SMTP credentials after import
- Avoid publishing sensitive account configuration details

## File

Source workflow:

- `Gmail Reminder.json`
