# Daily Weather

This n8n workflow fetches the current weather for Manila every day and sends the report through both email and Telegram.

It is useful for personal daily updates, simple weather notifications, or learning how to combine APIs with multi-channel alerts in n8n.

## What It Does

The workflow has 4 nodes:

1. `Schedule Trigger`
2. `HTTP Request`
3. `Send an Email`
4. `Send a text message`

Flow:

- The workflow starts on a daily schedule
- n8n sends an HTTP request to WeatherAPI
- The current weather data for Manila is returned
- A weather summary is sent by email
- The same summary is also sent to Telegram

## Schedule

The workflow is configured to trigger at:

```text
8:00
```

## Weather Source

The workflow requests current weather data from:

```text
http://api.weatherapi.com/v1/current.json
```

Current location:

```text
Manila
```

## Data Included

The email and Telegram message include:

- Temperature in Celsius
- Weather condition
- Wind speed
- Humidity
- Local time

## Delivery Channels

This workflow sends the weather report to:

- Email via SMTP
- Telegram chat or group

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A WeatherAPI account and API key
- SMTP credentials configured in n8n
- Telegram credentials configured in n8n
- A valid email sender and recipient
- A Telegram chat ID or group ID

## Workflow Details

- Workflow name: `Daily Weather`
- Trigger type: `Schedule Trigger`
- Weather provider: `WeatherAPI`
- Location: `Manila`
- Delivery methods: `Email` and `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `HTTP Request` node.
3. Replace the WeatherAPI key with your own key.
4. Change the location if you want weather for a different city.
5. Open the `Send an Email` node and update the sender and recipient email addresses.
6. Connect your SMTP credentials.
7. Open the Telegram node and replace the `chatId` with your own.
8. Connect your Telegram credentials.
9. Adjust the schedule time if needed.
10. Save and activate the workflow.

## Example Output

Example weather summary:

```text
Temperature: 31°C
Condition: Partly cloudy
Wind: 12 kph
Humidity: 70%
Time: 2026-04-07 08:00
```

## Use Cases

- Daily personal weather updates
- Morning automation routines
- Multi-channel alerts with API data
- n8n learning projects

## Notes

- The workflow is currently configured for Manila.
- It sends the same weather data to both email and Telegram.
- The subject line and Telegram message can be customized.
- The exported JSON appears to contain encoded emoji characters in the message text, which can be cleaned up in n8n if needed.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace the WeatherAPI key
- Remove or replace personal email addresses
- Remove or replace Telegram chat IDs
- Reconnect your own SMTP and Telegram credentials after import

## File

Source workflow:

- `Daily Weather.json`
