# Acceptance Checklist

This document maps each functional requirement (FR1–FR10) to a manual browser test. Run the app with:

```bash
python -m http.server 8000
```

Then open http://localhost:8000 in a modern browser.

## FR1: Task creation and editing

- [ ] Click **Add task**. A form with **Title** and **Description** fields appears.
- [ ] Submit with an empty title. Verify an inline error says the title is required and no task is created.
- [ ] Enter a title longer than 80 characters. Verify validation rejects it.
- [ ] Enter a description longer than 280 characters. Verify validation rejects it.
- [ ] Create a task with a valid title and description. Verify it appears in the **To do** column.
- [ ] Edit the task. Verify the saved changes appear and validation still applies.

## FR2: Task status management

- [ ] Each task card has a labeled status selector with **To do**, **In progress**, and **Done**.
- [ ] Change a task's status. Verify the task moves to the matching column and the column count updates.

## FR3: Task deletion

- [ ] Click **Delete** on a task. A confirmation dialog appears.
- [ ] Confirm deletion. Verify the task is removed and the column count updates.
- [ ] Cancel deletion. Verify the task remains.

## FR4: Search and filtering

- [ ] Type in the search box. Verify only tasks whose title or description contains the text are shown.
- [ ] Select a status filter. Verify only tasks in that status are shown.
- [ ] Combine search text and a status filter. Verify both conditions must match (AND logic).
- [ ] Click **Clear filters**. Verify all tasks are visible again.

## FR5: Column counts and empty state

- [ ] Each column header shows the number of tasks currently in that column.
- [ ] When no tasks match the current filters, verify an empty state message appears in the affected list.

## FR6: Task persistence

- [ ] Create, edit, and delete tasks, then reload the page. Verify the state is restored from `localStorage`.
- [ ] Verify task IDs remain stable across reloads and are never duplicated or reassigned.

## FR7: JSON export and import

- [ ] Click **Export JSON**. Verify a JSON file containing the current tasks array is downloaded.
- [ ] Click **Import JSON** and select a valid JSON file. Verify the tasks are loaded into the board.
- [ ] Import an invalid JSON file. Verify an error is shown and existing tasks are not corrupted.

## FR8: Reset demo data

- [ ] Click **Reset demo data**. A confirmation dialog appears.
- [ ] Confirm the reset. Verify exactly three sample tasks are restored, matching `assets/sample-tasks.json`.
- [ ] Cancel the reset. Verify the current tasks remain unchanged.

## FR9: Responsive layout

- [ ] On a desktop viewport, verify the three columns are displayed side by side.
- [ ] At a 360px viewport, verify the columns stack vertically.
- [ ] Verify all interactive controls have visible focus states.

## FR10: Offline limitation notice

- [ ] Verify the README and the app clearly state the app is offline-only and data is stored in `localStorage`.
- [ ] Verify no external network requests are made while using the app.


## User Story Verification (US10-US12)

- [ ] US10: Export the task board to JSON and re-import it. Verify the restored board matches the exported data.
- [ ] US11: Simulate unavailable localStorage and verify a graceful, visible warning is shown while the app remains usable.
- [ ] US12: Verify the layout at 360px (stacked columns) and desktop (three columns), with all controls usable.

- [ ] Verify no package.json, build step, framework, backend, or external network requests exist (single-file static app).
