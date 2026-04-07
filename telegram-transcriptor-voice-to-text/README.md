# Telegram Transcriptor: Voice to Text

This n8n workflow listens for Telegram voice messages, downloads the audio, transcribes it with Groq Whisper, and sends the transcript back to Telegram.

It is useful for voice note transcription, quick speech-to-text automation, and Telegram-based AI utilities.

## What It Does

The workflow has 7 nodes:

1. `Telegram Trigger`
2. `If`
3. `Get File Name`
4. `Download the File`
5. `File conversion`
6. `Transcript`
7. `Send a text message`

Flow:

- A Telegram message is received
- The workflow checks whether the message contains a voice file
- Telegram file metadata is fetched
- The voice file is downloaded
- The binary is normalized as an `.ogg` audio file
- Groq transcription is called with `whisper-large-v3-turbo`
- The transcript is sent back to Telegram

## Trigger

The workflow listens for:

```text
Telegram message updates
```

It continues only when a voice message exists.

## AI Transcription

The workflow sends the audio file to:

```text
https://api.groq.com/openai/v1/audio/transcriptions
```

Current model:

```text
whisper-large-v3-turbo
```

## Output

The Telegram reply contains the transcribed text from the voice note.

## Requirements

Before using this workflow, make sure you have:

- An n8n instance
- Telegram credentials configured in n8n
- A Groq API credential configured in n8n
- A Telegram bot connected to your workflow

## Workflow Details

- Workflow name: `Telegram Transcriptor: Voice to Text`
- Trigger type: `Telegram Trigger`
- AI provider: `Groq`
- Function: `Voice transcription`
- Status: `Active`

## Setup

1. Import the workflow JSON into n8n.
2. Open the `Telegram Trigger` node and connect your Telegram credentials.
3. Review the Telegram file download steps.
4. Open the `Transcript` node and connect your Groq credentials.
5. Confirm the transcription model you want to use.
6. Open the final Telegram node and replace the destination chat ID if needed.
7. Save and activate the workflow.

## Use Cases

- Telegram voice note transcription
- Speech-to-text automation
- Personal productivity bots
- AI messaging assistants

## Notes

- The workflow handles only voice messages, not general files or text messages.
- The code node prepares the Telegram audio file so the transcription API can process it correctly.
- The exported JSON appears to contain encoded emoji characters in the outgoing message text, which can be cleaned up in n8n.

## Security Reminder

If you plan to share this workflow publicly:

- Remove any embedded Telegram bot tokens from HTTP request URLs
- Remove or replace Telegram chat IDs
- Reconnect your own Telegram and Groq credentials after import

## File

Source workflow:

- `Telegram Transcriptor_ Voice to Text.json`
