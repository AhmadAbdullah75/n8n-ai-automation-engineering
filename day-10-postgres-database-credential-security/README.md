# Day 10 – Databases & Credential Security

## 🎯 Problem Statement
Spreadsheet logging doesn't scale, and doesn't separate "what's true right now" from "everything that happened." This project stands up a real Postgres database with a state table and a log table, plus a least-privilege database credential so automation access is structurally limited to only what it needs.

## 📖 Overview
Covered core SQL (SELECT, INSERT, UPDATE, JOIN), connecting Postgres to self-hosted n8n across Docker containers, schema design, and applying least privilege to a real credential.

## 🛠 Technologies & Tools
- Docker
- PostgreSQL 16
- n8n (self-hosted)

## ⚙ Workflow Explanation
1. Postgres run in its own Docker container, on a shared network with n8n.
2. Two linked tables designed: `packages` (state — current status, updated in place) and `tracking_events` (log — one row per event, foreign-keyed to `packages`).
3. n8n workflow: Manual Trigger → Set (tracking number) → Postgres Insert (create package) → Postgres Insert (log "received") → Postgres Update (advance status) → Postgres Insert (log "left_warehouse").
4. A least-privilege Postgres user was created and n8n's credential switched to it, verified by confirming it could not run `DROP TABLE`.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Day10.json` | Exported n8n workflow |

## 📚 Key Concepts Learned
- State tables are updated in place; log tables are append-only
- Primary keys should be auto-generated, never manually assigned (fixed a real duplicate-key bug caused by hardcoding `id`)
- Foreign keys are what make JOIN meaningful between two tables
- Docker containers reach each other by container name on a shared network, never `localhost`
- Least privilege is enforced by the database itself, not by careful usage

## 📁 Folder Structure
```
day-10-postgres-database-credential-security/
├── README.md
├── Day10.json
```

## 📝 Conclusion
Closed out the Foundation phase with a real, self-hosted database backend, a correctly designed state/log schema, and a verified least-privilege credential.
