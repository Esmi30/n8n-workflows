# Appointment Reminder Workflow

This n8n workflow checks Airtable every hour for upcoming appointments and sends Telegram reminders for bookings scheduled for tomorrow, then marks them as completed.

It is useful for booking reminder systems, service appointment follow-ups, and admin-side scheduling alerts.

## What It Does

The workflow has 6 nodes:

1. `Runs every hour`
2. `Get Appointment Records`
3. `Check Pending Records`
4. `Combine Appointment Date and Time`
5. `If the Appointment is Tomorrow and Status is Pending`
6. `Send Appointment Reminder`
7. `Update Reminder to Done`

Flow:

- The workflow runs every hour
- Appointment records are loaded from Airtable
- Records are expanded and their date/time values are combined
- The workflow checks whether the appointment is tomorrow
- Only records with `Reminder Status = Pending` continue
- A Telegram reminder is sent
- The Airtable record is updated to `Done`

## Schedule

The workflow is configured to run:

```text
Every hour
```

## Reminder Logic

The workflow sends a reminder when:

- The appointment date equals tomorrow in the `Asia/Manila` time zone
- The reminder status is still `Pending`

After sending, it updates:

```text
Reminder Status = Done
```

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Airtable credentials configured in n8n
- Telegram credentials configured in n8n
- Appointment records stored in Airtable with the expected fields

## Workflow Details

- Workflow name: `Appointment Reminder Workflow`
- Trigger type: `Schedule Trigger`
- Data source: `Airtable`
- Notification method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the Airtable nodes and connect your Airtable account.
3. Select the correct base and table.
4. Make sure your records include fields like `Booking ID`, `Customer Name`, `Appointment Date`, `Appointment Time`, and `Reminder Status`.
5. Open the Telegram node and replace the destination `chatId` if needed.
6. Save and activate the workflow.

## Use Cases

- Appointment reminder systems
- Admin notifications before scheduled services
- Airtable-based scheduling workflows
- Follow-up automation for bookings

## Notes

- The date parsing uses the `Asia/Manila` time zone.
- The workflow updates records by matching on `Booking ID`.
- The first `Check Pending Records` node only checks the first returned Airtable record, while the later logic properly iterates across records, so you may want to simplify or revise that first filter.
- The exported JSON appears to contain encoded emoji characters in the Telegram message, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Airtable base and table IDs
- Remove or replace Telegram chat IDs
- Reconnect your own Airtable and Telegram credentials after import

## File

Source workflow:

- `Appointment Reminder Workflow.json`
