# Sprint 3 — Business Rules & API Engineering

> Project: **TeamFlow — Project & Team Operations Platform**
> Duration: **2 weeks (~15 hours/week)**
> Evaluation: **100 points**

## Sprint Goal

Move TeamFlow beyond basic CRUD by enforcing business behavior and predictable API behavior.
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

### Task 1 — Business Rules

Identify important TeamFlow business rules.

Examples:
- A member cannot be added twice.
- A user cannot be assigned a task if they are not a project member.
- Only authorized users can modify a project.
- An archived project cannot be modified.

**Required output:** a rule catalog stating the rule, where it is enforced, and why.

### Resources
- **MUST** — [Microsoft — DDD/CQRS architecture guidance](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)
- **DEEP DIVE** — [Vladimir Khorikov — Domain model articles](https://enterprisecraftsmanship.com/)

---

### Task 2 — Business Rule Enforcement

Implement the identified rules in appropriate layers.

For every rule document:
- Rule
- Enforcement point
- Failure behavior
- Why that layer owns it

### Resources
- **MUST** — [Microsoft — DDD/CQRS architecture guidance](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)

---

### Task 3 — Task Completion

Implement task completion with the appropriate business rules.

### Resources
- **MUST** — [Microsoft — EF Core change tracking](https://learn.microsoft.com/en-us/ef/core/change-tracking/)

---

### Task 4 — Task Reopening

Implement task reopening with explicit state/business behavior.

### Resources
- **MUST** — [Microsoft — EF Core change tracking](https://learn.microsoft.com/en-us/ef/core/change-tracking/)

---

### Task 5 — Task Assignment Rules

Ensure users can only be assigned tasks when they satisfy the required project rules.

### Resources
- **MUST** — [ASP.NET Core resource-based authorization](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/resource-based)
- **MUST** — [EF Core relationships](https://learn.microsoft.com/en-us/ef/core/modeling/relationships)

---

### Task 6 — Pagination

Implement reusable pagination for an appropriate read endpoint.

Verify deterministic ordering and reasonable page-size limits.

### Resources
- **MUST** — [EF Core — Efficient querying](https://learn.microsoft.com/en-us/ef/core/performance/efficient-querying)

---

### Task 7 — Filtering

Implement useful filtering for TeamFlow task/project reads.

### Resources
- **MUST** — [EF Core — Efficient querying](https://learn.microsoft.com/en-us/ef/core/performance/efficient-querying)

---

### Task 8 — Sorting

Implement controlled sorting. Do not allow arbitrary SQL/order fragments from user input.

### Resources
- **MUST** — [EF Core — Efficient querying](https://learn.microsoft.com/en-us/ef/core/performance/efficient-querying)

---

### Task 9 — Searching

Implement basic database-backed searching.

### Resources
- **MUST** — [EF Core — Efficient querying](https://learn.microsoft.com/en-us/ef/core/performance/efficient-querying)

---

### Task 10 — ProblemDetails

Implement a consistent API error contract.

### Resources
- **MUST** — [ASP.NET Core — Handle errors in ASP.NET Core APIs](https://learn.microsoft.com/en-us/aspnet/core/web-api/handle-errors)

---

### Task 11 — Global Exception Handling

Handle unexpected exceptions consistently without exposing sensitive implementation details.

### Resources
- **MUST** — [ASP.NET Core — Handle errors](https://learn.microsoft.com/en-us/aspnet/core/web-api/handle-errors)

---

### Task 12 — Idempotency

Implement idempotency for one suitable operation.

Document:
- Why duplicates are dangerous
- Idempotency key
- Storage
- Replay behavior
- Expiration/cleanup strategy

### Resources
- **MUST** — [Stripe — Idempotent requests](https://docs.stripe.com/api/idempotent_requests)
- **DEEP DIVE** — [RFC 9110 — HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110)

---

## Sprint Deliverables

- [ ] Business rules
- [ ] Task management improvements
- [ ] Pagination
- [ ] Filtering
- [ ] Sorting
- [ ] Searching
- [ ] ProblemDetails
- [ ] Global exception handling
- [ ] One idempotent operation
- [ ] Rule-placement explanation

## Definition of Done

- [ ] Important rules enforced
- [ ] Task completion works
- [ ] Task reopening works
- [ ] Assignment rules work
- [ ] Pagination works
- [ ] Filtering works
- [ ] Sorting works
- [ ] Searching works
- [ ] ProblemDetails consistent
- [ ] Global exceptions handled
- [ ] One operation idempotent
- [ ] Learner can explain rule placement

## Review Rule

The learner should be able to explain not only **what** was implemented, but **why it belongs there, what alternatives existed, and what trade-off was accepted**.