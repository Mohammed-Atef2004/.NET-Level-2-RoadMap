# Sprint 2 — Application Architecture, CQRS, MediatR & Security

> Project: **TeamFlow — Project & Team Operations Platform**
> Duration: **2 weeks (~15 hours/week)**
> Evaluation: **100 points**

## Sprint Goal

Transform TeamFlow from a basic API into a use-case-oriented application and implement authentication/authorization.
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

### Task 1 — CQRS Conversion

Convert important existing features to:
```text
Command
Query
Handler
DTO
Validator
```
Keep CQRS as an organizational pattern; do not introduce distributed CQRS complexity.

### Resources
- **MUST** — [Microsoft — DDD/CQRS architecture guidance](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)
- **DEEP DIVE** — [Martin Fowler — CQRS](https://martinfowler.com/bliki/CQRS.html)

---

### Task 2 — MediatR

Introduce MediatR for application use cases.

Required:
- Requests/handlers
- Appropriate notifications
- Pipeline behaviors
- Clear dependency flow

### Resources
- **MUST** — [MediatR — GitHub](https://github.com/jbogard/MediatR)
- **DEEP DIVE** — [Martin Fowler — Mediator](https://martinfowler.com/eaaDev/Mediator.html)

---

### Task 3 — Validation Pipeline

Implement automatic validation through a MediatR pipeline behavior.

Separate:
- Input validation
- Business rules

### Resources
- **MUST** — [FluentValidation documentation](https://docs.fluentvalidation.net/)
- **MUST** — [MediatR — GitHub](https://github.com/jbogard/MediatR)

---

### Task 4 — Result Pattern

Introduce a consistent application result model for:
- Success
- Validation failures
- Business failures
- Not-found/conflict-style application outcomes where appropriate

### Resources
- **MUST** — [ASP.NET Core error handling / ProblemDetails](https://learn.microsoft.com/en-us/aspnet/core/web-api/handle-errors)
- **DEEP DIVE** — [Vladimir Khorikov — Domain model/testing material](https://enterprisecraftsmanship.com/)

---

### Task 5 — Cancellation

Propagate:
```text
HTTP Request
 ↓
Handler
 ↓
Repository / EF Core
```
using `CancellationToken`.

### Resources
- **MUST** — [Microsoft — Cancellation in managed threads](https://learn.microsoft.com/en-us/dotnet/standard/threading/cancellation-in-managed-threads)
- **MUST** — [EF Core async APIs](https://learn.microsoft.com/en-us/ef/core/querying/async)

---

### Task 6 — Identity

Implement:
- User registration
- Authentication
- Password management using ASP.NET Core Identity

### Resources
- **MUST** — [ASP.NET Core Identity](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/identity)
- **MUST** — [ASP.NET Core authentication overview](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/)

---

### Task 7 — JWT

Implement access-token authentication.

Verify:
- issuer
- audience
- signature
- expiration
- claims
- bearer authentication

### Resources
- **MUST** — [Configure JWT bearer authentication](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/configure-jwt-bearer-authentication)
- **MUST** — [JWT bearer authentication](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/configure-jwt-bearer-authentication)

---

### Task 8 — Refresh Tokens

Implement:
- Creation
- Expiration
- Rotation
- Revocation

Document the refresh-token lifecycle.

### Resources
- **MUST** — [ASP.NET Core authentication overview](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/)
- **DEEP DIVE** — [OAuth 2.0 Security Best Current Practice — RFC](https://datatracker.ietf.org/doc/html/rfc9700)

---

### Task 9 — Authorization

Implement project-level authorization:
- Project owner can update project
- Project member can access project
- Unauthorized users cannot access project data

### Resources
- **MUST** — [ASP.NET Core authorization](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/introduction)
- **MUST** — [Resource-based authorization](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/resource-based)

---

### Task 10 — Task Management

Create the initial Task feature using CQRS + MediatR:
- Create task
- Get task
- Update task
- Assign task

### Resources
- **MUST** — [EF Core querying](https://learn.microsoft.com/en-us/ef/core/querying/)
- **MUST** — [MediatR — GitHub](https://github.com/jbogard/MediatR)

---

## Sprint Deliverables

- [ ] CQRS
- [ ] MediatR
- [ ] Validation pipeline
- [ ] Result Pattern
- [ ] Cancellation propagation
- [ ] Authentication
- [ ] JWT
- [ ] Refresh tokens
- [ ] Authorization
- [ ] Task foundation
- [ ] Request-flow explanation

## Definition of Done

- [ ] Important use cases use CQRS
- [ ] MediatR correctly integrated
- [ ] Validation pipeline works
- [ ] Result Pattern consistent
- [ ] Cancellation propagated
- [ ] Registration works
- [ ] Login works
- [ ] JWT works
- [ ] Refresh tokens work
- [ ] Token revocation works
- [ ] Authorization works
- [ ] Task foundation works
- [ ] Learner can explain CQRS/Mediator decisions

## Review Rule

The learner should be able to explain not only **what** was implemented, but **why it belongs there, what alternatives existed, and what trade-off was accepted**.