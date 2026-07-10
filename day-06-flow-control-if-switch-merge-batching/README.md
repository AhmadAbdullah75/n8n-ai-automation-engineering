# Day 6 – Flow Control: IF, Switch, Merge & Batching

## 🎯 Problem Statement
Real lead-management systems need to route leads by source, escalate urgent cases immediately, and send the rest to external systems in rate-limit-safe batches. This project builds one workflow that ingests 12 simulated leads, routes them by source, escalates high-priority leads out of the normal flow, recombines the rest, and processes them through a batch loop.

## 📖 Overview
Combined n8n's core flow-control nodes — IF, Switch, Merge, Split in Batches — into a single realistic pipeline rather than four disconnected examples.

## 🛠 Technologies & Tools
- n8n

## ⚙ Workflow Explanation
1. Code node generates 12 leads with varied source and priority.
2. Switch routes leads into 3 branches by source (4/4/4).
3. Nested IF on the contact-form branch pulls out the 1 high-priority lead, escalating it out of the flow entirely.
4. Remaining 11 leads are recombined via Merge (Append).
5. Split in Batches processes them in batches of 3 (4 loop iterations) before reaching a "done" path.

## 📂 Project Files
| File | Description |
|---|---|
| `README.md` | This file |
| `Day6.json` | Exported n8n workflow |

## 📚 Key Concepts Learned
- IF for two outcomes, Switch for three or more
- Merge's Append mode simply stacks separate streams together
- Some decisions should remove an item from the flow entirely, not just relabel it
- Split in Batches avoids overwhelming rate-limited APIs

## 📁 Folder Structure
```
day-06-flow-control-if-switch-merge-batching/
├── README.md
├── Day6.json
```

## 📝 Conclusion
Verified correct at every stage by tracing item counts (12 → 4/4/4 → 1/3 → 11 → 4 batches) — a pattern reusable for both call routing and rate-limited API batching later.
