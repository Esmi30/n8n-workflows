# Website Uptime Monitor

This n8n workflow checks whether a website is online and sends a Telegram alert if the site does not return a `200` status code.

It is useful for simple uptime monitoring, portfolio site checks, landing page monitoring, or basic website alerting without a separate monitoring service.

## What It Does

The workflow has 4 nodes:

1. `Schedule Trigger`
2. `HTTP Request`
3. `If`
4. `Send a text message`

Flow:

- The workflow runs on a fixed schedule
- n8n requests the target website URL
- The response status code is checked
- If the status code is not `200`, a Telegram alert is sent

## Monitoring Schedule

The workflow is configured to run:

```text
Every 12 hours
```

## Website Checked

Current monitored URL:

```text
https://edqtorres.my.canva.site/edgardo-torres
```

## Alert Condition

The workflow sends an alert when:

```text
statusCode != 200
```

## Alert Sent

The Telegram alert includes:

- Website name or URL
- HTTP status code
- HTTP status message
- Trigger time

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Telegram credentials configured in n8n
- A Telegram chat ID or group ID
- A website URL to monitor

## Workflow Details

- Workflow name: `Website Uptime Monitor`
- Trigger type: `Schedule Trigger`
- Check method: `HTTP Request`
- Alert method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `HTTP Request` node.
3. Replace the monitored URL with your own website if needed.
4. Open the `If` node if you want to change the alert condition.
5. Open the Telegram node and replace the `chatId` with your own.
6. Connect your Telegram credentials.
7. Adjust the schedule interval if needed.
8. Save and activate the workflow.

## Use Cases

- Portfolio uptime checks
- Small business website monitoring
- Basic alerting without external monitoring tools
- Learning conditional automation in n8n

## Notes

- The workflow is configured to continue even when the HTTP request fails, so it can still send an alert.
- It currently alerts only when the status code is not `200`.
- The exported JSON appears to contain encoded emoji characters in the Telegram text, which can be cleaned up in n8n if needed.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Telegram chat IDs
- Reconnect your own Telegram credentials after import
- Review any personal website URLs before publishing

## File

Source workflow:

- `Website Uptime Monitor.json`
