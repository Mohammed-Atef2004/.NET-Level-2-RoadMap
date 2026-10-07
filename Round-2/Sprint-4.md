# Sprint 4 — Production Engineering

> Project: **TeamFlow — Project & Team Operations Platform**
> Duration: **2 weeks (~15 hours/week)**
> Evaluation: **100 points**

## Sprint Goal

Introduce observability, background processing, and caching without turning the sprint into a DevOps/distributed-systems curriculum.
## How to use this sprint plan

For every task:

1. Read the **MUST** resources before implementation.
2. Read **DEEP DIVE** only when the concept is unclear or the learner wants deeper understanding.
3. Implement the requested TeamFlow change.
4. Verify the behavior manually.
5. Add/update tests when the task naturally requires them.
6. Commit the work in small, meaningful commits.
7. Be able to explain the architectural decision during review.

**Important:** This document does not change the original Sprint scope. It expands the original tasks into an executable checklist.

## Sprint Tasks

### Task 1 — Structured Logging

Add useful structured logs around important workflows.

Do not log everything blindly. Include useful identifiers/context and avoid sensitive data.

### Resources
- **MUST** — [ASP.NET Core logging](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/logging/)

---

### Task 2 — Correlation ID

Implement request correlation and make the correlation information available to application logs.

### Resources
- **MUST** — [ASP.NET Core logging](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/logging/)

---

### Task 3 — Notification Model

Create the notification model and application workflow.

Examples:
- Task Assigned
- Task Completed

### Resources
- **MUST** — [ASP.NET Core hosted services](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services)

---

### Task 4 — Background Queue

Create a simple in-process background queue.

Use a bounded/asynchronous queue approach where appropriate. No message broker is required.

### Resources
- **MUST** — [Microsoft — Background tasks with hosted services](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services)
- **DEEP DIVE** — [System.Threading.Channels](https://learn.microsoft.com/en-us/dotnet/api/system.threading.channels)

---

### Task 5 — Background Worker

Process notification work outside the HTTP request using a hosted/background service.

### Resources
- **MUST** — [Microsoft — BackgroundService/hosted services](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services)

---

### Task 6 — Cancellation

Handle cancellation and application shutdown correctly.

### Resources
- **MUST** — [Microsoft — Cancellation in managed threads](https://learn.microsoft.com/en-us/dotnet/standard/threading/cancellation-in-managed-threads)
- **MUST** — [Microsoft — Hosted services](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services)

---

### Task 7 — Redis Integration

Introduce Redis for one justified use case.

### Resources
- **MUST** — [ASP.NET Core distributed caching](https://learn.microsoft.com/en-us/aspnet/core/performance/caching/distributed)
- **MUST** — [Redis documentation](https://redis.io/docs/latest/)

---

### Task 8 — Cache-Aside

Implement:
```text
Cache Hit
Cache Miss
Database
Cache Population
```

### Resources
- **MUST** — [ASP.NET Core distributed caching](https://learn.microsoft.com/en-us/aspnet/core/performance/caching/distributed)
- **MUST** — [Redis caching docs](https://redis.io/docs/latest/develop/use/patterns/cache-aside/)

---

### Task 9 — Cache Invalidation

Ensure relevant write operations invalidate or update affected cached data.

### Resources
- **MUST** — [ASP.NET Core distributed caching](https://learn.microsoft.com/en-us/aspnet/core/performance/caching/distributed)
- **DEEP DIVE** — [Martin Kleppmann — Designing Data-Intensive Applications](Book)

---

### Task 10 — Production Scenario

Document one failure scenario:
```text
Scenario
 ↓
Failure
 ↓
Impact
 ↓
Detection
 ↓
Handling
 ↓
Recovery
```

### Resources
- **DEEP DIVE** — Michael Nygard — Release It! — `Book: Release It! Design and Deploy Production-Ready Software`

---

## Sprint Deliverables

- [ ] Structured logging
- [ ] Correlation ID
- [ ] Notification system
- [ ] Background queue
- [ ] Background worker
- [ ] Cancellation/shutdown handling
- [ ] Redis
- [ ] Cache-aside
- [ ] Cache invalidation
- [ ] Production failure scenario

## Definition of Done

- [ ] Logging useful
- [ ] Correlation works
- [ ] Notification model exists
- [ ] Background queue works
- [ ] Worker works
- [ ] Cancellation handled
- [ ] Redis integrated
- [ ] Cache-aside works
- [ ] Invalidation works
- [ ] Failure scenario documented

## Review Rule

The learner should be able to explain not only **what** was implemented, but **why it belongs there, what alternatives existed, and what trade-off was accepted**.