# Invoice Generator

This n8n workflow collects invoice details from a form, calculates totals, generates an invoice file, converts it to PDF, and sends it to Telegram.

It is useful for simple invoicing, freelance billing, order invoices, and document generation workflows.

## What It Does

The workflow has 6 nodes:

1. `On form submission`
2. `Code in JavaScript`
3. `Convert to File`
4. `HTTP Request1`
5. `HTTP Request`
6. `Send a document`

Flow:

- A user submits invoice details through an n8n form
- A JavaScript node calculates subtotal, discount, tax, and total
- An HTML invoice is generated dynamically
- The HTML is converted into a file
- A PDF conversion service is used
- The final invoice PDF is sent through Telegram

## Form Fields

The current form collects:

- Customer Name
- Customer Email
- Item Description
- Quantity
- Unit Price
- Discount%
- Tax%
- Due Date

## Calculation Logic

The workflow calculates:

- `subtotal = quantity * unit price`
- `discount amount`
- `tax amount`
- `final total`
- Auto-generated invoice number in the format `INV-<timestamp>`

## PDF Generation

The workflow export includes two PDF conversion paths:

- `HTTP Request1` using a Gotenberg service
- `HTTP Request` using the Doppio API

In the current export:

- `Convert to File` is disabled
- `HTTP Request` is disabled
- The active path appears to rely on the HTML binary being passed to the Gotenberg request

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- A reachable PDF rendering service such as Gotenberg, or your preferred PDF API
- Telegram credentials configured in n8n

## Workflow Details

- Workflow name: `Invoice Generator`
- Trigger type: `Form Trigger`
- Output: `PDF invoice`
- Delivery method: `Telegram document`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the form node and customize the invoice fields if needed.
3. Review the JavaScript node if you want to change branding, layout, or calculation rules.
4. Decide which PDF conversion path you want to use.
5. If using Gotenberg, make sure the `gotenberg:3000` service is reachable from n8n.
6. If using Doppio or another API, enable and configure the correct HTTP node.
7. Open the Telegram document node and replace the destination `chatId` if needed.
8. Save and activate the workflow.

## Use Cases

- Freelance invoice generation
- Client billing automation
- Simple PDF document generation
- Form-to-document workflows

## Notes

- The invoice HTML is generated directly in the code node.
- The export contains disabled alternative conversion nodes, which suggests the workflow is still flexible or in progress.
- The exported JSON appears to contain encoded peso and symbol characters in the HTML template, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Telegram chat IDs
- Remove or replace any API credentials used for PDF services
- Reconnect your own Telegram and document conversion credentials after import

## File

Source workflow:

- `Invoice Generator.json`
