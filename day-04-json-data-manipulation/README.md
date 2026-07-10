# Day 4 – JSON & Data Manipulation

## 🎯 Problem Statement
Real API responses arrive as deeply nested, messy data that has to be reshaped, filtered, merged, and de-duplicated before it's usable. This project solves that with a workflow that traverses real nested API data, filters it by a nested field, then merges two overlapping data sources and removes duplicate records — a reusable pattern for the most common task in automation.

## 📖 Overview
Built fluency with JSON traversal, n8n expressions, and the four core array transformations: map, filter, merge, deduplicate.

## 🛠 Technologies & Tools
- n8n
- JSONPlaceholder

## ⚙ Workflow Explanation
1. HTTP Request fetches 10 nested user records.
2. Edit Fields extracts nested fields (`address.city`, `address.geo.lat`) using dot-notation.
3. Filter keeps only users whose company name contains "Group" (10 → 2 items).
4. Two Code nodes generate overlapping fake lead lists; Merge (Append) combines them; Remove Duplicates (by email) collapses the overlap (5 → 4 items).

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Day4.json` | Exported n8n workflow |

## 📚 Key Concepts Learned
- Reading nested JSON as relationships, not memorized paths
- Map changes shape, filter changes count, merge combines sources, deduplicate compares items to each other
- Flattening nested data for spreadsheet/database use
- Binary data travels separately from JSON data in n8n

## 📁 Folder Structure
```
day-04-json-data-manipulation/
├── README.md
├── Day4.json
```

## 📝 Conclusion
Built hands-on fluency with the data-cleaning operations underlying almost every automation: traversal, filtering, merging, and deduplication.
