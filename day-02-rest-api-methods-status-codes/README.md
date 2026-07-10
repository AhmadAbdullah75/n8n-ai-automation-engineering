# Day 2 – REST API Methods & Status Codes

## 🎯 Problem Statement
Automations that treat every API error identically end up retrying things they shouldn't, or failing silently on things they should retry. This project builds a small diagnostic workflow that deliberately triggers every major HTTP status category (success, client error, server error, rate limit) so correct, differentiated error handling becomes second nature before it's needed for real integrations.

## 📖 Overview
Practiced HTTP methods and status codes first in Postman, then rebuilt the same tests directly inside n8n's HTTP Request node.

## 🛠 Technologies & Tools
- Postman
- n8n
- JSONPlaceholder, httpbin.org

## ⚙ Workflow Explanation
1. Manual Trigger fans out into five branches.
2. Each branch makes a GET or POST request designed to return a specific status code: 200, 404, 201, 500, and 429.
3. Running all five together allows direct comparison of each response.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Day2.json` | Exported n8n workflow |

## 📚 Key Concepts Learned
- HTTP methods: GET, POST, PUT, PATCH, DELETE
- 2xx / 4xx / 5xx categories require different handling
- 429 specifically means "slow down," not "retry immediately"

## 📁 Folder Structure
```
day-02-rest-api-methods-status-codes/
├── README.md
├── Day2.json
```

## 📝 Conclusion
Built practical fluency reading and reacting correctly to HTTP status codes — the foundation every later integration depends on.
