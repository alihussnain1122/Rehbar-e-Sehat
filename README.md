# Rehbar e Sehat

Rehbar e Sehat is an Urdu-first medical assistant for people who find written prescriptions difficult to read. Photograph a prescription, hear it explained in spoken Urdu, and create medicine reminders that show a photo of the actual box.

## What It Does

- Reads prescription and medicine-box photos with Qwen vision models.
- Converts prescription directions into structured medicine schedules.
- Uses a second Qwen model for grounding, duplicate-ingredient checks, and safety warnings.
- Lets users confirm extracted schedules before creating alarms.
- Rings alarms with the medicine photo and an Urdu voice announcement.
- Supports voice questions and spoken Urdu answers.
- Provides an Urdu-first, right-to-left interface with an English toggle.
- Escalates emergency symptoms and clearly states that it is not a doctor.

## Architecture

The application is a Next.js progressive web app. Images and voice input are collected in the browser, while model calls are proxied through server-side API routes. Alarms and medicine photos are stored on the device using localStorage and IndexedDB.

```text
Browser PWA
  camera / gallery / Web Speech API
          |
          v
  Next.js API routes: /api/chat, /api/extract, /api/safety, /api/verify
          |
          +--> Qwen vision model: extraction, chat, medicine-box checks
          |
          +--> Qwen reasoning model: grounding and safety checks
```

## Technology

- Next.js 16 App Router, React 19, and TypeScript
- Tailwind CSS v4
- Google Gemini through its OpenAI-compatible API, with Qwen/DashScope support retained as a fallback
- Browser Web Speech API for Urdu speech input and output
- localStorage and IndexedDB for on-device alarm data and photos
- Service worker and Notification API for alarm notifications

## Setup

Requires Node.js 18 or newer.

```bash
npm install
cp .env.example .env.local
npm run dev
```

Open `http://localhost:3000` in a browser. For a production build:

```bash
npm run build
npm start
```

### Environment Variables

| Variable | Required | Purpose |
|---|---|---|
| `GEMINI_API_KEY` | Yes for Gemini | Server-side Gemini API key |
| `GEMINI_BASE_URL` | No | Defaults to Gemini's OpenAI-compatible endpoint |
| `GEMINI_VISION_MODEL` | No | Defaults to `gemini-3.8-flash` |
| `GEMINI_REASONING_MODEL` | No | Defaults to `gemini-3.8-flash` |
| `DASHSCOPE_API_KEY` | No | Qwen fallback key when Gemini is not configured |
| `DASHSCOPE_BASE_URL` | No | Qwen fallback endpoint |
| `QWEN_VISION_MODEL` | No | Qwen fallback vision model |
| `QWEN_REASONING_MODEL` | No | Qwen fallback reasoning model |
| `EVAL_URL` | No | Optional endpoint override for the evaluation harness |

See [`.env.example`](.env.example) for the full template. The API key is used only by server-side routes.

Set `GEMINI_API_KEY` in `.env.local` to use Gemini. The app selects Gemini automatically when that variable is present; otherwise it uses the Qwen/DashScope variables.

## Evaluation Harness

The `eval/` directory contains a small harness for measuring extraction accuracy against hand-labeled prescription photos.

```bash
npm run dev
npm run eval
```

See [`eval/README.md`](eval/README.md) for the label format and privacy guidance. Do not commit real patient data.

## Project Structure

- `app/` contains the application shell, pages, metadata, and API routes.
- `components/` contains the client UI and alarm workflow.
- `lib/` contains shared schemas, model clients, prompts, speech, image, storage, and scheduling helpers.
- `eval/` contains the extraction evaluation harness.
- `public/` and `Logos/` contain static assets and the service worker.

## Safety

Rehbar e Sehat does not diagnose, prescribe, or replace a qualified medical professional. It interprets what a prescription appears to say, refuses to guess unclear doses, and directs users to emergency care for red-flag symptoms. Always confirm medication instructions with a doctor or pharmacist.
# Rehbar-e-Sehat
