
# AI Appointment Booking Chatbot

**A conversational appointment-booking prototype built with n8n, OpenAI GPT-5 mini, and Google Calendar.**

This project connects an AI-powered chat interface to an automation workflow that can handle booking requests, maintain conversational context, and create appointments in Google Calendar.

A test booking was successfully confirmed, and the corresponding calendar event was verified.

## At a Glance

| Component | Technology |
|---|---|
| Workflow Automation | n8n |
| AI Agent | n8n AI Agent |
| Language Model | OpenAI GPT-5 mini |
| Chat Interface | n8n Hosted Chat |
| Memory | Simple Memory |
| Calendar Integration | Google Calendar API |
| Verified Outcome | Successful appointment creation in Google Calendar |

## Key Features

- **Natural Language Interaction:** Users can request appointments through a conversational interface.
- **AI-Powered Scheduling:** The assistant suggests three possible appointment slots.
- **Customer Information Collection:** The chatbot requests the customer's first name before confirming a booking.
- **Conversational Memory:** Simple Memory maintains context across multiple interactions.
- **Google Calendar Integration:** The workflow includes tools for retrieving and creating calendar events.
- **Automated Event Creation:** The assistant can create appointments directly in Google Calendar.
- **Timezone Handling:** Appointment times are presented with a specified timezone.
- **Business Hour Configuration:** The assistant is configured to suggest appointments within defined business hours.

## Technologies Used

| Technology | Purpose |
|---|---|
| n8n | Workflow orchestration and automation |
| OpenAI GPT-5 mini | Natural language processing and conversational responses |
| AI Agent | Managing user requests and tool interactions |
| Google Calendar API | Calendar event management |
| Simple Memory | Maintaining conversation context |
| n8n Hosted Chat | Web-based chatbot interface |

## Workflow Architecture

The chatbot follows an AI-driven automation workflow:

```text
                User
                 |
                 v
          n8n Hosted Chat
                 |
                 v
       When Chat Message Received
                 |
                 v
              AI Agent
                 |
       +---------+----------+
       |         |          |
       v         v          v
    OpenAI     Simple     Google
    GPT-5      Memory     Calendar
    mini                    |
                      +-----+-----+
                      |           |
                      v           v
                  Get Events  Create Event
                      |           |
                      +-----+-----+
                            |
                            v
                   Booking Confirmation
```

### Workflow Components

1. **Chat Trigger:** Receives messages from users.
2. **AI Agent:** Processes appointment requests and manages conversations.
3. **OpenAI Chat Model:** Generates natural-language responses.
4. **Simple Memory:** Maintains conversational context.
5. **Google Calendar – Get Many Events:** Provides access to existing calendar events.
6. **Google Calendar – Create Event:** Creates appointments in the connected calendar.

## Chatbot Interface

The chatbot provides a web-based conversational interface for requesting and managing appointments.

![AI Appointment Booking Chatbot](chatbot_bot.jpg)

## Booking Confirmation – Successfully Tested

The appointment-booking workflow was tested using the n8n chatbot.

### Test Scenario

The user requested a 30-minute appointment.

The chatbot proposed three appointment slots and asked for the customer's first name.

The user selected the first available option and provided the name "Test."

The assistant successfully confirmed the appointment and returned a Google Calendar event link.

### Test Details

| Parameter | Value |
|---|---|
| Customer Name | Test |
| Appointment Date | November 20, 2026 |
| Appointment Time | 10:00–10:30 GMT+3 |
| Duration | 30 minutes |
| Booking Confirmation | Successful |
| Calendar Event Creation | Verified |

### Screenshot 1 – AI Chatbot Booking Confirmation

The following screenshot demonstrates the complete conversation, from the initial booking request to the appointment confirmation.

![AI Chatbot Booking Confirmation](booking-confirmation.png)

**Result:** The chatbot successfully processed the appointment request, collected the customer's name, and confirmed the selected booking.

## Google Calendar Integration – Successfully Verified

Following the booking confirmation, the corresponding appointment was verified directly in Google Calendar.

The chatbot confirmed the appointment for:

**November 20, 2026 — 10:00–10:30 GMT+3**

Google Calendar displayed the corresponding event at:

**November 20, 2026 — 08:00–08:30 GMT+1 (Italy)**

These times represent the same appointment in different timezones.

### Screenshot 2 – Google Calendar Event Verification

The screenshot below shows the appointment recorded in Google Calendar after the booking conversation.

![Google Calendar Event Verification](google-calendar-event.png)

**Result:** The appointment was successfully created and independently observed in Google Calendar.

## End-to-End Testing Results

The chatbot was tested through a complete appointment-booking interaction.

| Test | Observed Result | Status |
|---|---|---|
| Request a 30-minute booking | Assistant proposed three appointment slots | ✅ Observed |
| Select an appointment slot | Assistant accepted the selected appointment | ✅ Observed |
| Provide customer name | Assistant acknowledged the customer's first name | ✅ Observed |
| Confirm appointment | Assistant returned a booking confirmation | ✅ Observed |
| Create Google Calendar event | Matching appointment appeared in Google Calendar | ✅ Observed |
| Timezone conversion | Calendar time matched the confirmed booking time | ✅ Observed |

### Test Summary

The test demonstrated successful end-to-end appointment creation through the conversational AI workflow.

The assistant received the user's request, proposed appointment options, collected the required information, and confirmed the booking.

The corresponding event was independently verified in Google Calendar.

**Validation scope:** This test confirms appointment creation and timezone consistency. Conflict detection and prevention of overlapping bookings would require additional tests.

## Reproduce the Workflow

To run this project:

1. Download `AI_Appointment_Booking_Chatbot_Sanitized.json` from this repository.
2. Open n8n and import the JSON workflow.
3. Configure OpenAI API or supported gateway credentials.
4. Connect a Google Calendar account.
5. Select the appropriate calendar for both Google Calendar tools.
6. Review the AI Agent's scheduling instructions, business hours, and timezone.
7. Publish the workflow.
8. Open the Hosted Chat interface.
9. Submit a test booking request.
10. Verify the resulting appointment in Google Calendar.

**Security Note:** API credentials and personal account identifiers are not included in the sanitized workflow.

## Repository Structure

```text
n8n-ai-appointment-booking-chatbot/
|
|-- README.md
|
|-- AI_Appointment_Booking_Chatbot_Sanitized.json
|
|-- chatbot_bot.jpg
|
|-- booking-confirmation.png
|
|-- google-calendar-event.png
```

## Skills Demonstrated

- AI Agent Development
- Workflow Automation with n8n
- OpenAI Integration
- Google Calendar API Integration
- Conversational AI
- Appointment Scheduling Automation
- Multi-Turn Conversation Management
- API-Based Workflow Integration
- End-to-End Workflow Testing
- Technical Documentation

## Project Objective

The objective of this project is to demonstrate how AI agents, conversational interfaces, and automation tools can be integrated to simplify appointment scheduling.

The implementation demonstrates a working booking flow that connects an AI assistant with Google Calendar and successfully creates appointments.

For production use, additional availability validation, double-booking prevention, authentication, and error-handling mechanisms would be required.

---

**Project Type:** AI Automation | AI Agents | Workflow Integration

**Built With:** n8n · OpenAI GPT-5 mini · Google Calendar

**Author:** Masoumeh Nikbakhtifard
