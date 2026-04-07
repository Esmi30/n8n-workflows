# Customer Support Bot

This n8n workflow uses Telegram and Groq AI to answer customer questions based on a built-in FAQ.

It is useful for basic support automation, FAQ bots, and simple AI assistants that stay within a limited knowledge base.

## What It Does

The workflow has 6 nodes:

1. `Telegram Trigger`
2. `Edit Fields`
3. `AI Agent`
4. `Groq Chat Model`
5. `Simple Memory`
6. `Send a text message`

Flow:

- A Telegram message is received
- The workflow prepares two values: the user's message and a built-in FAQ
- The AI Agent answers using a system instruction that limits responses to the FAQ
- Groq provides the language model
- Memory stores recent context for the conversation
- The response is sent back to Telegram

## FAQ Behavior

The bot is instructed to:

- Answer only from the provided FAQ
- Refuse questions not covered by the FAQ
- Redirect unsupported questions to `support@example.com`

Current FAQ topics include:

- Bot identity
- What the bot can help with
- Human support contact
- Operating hours
- Password reset

## AI Configuration

The workflow uses:

- Provider: `Groq`
- Model: `llama-3.3-70b-versatile`
- Memory type: `Buffer Window Memory`
- Context window length: `10`

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Telegram credentials configured in n8n
- Groq API credentials configured in n8n
- The LangChain AI nodes available in your n8n setup

## Workflow Details

- Workflow name: `Customer Support Bot`
- Trigger type: `Telegram Trigger`
- AI provider: `Groq`
- Delivery method: `Telegram`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the Telegram trigger node and connect your Telegram credentials.
3. Open the `Edit Fields` node and replace the sample FAQ with your own support knowledge.
4. Open the `Groq Chat Model` node and connect your Groq credentials.
5. Review the AI Agent system message and update the fallback response if needed.
6. Open the final Telegram node and replace the destination chat ID with your own.
7. Save and activate the workflow.

## Use Cases

- Telegram FAQ bot
- Small business customer support automation
- Internal helpdesk assistant
- Controlled AI support chatbot

## Notes

- The workflow uses a fixed FAQ stored directly in the workflow.
- Memory is grouped by Telegram chat ID, so conversations can maintain context per chat.
- The fallback support email is currently a placeholder and should be replaced with a real support address.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Telegram chat IDs
- Replace placeholder support emails with your preferred public contact
- Reconnect your own Telegram and Groq credentials after import

## File

Source workflow:

- `Customer Support Bot.json`
