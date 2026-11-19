[README (1).md](https://github.com/user-attachments/files/35093033/README.1.md)


# AI Appointment Booking Chatbot

**A conversational appointment-booking prototype built with n8n, OpenAI GPT-5 mini, and Google Calendar.**

This project connects an AI-powered chat interface to an automation workflow that can handle booking requests, maintain conversational context, and create appointments in Google Calendar. A test booking was successfully confirmed and the corresponding calendar event was observed.

## At a glance

| | |
|---|---|
| **Orchestration** | n8n AI Agent |
| **Language model** | OpenAI GPT-5 mini |
| **Chat interface** | n8n Hosted Chat |
| **Memory** | Simple Memory (20-message context window setting) |
| **Calendar tools** | Google Calendar — Get Many Events and Create Event |
| **Verified outcome** | A test appointment appeared in Google Calendar |

## Features

- **Natural-language booking:** Customers request an appointment in ordinary conversation.
- **Guided slot selection:** The assistant suggests three possible time slots and asks the customer to choose one.
- **Name collection:** The assistant requests the customer's first name before confirming a booking.
- **Conversational context:** Simple Memory supports multi-turn interactions.
- **Calendar integration:** The AI Agent has tools for retrieving events and creating an event in Google Calendar.
- **Time and business-hour instructions:** The demonstration prompt uses a seven-day booking window, 09:00–17:00 business hours, and GMT+3 for customer-facing times.

> **Scope of validation:** The test below verifies a successful **event-creation outcome**. It does **not** establish that all proposed slots were checked for conflicts, or that double bookings are prevented. Those require separate availability and concurrency tests.

## Workflow architecture

```text
n8n Hosted Chat
      |
      v
When chat message received
      |
      v
   AI Agent -------- OpenAI GPT-5 mini
      |
      +-------------- Simple Memory
      |
      +-------------- Google Calendar: Get Many Events
      |
      +-------------- Google Calendar: Create Event
      |
      v
Chat response / booking confirmation
```

The workflow is provided as an importable, sanitized n8n JSON export. Credentials, calendar IDs and instance-specific identifiers have been removed and must be configured after importing.

## Demo: appointment booking confirmation

A test user requested a 30-minute appointment. The assistant proposed three slots, asked for a first name, accepted the first selected slot, and returned a booking confirmation.

<img width="1280" height="768" alt="2026-11-19 15 37 01" src="https://github.com/user-attachments/assets/bfbd7ac2-d4fa-4d38-b43b-60740159fcb2" />


*Figure 1 — The chatbot conversation confirms a 30-minute appointment for 20 November 2026, 10:00–10:30 (GMT+3). The unique event URL is concealed in the public screenshot.*

## Demo: Google Calendar event created

The corresponding event is visible in Google Calendar at **08:00 on 20 November 2026**, displayed in **GMT+1 (Italy)**. That corresponds to **10:00 GMT+3**, matching the assistant's confirmed appointment time.

<img width="1280" height="769" alt=" calender" src="https://github.com/user-attachments/assets/b5cc2f94-923b-40e2-8616-d02fab6abc08" />


*Figure 2 — Calendar verification of the appointment created during the chat demonstration.*

### Test summary

| Test | Observed result | Status |
|---|---|---|
| Request a 30-minute booking | Assistant proposed three time slots | ✅ Observed |
| Select a slot and provide a first name | Assistant acknowledged the selected slot and name | ✅ Observed |
| Confirm booking | Assistant returned a dated, timed confirmation | ✅ Observed |
| Create calendar event | Matching event was visible in Google Calendar | ✅ Observed |
| Validate offered slots against existing events | Calendar lookup at suggestion time was not independently confirmed | ⏳ Not verified |
| Prevent overlapping bookings | Dedicated conflict test not performed | ⏳ Not verified |

## Reproduce the workflow

1. Download [`AI_Appointment_Booking_Chatbot_Sanitized.json`](AI_Appointment_Booking_Chatbot_Sanitized.json).
2. In n8n, **Import from File** and select the JSON export.
3. Connect an OpenAI API or supported gateway credential to **OpenAI Chat Model**.
4. Connect a Google Calendar credential to both Calendar tool nodes.
5. Replace `YOUR_GOOGLE_CALENDAR_ID` in the imported Calendar nodes with the calendar you intend to use.
6. Review the AI Agent's prompt, business hours, timezone, and event duration for your own use case.
7. Publish the workflow and test the Hosted Chat link.
8. Send a test booking request and verify the new event in Google Calendar and the corresponding n8n execution logs.

> **Before public deployment:** Add access controls, rate limiting and an explicit check for calendar conflicts before creating events. The example chat was configured for testing and should not be treated as a production-ready scheduling service.

## Repository contents

```text
.
├── README.md
├── AI_Appointment_Booking_Chatbot_Sanitized.json
├── chatbot_bot.jpg                  # Original chatbot interface preview
├── booking-confirmation.png        # Test conversation and confirmation
└── google-calendar-event.png       # Matching Google Calendar event
```

## What this project demonstrates

- AI agent orchestration in n8n
- Integration of a language model with external tools
- Multi-turn conversational interaction
- Calendar event creation with timezone conversion
- Practical workflow testing and documentation

---

**Project type:** AI automation / portfolio project  
**Built with:** n8n · OpenAI · Google Calendar

