# Cookie Order System Telegram Message

This n8n workflow watches the `Orders` sheet for new Cookie Order System orders and sends a formatted Telegram notification with customer and order details.

It is useful for bakery order alerts, admin notifications, and spreadsheet-based order intake tracking.

## What It Does

The workflow has 3 nodes:

1. `Google Sheets Trigger`
2. `Code in JavaScript`
3. `Send a text message`

Flow:

- A new row is added to the `Orders` sheet
- A JavaScript node scans the product columns after `Date of Delivery`
- Ordered items with quantities greater than zero are collected into a readable summary
- A Telegram message is sent with customer info, payment details, delivery date, and ordered flavors

## Trigger Schedule

The workflow checks the sheet:

```text
Every minute
```

## Data Included

The Telegram alert currently includes:

- Customer name
- Email
- Total amount
- Mode of payment
- Delivery date
- Product or flavor summary

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Google Sheets credentials configured in n8n
- Telegram credentials configured in n8n
- A Google Sheet with the expected order columns

## Workflow Details

- Workflow name: `Cookie Order System Telegram Message`
- Trigger type: `Google Sheets Trigger`
- Data source: `Google Sheets`
- Notification method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Google Sheets Trigger` node and connect your Google Sheets account.
3. Select the correct spreadsheet and `Orders` sheet.
4. Make sure the product columns are placed after `Date of Delivery`, since the code node depends on that layout.
5. Open the Telegram node and replace the destination `chatId` if needed.
6. Connect your Telegram credentials.
7. Save and activate the workflow.

## Use Cases

- New order notifications
- Bakery operations alerts
- Spreadsheet-driven order management
- Team order updates in Telegram

## Notes

- The JavaScript node assumes `Date of Delivery` is the divider before item columns.
- Product quantities must be numeric or convertible to numbers.
- The exported JSON appears to contain encoded emoji and currency characters in the Telegram text, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace spreadsheet IDs and URLs
- Remove or replace Telegram chat IDs
- Reconnect your own Google Sheets and Telegram credentials after import

## File

Source workflow:

- `Cookie Order System Telegram Message.json`
