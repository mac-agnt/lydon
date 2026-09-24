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

## Conventions the mockups should keep
- Helios never executes write/external tools; it proposes and waits for a confirmation bound to hashed arguments.
- The action inbox answers three things per item: what happened, why it matters, what I can do.
- Metrics, nav, pages and Helios tools all come from the registry — module contributions are labelled as the module's.
