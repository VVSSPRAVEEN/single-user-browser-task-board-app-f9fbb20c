# Browser Task Board

A single-user, offline task board built with plain HTML5, CSS3, and vanilla JavaScript in one self-contained `index.html`. No build step, no backend, no database, no external APIs, no package.json.

## Preview

```bash
python -m http.server 8000
```

Then open http://localhost:8000 in a browser.

Note: verification may run in a sandbox without Docker; the preview instruction above is the literal command required by the contract and does not depend on Docker.

## Limitations

This application is **offline-only**: it runs entirely in the browser with no network access. Tasks are persisted in the browser's `localStorage`, so data is local to the device and browser, and there is no server-side backup.

## Project files

- `index.html` — the complete single-file application (HTML5, CSS3, and ES2020+ vanilla JavaScript).
- `tests/manual_acceptance_checklist.md` — executable manual acceptance checklist.

## Manual acceptance checklist

Run every item in both a 360px viewport (single-column stacking) and a desktop viewport (>= 768px, three columns).

- [ ] Open `http://localhost:8000` via `python -m http.server 8000`
- [ ] Create a task with a title (required, max 80 chars) and description (max 280 chars)
- [ ] Move tasks across To do / In progress / Done columns; verify counts update
- [ ] Delete a task with confirmation
- [ ] Search and filter with AND logic; clear filters
- [ ] Empty state shows when no tasks match
- [ ] Reset demo data to exactly three samples with confirmation
- [ ] Verify responsive stacking at 360px viewport (single column) and three columns on desktop (>=768px)
- [ ] Verify tasks persist after page reload via `localStorage`
- [ ] Verify JSON export and import works
- [ ] Verify tasks have stable IDs across reloads
- [ ] Verify visible focus states on interactive elements
- [ ] Verify status is shown as text labels (To do / In progress / Done)
- [ ] Verify all task actions (Add task, Edit, Delete, Reset demo, Export, Import) are handled entirely by inline client-side DOM event handlers in `index.html`. There is no backend and no HTTP API.
- [ ] Verify the application runs from a single `index.html` with no external dependencies, build step, or package.json.

## Traceability

All BRD acceptance criteria are covered by `tests/manual_acceptance_checklist.md`. The traceability matrix maps each requirement to the `index.html` implementation and the checklist item that verifies it.

| Criterion | Covered by |
|---|---|
| FR1 Task CRUD | Add/Edit modal form submission, title/description validation |
| FR2 Delete with confirmation | Delete action opens confirmation dialog before removal |
| FR3 Status management | Status selector, column movement, live count updates |
| FR4 Search and filter | Search input + status dropdown combined with AND logic; clear filters button |
| FR5 Demo data reset | Reset demo button with confirmation; exactly three samples |
| FR6 Empty state | Empty-state message shown per column when no tasks match |
| FR7 Data export and import | Export button downloads JSON; import modal parses and loads JSON |
| FR8 Storage error handling | try/catch around localStorage read/write; graceful banner warning when storage is unavailable (private browsing, quota exceeded) |
| FR9 Responsive layout | CSS grid: 3 columns desktop, 1 column at 360px |
| FR10 Stable identifiers | `task_` prefixed IDs generated once at creation, preserved across reloads |
| US7 Export metadata | JSON export includes `exported_at` timestamp at the top level |
