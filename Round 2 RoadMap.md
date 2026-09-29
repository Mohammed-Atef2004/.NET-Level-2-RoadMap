# Tawjeh Level 2 — Advanced .NET Backend

# Sprint Specifications

> **Project:** TeamFlow — Project & Team Operations Platform
> **Duration:** 6 Sprints × 2 Weeks
> **Expected Commitment:** ~30 Hours / Sprint
> **Evaluation:** 100 Points / Sprint
> **Total:** 600 Points

---

# 📅 Sprint 1 — Domain Modeling, Clean Architecture & Persistence

## 🎯 Sprint Goal

Build the architectural and domain foundation of TeamFlow.

The learner should move from:

```text
Requirements
    ↓
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

The goal is **not** to teach DDD.

The goal is to teach the learner how to understand a business problem, model it correctly, separate responsibilities, and build a maintainable backend foundation.

---

# 📚 What You Will Learn

## 1. Domain Modeling

Learn:

* Requirements analysis
* Actors and use cases
* Entities
* Relationships
* Value Objects where appropriate
* Business rules
* Invariants
* Encapsulation
* Entity responsibilities
* Domain vs application responsibilities

Key question:

> What does the business actually allow or prevent?

Not:

> What tables should I create?

---

## 2. Clean Architecture

Learn:

* Separation of concerns
* Dependency direction
* Dependency Inversion
* Domain layer
* Application layer
* Infrastructure layer
* API layer
* Dependency Injection
* SOLID principles in practical architecture

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

---

## 3. Repository Pattern

Learn:

* Repository abstraction
* Why abstractions exist
* Repository responsibilities
* Repository vs DbContext
* Repository vs service
* When a repository abstraction is useful
* Avoiding unnecessary generic abstractions

The learner should understand:

> A repository is not simply a wrapper around every DbSet method.

---

## 4. EF Core Persistence

Learn:

* DbContext
* DbSet
* Entity configuration
* Fluent API
* Relationships
* Foreign Keys
* Constraints
* Migrations
* Transactions
* Persistence boundaries

The learner is expected to already understand database fundamentals.

---

# 🛠️ Practical Implementation

Build the first version of TeamFlow.

## Organization

Implement:

* Create organization
* Get organization
* Update organization

## Team

Implement:

* Create team
* Add member
* Remove member
* Get members

## Project

Implement:

* Create project
* Get project
* Update project
* Archive project

## Project Membership

Implement:

* Add member
* Remove member
* List members

---

# 📝 Sprint Tasks

### Task 1 — Requirements Analysis

Document:

* Actors
* Main use cases
* Core entities
* Relationships
* Initial business rules

---

### Task 2 — Domain Model

Create a domain model containing:

* Entities
* Important relationships
* Business responsibilities
* Important invariants
* Value Objects where appropriate

---

### Task 3 — Architecture

Create:

```text
Domain
Application
Infrastructure
API
```

Configure dependency direction correctly.

---

### Task 4 — Repository Abstraction

Create repository abstractions for the parts of the system that genuinely need them.

Implement them inside Infrastructure.

---

### Task 5 — EF Core Persistence

Configure:

* Relationships
* Foreign keys
* Required fields
* Constraints
* Indexes where appropriate
* Migrations

---

### Task 6 — Organization Feature

Implement the Organization use cases.

---

### Task 7 — Team Feature

Implement Team management.

---

### Task 8 — Project Feature

Implement Project management.

---

### Task 9 — Project Membership

Implement membership rules.

---

### Task 10 — API Documentation

Configure Swagger/OpenAPI.

---

# 📦 Sprint Deliverables

The learner must submit:

### 1. Domain Model

A documented model showing:

* Entities
* Relationships
* Responsibilities
* Business rules

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

### 3. Solution

Working TeamFlow solution with:

* Domain
* Application
* Infrastructure
* API

### 4. Persistence

* SQL Server
* EF Core
* Migrations
* Proper relationships

### 5. Features

* Organization
* Team
* Project
* Project Membership

### 6. Architecture Explanation

Short document answering:

> Why does each layer exist?

> Why is this dependency direction used?

> Why are repositories placed behind abstractions?

---

# 📊 Evaluation — 100 Points

| Area                                      |  Points |
| ----------------------------------------- | ------: |
| Requirements & Domain Modeling            |      15 |
| Clean Architecture & Dependency Direction |      20 |
| Repository Design                         |      15 |
| EF Core Persistence                       |      15 |
| Feature Implementation                    |      20 |
| Code Quality & Organization               |       5 |
| Documentation & Architecture Explanation  |      10 |
| **Total**                                 | **100** |

---

# ✅ Definition of Done

Sprint 1 is complete when:

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

The learner will understand how requests move through:

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

and secure the application using Authentication and Authorization.

---

# 📚 What You Will Learn

## 1. Application Architecture

Learn:

* Application use cases
* Commands
* Queries
* DTOs
* Request/Response models
* Application services
* Separation between API and Application

---

## 2. CQRS

Learn:

* Command
* Query
* Command Handler
* Query Handler
* Read vs Write responsibilities
* Why CQRS can improve application organization
* When CQRS adds unnecessary complexity

---

## 3. MediatR

Learn:

* Mediator Pattern
* Request/Handler
* Notifications
* Pipeline Behaviors
* Dependency flow

---

## 4. Validation

Learn:

* FluentValidation
* Validation vs business rules
* Validation pipeline
* Validation behavior

---

## 5. Result Pattern

Learn:

* Success results
* Failure results
* Validation failures
* Business failures
* Consistent application responses

---

## 6. Async Programming

Learn:

* async/await
* Task
* CancellationToken
* Cancellation propagation
* Async EF Core operations

---

## 7. Authentication

Learn:

* ASP.NET Core Identity
* Password management
* JWT
* Claims
* Refresh Tokens
* Logout / revocation

---

## 8. Authorization

Learn:

* Roles
* Policies
* Claims-based authorization
* Resource-based authorization
* Authentication vs Authorization

---

# 🛠️ Practical Implementation

## Authentication

Implement:

* Registration
* Login
* Refresh token
* Token revocation
* Logout
* Current user

---

## Authorization

Implement:

* Organization permissions
* Project permissions
* Project membership
* Project roles
* Resource authorization

---

## Tasks Foundation

Implement:

* Create task
* Update task
* Assign task
* Get task

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

### Task 3 — Pipeline Behavior

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
* Authentication
* JWT
* Refresh Tokens
* Authorization
* Task feature
* Short explanation of request flow

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
| Application Architecture    |      10 |
| CQRS Design                 |      15 |
| MediatR Implementation      |      15 |
| Validation & Result Pattern |      10 |
| Async / Cancellation        |      10 |
| Authentication              |      15 |
| Authorization               |      15 |
| Task Feature                |       5 |
| Code Quality & Explanation  |       5 |
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
* [ ] Revocation works
* [ ] Authorization rules work
* [ ] Task foundation works
* [ ] Learner can explain CQRS and Mediator decisions

---

# 🎓 Expected Outcome

The learner should now understand how to structure a non-trivial application around **use cases instead of controllers becoming the center of the application**.

---

# 📅 Sprint 3 — Business Rules & Advanced API Engineering

## 🎯 Sprint Goal

Move TeamFlow beyond CRUD.

The learner should learn how to represent **real business behavior** and build an API that behaves predictably under real usage.

---

# 📚 What You Will Learn

## 1. Business Rules

Learn:

* Business rules
* Invariants
* Encapsulation
* State transitions
* Domain behavior
* Application rules
* Domain Services where appropriate

No DDD course is introduced.

The focus is practical business modeling.

---

## 2. Task Lifecycle

Model:

```text
Todo
 ↓
InProgress
 ↓
Completed
```

with additional states:

```text
Blocked
Cancelled
```

The system must control valid transitions.

---

## 3. Task Dependencies

Learn how to model:

```text
Task A
  ↓ depends on
Task B
```

including:

* Dependency creation
* Dependency removal
* Circular dependency prevention

---

## 4. Advanced API Querying

Learn:

* Pagination
* Filtering
* Searching
* Sorting
* Query parameters
* API versioning

---

## 5. API Error Handling

Learn:

* ProblemDetails
* Global exception handling
* Business errors
* Validation errors
* Conflict responses
* Consistent error contracts

---

## 6. Reliability

Learn:

* Rate limiting
* Idempotency
* Duplicate requests
* Safe retry behavior

---

# 🛠️ Practical Implementation

## Task Lifecycle

Implement controlled state transitions.

Example:

```text
Todo → InProgress
InProgress → Completed
InProgress → Blocked
Blocked → InProgress
Todo → Cancelled
```

Invalid transitions must be rejected.

---

## Task Dependencies

Implement:

* Add dependency
* Remove dependency
* List dependencies

Prevent:

```text
A → B → C → A
```

---

## Sprints

Implement:

* Create sprint
* Start sprint
* Complete sprint
* Add task
* Remove task

---

## Labels

Implement:

* Create label
* Assign label
* Remove label

---

## Comments

Implement:

* Add comment
* Edit own comment
* Delete own comment

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

# 📝 Sprint Tasks

### Task 1 — Task State Machine

Implement valid state transitions.

---

### Task 2 — Business Rules

Identify and enforce important TeamFlow business rules.

---

### Task 3 — Dependency Management

Implement task dependencies.

---

### Task 4 — Circular Dependency Prevention

Prevent dependency cycles.

---

### Task 5 — Sprint Management

Implement sprint lifecycle.

---

### Task 6 — Labels

Implement task labels.

---

### Task 7 — Comments

Implement comments with proper authorization.

---

### Task 8 — Advanced Search

Implement:

* Pagination
* Filtering
* Sorting
* Searching

---

### Task 9 — ProblemDetails

Create a consistent API error contract.

---

### Task 10 — Global Exception Handling

Handle unexpected exceptions consistently.

---

### Task 11 — Rate Limiting

Protect selected endpoints.

---

### Task 12 — Idempotency

Choose a real operation where duplicate requests could cause a problem.

Make it safely idempotent.

---

# 📦 Sprint Deliverables

The learner must submit:

* Task lifecycle
* Business rules
* Dependencies
* Circular dependency protection
* Sprint management
* Labels
* Comments
* Search API
* Pagination
* Filtering
* Sorting
* ProblemDetails
* Global exception handling
* Rate limiting
* Idempotency

Plus a short document explaining:

> Which rules were implemented?

> Where were they enforced?

> Why were they placed there?

---

# 📊 Evaluation — 100 Points

| Area                                      |  Points |
| ----------------------------------------- | ------: |
| Business Rules & Modeling                 |      20 |
| Task Lifecycle                            |      10 |
| Dependencies & Cycle Prevention           |      10 |
| Sprint / Label / Comment Features         |      15 |
| Pagination / Filtering / Sorting / Search |      15 |
| Error Handling & ProblemDetails           |      10 |
| Rate Limiting                             |       5 |
| Idempotency                               |      10 |
| Code Quality & Explanation                |       5 |
| **Total**                                 | **100** |

---

# ✅ Definition of Done

* [ ] Task lifecycle is enforced
* [ ] Invalid state transitions fail
* [ ] Dependencies work
* [ ] Circular dependencies are prevented
* [ ] Sprints work
* [ ] Labels work
* [ ] Comments work
* [ ] Search works
* [ ] Pagination works
* [ ] Filtering works
* [ ] Sorting works
* [ ] ProblemDetails is consistent
* [ ] Global exceptions are handled
* [ ] Rate limiting works
* [ ] At least one operation is idempotent

---

# 🎓 Expected Outcome

TeamFlow should no longer behave like a simple CRUD application.

The learner should understand how backend engineering is largely about **controlling business behavior and system behavior**, not just creating endpoints.

---

# 📅 Sprint 4 — Production Engineering & Reliability

## 🎯 Sprint Goal

Teach the learner how to handle work that should not necessarily happen inside a single HTTP request and how to communicate safely with external systems.

---

# 📚 What You Will Learn

## 1. Logging

Learn:

* ILogger
* Log levels
* Structured logging
* Useful context
* Exception logging
* Correlation IDs

---

## 2. Background Processing

Learn:

* BackgroundService
* Hosted Services
* Background queues
* Cancellation
* Graceful shutdown
* Scheduled work

Understand:

> When should work leave the HTTP request?

---

## 3. Redis

Learn:

* Why caching exists
* Cache-aside
* TTL
* Cache invalidation
* Redis
* Choosing what should be cached

---

## 4. External HTTP Services

Learn:

* HttpClient
* IHttpClientFactory
* Typed clients
* Timeouts
* HTTP failures
* Invalid responses
* Cancellation

---

## 5. Resilience

Learn practical concepts:

* Retry
* Exponential backoff
* Circuit breaker
* Timeout
* Idempotency
* External service failure handling

The goal is not to study resilience theory.

The goal is to make a real integration safer.

---

# 🛠️ Practical Implementation

## Notifications

Generate notifications for:

* Task assignment
* Task completion
* Comments
* Upcoming deadlines

---

## Activity Feed

Record important project activities.

---

## Background Processing

Move suitable notification work outside the HTTP request.

---

## Scheduled Operation

Implement:

```text
Find tasks approaching deadline
          ↓
Create notifications
```

---

## Redis

Choose an appropriate read-heavy TeamFlow operation.

Examples:

* Project summary
* Frequently accessed project information
* User/project permissions

Implement:

```text
Request
 ↓
Cache
 ↓
Cache Miss
 ↓
Database
 ↓
Cache
```

---

## External Service

Integrate one external HTTP service.

Example:

```text
Email / Notification Provider
```

---

# 📝 Sprint Tasks

### Task 1 — Structured Logging

Add useful structured logs around important workflows.

---

### Task 2 — Correlation ID

Implement request correlation.

---

### Task 3 — Notification System

Create the notification model and workflow.

---

### Task 4 — Background Processing

Move notification processing outside the request lifecycle.

---

### Task 5 — Cancellation & Shutdown

Handle application shutdown correctly.

---

### Task 6 — Scheduled Operation

Implement deadline-based notification generation.

---

### Task 7 — Redis Integration

Introduce Redis for one justified use case.

---

### Task 8 — Cache Invalidation

Ensure relevant write operations invalidate/update affected cache entries.

---

### Task 9 — Typed HTTP Client

Create a typed client for an external service.

---

### Task 10 — External Failure Handling

Handle:

* Timeout
* HTTP errors
* Invalid responses
* Cancellation

---

### Task 11 — Resilience

Apply retry/circuit-breaker behavior where justified.

---

### Task 12 — Activity Feed

Record meaningful project actions.

---

# 📦 Sprint Deliverables

The learner must submit:

* Structured logging
* Correlation ID
* Notification system
* Background processing
* Scheduled operation
* Redis caching
* Cache invalidation
* External HTTP integration
* Timeout handling
* Retry/resilience
* Activity feed

And document at least one production failure scenario:

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

# 📊 Evaluation — 100 Points

| Area                                |  Points |
| ----------------------------------- | ------: |
| Logging & Correlation               |      10 |
| Background Processing               |      20 |
| Scheduled Processing                |      10 |
| Redis & Caching                     |      15 |
| Cache Invalidation                  |      10 |
| External HTTP Integration           |      15 |
| Resilience & Failure Handling       |      15 |
| Activity / Notification Integration |       5 |
| **Total**                           | **100** |

---

# ✅ Definition of Done

* [ ] Structured logging exists
* [ ] Correlation ID exists
* [ ] Notifications are implemented
* [ ] Notifications can be processed asynchronously
* [ ] Scheduled operation works
* [ ] Cancellation is handled
* [ ] Redis is integrated
* [ ] Cache invalidation works
* [ ] External HTTP client works
* [ ] Timeout/error handling exists
* [ ] Resilience is applied where justified
* [ ] Activity feed works

---

# 🎓 Expected Outcome

The learner should understand that backend systems do not consist only of:

```text
Request → Controller → Database → Response
```

They should understand background work, caching, external dependencies, failures, and operational behavior.

---

# 📅 Sprint 5 — Testing, AI & Payment Integration

## 🎯 Sprint Goal

Introduce **real verification and external business integrations**.

The learner will test important behavior and integrate two realistic external capabilities:

```text
TeamFlow
   ├── AI Assistant
   └── Payment Gateway
```

The focus is not learning AI or payments as isolated technologies.

The focus is learning how a backend integrates with external systems safely.

---

# 📚 What You Will Learn

## 1. Unit Testing

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

## 2. Integration Testing

Learn:

* What integration testing verifies
* API-level testing
* Real dependency boundaries
* Test database strategy
* Authentication in integration tests
* HTTP request/response testing
* Test isolation

Focus on meaningful integration tests.

---

## 3. AI Integration

Learn backend concepts behind integrating an LLM API:

* HTTP-based AI APIs
* Request/response models
* Prompt construction
* Structured output
* Provider abstraction
* Token/cost awareness
* Rate limits
* Timeout handling
* Prompt injection awareness
* Authorization and data exposure

Use OpenAI/ChatGPT API or an equivalent LLM provider.

Do NOT introduce:

* RAG
* Vector databases
* LangChain
* Multi-agent systems
* Fine-tuning

---

## 4. Payment Integration

Learn:

* Payment lifecycle
* Payment intent/order creation
* External payment API
* Payment status
* Redirect/checkout flow
* Webhooks
* Signature verification
* Idempotency
* Payment state transitions
* External failure handling

---

# 🛠️ Practical Implementation

# Part A — Testing

Test important business behavior.

Examples:

```text
Complete Task
Assign Task
Add Dependency
Reject Circular Dependency
Change Task State
Start Sprint
Complete Sprint
```

---

## Integration Tests

Create integration tests for important API flows.

Examples:

```text
Register
Login
Create Project
Create Task
Assign Task
Complete Task
```

Verify the actual application pipeline.

---

# Part B — AI Assistant

Create:

```text
Project AI Assistant
```

Users can ask:

```text
Which tasks are overdue?

Which tasks are blocked?

Summarize the current project status.

What are the most important unfinished tasks?
```

The AI should only receive information the current user is authorized to access.

---

# Part C — Payment

Introduce a paid TeamFlow capability.

Example:

```text
Organization
    ↓
Subscription / Paid Feature
    ↓
Payment Gateway
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

Identify the most important logic that requires unit tests.

---

### Task 2 — Domain Unit Tests

Test:

* State transitions
* Business rules
* Dependencies
* Invalid operations

---

### Task 3 — Application Unit Tests

Test important use cases.

---

### Task 4 — Validation Tests

Test important validation scenarios.

---

### Task 5 — Integration Test Infrastructure

Create the infrastructure required to run integration tests.

---

### Task 6 — API Integration Tests

Test important HTTP workflows.

---

### Task 7 — AI Provider Abstraction

Create an abstraction around the AI provider.

Avoid spreading provider-specific code across the application.

---

### Task 8 — AI Assistant

Implement project-related AI queries.

---

### Task 9 — AI Authorization

Ensure users cannot ask the AI about project data they cannot access.

---

### Task 10 — AI Failure Handling

Handle:

* Timeout
* Provider failure
* Rate limiting
* Invalid response

---

### Task 11 — Payment Gateway Integration

Integrate one payment provider.

---

### Task 12 — Payment State Machine

Represent payment states clearly.

Example:

```text
Pending
   ↓
Paid

Pending
   ↓
Failed

Pending
   ↓
Cancelled
```

---

### Task 13 — Webhooks

Implement payment webhook processing.

---

### Task 14 — Signature Verification

Verify that payment notifications actually come from the payment provider.

---

### Task 15 — Webhook Idempotency

Ensure the same webhook cannot process the same payment twice.

---

# 📦 Sprint Deliverables

The learner must submit:

### Testing

* Unit tests
* Integration tests
* Business-rule coverage
* Application-flow coverage

### AI

* AI provider abstraction
* Project AI assistant
* Authorization
* Error handling

### Payment

* Payment integration
* Payment state handling
* Webhook endpoint
* Signature verification
* Idempotent webhook processing

---

# 📊 Evaluation — 100 Points

| Area                                 |  Points |
| ------------------------------------ | ------: |
| Unit Testing                         |      20 |
| Integration Testing                  |      15 |
| Test Quality & Edge Cases            |      10 |
| AI Integration                       |      15 |
| AI Security / Authorization          |      10 |
| Payment Integration                  |      15 |
| Webhooks & Signature Verification    |      10 |
| Payment Idempotency / State Handling |       5 |
| **Total**                            | **100** |

---

# ✅ Definition of Done

* [ ] Important business rules have unit tests
* [ ] Important use cases have unit tests
* [ ] Important API flows have integration tests
* [ ] AI provider is isolated
* [ ] AI assistant works
* [ ] AI access respects authorization
* [ ] AI failures are handled
* [ ] Payment gateway is integrated
* [ ] Payment states are handled
* [ ] Webhook works
* [ ] Webhook signature is verified
* [ ] Duplicate webhook processing is prevented

---

# 🎓 Expected Outcome

The learner should now understand how to verify backend behavior and integrate external systems where:

```text
Your System
     ↓
External Provider
     ↓
Success / Failure / Timeout / Duplicate Request
```

must all be handled safely.

---

# 📅 Sprint 6 — Docker, CI/CD & Deployment

## 🎯 Sprint Goal

Take TeamFlow from:

> "It works on my machine."

to:

> "It can be built, tested, containerized, and deployed consistently."

---

# 📚 What You Will Learn

## 1. Docker

Learn:

* Images
* Containers
* Dockerfile
* Build
* Run
* Ports
* Environment variables
* Volumess
* Networks
* Docker Compose

---

## 2. Production Configuration

Learn:

* Environment variables
* Secrets
* Connection strings
* JWT configuration
* Redis configuration
* AI API keys
* Payment configuration
* Production settings

No secrets should be committed to source control.

---

## 3. CI/CD

Learn the practical basics of:

* GitHub Actions
* Workflow
* Jobs
* Steps
* Build
* Test
* Docker build
* Environment configuration
* Deployment

The goal is **not** to teach DevOps as a separate curriculum.

---

# 🚀 Target Pipeline

The learner should build approximately:

```text
Git Push
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
Docker Image
   ↓
Deployment
   ↓
Health Verification
```

---

# 🛠️ Practical Implementation

## Docker

Create a production-oriented Dockerfile.

---

## Docker Compose

Create a local environment containing:

```text
TeamFlow API
SQL Server
Redis
```

---

## Configuration

Move environment-specific values outside source code.

Examples:

```text
Connection Strings
JWT Configuration
Redis Configuration
AI API Keys
Payment API Keys
```

---

## CI Pipeline

Create GitHub Actions workflow:

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

## Docker Pipeline

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

## Deployment

Deploy TeamFlow to a real environment.

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
* External integrations
* AI
* Payment
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

---

# 📊 Evaluation — 100 Points

| Area                       |  Points |
| -------------------------- | ------: |
| Dockerfile                 |      15 |
| Docker Compose             |      10 |
| Configuration & Secrets    |      10 |
| GitHub Actions CI          |      20 |
| Automated Testing in CI    |      10 |
| Docker Image Build         |      10 |
| Deployment                 |      15 |
| Production Verification    |       5 |
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

A learner completes Level 2 when all six Sprints are completed and the final TeamFlow system contains:

```text
Domain Modeling
        ↓
Clean Architecture
        ↓
Repository Abstractions
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
External Services
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

| Sprint                                      |  Points |
| ------------------------------------------- | ------: |
| Sprint 1 — Architecture & Persistence       |     100 |
| Sprint 2 — CQRS & Security                  |     100 |
| Sprint 3 — Business Rules & API Engineering |     100 |
| Sprint 4 — Production Engineering           |     100 |
| Sprint 5 — Testing & Integrations           |     100 |
| Sprint 6 — Docker, CI/CD & Deployment       |     100 |
| **TOTAL**                                   | **600** |

---

# 🎯 Final Project Review

At the end of Level 2, the learner must be able to explain:

## 1. Domain

What does TeamFlow represent?

## 2. Architecture

Why is the solution structured this way?

## 3. Repository

Why is a repository abstraction used here?

## 4. Application

Why are commands and queries separated?

## 5. MediatR

Why is the Mediator pattern used?

## 6. Business Rules

Where are important rules enforced?

## 7. Security

How are authentication and authorization handled?

## 8. API

How does the API handle errors, duplicates, pagination, and rate limits?

## 9. Background Processing

Why should some operations happen outside the HTTP request?

## 10. Caching

Why is this data cached?

## 11. External Services

What happens when an external provider fails?

## 12. AI

How is AI access isolated and controlled?

## 13. Payment

How are payment state, webhooks, signatures, and duplicates handled?

## 14. Testing

What behavior is covered by Unit and Integration Tests?

## 15. Deployment

How does TeamFlow move from source code to a running production system?

## 16. Trade-offs

For major decisions:

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

---

# 🧠 Engineering Practice Throughout All Sprints

These are not separate lessons.

They are part of how the learner is evaluated throughout the project.

## Debugging

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

## Architecture Decisions

Before introducing an abstraction:

```text
What problem are we solving?

Why is the current solution insufficient?

What alternatives exist?

What complexity does this introduce?

Is the abstraction actually necessary?
```

## Performance

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

---

# 🚫 Explicitly Out of Scope

The following are NOT mandatory for Level 2:

* Microservices
* Kubernetes
* Terraform
* Kafka
* RabbitMQ
* GraphQL
* MongoDB
* PostgreSQL
* Elasticsearch
* RAG
* Vector Databases
* Multi-Agent Systems
* Fine-Tuning
* Advanced Cloud Architecture
* Dedicated System Design Sprint
* Large DevOps curriculum
* Architecture Testing curriculum

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

> Can the learner take a non-trivial backend requirement, engineer a solution, handle real problems, and explain the decisions behind it?

**One Project.**

**One Evolving Architecture.**

**Real Business Rules.**

**Real Integrations.**

**Real Testing.**

**Real Deployment.**

**Real Engineering Decisions.**
