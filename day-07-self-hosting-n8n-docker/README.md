# Day 7 – Self-Hosting n8n with Docker

## 🎯 Problem Statement
Relying on a cloud platform's free trial isn't a sustainable base for a cost-conscious automation practice. This project self-hosts n8n via Docker with persistent storage, and proves a workflow built on the cloud instance can be exported and imported with zero loss of functionality.

## 📖 Overview
Covered Docker containers, environment variables, persistent volumes, and workflow export/import portability.

## 🛠 Technologies & Tools
- Docker Desktop
- WSL2
- n8n (self-hosted)

## ⚙ Workflow Explanation
1. Docker Desktop installed with WSL2 backend (resolved a startup failure with a system restart).
2. Named volume created for persistent n8n data.
3. n8n launched as a container with timezone and security-related environment variables.
4. n8n auto-generated its own encryption key and local owner account on first run.
5. Day 6's workflow exported from Cloud and successfully imported into the self-hosted instance.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |

## 📚 Key Concepts Learned
- Containers guarantee identical behavior regardless of machine
- Environment variables configure behavior externally, without code changes
- Volumes are required for data to survive container restarts
- A workflow is portable because it's just structured JSON

## 📁 Folder Structure
```
day-07-self-hosting-n8n-docker/
├── README.md
```

## 📝 Conclusion
Replaced a paid cloud dependency with a fully self-hosted, cost-free n8n environment, with verified data persistence and cross-environment workflow portability.
