# Sprint 1 — Domain Modeling, Clean Architecture & Persistence

> Project: **TeamFlow — Project & Team Operations Platform**
> Duration: **2 weeks (~15 hours/week)**
> Evaluation: **100 points**

## Sprint Goal

Build the architectural and persistence foundation of TeamFlow.
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

### Task 1 — Domain Model

Create a domain model containing:
- Entities
- Important relationships
- Business responsibilities
- Important invariants
- Value Objects where appropriate

**Required output**
- Domain model diagram
- Entity/relationship explanation
- Written list of important invariants
- Explanation of why each behavior belongs where it does

### Resources
- **MUST** — [Microsoft — Common web application architectures](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures)
- **MUST** — [Microsoft — DDD and CQRS architecture guidance](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)
- **DEEP DIVE** — Eric Evans — Domain-Driven Design — `Book: Domain-Driven Design: Tackling Complexity in the Heart of Software`
- **DEEP DIVE** — Vaughn Vernon — Implementing Domain-Driven Design — `Book: Implementing Domain-Driven Design`

---

### Task 2 — Architecture

Create:
```text
Domain
Application
Infrastructure
API
```

Configure dependency direction correctly.

**Required output**
- Four projects/layers
- Correct project references
- DI/composition root
- Architecture diagram
- Short explanation of dependency direction

### Resources
- **MUST** — [Microsoft — Clean Architecture with ASP.NET Core](https://learn.microsoft.com/en-us/shows/dotnetconf-2022/clean-architecture-with-aspnet-core-7)
- **MUST** — [Microsoft — Common web application architectures](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures)
- **DEEP DIVE** — Robert C. Martin — Clean Architecture — `Book: Clean Architecture`
- **DEEP DIVE** — [Mark Seemann — Dependency Injection Principles, Practices, and Patterns](Book)

---

### Task 3 — Repository Abstractions

Create repository abstractions only where they provide meaningful value.

Implement them inside Infrastructure.

**Required output**
- Abstractions in the appropriate inner layer
- Implementations in Infrastructure
- No unnecessary generic repository
- Written explanation of repository vs DbContext

### Resources
- **MUST** — [Microsoft — EF Core documentation](https://learn.microsoft.com/en-us/ef/core/)
- **DEEP DIVE** — [Vaughn Vernon — Implementing Domain-Driven Design](Book)
- **DEEP DIVE** — [Mark Seemann — Dependency Injection Principles, Practices, and Patterns](Book)

---

### Task 4 — EF Core Persistence

Configure:
- Relationships
- Foreign keys
- Required fields
- Constraints
- Important indexes
- Migrations

**Required output**
- DbContext
- Fluent configurations
- SQL Server connection
- Initial migration
- Correct FK/unique constraints
- Justification for important indexes

### Resources
- **MUST** — [Microsoft — EF Core](https://learn.microsoft.com/en-us/ef/core/)
- **MUST** — [EF Core — Relationships](https://learn.microsoft.com/en-us/ef/core/modeling/relationships)
- **MUST** — [EF Core — Indexes](https://learn.microsoft.com/en-us/ef/core/modeling/indexes)
- **MUST** — [EF Core — Migrations](https://learn.microsoft.com/en-us/ef/core/managing-schemas/migrations/)

---

### Task 5 — Organization Feature

Implement:
- Create organization
- Get organization
- Update organization

**Required output**
- API endpoints
- Application use cases
- Persistence
- Validation appropriate to the feature

### Resources
- **MUST** — [ASP.NET Core fundamentals](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/)
- **MUST** — [OpenAPI/Swagger in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/tutorials/web-api-help-pages-using-swagger)

---

### Task 6 — Team Feature

Implement:
- Create team
- Add member
- Remove member
- Get members

Enforce the domain relationships and membership invariants.

### Resources
- **MUST** — [EF Core relationships](https://learn.microsoft.com/en-us/ef/core/modeling/relationships)

---

### Task 7 — Project Feature

Implement:
- Create project
- Get project
- Update project
- Archive project

Keep the project behavior consistent with the domain model.

### Resources
- **MUST** — [ASP.NET Core Web API fundamentals](https://learn.microsoft.com/en-us/aspnet/core/web-api/)

---

### Task 8 — Project Membership

Implement:
- Add member
- Remove member
- List members

Prevent invalid/duplicate membership according to the domain rules.

### Resources
- **MUST** — [EF Core relationships](https://learn.microsoft.com/en-us/ef/core/modeling/relationships)
- **MUST** — [EF Core indexes](https://learn.microsoft.com/en-us/ef/core/modeling/indexes)

---

### Task 9 — API Documentation

Configure Swagger/OpenAPI.

**Required output**
- Documented endpoints
- Request/response schemas
- Useful endpoint descriptions
- Authentication documentation if authentication exists at this stage

### Resources
- **MUST** — [Microsoft — Swagger/OpenAPI in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/tutorials/web-api-help-pages-using-swagger)

---

## Sprint Deliverables

- [ ] Domain model
- [ ] Architecture diagram
- [ ] TeamFlow solution
- [ ] SQL Server + EF Core persistence
- [ ] Organization
- [ ] Team
- [ ] Project
- [ ] Project Membership
- [ ] Swagger/OpenAPI
- [ ] Architecture explanation

## Definition of Done

- [ ] Domain model documented
- [ ] Architecture separated
- [ ] Dependency direction correct
- [ ] Repository abstractions meaningful
- [ ] EF Core persistence works
- [ ] Migrations work
- [ ] Organization works
- [ ] Team works
- [ ] Project works
- [ ] Project membership works
- [ ] Swagger configured
- [ ] Learner can explain architecture decisions

## Review Rule

The learner should be able to explain not only **what** was implemented, but **why it belongs there, what alternatives existed, and what trade-off was accepted**.