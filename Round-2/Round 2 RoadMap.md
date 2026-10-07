# Tawjeh Level 2 — Advanced .NET Backend

# Sprint Specifications

> **Project:** TeamFlow — Project & Team Operations Platform
> **Duration:** 6 Sprints × 2 Weeks
> **Expected Commitment:** ~15 Hours / Week
> **Total Commitment:** ~180 Hours
> **Evaluation:** 100 Points / Sprint
> **Total:** 600 Points

---

# 🎯 Level 2 Goal

The goal of Level 2 is not to teach as many technologies as possible.

The goal is to teach the learner how to take a non-trivial backend requirement and progressively turn it into a maintainable, secure, testable, production-ready backend system.

The learner should practice:

```text
Understand
    ↓
Model
    ↓
Design
    ↓
Implement
    ↓
Debug
    ↓
Refactor
    ↓
Test
    ↓
Deploy
    ↓
Explain
```

The project evolves throughout the six sprints.

The learner should **not** build six disconnected mini-projects.

---

# 🏗️ TeamFlow

TeamFlow is a project and team operations platform.

The system allows organizations to:

* Create teams
* Manage team members
* Create projects
* Manage project members
* Create and manage tasks
* Assign tasks
* Track task completion
* Organize project work
* Receive notifications
* Use an AI assistant
* Purchase a paid capability

The system will gradually evolve from a basic backend into a production-oriented application.

---

# 📅 Sprint 1 — Domain Modeling, Clean Architecture & Persistence

## 🎯 Sprint Goal

Build the architectural and persistence foundation of TeamFlow.

The learner should be able to move from:

```text
Domain Model
    ↓
Business Rules
    ↓
Architecture
    ↓
Persistence
    ↓
Working API
```

The focus is **practical domain modeling and architecture**, not learning DDD as a separate subject.

---

# 📚 What You Will Learn

## 1. Domain Modeling

Learn:

* Entities
* Relationships
* Encapsulation
* Business responsibilities
* Invariants
* Value Objects where appropriate
* Domain vs application responsibilities

The learner should understand why a behavior belongs to a particular part of the system.

---

# 2. Clean Architecture

Learn:

* Separation of concerns
* Dependency direction
* Dependency Inversion
* Domain layer
* Application layer
* Infrastructure layer
* API layer
* Dependency Injection

Target structure:

```text
TeamFlow.Domain
        ↑
TeamFlow.Application
        ↑
TeamFlow.Infrastructure
        ↑
TeamFlow.API
```

Infrastructure implements abstractions defined by the inner layers.

---

# 3. Repository Design

Learn:

* Repository abstraction
* Repository responsibilities
* Repository vs DbContext
* Repository vs application service
* When an abstraction is useful
* Avoiding unnecessary generic repositories

Important principle:

> A repository is not simply a wrapper around every DbSet method.

---

# 4. EF Core Persistence

Learn:

* DbContext
* DbSet
* Entity configuration
* Fluent API
* Relationships
* Foreign keys
* Constraints
* Indexes where appropriate
* Migrations
* Basic transaction boundaries

The learner is expected to already understand database fundamentals.

---

# 🛠️ Practical Implementation

## Organization

Implement:

* Create organization
* Get organization
* Update organization

---

## Team

Implement:

* Create team
* Add member
* Remove member
* Get members

---

## Project

Implement:

* Create project
* Get project
* Update project
* Archive project

---

## Project Membership

Implement:

* Add member
* Remove member
* List members

---

# 📝 Sprint Tasks

### Task 1 — Domain Model

Create a domain model containing:

* Entities
* Important relationships
* Business responsibilities
* Important invariants
* Value Objects where appropriate

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

---

### Task 3 — Repository Abstractions

Create repository abstractions only where they provide meaningful value.

Implement them inside Infrastructure.

---

### Task 4 — EF Core Persistence

Configure:

* Relationships
* Foreign keys
* Required fields
* Constraints
* Important indexes
* Migrations

---

### Task 5 — Organization Feature

Implement the Organization use cases.

---

### Task 6 — Team Feature

Implement Team management.

---

### Task 7 — Project Feature

Implement Project management.

---

### Task 8 — Project Membership

Implement membership rules.

---

### Task 9 — API Documentation

Configure Swagger/OpenAPI.

---

# 📦 Sprint Deliverables

The learner must submit:

### 1. Domain Model

Showing:

* Entities
* Relationships
* Responsibilities
* Important invariants

### 2. Architecture Diagram

Showing:

```text
API
 ↓
Application
 ↓
Domain

Infrastructure
```

and the dependency direction.

### 3. TeamFlow Solution

Containing:

* Domain
* Application
* Infrastructure
* API

### 4. Persistence

* SQL Server
* EF Core
* Fluent configurations
* Migrations
* Relationships

### 5. Features

* Organization
* Team
* Project
* Project Membership

### 6. Architecture Explanation

Answer:

> Why does each layer exist?

> Why is this dependency direction used?

> Why are repositories abstracted?

---

# 📊 Evaluation — 100 Points

| Area                                      |  Points |
| ----------------------------------------- | ------: |
| Domain Modeling                            |      20 |
| Clean Architecture & Dependency Direction |      25 |
| Repository Design                         |      15 |
| EF Core Persistence                       |      20 |
| Feature Implementation                    |      15 |
| Documentation & Explanation               |       5 |
| **Total**                                 | **100** |

---

# ✅ Definition of Done

* [ ] Domain model is documented
* [ ] Architecture is correctly separated
* [ ] Dependency direction is correct
* [ ] Repository abstractions are meaningful
* [ ] EF Core persistence works
* [ ] Migrations work
* [ ] Organization feature works
* [ ] Team feature works
* [ ] Project feature works
* [ ] Project membership works
* [ ] Swagger is configured
* [ ] Learner can explain the architecture decisions

---

# 🎓 Expected Outcome

By the end of Sprint 1, the learner should be able to take a business requirement and turn it into a structured backend foundation without immediately starting from database tables or controllers.

---

# 📅 Sprint 2 — Application Architecture, CQRS, MediatR & Security

## 🎯 Sprint Goal

Transform TeamFlow from a basic API into a **use-case-oriented application**.

The learner should understand:

```text
HTTP Request
    ↓
Application Use Case
    ↓
Command / Query
    ↓
Handler
    ↓
Domain
    ↓
Infrastructure
```

and implement authentication and authorization.

---

# 📚 What You Will Learn

## 1. Application Architecture

Learn:

* Application use cases
* Commands
* Queries
* DTOs
* Request/response models
* Separation between API and Application

---

# 2. CQRS

Learn:

* Command
* Query
* Command Handler
* Query Handler
* Read vs write responsibilities
* Why CQRS can improve application organization
* When CQRS adds unnecessary complexity

The learner should understand CQRS as an organizational pattern, not as a requirement for distributed systems.

---

# 3. MediatR

Learn:

* Mediator pattern
* Request/Handler
* Notifications where appropriate
* Pipeline behaviors
* Dependency flow

---

# 4. Validation

Learn:

* FluentValidation
* Input validation
* Validation vs business rules
* Validation pipeline
* Validation behavior

---

# 5. Result Pattern

Learn:

* Success results
* Failure results
* Validation failures
* Business failures
* Consistent application responses

---

# 6. Async Programming

Learn:

* async/await
* Task
* CancellationToken
* Cancellation propagation
* Async EF Core operations

---

# 7. Authentication

Learn:

* ASP.NET Core Identity
* Password management
* JWT
* Claims
* Refresh tokens
* Token expiration
* Token revocation
* Logout

---

# 8. Authorization

Learn:

* Authentication vs authorization
* Claims
* Policies
* Project-level authorization
* Resource authorization

Keep authorization intentionally simple.

Example:

```text
Project Owner
Project Member
```

No unnecessary role hierarchy.

---

# 🛠️ Practical Implementation

# Authentication

Implement:

* Registration
* Login
* Refresh token
* Token revocation
* Logout
* Current user

---

# Authorization

Implement project-level authorization.

Examples:

* Project owner can update project
* Project member can access project
* Unauthorized users cannot access project data

---

# Task Foundation

Implement:

* Create task
* Get task
* Update task
* Assign task

---

# 📝 Sprint Tasks

### Task 1 — CQRS Conversion

Convert important existing features to:

```text
Command
Query
Handler
DTO
Validator
```

---

### Task 2 — MediatR

Introduce MediatR for application use cases.

---

### Task 3 — Validation Pipeline

Implement automatic validation through a MediatR pipeline behavior.

---

### Task 4 — Result Pattern

Introduce a consistent application result model.

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

---

### Task 6 — Identity

Implement user registration and authentication.

---

### Task 7 — JWT

Implement access-token authentication.

---

### Task 8 — Refresh Tokens

Implement:

* Creation
* Expiration
* Rotation
* Revocation

---

### Task 9 — Authorization

Implement project-level authorization.

---

### Task 10 — Task Management

Create the initial Task feature using CQRS + MediatR.

---

# 📦 Sprint Deliverables

The learner must submit:

* CQRS implementation
* MediatR implementation
* Validation pipeline
* Result Pattern
* Cancellation propagation
* Authentication
* JWT
* Refresh Tokens
* Authorization
* Task feature
* Request-flow explanation

The learner should be able to explain:

```text
HTTP Request
     ↓
Controller
     ↓
MediatR
     ↓
Command / Query
     ↓
Handler
     ↓
Application Logic
     ↓
Domain
     ↓
Infrastructure
```

---

# 📊 Evaluation — 100 Points

| Area                        |  Points |
| --------------------------- | ------: |
| Application Architecture    |      15 |
| CQRS Design                 |      20 |
| MediatR Implementation      |      15 |
| Validation & Result Pattern |      10 |
| Async / Cancellation        |      10 |
| Authentication              |      15 |
| Authorization               |      10 |
| Task Feature                |       5 |
| **Total**                   | **100** |

---

# ✅ Definition of Done

* [ ] Important use cases use CQRS
* [ ] MediatR is correctly integrated
* [ ] Validation pipeline works
* [ ] Result Pattern is consistent
* [ ] Cancellation is propagated
* [ ] Registration works
* [ ] Login works
* [ ] JWT works
* [ ] Refresh tokens work
* [ ] Token revocation works
* [ ] Authorization rules work
* [ ] Task foundation works
* [ ] Learner can explain CQRS and Mediator decisions

---

# 🎓 Expected Outcome

The learner should now understand how to structure a non-trivial application around **use cases instead of controllers becoming the center of the application**.

---

# 📅 Sprint 3 — Business Rules & API Engineering

## 🎯 Sprint Goal

Move TeamFlow beyond basic CRUD.

The learner should understand that backend engineering is largely about controlling **business behavior and API behavior**, not simply creating endpoints.

---

# 📚 What You Will Learn

## 1. Practical Business Rules

Learn:

* Business rules
* Invariants
* Encapsulation
* Domain behavior
* Application rules
* Where business rules should be enforced

Examples:

```text
A member cannot be added twice.

A user cannot be assigned a task
if they are not a project member.

Only authorized users can modify a project.

A project cannot be modified
after it has been archived.
```

The focus is practical business modeling.

---

# 2. Task Management

Extend the Task feature with:

* Create
* Update
* Assign
* Complete
* Reopen

The system should enforce appropriate business rules.

---

# 3. Advanced API Querying

Learn:

* Pagination
* Filtering
* Searching
* Sorting
* Query parameters
* Query composition with EF Core

Example:

```text
GET /api/projects/{projectId}/tasks
    ?page=1
    &pageSize=20
    &status=Completed
    &search=authentication
    &sortBy=createdAt
```

---

# 4. API Error Handling

Learn:

* ProblemDetails
* Global exception handling
* Validation errors
* NotFound responses
* Conflict responses
* Unauthorized responses
* Forbidden responses
* Consistent error contracts

---

# 5. Idempotency

Learn:

* Why duplicate requests happen
* Why duplicate operations can be dangerous
* Idempotency keys
* Safe retry behavior

Implement idempotency for **one appropriate operation only**.

---

# 🛠️ Practical Implementation

## Task Management

Implement:

* Complete Task
* Reopen Task
* Assign Task
* Update Task

Enforce relevant business rules.

---

## Search API

Implement:

```text
Pagination
Filtering
Sorting
Searching
```

---

## Error Handling

Implement:

```text
Request
   ↓
Application
   ↓
Business / Validation Error
   ↓
Consistent ProblemDetails Response
```

---

## Idempotency

Choose one operation where duplicate requests could cause a real problem.

Implement safe handling for duplicate requests.

---

# 📝 Sprint Tasks

### Task 1 — Business Rules

Identify important TeamFlow business rules.

---

### Task 2 — Business Rule Enforcement

Implement the rules in appropriate layers.

---

### Task 3 — Task Completion

Implement task completion.

---

### Task 4 — Task Reopening

Implement task reopening.

---

### Task 5 — Task Assignment Rules

Ensure users can only be assigned tasks when they satisfy the required project rules.

---

### Task 6 — Pagination

Implement reusable pagination for an appropriate read endpoint.

---

### Task 7 — Filtering

Implement useful filtering.

---

### Task 8 — Sorting

Implement controlled sorting.

---

### Task 9 — Searching

Implement basic database-backed searching.

---

### Task 10 — ProblemDetails

Implement a consistent API error contract.

---

### Task 11 — Global Exception Handling

Handle unexpected exceptions consistently.

---

### Task 12 — Idempotency

Implement idempotency for one suitable operation.

---

# 📦 Sprint Deliverables

The learner must submit:

* Business rules
* Task management improvements
* Pagination
* Filtering
* Sorting
* Searching
* ProblemDetails
* Global exception handling
* One idempotent operation

Plus a short document answering:

> Which rules were implemented?

> Where were they enforced?

> Why were they placed there?

---

# 📊 Evaluation — 100 Points

| Area                                      |  Points |
| ----------------------------------------- | ------: |
| Business Rules & Modeling                 |      25 |
| Task Management                           |      15 |
| Pagination / Filtering / Sorting / Search |      25 |
| Error Handling & ProblemDetails           |      20 |
| Idempotency                               |      10 |
| Code Quality & Explanation                |       5 |
| **Total**                                 | **100** |

---

# ✅ Definition of Done

* [ ] Important business rules are enforced
* [ ] Task completion works
* [ ] Task reopening works
* [ ] Task assignment rules work
* [ ] Pagination works
* [ ] Filtering works
* [ ] Sorting works
* [ ] Searching works
* [ ] ProblemDetails is consistent
* [ ] Global exceptions are handled
* [ ] One operation is idempotent
* [ ] Learner can explain where business rules belong

---

# 🎓 Expected Outcome

TeamFlow should no longer behave like a simple CRUD application.

The learner should understand how to build APIs that enforce business behavior and provide predictable responses.

---

# 📅 Sprint 4 — Production Engineering

## 🎯 Sprint Goal

Introduce a small number of production-oriented concerns without turning the sprint into a DevOps or distributed-systems curriculum.

The learner will focus on:

```text
Observability
Background Processing
Caching
```

---

# 📚 What You Will Learn

# 1. Logging

Learn:

* ILogger
* Log levels
* Structured logging
* Useful context
* Exception logging
* Logging important workflows

The focus is writing useful logs, not simply adding logs everywhere.

---

# 2. Correlation IDs

Learn:

* What a correlation ID is
* Why request correlation is useful
* How to attach correlation information to logs
* How to trace a request through application logs

Basic flow:

```text
HTTP Request
      ↓
Correlation ID
      ↓
Application
      ↓
Logs
```

---

# 3. Background Processing

Learn:

* BackgroundService
* Hosted Services
* Background queues
* Cancellation
* Graceful shutdown
* When work should leave the HTTP request

---

# 4. Redis Caching

Learn:

* Why caching exists
* Cache-aside pattern
* TTL
* Cache invalidation
* Redis
* Choosing appropriate data to cache

The learner should understand:

> Caching is a trade-off, not automatically an optimization.

---

# 🛠️ Practical Implementation

# Notification System

Create a simple notification workflow.

Examples:

```text
Task Assigned
Task Completed
```

---

# Background Processing

Instead of performing notification work directly inside the HTTP request:

```text
HTTP Request
      ↓
Application
      ↓
Background Queue
      ↓
Background Worker
      ↓
Notification Processing
```

Use:

* BackgroundService
* A simple in-process background queue
* CancellationToken

No message broker is required.

---

# Redis

Choose one read-heavy TeamFlow operation.

Example:

```text
GET Project Summary
```

Implement:

```text
Request
   ↓
Redis
   ↓
Cache Hit → Response

Cache Miss
   ↓
Database
   ↓
Redis
   ↓
Response
```

Implement appropriate invalidation when relevant data changes.

---

# 📝 Sprint Tasks

### Task 1 — Structured Logging

Add useful structured logs around important workflows.

---

### Task 2 — Correlation ID

Implement request correlation.

---

### Task 3 — Notification Model

Create the notification model and application workflow.

---

### Task 4 — Background Queue

Create a simple in-process background queue.

---

### Task 5 — Background Worker

Process notification work outside the HTTP request.

---

### Task 6 — Cancellation

Handle cancellation and application shutdown correctly.

---

### Task 7 — Redis Integration

Introduce Redis for one justified use case.

---

### Task 8 — Cache-Aside

Implement:

```text
Cache Hit
Cache Miss
Database
Cache Population
```

---

### Task 9 — Cache Invalidation

Ensure relevant write operations invalidate or update affected cached data.

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

---

# 📦 Sprint Deliverables

The learner must submit:

* Structured logging
* Correlation ID
* Notification system
* Background queue
* Background worker
* Cancellation/shutdown handling
* Redis integration
* Cache-aside implementation
* Cache invalidation
* One documented production failure scenario

---

# 📊 Evaluation — 100 Points

| Area                        |  Points |
| --------------------------- | ------: |
| Logging & Correlation       |      20 |
| Background Processing       |      35 |
| Redis & Caching             |      30 |
| Failure Handling            |      10 |
| Explanation & Documentation |       5 |
| **Total**                   | **100** |

---

# ❌ Explicitly Out of Scope for Sprint 4

The learner does NOT need to implement:

* Kafka
* RabbitMQ
* MassTransit
* Distributed queues
* OpenTelemetry
* Complex scheduling systems
* Activity feeds
* External HTTP integrations
* Circuit breakers as a separate topic
* Complex distributed caching

---

# 🎓 Expected Outcome

The learner should understand that backend systems do not consist only of:

```text
Request → Controller → Database → Response
```

They should understand basic background processing, logging, caching, cancellation, and production-oriented failure handling.

---

# 📅 Sprint 5 — Testing, AI & Payment Integration

## 🎯 Sprint Goal

Teach the learner how to verify important backend behavior and safely integrate two realistic external systems:

```text
TeamFlow
   ├── AI Assistant
   └── Payment Gateway
```

The focus is not learning AI or payment systems as separate curricula.

The focus is learning how a backend communicates safely with external providers.

---

# 📚 What You Will Learn

# 1. Unit Testing

Learn:

* xUnit
* Arrange / Act / Assert
* Test isolation
* Test naming
* Business-rule testing
* Application use-case testing
* Edge cases
* Mocking dependencies

Do not waste time testing trivial getters/setters.

---

# 2. Integration Testing

Learn:

* What integration testing verifies
* HTTP-level testing
* Real application pipeline
* Test database strategy
* Authentication in integration tests
* Test isolation

Focus on important application flows rather than testing every endpoint.

---

# 3. AI Integration

Learn the backend concerns behind integrating an LLM API:

* HTTP-based AI APIs
* Request/response models
* Prompt construction
* Structured output where useful
* Provider abstraction
* Token/cost awareness
* Rate limits
* Timeout handling
* Prompt injection awareness
* Authorization and data exposure

The learner should NOT build:

* RAG
* Vector databases
* LangChain
* Multi-agent systems
* Fine-tuning

---

# 4. Payment Integration

Learn:

* Payment lifecycle
* Payment intent/order creation
* External payment API
* Payment status
* Checkout flow
* Webhooks
* Signature verification
* Idempotency
* External failure handling

---

# 🛠️ Practical Implementation

# Part A — Unit Testing

Test important business behavior.

Examples:

```text
Assign Task
Complete Task
Reopen Task
Archive Project
Add Member
```

Focus on behavior and edge cases.

---

# Part B — Integration Testing

Create integration tests for a limited number of critical workflows.

Examples:

```text
Register → Login

Create Project

Create Task → Assign Task

Complete Task
```

The goal is to verify the actual application pipeline.

---

# Part C — AI Assistant

Create:

```text
TeamFlow AI Assistant
```

Users can ask questions such as:

```text
Which tasks are overdue?

Which tasks are incomplete?

Summarize the current project status.

What are the most important unfinished tasks?
```

The AI must only receive data that the current user is authorized to access.

---

# AI Request Flow

```text
User
 ↓
API
 ↓
Authorization
 ↓
Application
 ↓
Retrieve allowed project data
 ↓
Build AI request
 ↓
AI Provider
 ↓
Response
```

The AI provider must not receive unrestricted database access.

---

# Part D — Payment

Introduce one paid TeamFlow capability.

Example:

```text
Organization
      ↓
Paid Capability
      ↓
Payment
      ↓
Webhook
      ↓
Update Subscription / Entitlement
```

Implement:

* Create payment
* Track payment status
* Handle successful payment
* Handle failed payment
* Process webhook
* Verify webhook signature
* Prevent duplicate webhook processing

---

# 📝 Sprint Tasks

### Task 1 — Unit Test Strategy

Identify the most important business logic and use cases that require unit tests.

---

### Task 2 — Business Rule Unit Tests

Test:

* Task assignment rules
* Task completion
* Task reopening
* Project membership rules
* Important invalid operations

---

### Task 3 — Application Unit Tests

Test important application use cases.

---

### Task 4 — Integration Test Infrastructure

Create the infrastructure required to run integration tests.

---

### Task 5 — Critical API Integration Tests

Test a small number of important HTTP workflows.

---

### Task 6 — AI Provider Abstraction

Create an abstraction around the AI provider.

Avoid spreading provider-specific implementation across the application.

---

### Task 7 — AI Assistant

Implement project-related AI queries.

---

### Task 8 — AI Authorization

Ensure users cannot ask the AI about project data they cannot access.

---

### Task 9 — AI Failure Handling

Handle:

* Timeout
* Provider failure
* Rate limiting
* Invalid responses

---

### Task 10 — Payment Gateway Integration

Integrate one payment provider.

---

### Task 11 — Payment Status

Track payment status and update the appropriate TeamFlow entitlement.

---

### Task 12 — Payment Webhook

Implement the payment webhook endpoint.

---

### Task 13 — Signature Verification

Verify that webhook notifications are authentic.

---

### Task 14 — Webhook Idempotency

Ensure duplicate webhook delivery cannot process the same event twice.

---

# 📦 Sprint Deliverables

## Testing

* Unit tests
* Important integration tests
* Business-rule coverage
* Application-flow coverage

## AI

* AI provider abstraction
* Project AI assistant
* Authorization
* Timeout handling
* Provider failure handling

## Payment

* Payment integration
* Payment status handling
* Webhook endpoint
* Signature verification
* Idempotent webhook processing

---

# 📊 Evaluation — 100 Points

| Area                        |  Points |
| --------------------------- | ------: |
| Unit Testing                |      25 |
| Integration Testing         |      15 |
| AI Integration              |      20 |
| AI Security & Authorization |      10 |
| Payment Integration         |      20 |
| Webhooks & Idempotency      |      10 |
| **Total**                   | **100** |

---

# ❌ Explicitly Out of Scope for Sprint 5

The learner does NOT need to implement:

* RAG
* Vector databases
* AI agents
* Multi-agent systems
* Fine-tuning
* Multiple AI providers
* Multiple payment providers
* Complex subscription billing
* Advanced payment reconciliation
* Advanced test automation frameworks
* Large-scale test coverage targets

---

# 🎓 Expected Outcome

The learner should understand how to verify backend behavior and integrate external systems where:

```text
Your System
     ↓
External Provider
     ↓
Success
Failure
Timeout
Duplicate Request
Unauthorized Data
```

must all be handled safely.

---

# 📅 Sprint 6 — Docker, CI/CD & Deployment

## 🎯 Sprint Goal

Take TeamFlow from:

> "It works on my machine."

to:

> "It can be built, tested, containerized, and deployed consistently."

The goal is practical deployment knowledge, not a full DevOps curriculum.

---

# 📚 What You Will Learn

# 1. Docker

Learn:

* Images
* Containers
* Dockerfile
* Build
* Run
* Ports
* Environment variables
* Networks
* Docker Compose

---

# 2. Production Configuration

Learn:

* Environment variables
* Connection strings
* JWT configuration
* Redis configuration
* AI API keys
* Payment configuration
* Environment-specific settings

No secrets should be committed to source control.

---

# 3. CI/CD

Learn the practical basics of:

* GitHub Actions
* Workflows
* Jobs
* Steps
* Restore
* Build
* Test
* Docker build
* Deployment

---

# 🚀 Target Pipeline

The learner should build approximately:

```text
Git Push / Pull Request
        ↓
GitHub Actions
        ↓
Restore
        ↓
Build
        ↓
Unit Tests
        ↓
Integration Tests
        ↓
Docker Build
        ↓
Deployment
        ↓
Health Verification
```

---

# 🛠️ Practical Implementation

# Docker

Create a production-oriented Dockerfile.

---

# Docker Compose

Create a local environment containing:

```text
TeamFlow API
SQL Server
Redis
```

---

# Configuration

Move environment-specific values outside the source code.

Examples:

```text
Connection Strings
JWT Configuration
Redis Configuration
AI API Keys
Payment API Keys
```

---

# Secrets

Ensure secrets are not committed to Git.

Use environment configuration or the appropriate CI/CD secret mechanism.

---

# CI Pipeline

Create a GitHub Actions workflow:

```text
Push / Pull Request
        ↓
Restore
        ↓
Build
        ↓
Unit Tests
        ↓
Integration Tests
```

---

# Docker Pipeline

Extend the workflow:

```text
Build
 ↓
Test
 ↓
Docker Build
 ↓
Image
```

---

# Deployment

Deploy TeamFlow to a real hosting environment.

The exact hosting provider is not the primary learning objective.

The learner must understand the deployment process.

---

# 📝 Sprint Tasks

### Task 1 — Dockerfile

Create a production-oriented Dockerfile.

---

### Task 2 — Docker Compose

Create:

```text
API
SQL Server
Redis
```

---

### Task 3 — Environment Configuration

Move environment-specific configuration outside the source code.

---

### Task 4 — Secrets

Ensure secrets are not committed to Git.

---

### Task 5 — Local Production-like Environment

Run TeamFlow through Docker Compose.

---

### Task 6 — GitHub Actions

Create a CI workflow.

---

### Task 7 — Build Validation

The pipeline must fail when the application does not build.

---

### Task 8 — Automated Tests

The pipeline must execute:

* Unit tests
* Integration tests

---

### Task 9 — Docker Build

Build the Docker image through CI.

---

### Task 10 — Deployment

Deploy the application.

---

### Task 11 — Production Verification

Verify:

* API availability
* Database connectivity
* Authentication
* Important endpoints
* Redis
* Background processing
* AI integration
* Payment integration

---

### Task 12 — Final Refactoring

Review:

* Architecture
* Naming
* Dead code
* Unnecessary abstractions
* Error handling
* Business rules
* Configuration
* Logging
* API consistency

---

### Task 13 — Final README

Document:

* Project overview
* Architecture
* Domain
* Authentication
* Authorization
* Data access
* Background processing
* Caching
* AI integration
* Payment integration
* Testing
* Docker
* CI/CD
* Deployment

---

# 📦 Sprint Deliverables

The learner must submit:

* Production Dockerfile
* Docker Compose
* Environment configuration
* Secrets strategy
* GitHub Actions workflow
* Automated build
* Automated tests
* Docker image build
* Deployed API
* Production verification
* Final README
* Final refactoring

---

# 📊 Evaluation — 100 Points

| Area                       |  Points |
| -------------------------- | ------: |
| Dockerfile                 |      25 |
| Docker Compose             |      15 |
| Configuration & Secrets    |      15 |
| GitHub Actions CI/CD       |      25 |
| Deployment                 |      15 |
| Final README & Refactoring |       5 |
| **Total**                  | **100** |

---

# ✅ Definition of Done

* [ ] Dockerfile works
* [ ] Docker Compose works
* [ ] API runs inside Docker
* [ ] SQL Server runs correctly
* [ ] Redis runs correctly
* [ ] Configuration is environment-based
* [ ] Secrets are protected
* [ ] GitHub Actions runs successfully
* [ ] Build is automated
* [ ] Tests are automated
* [ ] Docker image is built automatically
* [ ] Application is deployed
* [ ] Production environment is verified
* [ ] README is complete

---

# 🎓 Expected Outcome

The learner should understand the complete path:

```text
Code
 ↓
Build
 ↓
Test
 ↓
Containerize
 ↓
Automate
 ↓
Deploy
 ↓
Verify
```

and should be able to explain what happens at each stage.

---

# 🏁 Final Level Completion

A learner completes Level 2 when all six sprints are completed and TeamFlow contains:

```text
Domain Modeling
        ↓
Clean Architecture
        ↓
Repository Abstractions
        ↓
EF Core Persistence
        ↓
CQRS
        ↓
MediatR
        ↓
Validation
        ↓
Authentication
        ↓
Authorization
        ↓
Business Rules
        ↓
Advanced API Engineering
        ↓
Background Processing
        ↓
Redis / Caching
        ↓
Unit Testing
        ↓
Integration Testing
        ↓
AI Integration
        ↓
Payment Integration
        ↓
Docker
        ↓
GitHub Actions
        ↓
CI/CD
        ↓
Deployment
```

---

# 📊 Final Evaluation

| Sprint    | Focus                                     |  Points |
| --------- | ----------------------------------------- | ------: |
| Sprint 1  | Domain, Architecture & Persistence        |     100 |
| Sprint 2  | CQRS, Application Architecture & Security |     100 |
| Sprint 3  | Business Rules & API Engineering          |     100 |
| Sprint 4  | Production Engineering                    |     100 |
| Sprint 5  | Testing, AI & Payment                     |     100 |
| Sprint 6  | Docker, CI/CD & Deployment                |     100 |
| **TOTAL** |                                           | **600** |

---

# 🎯 Final Project Review

At the end of Level 2, the learner must be able to explain:

## 1. Domain

What does TeamFlow represent?

What are the important entities and business rules?

---

## 1. Architecture

Why is the solution structured this way?

Why does each layer exist?

---

## 1. Repository

Why is a repository abstraction used?

Where would a repository abstraction become unnecessary?

---

## 1. Application

Why are commands and queries separated?

Where does application logic belong?

---

## 1. MediatR

What problem does the Mediator pattern solve?

What complexity does it introduce?

---

## 1. Business Rules

Where are important business rules enforced?

Why are they enforced there?

---

## 1. Security

How are authentication and authorization handled?

What is the difference between authentication and authorization?

---

## 1. API

How does the API handle:

* Validation?
* Errors?
* Pagination?
* Filtering?
* Searching?
* Sorting?
* Duplicate requests?

---

## 1. Background Processing

Why should some work happen outside the HTTP request?

What happens if the background worker is cancelled?

---

## 1. Caching

Why is this data cached?

What is the cache invalidation strategy?

What happens when Redis is unavailable?

---

## 1. AI

How is AI access isolated?

How do you ensure the AI only receives authorized project information?

What happens when the provider fails?

---

## 1. Payment

How does the payment lifecycle work?

How are webhooks verified?

How are duplicate webhooks handled?

---

## 1. Testing

What behavior is covered by unit tests?

What application flows are covered by integration tests?

Why were these cases selected?

---

## 1. Deployment

How does TeamFlow move from source code to a running environment?

```text
Source Code
 ↓
CI
 ↓
Build
 ↓
Tests
 ↓
Docker
 ↓
Deployment
 ↓
Verification
```

---

## 1. Trade-offs

For important architectural decisions, the learner should be able to explain:

```text
Problem
   ↓
Possible Solutions
   ↓
Chosen Solution
   ↓
Why?
   ↓
Trade-offs
```

The learner should not be rewarded for choosing the most sophisticated technology.

The learner should be rewarded for choosing a solution that is:

* Appropriate
* Understandable
* Maintainable
* Justified
* Consistent with the project's requirements

---

# 🧠 Engineering Practice Throughout All Sprints

These are not separate lessons.

They are part of how the learner is evaluated throughout the project.

---

# 1. Debugging

Use:

```text
Symptom
 ↓
Observation
 ↓
Hypothesis
 ↓
Experiment
 ↓
Evidence
 ↓
Root Cause
 ↓
Fix
 ↓
Prevention
```

The learner should avoid:

> "Change random code until it works."

---

# 2. Architecture Decisions

Before introducing an abstraction:

```text
What problem are we solving?

Why is the current solution insufficient?

What alternatives exist?

What complexity does this introduce?

Is the abstraction actually necessary?
```

---

# 3. Performance

Use:

```text
Measure
 ↓
Find Bottleneck
 ↓
Understand Root Cause
 ↓
Optimize
 ↓
Measure Again
```

Performance optimization should be evidence-driven.

---

# 4. Code Review

Throughout the project, review:

* Naming
* Responsibility boundaries
* Duplication
* Abstractions
* Error handling
* Security
* Query efficiency
* Maintainability
* Testability

---

# 🚫 Explicitly Out of Scope

The following are NOT mandatory for Level 2:

* Microservices
* Kubernetes
* Terraform
* Kafka
* RabbitMQ
* MassTransit
* GraphQL
* MongoDB
* PostgreSQL
* Elasticsearch
* RAG
* Vector databases
* Multi-agent systems
* Fine-tuning
* Advanced cloud architecture
* Dedicated system design curriculum
* Large DevOps curriculum
* OpenTelemetry
* Advanced distributed systems
* Complex event-driven architecture
* Complex task dependency graphs
* Circular dependency detection
* Advanced payment systems
* Multiple AI providers
* Multiple payment providers

Additional technologies should only be introduced when they solve a genuine TeamFlow problem.

---

# 🏆 Level 2 Philosophy

```text
Learn
  ↓
Understand
  ↓
Build
  ↓
Break
  ↓
Debug
  ↓
Refactor
  ↓
Test
  ↓
Deploy
  ↓
Explain
```

The goal is not:

> How many technologies did the learner use?

The goal is:

> Can the learner take a non-trivial backend requirement, engineer a maintainable solution, handle realistic problems, test important behavior, deploy the system, and explain the decisions behind it?

---

# Final Principle

**One Project.**

**One Evolving Architecture.**

**Focused Scope.**

**Real Business Rules.**

**Two External Integrations.**

**Meaningful Testing.**

**Real Deployment.**

**Real Engineering Decisions.**

**No Technology for Technology's Sake.**
