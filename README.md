# AI Appointment Booking Chatbot

An AI-powered appointment booking chatbot built with **n8n, OpenAI GPT-5 mini, and Google Calendar**.

This project demonstrates how conversational AI and workflow automation can simplify appointment scheduling by allowing users to request appointments, select time slots, and automatically create events in Google Calendar.

**Project Status:** Functional prototype — Appointment creation successfully tested and verified.

## Project Overview

The objective of this project is to integrate an AI-powered conversational interface with an automated scheduling workflow.

The chatbot processes natural-language requests, maintains conversational context, provides appointment options, and connects to Google Calendar to manage booking operations.

The system was tested through an end-to-end booking scenario, successfully creating an appointment that was subsequently verified in Google Calendar.

## Key Features

- **AI-Powered Chatbot:** Natural-language interaction using OpenAI GPT-5 mini.
- **Appointment Scheduling:** Suggests three appointment options within configured business hours.
- **Google Calendar Integration:** Connects to Google Calendar for event retrieval and creation.
- **Automated Booking:** Creates calendar events based on user requests.
- **Conversation Memory:** Maintains conversational context using n8n Simple Memory.
- **Customer Information:** Collects the customer's first name before confirming appointments.
- **Timezone Handling:** Provides appointment times with an explicitly specified timezone.
- **Web-Based Interface:** Accessible through n8n Hosted Chat.

## Technologies Used

| Technology | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| OpenAI GPT-5 mini | Natural-language processing and response generation |
| AI Agent | Conversation management and tool execution |
| Google Calendar API | Calendar event retrieval and creation |
| Simple Memory | Conversation context management |
| n8n Hosted Chat | Web-based chatbot interface |

## Workflow Architecture

The workflow consists of six interconnected components:

1. **Chat Trigger:** Receives messages from the user.
2. **AI Agent:** Interprets booking requests and coordinates actions.
3. **OpenAI Chat Model:** Generates conversational responses.
4. **Simple Memory:** Maintains conversation history and context.
5. **Google Calendar – Get Many Events:** Retrieves existing calendar events.
6. **Google Calendar – Create Event:** Creates confirmed appointments in Google Calendar.

### Workflow Process

User Message → Chat Trigger → AI Agent → OpenAI Model → Google Calendar Integration → Booking Confirmation

The AI Agent is connected to the language model, conversation memory, and Google Calendar tools to support the appointment-booking process.

---

## End-to-End Booking Test

A complete appointment-booking scenario was performed to validate the integration between the AI chatbot and Google Calendar.

### Test Scenario

The user initiated the conversation with the following request:

*Hi, I want to book a 30-minute appointment.*

The chatbot responded by proposing three appointment slots and requesting the customer's first name.

The user selected the first available option:

*My name is Test. I would like to book the first available slot.*

The chatbot processed the request, confirmed the appointment, and returned a Google Calendar event link.

### Test 1 — AI Chatbot Booking Confirmation

The screenshot below demonstrates the conversation between the user and the AI assistant, including the appointment request, proposed time slots, customer information, and booking confirmation.

![AI Chatbot Booking Confirmation](booking-confirmation.png)

*Figure 1. Successful appointment booking and confirmation through the AI-powered chatbot.*

**Observed Result:** The chatbot successfully processed the appointment request and returned a booking confirmation.

---

## Google Calendar Integration Verification

Following the chatbot confirmation, the corresponding appointment was checked directly in Google Calendar.

### Booking Details

| Parameter | Value |
|---|---|
| Customer Name | Test |
| Appointment Date | November 20, 2026 |
| Appointment Duration | 30 minutes |
| Chatbot Booking Time | 10:00–10:30 (GMT+3) |
| Google Calendar Time | 08:00–08:30 (GMT+1) |
| Booking Confirmation | Successful |
| Calendar Event Creation | Verified |

The difference between the chatbot time and Google Calendar time reflects the timezone conversion from GMT+3 to GMT+1.

### Test 2 — Google Calendar Event Creation

The screenshot below shows the appointment successfully recorded in Google Calendar following the chatbot interaction.

![Google Calendar Appointment Verification](google-calendar-event.png)

*Figure 2. Google Calendar verification of the appointment created during the chatbot booking test.*

**Observed Result:** The corresponding event was successfully created and independently verified in Google Calendar.

---

## Test Results

The workflow was tested using an actual appointment-booking interaction.

| Test Case | Observed Result | Status |
|---|---|---|
| Appointment request | Chatbot processed the user's request | ✅ Observed |
| Appointment suggestions | Three time slots were proposed | ✅ Observed |
| Customer name collection | Assistant received the customer's first name | ✅ Observed |
| Slot selection | Assistant accepted the selected appointment | ✅ Observed |
| Booking confirmation | Confirmation message and calendar link returned | ✅ Observed |
| Google Calendar event creation | Matching event appeared in Google Calendar | ✅ Observed |
| Timezone conversion | Calendar event matched the confirmed appointment time | ✅ Observed |

### Validation Summary

The test successfully demonstrated the integration between the conversational AI workflow and Google Calendar.

The chatbot received an appointment request, guided the user through selecting a time slot, collected the required information, and confirmed the booking.

The corresponding appointment was independently observed in Google Calendar.

**Testing Scope:** Successful appointment creation and timezone consistency were verified. Automated conflict detection and double-booking prevention have not yet been independently validated.

---

## Setup and Configuration

### Requirements

- n8n account or self-hosted instance
- OpenAI API access or supported AI gateway credentials
- Google account with Calendar access
- Configured n8n credentials

### Installation Steps

1. Download the sanitized workflow JSON file from this repository.
2. Open your n8n instance.
3. Import the JSON workflow.
4. Configure the OpenAI Chat Model credentials.
5. Connect your Google Calendar account.
6. Configure the calendar selection and appointment settings.
7. Review the AI Agent system instructions.
8. Publish the workflow.
9. Open the Hosted Chat interface.
10. Test the appointment-booking process and verify the resulting calendar event.

## Security and Privacy

The shared workflow has been sanitized to exclude sensitive account information.

API keys and personal credentials are not included in this repository.

Users must configure their own OpenAI and Google Calendar credentials before running the workflow.

For production deployment, additional security controls, calendar conflict validation, and error handling are recommended.

## Repository Structure

- `README.md` — Project documentation
- `AI_Appointment_Booking_Chatbot_Sanitized.json` — Exported n8n workflow
- `booking-confirmation.png` — Chatbot booking confirmation screenshot
- `google-calendar-event.png` — Google Calendar event verification screenshot

## Skills Demonstrated

- AI Agent Development
- Workflow Automation
- n8n
- OpenAI Integration
- Google Calendar API Integration
- Conversational AI
- Appointment Scheduling Automation
- API Integration
- Workflow Testing and Validation
- Technical Documentation

## Project Objective

This project demonstrates how AI-powered conversational systems can be combined with workflow automation and third-party APIs to support appointment scheduling.

The successful booking test demonstrates a working integration between an AI Agent and Google Calendar event creation.

---

**Author:** Masoumeh Nikbakhtifard

**Project Type:** AI Automation | AI Agents | Workflow Integration

**Technologies:** n8n · OpenAI GPT-5 mini · Google Calendar
