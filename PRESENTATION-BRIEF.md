# Rehbar e Sehat Product Brief

## One-Liner

Rehbar e Sehat turns a difficult-to-read prescription into a spoken Urdu explanation and confirmed medicine reminders.

## Audience

The product is for patients and families who need help reading prescriptions, understanding medicine timing, or identifying a medicine box. It is especially useful for Urdu-speaking users and people who prefer voice over typing.

## Product Story

A user photographs a prescription. The app reads the medicine names and directions, explains them in simple Urdu, checks the extracted schedule for safety concerns, and asks for confirmation before adding alarms. Each alarm shows the photo of the actual medicine box and speaks the reminder aloud.

## Feature Highlights

- Voice-message chat with spoken Urdu responses.
- Prescription extraction into structured medicine schedules.
- Safety review for duplicate active ingredients and implausible directions.
- Medicine-box comparison and visible expiry-date checks.
- Urdu-first right-to-left interface with English support.
- Emergency red-flag escalation and a persistent medical disclaimer.

## How It Works

Qwen 3.7 Plus handles vision, extraction, medicine-box verification, and chat. Qwen 3.7 Max performs text-based grounding and safety reasoning. Browser APIs handle speech, camera access, PDF rendering, image preparation, local storage, and notifications.

## Responsible Use

The product does not diagnose, prescribe, or replace a healthcare professional. It refuses to guess unclear doses and asks the user to confirm uncertain information with a doctor or pharmacist. Emergency symptoms are directed to a hospital or Rescue 1122.

## Presentation Flow

1. Show the Urdu-first home screen.
2. Photograph a sample prescription.
3. Review the extracted medicine and schedule.
4. Show a safety warning or uncertainty state when applicable.
5. Confirm the schedule and open the alarm list.
6. Trigger a test alarm to show the medicine photo and spoken Urdu reminder.
7. Explain the two-model pipeline and the safety boundaries.
