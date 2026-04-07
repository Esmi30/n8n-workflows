# AI Telegram Assistant

This n8n workflow turns Telegram messages into AI chat prompts and sends the assistant response back to Telegram.

It is useful for building a personal AI bot, a simple chat assistant, or a Telegram-based AI playground.

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
- The message text is mapped into a `chatInput` field
- The AI Agent processes the input
- Groq provides the language model
- Memory keeps recent conversation context
- The AI response is sent back to Telegram

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

- Workflow name: `AI Telegram Assistant`
- Trigger type: `Telegram Trigger`
- AI provider: `Groq`
- Model: `llama-3.3-70b-versatile`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the Telegram trigger node and connect your Telegram credentials.
3. Open the `Groq Chat Model` node and connect your Groq credentials.
4. Review the `Simple Memory` node if you want a different conversation length.
5. Open the final Telegram node and replace the destination chat ID if needed.
6. Save and activate the workflow.

## Use Cases

- Personal AI Telegram bot
- AI Q&A assistant
- Telegram chatbot experiments
- Lightweight conversational automation

## Notes

- The workflow currently uses a fixed Telegram chat ID for sending replies.
- Memory is configured with a custom session key set to `default`, so all messages share one conversation session.
- If you want separate conversation memory per user or chat, update the memory session key logic.

## Security Reminder

If you plan to share this workflow publicly:

- Remove or replace Telegram chat IDs
- Reconnect your own Telegram and Groq credentials after import
- Review prompts and agent behavior before publishing

## File

Source workflow:

- `AI Telegram Assistant.json`
