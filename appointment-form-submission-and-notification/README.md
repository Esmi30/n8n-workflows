# Appointment Form Submission and Notification

This n8n workflow receives appointment bookings from Jotform, generates a booking ID, stores the appointment in Airtable, sends a Telegram notification, and emails a confirmation to the customer.

It is useful for appointment intake, booking systems, and service scheduling automation.

## What It Does

The workflow has 6 nodes:

1. `Form Submission`
2. `Set Booking ID`
3. `Get List of Appointment`
4. `Create record in Airtable`
5. `Form Submission Notification`
6. `Send a message`

Flow:

- A user submits the appointment form through Jotform
- A unique booking ID is generated
- Appointment details are normalized and formatted
- A new record is saved to Airtable
- A Telegram notification is sent to the admin side
- A Gmail confirmation is sent to the customer

## Booking Data Captured

The workflow prepares fields such as:

- Booking ID
- Customer Name
- Email Address
- Phone Number
- Service
- Appointment Date
- Appointment Time
- Reminder Status
- Notes

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Jotform credentials configured in n8n
- Airtable credentials configured in n8n
- Gmail credentials configured in n8n
- Telegram credentials configured in n8n

## Workflow Details

- Workflow name: `Appointment Form Submission and Notification`
- Trigger type: `Jotform Trigger`
- Storage: `Airtable`
- Notification methods: `Telegram` and `Gmail`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Form Submission` node and connect your Jotform account.
3. Make sure your form fields still match the workflow logic used in the code node.
4. Open the Airtable nodes and connect your Airtable account.
5. Select your base and table.
6. Open the Telegram node and replace the destination `chatId` if needed.
7. Open the Gmail node and connect your Gmail account.
8. Review the email confirmation text and customize it if needed.
9. Save and activate the workflow.

## Use Cases

- Booking automation
- Appointment intake systems
- Service scheduling workflows
- Customer confirmation flows

## Notes

- The code node formats the date and time for human-readable output and also stores raw values for later reminders.
- `Reminder Status` is initialized as `Pending` for follow-up workflows.
- One Airtable node named `Get List of Appointment` appears to be present in the flow but may not be doing meaningful retrieval in the current version.
- The exported JSON appears to contain encoded emoji characters in the Telegram and email messages, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Jotform form IDs
- Remove or replace Airtable base and table IDs
- Remove or replace Telegram chat IDs
- Reconnect your own Jotform, Airtable, Gmail, and Telegram credentials after import

## File

Source workflow:

- `Appointment Form Submission and Notification.json`
