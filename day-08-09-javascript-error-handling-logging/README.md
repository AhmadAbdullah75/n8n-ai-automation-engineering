# Day 8+9 – JavaScript for Automation & Error Handling, Logging, Monitoring

## 🎯 Problem Statement
Built-in nodes can't express every transformation, and a workflow with no error handling can fail silently in production. This project solves both: a Code-node pipeline that chains two dependent API calls with hand-written retry logic, plus a dedicated Error Trigger workflow that automatically catches and logs failures — with every outcome, success or failure, permanently recorded to Google Sheets.

## 📖 Overview
Combined two days into one build: custom JavaScript inside n8n's Code node (destructuring, find, reduce, async/await), and a full reliability layer (Error Trigger workflow, manual retry-with-backoff, Google Sheets logging) applied to a real weather-lookup pipeline.

## 🛠 Technologies & Tools
- n8n
- Google Cloud Console (OAuth2)
- Google Sheets API
- OpenWeatherMap Geocoding + Weather APIs

## ⚙ Workflow Explanation
**Main pipeline (`Day 8+9.json`):**
1. Code node generates a list of test cities, one deliberately invalid.
2. Code node chains a geocoding call into a weather call using async/await, with a hand-written exponential-backoff retry function.
3. Successful results are appended to a Google Sheets "Success" tab.
4. The invalid city throws an error, stopping the whole execution — intentionally, to trigger the error handler.

**Error handler (`Error Handler:Day 8+9.json`):**
1. Error Trigger node, set as the main workflow's designated Error Workflow.
2. Automatically fires when the main workflow fails, logging the failure to a Google Sheets "Errors" tab.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Day 8+9.json` | Exported main pipeline workflow |
| `Error Handler:Day 8+9.json` | Exported error handler workflow |

## 📚 Key Concepts Learned
- Destructuring, `find` vs. `reduce`, and async/await for chained dependent API calls
- Code nodes lose built-in "Retry On Fail" — retries must be hand-written
- Error Trigger workflows only fire for production-triggered executions, not manual runs (confirmed via n8n's own docs)
- Continue On Fail (per-item) vs. Error Trigger (whole-workflow) solve different problems

## 🚧 Notes
Resolved a Google Drive API permission error (separate from the Sheets API), a header-row misplacement issue in the sheet, and confirmed the Error Trigger's manual-execution limitation directly against n8n's documentation.

## 📁 Folder Structure
```
day-08-09-javascript-error-handling-logging/
├── README.md
├── Day 8+9.json
├── Error Handler:Day 8+9.json
```

## 📝 Conclusion
Delivered a working reliability layer — automatic error notification, hand-written retry logic, and permanent success/failure logging — combined with the JavaScript patterns needed to build it.
