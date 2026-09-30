# Lydon demo script

## Start and stop

1. Double-click **Start Demo.command**. Chrome opens at **http://pulse.localhost:8080**.
2. Close that Terminal window when you're done. That stops the demo.

If another demo is already using port 8080, run `python3 serve.py 8092` from this folder and open http://pulse.localhost:8092 instead.
No internet needed; React and the fonts are bundled in `vendor/`.

Everything is sample data. The **DEMO · SAMPLE DATA** pill in the header opens what is simulated, the changes made in
this session, and **Reset sample data** (reloading the page does the same). No email, signature request, accounting
change or BCMS submission leaves the demo.

## The 30-second moment

Home → **Attention** panel → click **Priory Fields · 4 closings delayed**. The side panel shows what happened, why,
and what changed: November sales receipts −€1.74m gross, January +€1.74m, and November closing cash €0.66m lower,
because 62% of those receipts would have gone straight to the lender. Then the draw timing, the four homes, the root
causes and the recommended actions. **Create Tasks** puts four owned tasks in Work.

## Five journeys

| # | Path | What it proves |
|---|---|---|
| 1 | Developments → Units → **Blocked** view → PF-1-084 → Compliance tab → **Review match** on the AirSeal file → **Accept suggestion** → **Open the requirement** → **Approve** | A received document is not approved until a person reviews it. The checklist moves to 39 of 40; the home stays blocked by the electrical certificate |
| 2 | Compliance → Packs → GG-1-041 → Signatures → **Simulate signature completion** → Pack → **Mark ready for certifier** → **Download pack (ZIP)** → **Record handover** → **Record BCMS submission (simulated)** → **Record confirmation** | Ready is blocked while signatures are open; the ZIP has a cover sheet, manifest and sample documents; confirmation leaves other closing blockers alone |
| 3 | Work → Meetings → **Confirm** the first suggested action → Work → Tasks, then PF-1-084 → Emails & meetings | A suggested action becomes work only once a person confirms owner and date, and then shows up in Work and on the home |
| 4 | Procurement → Invoices → INV-88341 → **Approve in Lightyear** → Counted once tab | Lightyear holds the approval, AccountsIQ the posting; committed, invoiced and paid stay separate and the invoice counts once |
| 5 | Finance → Overview, then **Monthly Report** (September, Group view) | The same delay in the cash chart, the brief and the report: €1.74m gross, €661,200 at closing, €207,060 VAT later |

## Suggested walkthrough (10 to 20 minutes)

| Step | Where | What it shows |
|---|---|---|
| 1 | Home → Today | Group cash €14.8m, 146 closings in 90 days, 8 issues, the briefing, decisions, and the chain from one delay to the directors |
| 2 | Group → Overview → Priory Fields card | The development record: budget, spend vs build, phases, homes, drawings |
| 3 | Record → Costs → CON-210 → an invoice | Group → site → cost code → invoice drill-down |
| 4 | Developments → Units | 240 homes: filters, saved views, sticky IDs, sale value separate from Lydon's receipt at closing |
| 5 | Group → Cash Flow | 24 months, switch sites off, November sits €0.66m under last week's forecast |
| 6 | Costs → Variances → Coach Ashbourne → **Explain this cost variance** | €610k, 68% groundworks and concrete, the invoices behind it, what is not yet approved |
| 7 | Finance → Development Funding | Priory Fields facility €48.0m, drawn €31.2m, €3.8m draw waiting on the QS |
| 8 | Compliance → Overview and Blockers | 194 homes in scope, 6 blocked by 17 critical documents, who owes what |
| 9 | Procurement → Overview | INV-88341 from Lightyear capture to AccountsIQ posting; the exceptions the agent held |
| 10 | Group → Board Pack → Generate | Ten sections drafted from the same numbers, from the Word template |
| 11 | Settings → Systems | Thirteen systems shown with sample records, all simulated; Team Talk marked To confirm |

Any source label (for example **Excel · Priory Fields budget v7 · simulated**) opens the record, its field mapping and
activity. **Check for updates (simulated)** and **Simulate a failed check** show the loading and failed states.

## Views worth a moment

| Where | What to point at |
|---|---|
| Home → Attention | Pick any issue: what happened, why it matters and what you can do, then when each falls due |
| Home → Today | The week ahead: deadlines, milestones, closings, board pack reviews and routines, day by day |
| Developments → Sites | Each site's photo, its programme clock (built against time gone) and its next milestone |
| Developments → Phases | Every phase on one timeline, filled to its build progress, with today marked |
| Developments → Risks | The likelihood and impact matrix; the numbers match the register below it |
| Programme → Milestones | Original date (ring) against forecast (dot); Priory Fields' three +21 day milestones in a row |
| Procurement → Suppliers | Approval time against price variance; Tolka and Clearline sit in the slow and over-price corner |
| Finance → Funding | Headroom per facility and the draw calendar, with the Priory Fields draw pulled forward to 4 Oct |
| Compliance → BCAR | Who owes what: documents not yet approved, by provider and development (768 in all) |
| Group → Board Pack | The pack as a document before and after **Generate**, with reviewers and what changed since August |

## The ontology

Records opens on the **Ontology**: every record the demo holds and how they connect. Hover names a record, click one to see
what it touches and open it. Try **PF-1-084**, **INV-88341**, **Chadwicks**, or **invoices homes** (a real route between two kinds).

## Questions Helios answers

Type these on Home, or click a suggestion. Answers are built from the same records the pages read, so a change made a
minute ago shows up. Helios explains figures; it does not compute its own.

| Ask | Helios shows |
|---|---|
| Why did Priory Fields closings move? | The four homes, causes, gross and net cash effect |
| What is our cash position? | 30-day in and out, November change net of the lender release |
| Which units are blocked from BCAR? | The blocked homes, documents and who owes them, from the live register |
| PF-1-084 | Status, dates, what is holding it, next step and owner |
| Explain the delay on PF-1-084 | Planned against forecast, causes, the records behind it |
| What is missing for PF-1-084? | Required documents not yet approved, and anything waiting to be matched |
| What changed on PF-1-084? | The last seven days of changes, with sources |
| Find the meeting where PF-1-084 was agreed | The meeting, the transcript line and the decision |
| Where did we agree to bring the draw forward? | The September finance review, decision D2 |
| Show me the monthly report | September figures and the delayed receipts, gross and net |
| Was INV-88341 counted once? | Lightyear status, AccountsIQ posting, committed, invoiced and paid |
| Which packs are in progress? | Packs by stage and what each one is waiting for |
| What is Coach Ashbourne's cost variance? | Drivers by cost code, invoices, what is missing |
| Draft a document request for PF-1-084 | A write proposal. **Approve** saves a simulated Outlook draft on the home; nothing is sent |
| Chase the Tipperstown certificates | One draft per provider, waiting for your yes |

Anything else gets the fallback with buttons for the common questions.

## Watch out for

- **Header on smaller screens:** long tab labels shorten (Development Funding shows as Funding) and on phones the tab row scrolls sideways.
- **Downloads** (completion pack ZIP, monthly report PDF) are generated in the browser from sample documents.
- **Dates are fixed** to the September 2026 story (today is Wednesday 30 September; draw on 18 Oct; closings moving from November to January).
- **Demo data:** unit counts, budgets, lenders, suppliers' figures and consultant firm names are illustrative. The programme and sales workbooks are examples until their sources are confirmed. Confirm locations for Briscoe Gardens and Golding Green before a live showing.
