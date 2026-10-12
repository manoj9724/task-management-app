# Taskify – Team Responsibilities

**Project:** Taskify (Task Management App)
**Document:** Team roles, responsibilities, deliverables and collaboration plan

---

## 1. Project Overview

Taskify is a task management application that helps users create, organise, assign, track and complete tasks. This document defines who owns which part of the project, what each person delivers, and how the team works together across the software development life cycle (SDLC) and the software testing life cycle (STLC).

## 2. Team at a Glance

| Member | Role | Primary Focus | Key Deliverables |
|---|---|---|---|
| **Manoj** | Frontend & Prototype Developer | Building the UI and working prototype | Frontend code, interactive prototype |
| **Dinesh** | Tester & Defect Analyser | Quality assurance and defect tracking | Test cases, bug reports, defect analysis |
| **Dillibabu** | Documentation (SRS) | Software Requirements Specification | SRS document |
| **Hemanth** | System Designer (Wireframe & UI) | System design and UI/UX | Wireframes, UI mockups, design specs |
| **Dharshan** | Documentation (STLC) | Test life cycle documentation | Test plan, test reports, STLC records |
| **Iniyan** | Requirements & Retrospective Manager | Requirement gathering and team retrospectives | Requirement list, retrospective reports |

---

## 3. Detailed Responsibilities

### 3.1 Manoj – Frontend & Prototype Developer

**Purpose:** Turn the approved designs into a working, user-friendly interface and prototype.

**Responsibilities**
- Develop the frontend of Taskify based on Hemanth's wireframes and UI designs.
- Build screens such as login/signup, dashboard, task list, task creation/edit form, task details, and status/priority views.
- Create a clickable prototype early so the team can review and give feedback.
- Implement responsive layouts so the app works on desktop and mobile screens.
- Add client-side validation (required fields, date formats, etc.).
- Connect UI components to data or mock APIs for the prototype.
- Fix UI defects reported by Dinesh and re-submit for retesting.
- Maintain clean, readable and well-commented code.
- Keep the code in version control with clear commit messages.

**Deliverables**
- Working frontend prototype
- Source code for all UI screens
- Short setup/run instructions
- Fixes for reported UI defects

**Works closely with:** Hemanth (design input), Dinesh (defect feedback), Iniyan (requirement clarification)

---

### 3.2 Dinesh – Tester & Defect Analyser

**Purpose:** Make sure Taskify works correctly, reliably and meets the requirements.

**Responsibilities**
- Study the SRS and requirements to understand expected behaviour.
- Write test cases and test scenarios covering functional and UI behaviour.
- Execute test cases on the prototype and record pass/fail results.
- Log defects with clear details: title, steps to reproduce, expected vs actual result, severity, priority and screenshots.
- Analyse defects to find root causes, patterns and high-risk areas.
- Track defects through their life cycle (New → Assigned → Fixed → Retested → Closed).
- Perform retesting and regression testing after fixes.
- Provide defect summaries to the team and to Dharshan for the test reports.

**Deliverables**
- Test cases and test scenarios
- Defect/bug reports
- Defect analysis summary (counts, severity, trends)
- Retest and regression results

**Works closely with:** Manoj (defect fixes), Dharshan (STLC documents), Dillibabu (requirements reference)

---

### 3.3 Dillibabu – Documentation (SRS)

**Purpose:** Produce the Software Requirements Specification that defines what Taskify must do.

**Responsibilities**
- Prepare the SRS document using the requirements collected by Iniyan.
- Define the purpose, scope, intended users and overall description of Taskify.
- Document functional requirements (task creation, editing, deletion, assignment, due dates, priorities, status updates, search/filter, notifications, etc.).
- Document non-functional requirements (performance, usability, security, reliability, compatibility).
- Describe user classes, assumptions, constraints and dependencies.
- Give each requirement a unique ID so it can be traced to design and test cases.
- Keep the SRS updated when requirements change and maintain version history.
- Get the SRS reviewed by the team before it is finalised.

**Deliverables**
- SRS document (versioned)
- Requirement traceability references
- Updated revisions after reviews

**Works closely with:** Iniyan (requirements), Hemanth (design alignment), Dinesh (testability of requirements)

---

### 3.4 Hemanth – System Designer (Wireframe & UI)

**Purpose:** Design how Taskify is structured and how it looks and feels.

**Responsibilities**
- Design the overall system structure and the flow between screens.
- Create low-fidelity and high-fidelity wireframes for all major screens.
- Design the UI: layout, colour scheme, typography, icons and component styles.
- Define the user flow for key actions (add task, edit task, mark complete, filter, etc.).
- Ensure the design is simple, consistent and easy to use.
- Provide design specifications and assets to Manoj for implementation.
- Review the built prototype against the design and suggest corrections.
- Update designs based on feedback and changed requirements.

**Deliverables**
- Wireframes
- UI mockups and style guide
- User flow / screen navigation diagram
- Design review feedback

**Works closely with:** Manoj (implementation), Iniyan (requirements), Dillibabu (SRS alignment)

---

### 3.5 Dharshan – Documentation (STLC)

**Purpose:** Document the complete software testing life cycle so testing is planned, traceable and reportable.

**Responsibilities**
- Prepare the test plan: objectives, scope, approach, resources, schedule, entry/exit criteria and risks.
- Document each STLC phase: requirement analysis, test planning, test case design, test environment setup, test execution, and test closure.
- Maintain the requirement traceability matrix (requirements ↔ test cases).
- Compile test execution results and metrics provided by Dinesh.
- Prepare test summary and test closure reports.
- Keep all testing documents organised, versioned and up to date.
- Review test documents with Dinesh for accuracy.

**Deliverables**
- Test plan
- Requirement traceability matrix
- Test execution report
- Test summary / closure report

**Works closely with:** Dinesh (test data and results), Dillibabu (requirements), Iniyan (project status)

---

### 3.6 Iniyan – Requirements & Retrospective Manager

**Purpose:** Capture what users need and help the team continuously improve how it works.

**Responsibilities**

*Requirements*
- Gather and clarify requirements for Taskify from stakeholders and the team.
- Write user stories and acceptance criteria.
- Prioritise requirements (must-have, should-have, nice-to-have).
- Manage requirement changes and communicate them to everyone affected.
- Hand over finalised requirements to Dillibabu for the SRS.

*Retrospectives*
- Plan and run retrospective meetings at the end of each phase or sprint.
- Collect feedback on what went well, what did not, and what to improve.
- Record action items with owners and follow up on them.
- Share the retrospective report with the team.

**Deliverables**
- Requirement list and user stories
- Prioritised backlog
- Retrospective reports and action item tracker

**Works closely with:** Dillibabu (SRS), Manoj and Hemanth (clarifying scope), the whole team (retrospectives)

---

## 4. Project Workflow

1. **Requirements** – Iniyan gathers and prioritises requirements.
2. **Documentation (SRS)** – Dillibabu writes and reviews the SRS.
3. **Design** – Hemanth creates wireframes and UI designs.
4. **Development** – Manoj builds the frontend and prototype.
5. **Test preparation** – Dharshan prepares the test plan; Dinesh writes test cases.
6. **Testing** – Dinesh executes tests and logs defects; Manoj fixes them; Dinesh retests.
7. **Test closure** – Dharshan produces the test summary and closure report.
8. **Retrospective** – Iniyan facilitates a review and records improvements.

## 5. RACI Matrix

**R** = Responsible, **A** = Accountable, **C** = Consulted, **I** = Informed

| Activity | Manoj | Dinesh | Dillibabu | Hemanth | Dharshan | Iniyan |
|---|---|---|---|---|---|---|
| Requirement gathering | C | C | C | C | I | **A/R** |
| SRS document | I | C | **A/R** | C | I | C |
| Wireframes & UI design | C | I | C | **A/R** | I | C |
| Frontend development | **A/R** | I | I | C | I | C |
| Prototype | **A/R** | C | I | C | I | C |
| Test case design | I | **A/R** | C | I | C | C |
| Test execution & defect logging | C | **A/R** | I | I | C | I |
| Defect analysis | C | **A/R** | I | I | C | I |
| STLC documentation | I | C | I | I | **A/R** | I |
| Retrospective | C | C | C | C | C | **A/R** |

## 6. Collaboration Guidelines

- **Communication:** Use one shared team channel for updates; raise blockers early.
- **Meetings:** Short regular sync-ups, plus a retrospective at the end of each phase.
- **Version control:** All code and documents are stored in a shared repository with meaningful version names.
- **Reviews:** Every major document (SRS, design, test plan) is reviewed by at least one other team member before approval.
- **Change handling:** Any requirement change goes through Iniyan, is reflected in the SRS by Dillibabu, and the affected design, code and tests are updated.
- **Defect handling:** Defects are logged by Dinesh, fixed by the owner of the affected area, and verified by Dinesh before closure.

## 7. Dependencies Between Members

| Who needs something | From whom | What |
|---|---|---|
| Dillibabu | Iniyan | Finalised requirements for the SRS |
| Hemanth | Iniyan, Dillibabu | Requirements and SRS to guide design |
| Manoj | Hemanth | Wireframes, UI designs and assets |
| Dinesh | Dillibabu, Manoj | SRS for test cases; prototype to test |
| Dharshan | Dinesh | Test cases, results and defect data |
| Iniyan | All members | Feedback and input for retrospectives |

## 8. Success Criteria

- All requirements are documented, prioritised and traceable.
- The prototype matches the approved designs and covers the key Taskify features.
- Test cases cover all major requirements, and critical defects are fixed and verified.
- SRS and STLC documents are complete, reviewed and version-controlled.
- Retrospective action items are recorded and followed up.

---

*Prepared for the Taskify project team. Update this document if roles or responsibilities change.*
