# AI-Powered Customer Support Ticket Triage System

An n8n workflow that receives support requests via a public form, classifies them
using an LLM (Groq / Llama 4 Scout), logs them to Google Sheets, routes internal
Slack notifications by department, and sends the customer a confirmation email —
fully automated end to end.

## Architecture

```
Form Trigger → Validation → AI Classification (Groq) → JSON Parsing →
Confidence Check → Ticket ID Generation → Google Sheets Logging →
Department Routing (Switch) → Slack Notification + Email Confirmation
```

## Features

- Required-field and email-format validation before any AI/API calls run
- LLM-based classification into category, department, priority, sentiment,
  with a confidence score
- Low-confidence tickets (<80%) automatically route to a Manual Review channel
  instead of a department, while still preserving all ticket data
- Sequential-looking unique ticket IDs (`SUP-YYYYMMDD-XXXX`)
- Department-based Slack routing via a Switch node, no hardcoded channel IDs
- Google Sheets logging with 15 structured columns
- Automated customer confirmation emails with priority-based ETA messaging
- Error-output branches on every external integration (Sheets, Slack, Gmail)
  so one failing service doesn't silently break the run

## Known limitations

- Email deliverability verification (checking whether a mailbox actually
  exists, not just its format) was attempted via AbstractAPI but shelved due
  to persistent 401/500 errors on their end unrelated to this workflow's
  configuration. Format validation (regex) is in place; true deliverability
  checking is a documented next step if revisited.
- Currently runs on a local n8n instance (not publicly deployed).

## Setup

1. Import `workflow-export/customer-support-triage.json` into n8n
2. Connect your own credentials: Groq API, Google Sheets OAuth2, Slack API
   (bot token with `chat:write` + `chat:write.public` scopes), Gmail OAuth2
3. Create a Google Sheet with a "Tickets" tab and these headers:
   Ticket ID, Timestamp, Customer Name, Email, Company, Subject, Description,
   Category, Department, Priority, Sentiment, Confidence, Ticket Title,
   Summary, Status
4. Update the Google Sheets node's document ID to point at your sheet
5. Create Slack channels matching the routing map (billing-support,
   technical-support, sales-support, refund-support, manual-review,
   general-support) and give the bot `chat:write.public` scope, or invite it
   to each channel manually
6. Activate the workflow and use the Form Trigger's production URL

## Screenshots

(see `/screenshots`)
