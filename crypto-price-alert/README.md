# Crypto Price Alert

This n8n workflow checks the PHP price of USDT on a schedule and sends a Telegram alert when the price falls below or rises above configured thresholds.

It is useful for simple crypto monitoring, peso-based stablecoin tracking, or Telegram-based market alerts.

## What It Does

The workflow has 5 nodes:

1. `Schedule Trigger`
2. `HTTP Request`
3. `Switch`
4. `Telegram Alert`
5. `Telegram Alert`
6. `Telegram Alert`

Flow:

- The workflow runs on a daily schedule
- n8n fetches the current `tether` price in `php` from CoinGecko
- A switch checks the result against threshold conditions
- A Telegram alert is sent depending on whether the price is below, above, or outside the expected range

## Schedule

The workflow is configured with this cron expression:

```text
0 6 * * *
```

This means it runs every day at `06:00`.

## Price Source

The workflow requests price data from:

```text
https://api.coingecko.com/api/v3/simple/price?ids=tether&vs_currencies=php
```

## Thresholds

Current alert rules:

- Alert if USDT is lower than `55`
- Alert if USDT is greater than `65`
- A fallback branch also sends a general crypto alert when the value exists

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Internet access from your n8n instance to CoinGecko
- Telegram credentials configured in n8n
- A Telegram chat ID or group ID

## Workflow Details

- Workflow file name: `Crypto Price Alert`
- Workflow display name in export: `My workflow 3`
- Trigger type: `Schedule Trigger`
- Data source: `CoinGecko`
- Alert method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Rename the workflow if you want a clearer title inside n8n.
3. Open the `HTTP Request` node and update the token or currency pair if needed.
4. Review the `Switch` node and adjust the threshold values to your preferred alert range.
5. Open each Telegram node and replace the `chatId` with your own.
6. Connect your Telegram credentials.
7. Adjust the schedule if needed.
8. Save and activate the workflow.

## Use Cases

- Daily USDT monitoring
- Peso exchange tracking
- Telegram market alerts
- Basic threshold-based price notifications

## Notes

- The exported workflow name inside n8n is currently `My workflow 3`, even though the file is labeled `Crypto Price Alert`.
- The third switch branch triggers whenever the price value exists, so it may send an alert even when the price is within range.
- The exported JSON appears to contain encoded emoji and currency characters in the Telegram text, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Telegram chat IDs
- Reconnect your own Telegram credentials after import
- Review threshold logic before publishing so others do not inherit unintended alerts

## File

Source workflow:

- `Crypto Price Alert.json`
