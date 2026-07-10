# Day 1 – Automation & Systems Thinking

## 🎯 Problem Statement
Businesses often lose track of incomplete or invalid form submissions because there's no automatic check before a lead reaches the sales team. This project builds a workflow that validates an incoming submission, transforms valid ones into a routable message, decides how to handle them, and logs the outcome — giving anyone who implements it a reliable first line of defense against bad data reaching a real process.

## 📖 Overview
First day of the training track: built the mental model behind automation (trigger → validate → transform → decide → act → log) and applied it in a real n8n workflow.

## 🛠 Technologies & Tools
- n8n

## ⚙ Workflow Explanation
1. Manual Trigger simulates an incoming form submission.
2. Edit Fields node creates test data (name, email, source).
3. IF node validates the email field — invalid data is routed straight to a rejection log.
4. Valid data is transformed into a message, passed through a second IF for routing.
5. Placeholder nodes represent the final action (Slack alert) and logging step.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Day 1.json` | Exported n8n workflow |
```

## 📚 Key Concepts Learned
- Trigger models: manual, webhook, schedule, polling
- The six-stage workflow anatomy
- Idempotency and why duplicate-safe automation matters
- Synchronous vs. asynchronous processing

## 📁 Folder Structure
```
day-01-automation-systems-thinking/
├── README.md
├── Day 1.json
```

## 📝 Conclusion
Established the six-stage pattern used throughout the rest of this training track, applied in a working, branching n8n workflow.
