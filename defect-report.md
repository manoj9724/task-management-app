# Defect Report – Taskify (Task Management App)

**Project:** Taskify – Task Management App
**Build tested:** `src/index.html` (HTML, CSS, JavaScript prototype, data in browser `localStorage`)
**Date:** 12 October 2026
**Prepared for:** Dinesh (Tester & Defect Analyser), Manoj (Developer)
**Reference documents:** `requirements.md` v1.0, `SRS_Document.pdf` v1.0, README, wireframes, workflow diagram, team presentation

> **How these defects were found:** by reviewing the prototype source code against the requirements (`FR-xx`, `NFR-xx`, `US-xx`) and by cross-checking the project documents against each other. Steps to reproduce are derived from the code. Dinesh should confirm each item in the browser, record the actual result in `test-cases.xlsx`, and update the status column.

---

## 1. Summary

| Category | Total | Open | Deferred |
|----------|:-----:|:----:|:--------:|
| Application defects (BUG) | 12 | 10 | 2 |
| Documentation defects (DOC) | 8 | 8 | 0 |
| **Total** | **20** | **18** | **2** |

| Severity | Application | Documentation |
|----------|:-----------:|:-------------:|
| High | 1 | 0 |
| Medium | 6 | 3 |
| Low | 5 | 5 |

**Working correctly (verified in code):** create task with required-title validation (US-03), view list, edit, delete with confirmation (US-06), status change and mark complete/reopen (US-07), Low/Medium/High priority with colour labels (US-08), filter by status and priority, overdue highlighting (FR-19), calendar view, persistence in `localStorage`, safe rendering of user text (no HTML injection), keyboard support for menus and the confirm dialog.

## 2. Severity and Priority Scale

| Severity | Meaning |
|----------|---------|
| **High** | A required feature is missing or broken, or data can be lost. |
| **Medium** | A feature works only partly or does not match its acceptance criteria. |
| **Low** | Minor, cosmetic or edge-case issue with a simple workaround. |

| Status | Meaning |
|--------|---------|
| **Open** | Logged and waiting for a fix. |
| **Deferred** | Accepted as out of scope for this prototype; kept in the backlog. |

Defect life cycle used by the team: New → Assigned → Fixed → Retested → Closed.

---

## 3. Defect Summary Table

### 3.1 Application defects

| ID | Title | Requirement | Severity | Priority | Status | Owner |
|----|-------|-------------|----------|----------|--------|-------|
| BUG-01 | No registration, login, logout or password reset | FR-01–05, US-01, US-02, US-15 | High | High | Deferred | Manoj |
| BUG-02 | Dashboard has no Overdue count | FR-20, US-13 | Medium | Medium | Open | Manoj |
| BUG-03 | No warning when a past due date is chosen | US-03 | Medium | Medium | Open | Manoj |
| BUG-04 | Search matches title only | FR-14, US-09 | Medium | Medium | Open | Manoj |
| BUG-05 | "Task saved" is shown even if storage fails | NFR-12 | Medium | High | Open | Manoj |
| BUG-06 | White text on amber, green and sky-blue fails contrast | NFR-11 | Medium | Medium | Open | Manoj / Hemanth |
| BUG-07 | Sort, due-date filter, categories, reminders and assignment not implemented | FR-15, 16, 17, 18, 21–23 | Medium | Low | Deferred | Manoj |
| BUG-08 | Keyboard focus is lost after ticking a task | NFR-11 | Low | Low | Open | Manoj |
| BUG-09 | Empty-state wording differs from acceptance criteria | US-04, US-09 | Low | Low | Open | Manoj |
| BUG-10 | Task with unknown status or priority disappears from the board | NFR-12 | Low | Low | Open | Manoj |
| BUG-11 | Two open tabs overwrite each other's changes | NFR-12 | Low | Low | Open | Manoj |
| BUG-12 | Page behind the confirm dialog can still scroll | NFR-11 | Low | Low | Open | Manoj |

### 3.2 Documentation defects

| ID | Title | Document(s) | Severity | Status | Owner |
|----|-------|-------------|----------|--------|-------|
| DOC-01 | Team roles differ between documents | README, retrospective, team-responsibilities, requirements | Medium | Open | Dharshan |
| DOC-02 | Presentation lists a different team and roles | `Task_Management_App.pptx` | Medium | Open | Dharshan |
| DOC-03 | Requirements and SRS disagree on scope | requirements.md, SRS | Medium | Open | Dillibabu / Iniyan |
| DOC-04 | Workflow diagram is linear but project uses Agile | Workflow diagram, README | Low | Open | Hemanth |
| DOC-05 | Workflow diagram text runs together | Workflow diagram | Low | Open | Hemanth |
| DOC-06 | Wireframe spelling and format errors | Wireframe | Low | Open | Hemanth |
| DOC-07 | README team table does not render; "future" features already built | README, retrospective | Low | Open | Dharshan |
| DOC-08 | Terminology differs between documents and the app | All | Low | Open | Dharshan |

---

## 4. Application Defect Details

### BUG-01 – No registration, login, logout or password reset
- **Severity / Priority:** High / High
- **Status:** Deferred (prototype is single-user and frontend-only)
- **Requirement:** FR-01 to FR-05, US-01, US-02, US-15. The SRS acceptance criteria also say "users can successfully log in and manage their tasks".
- **Steps to reproduce:** Open `index.html`. The app opens straight to the dashboard. There is no login screen, sign-up form, logout button or password reset. The Profile screen shows a fixed name and email (`Hemanth`, `hemanth@example.com`), and only the display name can be changed.
- **Expected:** A user can register, log in, log out and reset a password.
- **Actual:** None of these exist. All data belongs to whoever opens the browser.
- **Impact:** SRS acceptance and the security requirements NFR-03 to NFR-05 cannot be met.
- **Suggested fix:** Keep as a backlog item for the next sprint, which needs a backend and database. For the prototype, state clearly in the README and SRS that authentication is out of scope.

### BUG-02 – Dashboard has no Overdue count
- **Severity / Priority:** Medium / Medium
- **Status:** Open
- **Requirement:** FR-20, US-13 ("counts of To Do, In Progress, Completed and Overdue tasks")
- **Steps to reproduce:**
  1. Open Home.
  2. Add a task with a due date in the past.
  3. Look at the four summary tiles.
- **Expected:** An Overdue count that increases.
- **Actual:** Only Total, Pending, In Progress and Completed are shown. The task is marked "Overdue" in the list, but the dashboard does not count it.
- **Suggested fix:** Add an Overdue tile or a line below the tiles. In `counts()`, add `overdue: state.tasks.filter(t => t.dueDate && t.dueDate < todayISO() && t.status !== 'completed').length`, then show it in `renderHome()`. If a fifth tile does not fit on small screens, use a 2×2 grid.

### BUG-03 – No warning when a past due date is chosen
- **Severity / Priority:** Medium / Medium
- **Status:** Open
- **Requirement:** US-03 ("Given I select a due date in the past, then a warning is displayed.")
- **Steps to reproduce:** Tap **+**, enter a title, choose yesterday's date, and tap **Save Task**.
- **Expected:** A warning is shown.
- **Actual:** The task is saved and the success toast appears. No warning.
- **Suggested fix:** In `submitForm()`, after validation, check `data.dueDate && data.dueDate < todayISO() && data.status !== 'completed'`. Show an inline warning under the date field. Saving can stay allowed, because the acceptance criterion asks only for a warning.

### BUG-04 – Search matches title only
- **Severity / Priority:** Medium / Medium
- **Status:** Open
- **Requirement:** FR-14, US-09 ("only tasks whose title/description match are shown")
- **Steps to reproduce:** Open Tasks and search for `proofread`. This word appears only in the description of "Complete project report".
- **Expected:** The task is listed.
- **Actual:** "No matching tasks" is shown. The placeholder reads "Search tasks by title".
- **Suggested fix:** In `filteredTasks()`, use `(t.title + ' ' + (t.description || '')).toLowerCase().includes(q)` and change the placeholder to "Search tasks".

### BUG-05 – "Task saved" is shown even if storage fails
- **Severity / Priority:** Medium / High
- **Status:** Open
- **Requirement:** NFR-12 ("all create/update/delete actions shall be persisted")
- **Steps to reproduce:** Open the app in a browser where `localStorage` is blocked or full (some private-browsing modes, or storage cleared by policy). Create a task, then refresh.
- **Expected:** The user is told that the task could not be saved.
- **Actual:** `store()` swallows the error (`catch (e) { /* storage unavailable */ }`). The app shows "Task saved successfully", and the task is gone after a refresh.
- **Suggested fix:** Make `store()` return `true` or `false`. If it fails, show a toast such as "Could not save – storage is unavailable. Your changes will be lost on refresh."

### BUG-06 – White text fails contrast on the amber, green and sky-blue tiles
- **Severity / Priority:** Medium / Medium
- **Status:** Open
- **Requirement:** NFR-11 (WCAG 2.1 AA basics)
- **Steps to reproduce:** Open Home and read the "Pending", "In Progress" and "Completed" tiles. Open Tasks and read the "To Do", "In Progress" and "Completed" column headers.
- **Expected:** Text contrast of at least 4.5:1 (3:1 for large text).
- **Actual:** White text on `#f59e0b`/`#fbbf24` (amber), `#38bdf8` (sky blue) and `#34d399` (green) has a contrast of about 2:1 or lower. The small `.72rem` tile labels are the worst case.
- **Suggested fix:** Use darker gradient colours (for example amber `#b45309`, blue `#1d4ed8`, green `#047857`) or dark text on the light colours. Re-check with a contrast checker.

### BUG-07 – Several planned features are not implemented
- **Severity / Priority:** Medium / Low
- **Status:** Deferred
- **Requirement:** FR-15 (filter by due date and category), FR-16 (sort), FR-17 (categories), FR-18 (reminders), FR-13 (subtasks), FR-21 to FR-23 (assignment, notifications, comments)
- **Actual:** The prototype has only status and priority filters. There is no sorting, no due-date filter, no category field, no reminder and no assignee. The Home screen shows tasks in creation order (newest first), not by due date.
- **Suggested fix:** Plan for a later sprint. Sorting by due date is the cheapest next step, as a single `<select>` and a `sort()` call in `renderBoard()`.

### BUG-08 – Keyboard focus is lost after ticking a task
- **Severity / Priority:** Low / Low
- **Status:** Open
- **Requirement:** NFR-11 (keyboard navigation)
- **Steps to reproduce:** Use the keyboard to tab to a task checkbox on Home and press Space.
- **Expected:** Focus stays on the checkbox.
- **Actual:** `toggleComplete()` calls `renderAll()`, which rebuilds the list (`replaceChildren()`), so focus returns to the page start. The same happens after choosing an item from a task's options menu.
- **Suggested fix:** Remember the task id and control before rendering, then focus the matching element after rendering. Or update the one row instead of rebuilding the whole list.

### BUG-09 – Empty-state wording differs from the acceptance criteria
- **Severity / Priority:** Low / Low
- **Status:** Open
- **Requirement:** US-04 ("No tasks yet. Create your first task!"), US-09 ("No results found")
- **Actual:** The app shows "No tasks yet / Tap the + button to create your first task." and "No matching tasks".
- **Suggested fix:** Either change the app text to match the user stories, or update the user stories to match the app. Pick one so test cases have a single expected result.

### BUG-10 – A task with an unknown status or priority disappears from the board
- **Severity / Priority:** Low / Low
- **Status:** Open
- **Requirement:** NFR-12 (data integrity)
- **Steps to reproduce:** In the browser console, edit `taskify.tasks.v1` so one task has `"status":"done"` (the word used in the README). Refresh.
- **Expected:** The task is shown or repaired.
- **Actual:** The task counts toward Total but appears in no column and in no status count, so the dashboard numbers do not add up. An unknown priority shows the raw text in the badge.
- **Suggested fix:** In `init()`, normalise loaded tasks: `status` not in `STATUSES` becomes `'todo'` and `priority` not in `PRIORITIES` becomes `'medium'`.

### BUG-11 – Two open tabs overwrite each other's changes
- **Severity / Priority:** Low / Low
- **Status:** Open
- **Requirement:** NFR-12
- **Steps to reproduce:** Open the app in two tabs. Add a task in tab A. Add a different task in tab B without refreshing.
- **Expected:** Both tasks are kept.
- **Actual:** Each tab saves its whole in-memory list, so the task from tab A is lost.
- **Suggested fix:** Listen for the `storage` event and reload `state.tasks`, then call `renderAll()`.

### BUG-12 – Page behind the confirm dialog can still scroll
- **Severity / Priority:** Low / Low
- **Status:** Open
- **Requirement:** NFR-11
- **Steps to reproduce:** On a long task list, open "Delete task?" and scroll with the mouse wheel or touch.
- **Expected:** The background stays still while the dialog is open.
- **Actual:** The page behind the dialog scrolls.
- **Suggested fix:** Set `document.body.style.overflow = 'hidden'` in `askConfirm()` and restore it in `closeModal()`.

---

## 5. Documentation Defect Details

### DOC-01 – Team roles differ between documents
- **Severity:** Medium
- **Details:** The README and retrospective say Dillibabu is Project Manager, Iniyan is Requirements Analyst and Dharshan is Documentation Lead. `team-responsibilities.md` says Dillibabu writes the SRS, Iniyan is Requirements & Retrospective Manager and Dharshan owns STLC documentation. `requirements.md` lists Manoj as "Developer Lead" while the other files say "Developer" or "Frontend & Prototype Developer".
- **Fix:** Agree one role list and use it in every file.

### DOC-02 – Presentation lists a different team and roles
- **Severity:** Medium
- **Details:** `Task_Management_App.pptx` (slides 1, 4, 13) names Allen Davidson, Jeeva, Devanathan and Kishore Dharshan, with roles Product Owner, Developer, Stakeholder and Scrum Master. None of these match the Taskify team. Its requirements slide also lists "assignee" filtering and "secure login", which the prototype does not have. Slides 6 to 10 (workflow, wireframe, test case, defect case) have no text, so the pictures could not be checked.
- **Fix:** Replace the names, roles and requirements with the Taskify team and scope, and fill the "Defect Case" slide from this report.

### DOC-03 – Requirements and SRS disagree on scope
- **Severity:** Medium
- **Details:**
  - `requirements.md` puts due-date reminders in the MVP (FR-18, US-12). The SRS lists reminders and calendar integration as future considerations.
  - The SRS says "Administrators manage users"; `requirements.md` calls this role "Admin / Team Lead" and gives it only task assignment.
  - The SRS Doc ID is `TASKIFY-SRH-001`, which looks like a typo for `SRS`.
  - The SRS is generic (no requirement IDs), although `team-responsibilities.md` says every requirement must have a unique ID for traceability.
- **Fix:** Align reminders and admin scope, correct the Doc ID, and add FR/NFR IDs to the SRS.

### DOC-04 – Workflow diagram is linear but the project uses Agile
- **Severity:** Low
- **Details:** The diagram shows Planning → Analysis → Design → Implementation → Testing → Deployment → Maintenance as one downward chain (a waterfall flow). The README, retrospective and presentation all say the project follows Agile. It also describes backend APIs and a production database, but the prototype is frontend-only with `localStorage`.
- **Fix:** Redraw with a loop between sprints (plan → build → test → review → repeat), or retitle it as the general SDLC. Mark the backend and database steps as future work.

### DOC-05 – Workflow diagram text runs together
- **Severity:** Low
- **Details:** Missing spaces or line breaks: "user experienceCreate system architecture", "workflow diagramsDesign the database schema", "tasks.Select suitable technologies", "individual modulesConduct integration testing", and a stray full stop before "Fix bugs". The Design box also starts without a verb ("the user interface and user experience").
- **Fix:** Put each item on its own line and start every item with a verb.

### DOC-06 – Wireframe spelling and format errors
- **Severity:** Low
- **Details:** "My Tsaks", "Submit assingnment", "Hello,Hemanth!" (missing space), "Today 12, oct" (day and month order, lower-case month), and "Stay Productive" does not match the app's capitalisation. The **Save Task** button has a drop-down arrow, which makes it look like a select box. (The built prototype already spells these correctly.)
- **Fix:** Correct the text and remove the arrow, then re-export `wireframe.png`.

### DOC-07 – README team table does not render; "future" features already built
- **Severity:** Low
- **Details:** In the README, a blank line sits between the table header and its rows and the separator row is missing, so the team table shows as plain text. Section 12 (Future Enhancements) lists task deadlines, priority levels and search/filter, and the retrospective says the prototype lacks "deadlines and search". The prototype already has all three.
- **Fix:** Repair the table and update both lists to match the actual build. Real gaps: login, reminders, sorting, categories, collaboration.

### DOC-08 – Terminology differs between documents and the app
- **Severity:** Low
- **Details:** The README and retrospective use "To Do / In Progress / **Done**". The requirements and the app use "Completed". The dashboard says "**Pending**", the board says "**To Do**" for the same status.
- **Fix:** Use one set of words everywhere (suggested: To Do, In Progress, Completed).

---

## 6. Defect Analysis

- **Risk areas:** Requirement coverage (BUG-01, 02, 03, 04, 07) and data safety (BUG-05, 10, 11). Core task create/edit/delete/status flows had no defects in this review.
- **Pattern:** Most application defects are places where the build does not match a written acceptance criterion. Wording and scope conflicts between the documents (DOC-01 to DOC-03) make it unclear which version is correct.
- **Recommended fix order:** BUG-05, then BUG-03, BUG-04 and BUG-02 (small changes, high visibility), then BUG-06, then the Low items. DOC-01 to DOC-03 should be settled before the final submission.

## 7. Retest Plan

1. Manoj fixes the items marked Open and updates the Status column to **Fixed**.
2. Dinesh retests each fixed item, records the result in `test-cases.xlsx`, and sets the status to **Closed** or back to **Open**.
3. Dinesh runs a quick regression on create, edit, delete, status change, filter and calendar after each batch of fixes.
4. Dharshan copies the final counts into the test summary report.

## 8. Sign-off

| Name | Role | Date | Sign-off |
|------|------|------|----------|
| Manoj | Developer | 12-10-2026 | |
| Dinesh | Tester | 12-10-2026 | |
| Dharshan | Documentation | 12-10-2026 | |
