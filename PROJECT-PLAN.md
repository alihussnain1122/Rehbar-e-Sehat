# Rehbar e Sehat Product Plan

## Purpose

Rehbar e Sehat helps people who cannot easily read a written prescription understand what their doctor wrote and remember when to take each medicine. The experience is designed around camera input, voice, pictures, and large touch targets.

## Core Workflow

1. The user photographs a prescription or medicine box.
2. Qwen vision extracts readable medicine names and directions into strict JSON.
3. A second Qwen pass checks grounding, duplicate ingredients, interactions, and implausible schedules.
4. The user reviews and confirms the schedule.
5. The app creates local medicine alarms with the medicine-box photo and Urdu announcement.

## Current Scope

- Urdu-first and bilingual responsive PWA.
- Prescription extraction with self-consistency voting.
- Medicine-box comparison and expiry reading.
- Voice questions and spoken Urdu responses.
- On-device alarm storage using localStorage and IndexedDB.
- Foreground alarm ring experience and service-worker notifications.
- Safety guardrails for unclear doses and emergency symptoms.

## Technical Boundaries

The browser handles camera, image preparation, PDF rendering, speech input, speech output, local storage, and notifications. Server-side Next.js routes handle model calls so the API key never reaches the client. There is no account system or server database.

## Safety Requirements

- Never invent an unreadable dose or schedule.
- Ask the user to confirm extracted directions before creating alarms.
- Never diagnose or prescribe.
- Escalate chest pain, breathing difficulty, heavy bleeding, unconsciousness, stroke signs, seizures, poisoning, overdose, or severe allergic reactions to emergency care and Rescue 1122.
- Clearly remind users to confirm medication instructions with a doctor or pharmacist.

## Future Work

- Server-side push notifications for alarms when the app is closed.
- Caregiver profiles and adherence summaries.
- Broader medicine-image coverage for box verification.
- Offline support for saved alarms and medicine photos.

## Development Commands

```bash
npm install
npm run dev
npm run lint
npm run build
npm run eval
```
