# Day 1 – Automation & Systems Thinking

## 🎯 Problem Statement
Businesses often lose track of incomplete or invalid form submissions because there is no automated validation before leads reach downstream systems. This project demonstrates how to validate incoming data, transform it into a structured format, route it based on business logic, and record the outcome to prevent invalid data from entering production workflows.

---

## 📖 Project Overview
This project introduces the core principles of workflow automation by implementing a complete automation pipeline in n8n.

The workflow follows the standard automation lifecycle:

**Trigger → Validate → Transform → Decide → Act → Log**

Using a simulated form submission, the workflow validates user input, routes data based on conditions, and records the result.

---

## 🛠 Technologies Used

- n8n

---

## 🏗 Workflow Architecture

```
Manual Trigger
      │
      ▼
Edit Fields (Sample Form Data)
      │
      ▼
Validate Email (IF)
   ┌───────┴────────┐
Invalid             Valid
   │                  │
   ▼                  ▼
Reject Log      Transform Message
                     │
                     ▼
              Route Decision (IF)
               ┌────────┴────────┐
               ▼                 ▼
        Placeholder Action   Placeholder Action
               │                 │
               └────────┬────────┘
                        ▼
                    Final Logging
```

---

## ⚙ Workflow Explanation

### 1. Manual Trigger
Simulates an incoming form submission to test the workflow.

### 2. Edit Fields
Creates sample data including:
- Name
- Email
- Source

### 3. Email Validation
Checks whether the submitted email is valid.

- Invalid submissions are sent directly to the rejection path.
- Valid submissions continue through the workflow.

### 4. Data Transformation
Formats the validated submission into a structured message suitable for downstream systems.

### 5. Routing Decision
Applies business rules to determine where the validated data should be sent.

### 6. Action & Logging
Placeholder nodes simulate sending notifications (e.g., Slack) and recording workflow outcomes for auditing.

---

## 📂 Project Files

| File | Description |
|------|-------------|
| `README.md` | Project documentation |
| `Day 1.json` | Exported n8n workflow |

---

## 📚 Key Concepts Learned

- Automation workflow lifecycle
- Trigger models
  - Manual Trigger
  - Webhook Trigger
  - Schedule Trigger
  - Polling Trigger
- Data validation
- Conditional branching using IF nodes
- Data transformation
- Workflow routing
- Logging and audit trails
- Idempotency (duplicate-safe automation)
- Synchronous vs. asynchronous processing

---

## 📁 Folder Structure

```
day-01-automation-systems-thinking/
│
├── README.md
└── Day 1.json
```

---

## 🚀 Outcome

Successfully built a foundational automation workflow that demonstrates:

- Simulating incoming data
- Validating user input
- Branching based on business rules
- Transforming data for downstream systems
- Logging workflow outcomes

This six-stage workflow pattern serves as the foundation for more advanced automation projects throughout the training journey.
