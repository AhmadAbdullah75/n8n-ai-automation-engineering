# Day 5 – Webhooks & HMAC Signature Verification

## 🎯 Problem Statement
Any webhook URL, once discovered, can be sent fake data by anyone pretending to be a trusted service. This project implements HMAC signature verification — proving a webhook request genuinely came from a trusted sender before its data is trusted — using the same underlying mechanism real services like Twilio use to sign their webhook calls.

## 📖 Overview
Built two connected workflows: a receiver that verifies incoming signatures before responding, and a sender that signs outgoing requests — simulating a real external service notifying an automation of an event.

## 🛠 Technologies & Tools
- n8n
- HMAC (SHA256)

## ⚙ Workflow Explanation
**Receiver:** Webhook node (Raw Body enabled) → Crypto node recomputes the HMAC signature → IF node compares it to the incoming `x-signature` header → Respond to Webhook returns 200 (verified) or 401 (invalid).
**Sender:** Manual Trigger → Edit Fields builds the exact payload string → Crypto node signs it → HTTP Request sends the payload and signature header to the receiver.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Webhook Receiver - Day 5.json` | Exported receiver workflow |
| `Webhook Sender- Day 5.json` | Exported sender workflow |

## 📚 Key Concepts Learned
- HMAC verification requires the exact original bytes — any reformatting breaks it
- n8n auto-parses JSON bodies even with Raw Body enabled if `Content-Type: application/json` is used; sending as `text/plain` preserved the raw string
- "Respond to Webhook" mode is required when the response depends on logic evaluated mid-workflow

## 🚧 Notes
Resolved a real signature-mismatch bug caused by JSON auto-parsing, and an intermittent "webhook not registered" error caused by the test listener expiring between setup and execution.

## 📁 Folder Structure
```
day-05-webhooks-hmac-security/
├── README.md
├── Webhook Receiver - Day 5.json
├── Webhook Sender- Day 5.json
```

## 📝 Conclusion
Delivered a working, security-verified webhook exchange between two independent workflows — directly applicable to securing a real Twilio voice-agent integration.
