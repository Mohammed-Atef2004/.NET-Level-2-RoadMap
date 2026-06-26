# Sprint 5 — API Security & Resilience

> Duration: Weeks 9–10

## 🎯 Sprint Goal

Secure the API using JWT authentication and build a resilient backend capable of handling errors gracefully while providing consistent responses.

By the end of this sprint, the API should implement authentication, authorization, centralized validation, structured logging, and global exception handling.

---

# Task 1 — JWT Authentication & Authorization

## Objective

Secure the API using JWT Access Tokens and Refresh Tokens.

---

## Requirements

### Configure JWT

Configure JWT settings inside `appsettings.json`.

Include:

- Secret Key
- Issuer
- Audience
- Access Token Expiration
- Refresh Token Expiration

Bind settings using the Options Pattern.

---

### Identity

Configure ASP.NET Core Identity.

Create:

- ApplicationUser

Seed the following roles:

- Admin
- User

---

### Token Service

Create:

- ITokenService
- TokenService

The service should generate:

- Access Token
- Refresh Token

Include the following claims:

- User Id
- Email
- Role

---

### Authentication Endpoints

Implement:

- Register
- Login
- Refresh Token
- Logout

Store refresh tokens securely in the database.

Allow users to obtain a new Access Token without logging in again.

---

### Authorization

Protect endpoints using:

- Role-based Authorization
- Policy-based Authorization

Examples:

- Admin-only endpoints
- User-only endpoints

---

## Concepts

- JWT
- Claims
- Refresh Tokens
- Authentication
- Authorization
- Identity

---

## Deliverable

A secure API using JWT authentication with refresh token support.

---

# Task 2 — Validation & Error Handling

## Objective

Create a centralized validation and error handling system.

---

## Requirements

### FluentValidation

Install FluentValidation.

Create validators for all Commands.

Examples:

- CreateTaskCommand
- UpdateTaskCommand
- CreateProjectCommand

Move all validation logic out of controllers and handlers.

---

### Validation Pipeline

Configure the Validation Pipeline Behavior.

Every request should be validated automatically before reaching its handler.

If validation fails:

- Return validation errors
- Skip handler execution

---

### Result Pattern

Create a reusable `Result<T>` class.

Include:

- Success
- Failure
- Error Message
- Error Code

Handlers should return Result objects instead of throwing business exceptions.

---

### Global Exception Middleware

Create middleware responsible for handling unexpected exceptions.

Return standardized responses for:

- Validation Errors
- Not Found
- Unauthorized
- Internal Server Error

Use ProblemDetails as the response format.

Never expose stack traces to clients.

---

## Concepts

- FluentValidation
- Result Pattern
- ProblemDetails
- Middleware
- Exception Handling

---

## Deliverable

A centralized validation and exception handling system with standardized API responses.

---

# Task 3 — Structured Logging

## Objective

Monitor application behavior using structured logging.

---

## Requirements

### Serilog

Configure Serilog.

Log to:

- Console
- Rolling File

---

### Request Logging

Log:

- Request Path
- HTTP Method
- Status Code
- Execution Time

---

### Error Logging

Log:

- Exception Message
- Stack Trace
- Inner Exceptions

Include contextual information whenever possible.

---

### Configuration

Move logging configuration to:

- appsettings.json

Configure different log levels for:

- Development
- Production

---

## Concepts

- Structured Logging
- Log Levels
- Sinks
- Diagnostics

---

## Deliverable

A production-ready logging system that captures requests, errors, and application events.

---

# Sprint Deliverables

Students should have completed:

- ✅ JWT Authentication
- ✅ Refresh Tokens
- ✅ ASP.NET Core Identity
- ✅ Role-based Authorization
- ✅ Policy-based Authorization
- ✅ FluentValidation
- ✅ Validation Pipeline
- ✅ Result Pattern
- ✅ Global Exception Middleware
- ✅ ProblemDetails
- ✅ Serilog Logging

The API is now secure, resilient, and capable of handling requests and failures using modern backend development practices.