# AI-Powered Support Ticket Triage

An event-driven AI workflow that automatically classifies customer support
tickets by priority, product area, and ticket type.

> **Portfolio Reproduction**
>
> This repository is an independently recreated implementation inspired by
> an AI-powered support-ticket workflow I worked with professionally.
> It contains no proprietary company code, customer data, credentials,
> or internal configuration.

---

## Overview

Customer support teams receive large numbers of tickets containing
unstructured descriptions of bugs, feature requests, and product issues.

Manually reviewing each ticket to determine its priority, affected product
area, and request type introduces repetitive work and can lead to inconsistent
classification.

This project demonstrates how an AI model can be integrated into an
event-driven workflow to transform an unstructured support ticket into
structured information that can be used for downstream routing and analysis.

### The workflow

Support Ticket
↓
Webhook
↓
AI Priority Classification
↓
AI Product Area Classification
↓
AI Ticket Type Classification
↓
JavaScript Normalization
↓
Structured Result
↓
Slack Notification

---

## Problem

For every incoming support ticket, a support engineer may need to determine:

### Priority

- Critical
- Urgent
- Normal

### Product Area

- Controls
- Workflows
- Routing
- Billing & Subscription
- Data Binding
- Actions
- Preview
- Connectors
- Data Queries
- Builder
- Embed
- Navigation
- Publish

### Ticket Type

- Bug
- Enhancement
- Other

The goal of this workflow is to automate this initial classification step.

---

## Architecture

The workflow uses an event-driven architecture.

A support ticket is sent to a webhook endpoint containing information such
as the ticket ID, subject, description, and requester.

The workflow then performs three independent AI classification tasks:

1. Priority classification
2. Product-area classification
3. Ticket-type classification

The outputs are normalized using JavaScript and combined with the original
ticket metadata into a structured result.

The structured result can then be sent to downstream systems such as Slack.

See:

- [Architecture](docs/architecture.md)
- [Design Decisions](docs/design-decisions.md)
- [AI Prompts](docs/ai-prompts.md)

---

## Example

### Input

```json
{
  "ticket_id": "DEMO-1814",
  "subject": "File Upload",
  "description": "Image upload works in Preview but not on Web.",
  "requester": "demo@example.com"
}
