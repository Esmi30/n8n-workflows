# Server Monitor

This n8n workflow receives server health metrics through a webhook and sends a Telegram alert when CPU, RAM, and disk usage exceed configured thresholds.

It is useful for lightweight infrastructure monitoring, custom metric alerts, or internal server status notifications.

## What It Does

The workflow has 3 nodes:

1. `Webhook`
2. `If`
3. `Send a text message`

Flow:

- A monitoring client sends a POST request to the webhook
- n8n checks the incoming `cpu`, `ram`, and `disk` values
- If all configured thresholds are exceeded, a Telegram alert is sent

## Webhook

Current webhook path:

```text
server-monitor
```

HTTP method:

```text
POST
```

## Threshold Logic

The workflow currently alerts when:

- `cpu > 80`
- `ram > 80`
- `disk > 90`

The conditions are combined with `and`, which means all of them must be true before an alert is sent.

## Expected Payload

The webhook expects values inside `body`, such as:

```json
{
  "cpu": 85,
  "ram": 83,
  "disk": 92,
  "temp": 67
}
```

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A monitoring script or service that can send webhook POST requests
- Telegram credentials configured in n8n
- A Telegram chat ID or group ID

## Workflow Details

- Workflow name: `Server Monitor`
- Trigger type: `Webhook`
- Notification method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Webhook` node and copy the generated webhook URL.
3. Point your server monitoring script or tool to that URL.
4. Open the `If` node and adjust the threshold values if needed.
5. Open the Telegram node and replace the destination `chatId` with your own.
6. Connect your Telegram credentials.
7. Save and activate the workflow.

## Use Cases

- Custom server metric alerts
- VPS monitoring
- Small infrastructure notifications
- Home lab monitoring

## Notes

- The current logic alerts only when all threshold conditions are exceeded at the same time.
- If you want alerts when any single metric is too high, change the condition combinator from `and` to `or`.
- The exported JSON appears to contain encoded emoji and degree symbols in the Telegram message, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Telegram chat IDs
- Avoid exposing production webhook URLs
- Reconnect your own Telegram credentials after import

## File

Source workflow:

- `Server Monitor.json`
