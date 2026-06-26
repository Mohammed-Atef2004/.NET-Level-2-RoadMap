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