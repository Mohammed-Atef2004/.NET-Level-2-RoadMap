# 🏃 Sprint 5 — Task Management Core

**Duration:** 2 Weeks

## 🎯 Sprint Goal

Extend the existing Task Management API with relationships, business rules, authentication, authorization, and improved validation.

> The existing **Task**, **Project**, and **Comment** features from Sprint 4 must remain the foundation of the system.

---

## Task 1 — Task & Project Business Rules

Build on the existing entities and features.

### Implement

**Project**
- Create Project
- Get Project
- Get Projects
- Update Project
- Delete Project

**Task**
- Create Task
- Get Task
- Get Tasks
- Update Task
- Delete Task

**Comment**
- Add Comment
- Get Task Comments
- Delete Comment

> ⚠️ Do **not** rebuild the existing endpoints. Extend them with business rules.

### Business Rules (examples)

- A Task must belong to an existing Project
- A Comment must belong to an existing Task
- A deleted Project cannot receive new Tasks
- A deleted Task cannot receive new Comments
- Task title is required
- Project name is required
- Comment content is required

### Concepts

- Domain Rules
- Application Validation
- Entity Relationships
- EF Core
- CQRS

### Deliverable

A consistent **Task → Project → Comment** workflow.

---

## Task 2 — Task Status & Workflow

Introduce a simple Task lifecycle.

### Create `TaskStatus`

```csharp
public enum TaskStatus
{
    Todo,
    InProgress,
    Completed,
    Cancelled
}
```

### Implement

- Update Task Status

### Rules

**Allowed transitions (examples):**

| From | To |
|---|---|
| Todo | InProgress |
| InProgress | Completed |
| Todo | Cancelled |
| InProgress | Cancelled |

**Invalid transitions must be prevented, for example:**

- ❌ Completed → InProgress
- ❌ Cancelled → Completed

### Deliverable

A controlled Task workflow instead of treating Task as simple CRUD data.

---

## Task 3 — Authentication

Add authentication to the existing Task Management API.

### Implement

- Register
- Login
- Refresh Token
- Logout

### Use

- ASP.NET Core Identity
- JWT
- Refresh Tokens
- Claims

### Create `User`

Connect users to the existing system:

```text
User
 │
 ├── Projects
 │
 └── Tasks
```

### Deliverable

Users can authenticate and receive JWT access tokens.

---

## Task 4 — Authorization

### Introduce Roles

| Role | Permissions |
|---|---|
| **Admin** | Can manage the system |
| **User** | Can manage their own resources |

### Examples

- User → Create Project
- User → Modify Own Project
- User → Create Task in Own Project
- User → Add Comment

> Users should **not** be able to modify another user's resources.

### Use

- Role-based Authorization
- Policy-based Authorization where appropriate
- Claims

### Deliverable

The existing Task Management endpoints become secured.

---

## Task 5 — Validation & Error Handling

Extend the existing validation pipeline.

### Add FluentValidation for the important commands

- `CreateProject`
- `UpdateProject`
- `CreateTask`
- `UpdateTask`
- `CreateComment`

### Implement consistent API errors using

- `Result<T>`
- `ProblemDetails`
- Global Exception Handling

### Handle

| Status Code | Meaning |
|---|---|
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 500 | Internal Server Error |

### Deliverable

The API has consistent validation and error handling.
