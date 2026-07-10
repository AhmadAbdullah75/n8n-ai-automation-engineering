# Day 3 – API Authentication & OAuth2

## 🎯 Problem Statement
Choosing the wrong authentication method — or implementing it insecurely — is a common source of both bugs and real security risk in automation. This project implements and compares two real mechanisms, API Key and OAuth2, against two live APIs, so the difference is understood through direct experience rather than definitions alone.

## 📖 Overview
Covered API Key, Basic Auth, Bearer Token, and OAuth2, then implemented working API-key and OAuth2 (Client Credentials) integrations, including a real authentication failure diagnosed and resolved.

## 🛠 Technologies & Tools
- Postman
- n8n
- OpenWeatherMap (API Key)
- Spotify Web API (OAuth2 Client Credentials)

## ⚙ Workflow Explanation
1. HTTP Request node calls OpenWeatherMap with the API key as a query parameter — initially failed with a 401 due to a newly generated key not yet being active.
2. n8n OAuth2 credential configured with Spotify's token URL and Client Credentials grant.
3. HTTP Request node uses this credential directly to call Spotify's API, with n8n handling the token exchange automatically.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Day3.json` | Exported n8n workflow |

## 📚 Key Concepts Learned
- API Key vs. Basic Auth vs. Bearer Token vs. OAuth2
- OAuth2 Client Credentials vs. Authorization Code flow
- JWTs and why servers can verify them without a database lookup
- Exponential backoff for rate-limited APIs

## 📁 Folder Structure
```
day-03-api-authentication-oauth2/
├── README.md
├── Day3.json
```

## 📝 Conclusion
Moved from simple key-based auth to a fully working OAuth2 integration, including resolving a real authentication failure — direct preparation for later OAuth2 work with Google Sheets and YouTube.
