# 🏃 Sprint 6 — Task Management Advanced Features

**Duration:** 2 Weeks

## 🎯 Sprint Goal

Add practical querying, assignment, background processing, logging, and testing to the existing Task Management system.

- No new business domain.
- No unnecessary infrastructure.

---

## Task 1 — Advanced Task Querying

Extend:

```http
GET /api/v1/tasks
```

### Pagination

- `pageNumber`
- `pageSize`

### Search

Search by:
- Title
- Description

### Filtering

Filter by:
- Status
- Project
- CreatedDate

### Sorting

Support sorting by:
- Title
- CreatedDate
- Status

### Use `IQueryable` and apply in this order

```text
Filter → Search → Sort → Pagination → Projection
```

### Deliverable

A flexible Task listing endpoint.

---

## Task 2 — Task Assignment

Extend the existing Task entity with assignment, for example: `AssignedToUserId`.

### Implement

- Assign Task
- Unassign Task
- Get My Tasks

### Rules

- Only authorized users can assign tasks
- A user cannot assign a task to a non-existing user
- Only the project owner / authorized user can modify assignment
- Users can retrieve their assigned tasks

### Deliverable

A basic workflow:

```text
Project
   ↓
Task
   ↓
Assigned User
```

> This is a natural extension of the existing Task Management domain, not a new feature domain.

---

## Task 3 — Background Task Notifications

Add a very simple background processing mechanism.

### Create

- `INotificationQueue`
- `BackgroundService`

### Use it for a small number of events

- Task Assigned
- Task Completed

### Example flow

```text
Assign Task
     ↓
Queue Notification
     ↓
BackgroundService
     ↓
Process Notification
```

No need for actual external email infrastructure.

### Learning goals

- BackgroundService
- Queues
- Async processing
- Dependency Injection

### Do NOT add

- ❌ RabbitMQ
- ❌ Kafka
- ❌ MassTransit
- ❌ Redis
- ❌ Microservices

---

## Task 4 — Structured Logging

### Configure

- Serilog

### Log (HTTP)

- HTTP Method
- Request Path
- Status Code
- Execution Time
- Exceptions

### Log important business actions

- Project Created
- Task Created
- Task Assigned
- Task Completed
- Comment Added

### Deliverable

Structured application logging across the existing features.

---

## Task 5 — Testing & Documentation

### Unit Tests

Focus on actual business rules.

| Area | Test |
|---|---|
| **Task** | Valid Status Transition |
| **Task** | Invalid Status Transition |
| **Project** | Cannot create Task for invalid Project |
| **Comment** | Cannot add Comment to invalid Task |
| **Assignment** | Cannot assign to non-existing User |

### Integration Tests

Test the main workflow:

```text
Register
   ↓
Login
   ↓
Create Project
   ↓
Create Task
   ↓
Assign Task
   ↓
Complete Task
   ↓
Add Comment
```

> You don't need integration tests for every endpoint.

### Swagger & API Documentation

**Document:**
- Endpoints
- Request models
- Response models
- Status codes
- JWT Authentication

**Routes:**
- `/api/v1/projects`
- `/api/v1/tasks`
- `/api/v1/comments`
