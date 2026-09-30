# Project notes

## Source of truth
Pulse is an attached local codebase folder (`Pulse/`), not a GitHub repo. Browse with the
`local_*` tools (`local_ls`, `local_read`, `local_grep`). Key docs:

- `Pulse/docs/ARCHITECTURE.md` — layers, record spine, module contract, permissions, Helios chain
- `Pulse/docs/HELIOS.md` — tools, effects (read/write/external), confirmation hashes, channels
- `Pulse/packages/core/src/domain/core-module.ts` — core routes + navigation (sections: primary, work, data, admin)
- `Pulse/apps/demo/pulse.config.ts` — client config: branding, terminology, modules, home widgets, features
- `Pulse/packages/modules/site-visits` — the reusable module fixture

## Mockup files
- `Pulse v4 Glass.dc.html` — current direction: dark liquid glass, lime accent, icon rail with
  hover labels, Home = Helios chat + right rail, plus the real page set (inbox, work queues,
  approvals, directories, universal record page, insights, automations, system health, modules,
  notifications, settings).
- `Pulse v2.dc.html`, `Pulse v3 Apple.dc.html`, `Pulse v3 Console.dc.html`, `Pulse Home.dc.html` — earlier directions, keep.

## Running the demo
- `python3 serve.py` (or double-click `Start Demo.command`) serves `Pulse v4 Glass.dc.html` at
  http://pulse.localhost:8080, plus only the files it needs. The preview pane's launcher can't read
  ~/Downloads (macOS privacy), so start the server from the shell and attach the pane via `.claude/launch.json`.
- `vendor/` holds React 18.3.1 and the fonts so the demo runs offline; the page loads them before `support.js`.
- Upcoming dates in the mockup data are computed from today (helpers at the top of the logic script).
- `DEMO-SCRIPT.md` lists the questions Helios has real answers for.

## Lydon build
- `Pulse v4 Glass.dc.html` is configured for Lydon (builder-developer, 7 developments). All Lydon figures live in
  one data layer near the top of the logic script (`LY_DEVS`, `LY_STORY`, `LY_FACILITIES`, `LY_CF`, ...). Totals
  are computed from rows; story numbers are defined once in `LY_STORY`. Change data there, never in page copy.
- Module pages (Home, Group, Developments, Programme, Costs, Procurement, Finance, Sales, Compliance, Records) are
  built by `lyBuildPage` as lists of blocks and rendered by the single `<sc-if isModule>` template. Drill-downs
  open `lyDrawer(key)` side panels (`story:priory`, `unit:PF-1-084`, `inv:INV-88341`, `cost:coach:CON-210`, ...).
- Work, Agents, Activity, Records → Files and Settings keep their original templates with Lydon data.
- Homes: `LY_REG` (240, deterministic, reconciles to the closings plan `LY_CLOSE`), `lyUnit(id)`, and
  `lyUnitView(u)` for status, blockers, owner and next step (cached per `LYDB.rev`). Units grids use `lyUnitGrid`.
- Session store `LYDB` (documents, incoming files, packs, signatures, meeting actions, drafts, invoices, change log).
  Every write goes through an `ly*` store function that calls `lyLog`, which bumps the revision and re-derives
  compliance (`lyDocState`, `LY_BLOCKED`, `lyRefreshCompliance`). Pages call it through `ui.act(fn, toast)`.
  `lyResetDb()` puts the sample data back.
- Custom blocks and drawer sections are React components in `LYC` (plain `createElement`), mounted through
  `x-import` via `LYB.custom(kind, props)` and `sec.custom(kind, props, title)`. Unit, pack, meeting, source and
  Helios drawers live in `lyDrawerX`.
- Cash: sale receipts are gross; `LY_RELEASE` (62%) and `LY_VAT` move with the closing. The Priory Fields delay is
  `LY_STORY.priory.deferred` (€1.74m gross) and `.net` (the November closing-cash effect, about €0.66m).
- Systems: `LY_SYS` / `LY_SYS_ORDER`, all simulated with sample records; Team Talk is To confirm. Source labels open
  `src:<system>:<ref>`. Never present a connection as live or link out to a real record.
- Helios on Home: `lyHelios(q, ui)` answers from the live records before the static `ANSWERS`. Writes return
  `confirm` plus `confirmRun`; only `heliosConfirm` runs them, once, and they stay inside the demo.
- Development cards show `vendor/lydon/<dev id>.jpg`, the featured image from each project page on lydon.ie/projects
  (resized to 1200px). Names and places in `LY_DEVS` match that page's "In Construction" list.
- Records → Ontology is one 3D brain (think Ultron/Jarvis): `ontoLayout` puts every record in a brain shape, kinds as
  regions (homes over the cortex by development, each document beside its home, money kinds at the front, people and
  meetings at the sides, drawings and milestones at the back, systems down the stem, developments at the core). WebGL
  draws small points, the real relationships as filaments (`near` doc-home, `far` the rest) and sparks firing along
  them, from buffers filled once (`ontoGlData`). The 2D layer draws callouts, corner readouts, hover arcs, routes
  and the selection. No blue hologram and no spinning rings (the user asked for both to go): kinds are multicolour,
  approved documents are warm gold tissue, the panel is neutral black. Frame cost is about 0.6 ms CPU; keep it
  there, low-end machines matter. Shared shader uniforms must match precision or the link fails and `drawFlat` shows.
- Downloads are generated in the browser: `lyPdfDoc` (PDF), `lyZip` (ZIP), `lyDownload`.
- Tables never scroll sideways. `lyNorm` fits each table to its block: columns give way in order (`pr`, higher goes first;
  default long text, then plain numbers left to right) and their values move onto a second line under the lead cell
  (`lead`, default column 0). Set `pr` on wide tables so the important columns stay. `rowSpan` lets a tall card sit
  beside two short ones; cards in a row share one height.
- Single-choice switchers (chips, dev record tabs, drawer tabs, saved views, report month) are one sliding control:
  `lySegModel` (template blocks) or `LySeg` (React). Give options a `short` label for narrow screens. Several-at-once
  toggles use `LYB.chips(..., {multi:true})`.
- Records opens on the Ontology (first tab). `buildOntologyGraph()` makes one node per real record (homes, open documents,
  invoices, POs, budget lines, drawings, meetings, people, systems...) and one link per real relationship (how it is drawn
  is the brain note above). It rebuilds when `LYDB.rev` changes. Nodes carry `ref` (a drawer key, `{dev}` or `{go}`),
  so hover names a record, click selects it and Open record opens the real drawer. Keep links real: decoration edges are kind "d".
- Visual kit (`LYC.*`, styles `.lyv-*`): triage board `issueBoard`, day strip `dueStrip`, site `dossiers`, `phaseTimeline`,
  `stackBars`, `riskMatrix` / `riskList`, milestone `slipChart`, `stackCols`, `heatTable`, `funnel`, `meters`, maturity
  `ladder`, supplier `bubbles`, board pack `packDoc` / `packSide`, `briefing`, `delayCard`. Mount with `LYB.custom(kind, props)`.
  Every `.lyv` root is an inline-size container, so a block reflows to its card (container queries), not the window.
  Chart colour per site is `LY_DEV_TINT` (categorical, always with a legend, never a status). Page data they need:
  `lyIssueText` (what happened / why it matters per attention issue), `LY_RISKS` (likelihood x impact, severity from the
  score), `LY_BOARD` (meeting, reviewers, pages), `lyPhaseWindows`, `lyBcarHeat` (not-approved documents by provider).
  Dates relative to the story's today go through `LY_ASOF` (`lyWorkdays`, `lyRel`, `lyParseDM`), never the real clock.
  Pages built on it: Home Today and Attention, Group Portfolio and Board Pack, Developments Sites, Phases and Risks,
  Programme Milestones, Delays and Forecast, Procurement Suppliers, Finance Funding and Financing, Compliance BCAR.
- The header is one row: `lyNavFit` / `LY_TAB_SHORT` shorten long tab labels, then the bar icons step aside, then
  the tab row scrolls (phones). Check new tabs at 1024px with the rail open.

## Conventions the mockups should keep
- Helios never executes write/external tools; it proposes and waits for a confirmation bound to hashed arguments.
- The action inbox answers three things per item: what happened, why it matters, what I can do.
- Metrics, nav, pages and Helios tools all come from the registry — module contributions are labelled as the module's.
