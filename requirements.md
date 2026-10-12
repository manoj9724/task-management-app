# Task Management App – Requirements Specification

**Document Owner:** Requirement Analyst
**Version:** 1.0
**Date:** 12 October 2026
**Status:** Draft for team review

---

## 1. Introduction

### 1.1 Purpose
This document captures the functional and non-functional requirements, user stories and acceptance criteria for the **Task Management App**. It is the single reference for the development, testing and project management teams.

### 1.2 Scope
**In scope (MVP):**
- User registration, login and logout
- Create, view, edit, delete tasks
- Assign priority, due date, category and status to tasks
- Mark tasks complete / reopen them
- Search, filter and sort tasks
- Dashboard with task summary
- Due-date reminders / notifications

**Out of scope (future releases):**
- Real-time chat between team members
- Third-party calendar integration (Google/Outlook)
- Native mobile apps (MVP is responsive web)
- File attachments larger than 5 MB
- Payment / subscription features

### 1.3 Definitions
| Term | Meaning |
|------|---------|
| Task | A unit of work with a title, description, due date, priority and status |
| Project/Category | A group of related tasks |
| MVP | Minimum Viable Product |
| SRS | Software Requirements Specification |

### 1.4 Stakeholders
| Role | Responsibility |
|------|----------------|
| Requirement Analyst | Gather and document requirements, user stories, acceptance criteria |
| Developer(s) | Build prototype / feature |
| Tester | Write and execute test cases, log defects |
| Project Manager / Scrum Master | Plan sprints, track on Jira |
| End Users | Individuals and small teams managing daily work |

---

## 2. Overall Description

### 2.1 Product Perspective
A web-based application that lets users plan, organise, track and complete their tasks from a single place.

### 2.2 User Classes
| User Type | Description |
|-----------|-------------|
| Registered User | Creates and manages own tasks |
| Team Member | Views and updates tasks assigned to them |
| Admin / Team Lead | Manages users, assigns tasks, views team progress |

### 2.3 Assumptions and Dependencies
- Users have a modern browser and internet access.
- Email service is available for reminders and password reset.
- The app is built using the starter code provided.

### 2.4 Constraints
- Must be delivered within the Day 6 activity timeframe.
- GitHub is used for version control; Jira for task tracking.

---

## 3. Functional Requirements

### 3.1 User Management
| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | The system shall allow a new user to register with name, email and password. | High |
| FR-02 | The system shall validate that the email is unique and correctly formatted. | High |
| FR-03 | The system shall allow registered users to log in and log out securely. | High |
| FR-04 | The system shall allow users to reset a forgotten password via email. | Medium |
| FR-05 | The system shall allow users to view and edit their profile. | Low |

### 3.2 Task Management
| ID | Requirement | Priority |
|----|-------------|----------|
| FR-06 | The system shall allow users to create a task with title (mandatory), description, due date, priority and category. | High |
| FR-07 | The system shall allow users to view a list of all their tasks. | High |
| FR-08 | The system shall allow users to edit any detail of an existing task. | High |
| FR-09 | The system shall allow users to delete a task after confirmation. | High |
| FR-10 | The system shall allow users to set task status: *To Do, In Progress, Completed*. | High |
| FR-11 | The system shall allow users to mark a task as completed and reopen it. | High |
| FR-12 | The system shall support priority levels: *Low, Medium, High*. | Medium |
| FR-13 | The system shall allow users to add subtasks/checklist items to a task. | Low |

### 3.3 Organisation, Search and Filter
| ID | Requirement | Priority |
|----|-------------|----------|
| FR-14 | The system shall allow users to search tasks by title or keyword. | Medium |
| FR-15 | The system shall allow filtering by status, priority, category and due date. | Medium |
| FR-16 | The system shall allow sorting by due date, priority and creation date. | Medium |
| FR-17 | The system shall allow users to create and manage categories/projects. | Medium |

### 3.4 Notifications and Dashboard
| ID | Requirement | Priority |
|----|-------------|----------|
| FR-18 | The system shall send a reminder before a task's due date. | Medium |
| FR-19 | The system shall highlight overdue tasks. | Medium |
| FR-20 | The system shall display a dashboard showing counts of pending, in-progress, completed and overdue tasks. | Medium |

### 3.5 Collaboration (Team Features)
| ID | Requirement | Priority |
|----|-------------|----------|
| FR-21 | The system shall allow an admin/team lead to assign a task to another user. | Medium |
| FR-22 | The system shall notify the assignee when a task is assigned. | Low |
| FR-23 | The system shall allow users to add comments on a task. | Low |

---

## 4. Non-Functional Requirements

| ID | Category | Requirement |
|----|----------|-------------|
| NFR-01 | Performance | Pages shall load within 3 seconds under normal load; task actions shall respond within 2 seconds. |
| NFR-02 | Scalability | The system shall support at least 500 concurrent users without degradation. |
| NFR-03 | Security | Passwords shall be hashed (e.g., bcrypt) and never stored in plain text. |
| NFR-04 | Security | All data transmission shall use HTTPS; sessions shall expire after 30 minutes of inactivity. |
| NFR-05 | Security | A user shall be able to access only their own (or assigned) tasks. |
| NFR-06 | Usability | A new user shall be able to create their first task within 2 minutes without training. |
| NFR-07 | Usability | The UI shall be responsive on desktop, tablet and mobile screens. |
| NFR-08 | Reliability | The system shall have 99% uptime and daily data backup. |
| NFR-09 | Compatibility | The app shall work on the latest versions of Chrome, Firefox, Edge and Safari. |
| NFR-10 | Maintainability | Code shall follow a consistent style, be modular and documented. |
| NFR-11 | Accessibility | The UI shall follow WCAG 2.1 AA basics (contrast, keyboard navigation, labels). |
| NFR-12 | Data Integrity | Tasks shall not be lost on failure; all create/update/delete actions shall be persisted. |

---

## 5. User Stories and Acceptance Criteria

> Format: **As a** [role], **I want** [feature], **so that** [benefit].

### US-01: User Registration
**As a** new user, **I want** to register with my name, email and password, **so that** I can have my own account.

**Acceptance Criteria**
- Given I am on the registration page, when I enter valid details and submit, then my account is created and I am redirected to login/dashboard.
- Given I enter an email that already exists, then an error "Email already registered" is shown.
- Given I enter an invalid email or a password shorter than 8 characters, then a validation message is shown and no account is created.

### US-02: User Login
**As a** registered user, **I want** to log in, **so that** I can access my tasks.

**Acceptance Criteria**
- Given valid credentials, when I click Login, then I am taken to my dashboard.
- Given wrong credentials, then an error "Invalid email or password" is displayed.
- Given I click Logout, then my session ends and I am redirected to the login page.

### US-03: Create Task
**As a** user, **I want** to create a task with title, description, due date and priority, **so that** I can keep track of my work.

**Acceptance Criteria**
- Given I am logged in, when I fill in the title and click Save, then the task appears in my task list with status "To Do".
- Given the title is empty, then the task is not saved and "Title is required" is shown.
- Given I select a due date in the past, then a warning is displayed.
- Given the task is saved, then a success message is displayed.

### US-04: View Tasks
**As a** user, **I want** to see all my tasks in a list, **so that** I know what needs to be done.

**Acceptance Criteria**
- Given I have tasks, when I open the Tasks page, then all my tasks are listed with title, priority, due date and status.
- Given I have no tasks, then a message "No tasks yet. Create your first task!" is shown.

### US-05: Edit Task
**As a** user, **I want** to edit a task, **so that** I can correct or update its details.

**Acceptance Criteria**
- Given I open a task and change details, when I click Save, then the updated details are reflected in the list.
- Given I clear the title and save, then validation prevents the update.

### US-06: Delete Task
**As a** user, **I want** to delete a task, **so that** I can remove tasks I no longer need.

**Acceptance Criteria**
- Given I click Delete, then a confirmation prompt is displayed.
- Given I confirm, then the task is removed from the list permanently.
- Given I cancel, then the task remains unchanged.

### US-07: Update Status / Mark Complete
**As a** user, **I want** to change a task's status or mark it complete, **so that** I can track my progress.

**Acceptance Criteria**
- Given a task in "To Do", when I mark it "In Progress" or "Completed", then the status updates immediately.
- Given a completed task, when I click Reopen, then the status returns to "To Do".
- Given a task is completed, then it is visually distinguished (e.g., strikethrough or green tag).

### US-08: Set Priority
**As a** user, **I want** to set priority on tasks, **so that** I can focus on the most important work first.

**Acceptance Criteria**
- Given I create/edit a task, then I can choose Low, Medium or High.
- Given tasks have priorities, then each is displayed with a distinct colour/label.

### US-09: Search Tasks
**As a** user, **I want** to search tasks by keyword, **so that** I can find them quickly.

**Acceptance Criteria**
- Given I type a keyword, then only tasks whose title/description match are shown.
- Given no tasks match, then "No results found" is displayed.

### US-10: Filter and Sort
**As a** user, **I want** to filter and sort tasks, **so that** I can view only what is relevant.

**Acceptance Criteria**
- Given I select a filter (status, priority, category, due date), then only matching tasks are displayed.
- Given I choose a sort option, then tasks are reordered accordingly.
- Given I click Clear Filters, then all tasks are shown again.

### US-11: Categories / Projects
**As a** user, **I want** to group tasks into categories, **so that** I can organise related work.

**Acceptance Criteria**
- Given I create a category, then it is available in the task form.
- Given I select a category, then only tasks in that category are shown.

### US-12: Due-Date Reminders
**As a** user, **I want** to get reminders before a task is due, **so that** I don't miss deadlines.

**Acceptance Criteria**
- Given a task is due within 24 hours, then I receive a reminder notification/email.
- Given a task's due date has passed and it is not completed, then it is marked "Overdue".

### US-13: Dashboard
**As a** user, **I want** a dashboard summary, **so that** I can see my progress at a glance.

**Acceptance Criteria**
- Given I open the dashboard, then I see counts of To Do, In Progress, Completed and Overdue tasks.
- Given I complete a task, then the counts update accordingly.

### US-14: Assign Tasks (Team Lead)
**As a** team lead, **I want** to assign tasks to team members, **so that** work is distributed clearly.

**Acceptance Criteria**
- Given I select a team member in the Assignee field, then the task appears in that member's list.
- Given a task is assigned, then the assignee receives a notification.

### US-15: Password Reset
**As a** user, **I want** to reset my password, **so that** I can regain access if I forget it.

**Acceptance Criteria**
- Given I enter my registered email, then a reset link is sent.
- Given I use a valid link and enter a new valid password, then my password is updated.
- Given the link is expired, then an error message is displayed.

---

## 6. Requirements Traceability Matrix

| User Story | Functional Requirement(s) | Priority |
|------------|---------------------------|----------|
| US-01 | FR-01, FR-02 | High |
| US-02 | FR-03 | High |
| US-03 | FR-06 | High |
| US-04 | FR-07 | High |
| US-05 | FR-08 | High |
| US-06 | FR-09 | High |
| US-07 | FR-10, FR-11 | High |
| US-08 | FR-12 | Medium |
| US-09 | FR-14 | Medium |
| US-10 | FR-15, FR-16 | Medium |
| US-11 | FR-17 | Medium |
| US-12 | FR-18, FR-19 | Medium |
| US-13 | FR-20 | Medium |
| US-14 | FR-21, FR-22 | Medium |
| US-15 | FR-04 | Medium |

---

## 7. Prioritisation (MoSCoW)

| Category | Items |
|----------|-------|
| **Must have** | Registration, Login/Logout, Create/View/Edit/Delete task, Status update |
| **Should have** | Priority, Search, Filter/Sort, Categories, Dashboard |
| **Could have** | Reminders, Task assignment, Password reset, Comments, Subtasks |
| **Won't have (now)** | Chat, Calendar integration, Native mobile app |

**Suggested prototype / small feature:** US-03 *Create Task* (with US-04 *View Tasks*).

---

## 8. Risks and Open Questions

| # | Risk / Question | Mitigation / Owner |
|---|-----------------|--------------------|
| 1 | Scope creep from team features | Freeze MVP scope; move extras to backlog |
| 2 | Email service for reminders may not be available in prototype | Use in-app notifications for MVP |
| 3 | Should tasks be shareable between users in MVP? | Confirm with Project Manager |
| 4 | Final tech stack not yet confirmed | Confirm with developers |

---

## 9. Approval

| Name | Role | Date | Sign-off |
|------|------|------|----------|
|iniyan| Requirement Analyst |  |  |
|dillibabu| Project Manager |  |  |
|manoj | Developer Lead |  |  |
|dhinesh| Tester |  |  |
