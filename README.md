# Udhaar Book

Udhaar Book is a voice-first digital khaata for small shopkeepers. Speak or type a note in Urdu, Roman Urdu, Punjabi, Hindi, English, or a mix; review the suggested credit and payment entries; then save them to a ledger on this device. The app calculates customer balances and prepares polite, individual WhatsApp reminders.

## Run it

This project runs as a Replit web app with two services:

1. Add `GEMINI_API_KEY` in Replit Secrets. Optionally set `GEMMA_MODEL`; the default is `gemma-4-26b-a4b-it`.
2. Start the **API Server** and **Udhaar Book** workflows.

The frontend is served by the `@workspace/udhaar-book` React/Vite artifact. AI requests run through the existing `@workspace/api-server` service; the API key remains server-side. The shared API service needs Node.js and pnpm as provided by the project.

## Screenshot

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/2386b761-f54d-48b0-8588-98830a3336b7" />


## Powered by Gemma 4

The app uses `gemma-4-26b-a4b-it` through the Gemini API. You can change the model ID with `GEMMA_MODEL` after checking the exact available ID in [Google AI Studio](https://aistudio.google.com/).

- [Gemma terms and license](https://ai.google.dev/gemma/terms)
- [Gemini API terms](https://ai.google.dev/gemini-api/terms)

## Your data stays with you

Ledger entries and settings are stored only in this browser's local storage. There are no accounts, phone numbers, or server-side ledger database. When you ask to parse a note, its text is sent to the server and Gemini API for processing. When you generate reminders, only customers with positive balances are sent for reminder generation. WhatsApp opens with a prepared message so the shopkeeper chooses the contact.

## How the AI is used

The server loads the complete [Udhaar Ledger prompt](prompts/udhaar-ledger.md) at startup and uses it as the system instruction for parsing and reminder requests. The app validates model responses before showing them. Low-confidence entries are never saved without the shopkeeper's review.
