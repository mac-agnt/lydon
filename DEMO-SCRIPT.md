# Lydon demo script

## Start and stop

1. Double-click **Start Demo.command**. Chrome opens at **http://pulse.localhost:8080**.
2. Close that Terminal window when you're done. That stops the demo.

If another demo is already using port 8080, run `python3 serve.py 8092` from this folder and open http://pulse.localhost:8092 instead.
No internet needed; React and the fonts are bundled in `vendor/`.

## The 30-second moment

Home → **Attention** panel → click **Priory Fields · 4 closings delayed**. The side panel shows what happened,
why, what changed (November revenue −€1.74m, January +€1.74m, November cash revised down, draw timing),
the four units, the three root causes and the recommended actions. **Create Tasks** puts four owned tasks in Work.

## Suggested walkthrough (10 to 20 minutes)

| Step | Where | What it shows |
|---|---|---|
| 1 | Home → Today | Group cash €14.8m, 146 closings, 8 issues, the briefing, decisions, and the chain from one delay to the directors |
| 2 | Group → Overview → Priory Fields card | The development record: budget, spend vs build, phases, the same chain |
| 3 | Record → Costs → CON-210 → an invoice | Group → site → cost code → invoice drill-down |
| 4 | Record → Sales → PF-1-084 → missing document | Unit → closing → BCAR blocker → the missing electrical certificate |
| 5 | Group → Cash Flow | 24 months, switch sites off, November sits €1.74m under last week's forecast |
| 6 | Costs → Variances | Coach Ashbourne +€610k, 68% groundworks and concrete, margin effect |
| 7 | Finance → Development Funding | Priory Fields facility €48.0m, drawn €31.2m, €3.8m draw waiting on the QS |
| 8 | Compliance → Blockers | 6 units, 17 critical documents, who owes what |
| 9 | Procurement → Overview | INV-88341 from AccountsIQ to MAT-240 in one chain; the exceptions the agent held |
| 10 | Group → Board Pack → Generate | Ten sections drafted from the same numbers |
| 11 | Settings → Systems | AccountsIQ, Wrike and SharePoint connected; Pulse sits above them |

## Questions Helios answers

Type these on Home (Today → Ask Helios), or click a suggestion. Helios listens for the key words.

| Ask | Helios shows | Key words it listens for |
|---|---|---|
| Why did Priory Fields closings move? | The four units, causes and the knock-on to cash and funding | priory, closings, delay, deferred, sales |
| What is our cash position? | 30-day in/out and the November change | cash, position |
| What is Coach Ashbourne's cost variance? | €610k and its drivers, margin effect | coach, ashbourne, variance, concrete, cost |
| Which units are blocked from BCAR? | 6 units, 17 documents, who owes them | bcar, compliance, certificates, blocked |
| Which draws are waiting? | Facilities, next draws and conditions | draw, funding, facility, lender |
| Tell me about INV-88341 | Classification, budget before and after | invoice, Chadwicks, procurement |
| Draft the escalation for PF-1-084 | A write tool: drafts it and waits for your yes | draft, escalate, chase, send |

Anything else gets the fallback with buttons for the questions above.

## Watch out for

- **Escalation drafts:** stop at the **NEEDS YOUR YES** card; that is the point. Clicking **Confirm and send** drafts it again.
- **Dates are fixed** to the September 2026 story (draw on 18 Oct, closings moving from November to January).
- **Demo data:** unit counts, budgets, lenders, suppliers' figures and consultant firm names are illustrative. Confirm locations for Briscoe Gardens and Golding Green before a live showing.
