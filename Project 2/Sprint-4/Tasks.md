# Sprint 4 — Clean Architecture & CQRS

> Duration: Weeks 7–8

## 🎯 Sprint Goal

Move from traditional N-Tier Architecture to a modern Clean Architecture and implement the CQRS pattern using MediatR.

By the end of this sprint, the API should have a clean separation of concerns, feature-based organization, and all requests handled through MediatR.

---

# Task 1 — Clean Architecture Setup

## Objective

Create a new API solution using Clean Architecture principles.

---

## Requirements

### Create Solution Structure

Create the following projects:

- Domain
- Application
- Infrastructure
- API

Configure project references correctly.

---

### Domain Layer

Create the core business entities.

Examples:

- Task
- Project
- Comment

Also create a shared:

- BaseEntity

Include common properties:

- Id
- CreatedAt
- UpdatedAt

The Domain project should not reference any external packages.

---

### Application Layer

Create:

- DTOs
- Interfaces
- Contracts

Examples:

- ITaskRepository
- IProjectRepository
- IUnitOfWork

Create folders for:

- Features
- Behaviors
- Common
- Interfaces

---

### Infrastructure Layer

Implement:

- AppDbContext
- Repository Pattern
- Unit of Work

Register all services inside a single:

- DependencyInjection.cs

The API project should never instantiate Infrastructure classes directly.

---

### API Layer

Configure:

- Dependency Injection
- Controllers
- Swagger
- Database Connection

Verify the application builds successfully.

---

## Concepts

- Clean Architecture
- Dependency Rule
- Dependency Injection
- Layer Separation

---

## Deliverable

A fully configured Clean Architecture solution with four independent layers.

## 📚 Resources — Task 1

- **[Clean Architecture in .NET — Complete Guide (Milan Jovanović)](https://milanjovanovic.tech/blog/clean-architecture-dotnet)** — the dependency rule, why four layers, and when Clean Architecture is (and isn't) worth it.
- **[Free Clean Architecture Template for .NET (Milan Jovanović)](https://milanjovanovic.tech/templates/clean-architecture)** — a real, downloadable reference solution with the exact layer split this task asks for (Domain has zero dependencies, architecture tests enforce the rule).
- **[Clean Architecture Solution Template — Ardalis / Steve Smith (GitHub)](https://github.com/ardalis/CleanArchitecture)** — the most widely used open-source starting template for this exact structure; good to compare folder layouts against.
- **[Clean Architecture with ASP.NET Core 7 — .NET Conf session, Steve Smith (Microsoft Learn)](https://learn.microsoft.com/en-us/shows/dotnetconf-2022/clean-architecture-with-aspnet-core-7)** — official Microsoft-hosted talk covering the same four-layer setup end to end.
- **[eShopOnWeb reference app (Microsoft, GitHub)](https://github.com/dotnet-architecture/eShopOnWeb)** — a full, Microsoft-maintained sample showing DependencyInjection.cs-style service registration per layer.

---

# Task 2 — Feature-Based Folder Structure

## Objective

Organize the Application layer using Feature-Based Architecture.

---

## Requirements

Instead of grouping files by type, organize them by feature.

Example:

Features/

- Tasks
    - Commands
    - Queries
    - DTOs
    - Validators

- Projects
    - Commands
    - Queries
    - DTOs
    - Validators

Each feature should contain everything related to it.

Avoid large generic folders like:

- Services
- Helpers
- Managers

---

### Benefits

Students should understand why Feature-Based Architecture:

- Improves maintainability
- Reduces coupling
- Makes navigation easier
- Scales much better for large systems

---

## Concepts

- Vertical Slice Architecture
- Feature-Based Structure
- High Cohesion

---

## Deliverable

A clean and scalable project structure organized by features.

## 📚 Resources — Task 2

- **[Vertical Slice Architecture — Jimmy Bogard](https://www.jimmybogard.com/vertical-slice-architecture/)** — the original article, by the creator of MediatR, that coined this pattern ("minimize coupling between slices, maximize coupling in a slice").
- **[Vertical Slice Architecture — Jimmy Bogard, NDC talk (YouTube)](https://www.youtube.com/watch?v=oAoaMlS1PWo)** — a full conference talk walking through why and how, including where CQRS fits in.
- **[My thoughts on Vertical Slices, CQRS, and other fancy words (Oskar Dudycz)](https://www.architecture-weekly.com/p/my-thoughts-on-vertical-slices-cqrs)** — a practical, opinionated breakdown of feature-folder organization vs. traditional layer-by-type folders.

---

# Task 3 — CQRS with MediatR

## Objective

Separate read operations from write operations using CQRS.

---

## Requirements

### Install MediatR

Configure MediatR inside the Application layer.

Register it inside Dependency Injection.

---

### Commands

Create commands for:

- Create Task
- Update Task
- Delete Task
- Create Project

Each command should contain:

- Command
- Handler

---

### Queries

Create queries for:

- Get Tasks
- Get Task By Id
- Get Projects

Queries should never modify data.

---

### Controllers

Controllers should never access repositories directly.

Each endpoint should simply:

- Receive Request
- Send Request to MediatR
- Return Response

---

### DTO Mapping

Return DTOs instead of entities.

Never expose EF Core entities directly.

---

## Concepts

- CQRS
- IRequest
- IRequestHandler
- Commands
- Queries
- MediatR

---

## Deliverable

Every API endpoint communicates through MediatR and follows the CQRS pattern.

## 📚 Resources — Task 3

- **[MediatR (jbogard, GitHub)](https://github.com/jbogard/MediatR)** — the official source repo. Read the README before installing: as of 2025, MediatR moved to a commercial license for new major versions past a free-tier version cap, so check current licensing terms before adding it to a student project.
- **[CQRS with MediatR in ASP.NET Core — Complete Guide (codewithmukesh)](https://codewithmukesh.com/blog/cqrs-and-mediatr-in-aspnet-core/)** — up-to-date, hands-on walkthrough of exactly this task: commands, queries, and controllers that only talk to `IMediator`.
- **[Implementing Clean Architecture in ASP.NET Core with MediatR and CQRS (Atal Upadhyay)](https://atalupadhyay.wordpress.com/2025/03/31/2486/)** — step-by-step refactor of a traditional controller into `IRequest`/`IRequestHandler` pairs.
- **[Pragmatic Clean Architecture course (Milan Jovanović)](https://milanjovanovic.tech/pragmatic-clean-architecture)** — paid course, but the linked page has enough free detail on the CQRS/DTO-mapping approach to be useful context even without buying it.

> Note for the instructor: because MediatR's licensing changed, it may be worth mentioning [Nick Chapsas' "Build Your Own MediatR"](https://www.youtube.com/@nickchapsas) style lightweight in-process mediator as an optional alternative for students who want to avoid the dependency entirely.

---

# Task 4 — Pipeline Behaviors

## Objective

Implement cross-cutting concerns using MediatR Pipeline Behaviors.

---

## Requirements

Create:

### Logging Behavior

Log:

- Request Name
- Execution Time

---

### Validation Behavior

Automatically execute validators before handlers.

If validation fails:

- Stop execution
- Return validation errors

Handlers should never contain validation logic.

---

Register behaviors in the correct order.

---

## Concepts

- Middleware vs Pipeline Behavior
- Cross-Cutting Concerns
- Open Generic Registration

---

## Deliverable

A centralized pipeline that handles logging and validation automatically.

## 📚 Resources — Task 4

- **[Validation using MediatR's Pipeline Behaviors and FluentValidation — Nick Chapsas (YouTube)](https://www.youtube.com/watch?v=2JzQuIvxIqk)** — the classic, widely-referenced walkthrough of building exactly this validation behavior with FluentValidation.
- **[Validation with MediatR Pipeline Behavior and FluentValidation in .NET 10 (codewithmukesh)](https://codewithmukesh.com/blog/validation-with-mediatr-pipeline-behavior-and-fluentvalidation/)** — a current (2026) version of the same pattern, paired with `IExceptionHandler` for clean Problem Details responses.
- **[MediatR Pipeline Behavior — TheCodeMan](https://thecodeman.net/posts/mediatr-pipeline-behavior)** — short, focused article on `IPipelineBehavior<TRequest, TResponse>`, including the logging-behavior use case and correct DI registration/order.
- **[MediatR Behaviors — Derek Comartin (CodeOpinion)](https://codeopinion.com/mediatr-behaviors/)** — explains `IPipelineBehavior<TRequest, TResponse>`, how it compares to ASP.NET Core middleware, and how to register behaviors.
- **[Why use MediatR? 3 reasons why and 1 reason not — Derek Comartin (CodeOpinion)](https://codeopinion.com/why-use-mediatr-3-reasons-why-and-1-reason-not/)** — good balanced framing for students on when pipeline behaviors genuinely help vs. add ceremony.

---

# Sprint Deliverables

Students should have completed:

- ✅ Clean Architecture
- ✅ Dependency Injection
- ✅ Feature-Based Structure
- ✅ CQRS
- ✅ MediatR
- ✅ Commands & Queries
- ✅ DTO-based Responses
- ✅ Pipeline Behaviors

The project now follows a modern enterprise architecture used in professional .NET applications.
