# 🏃 Sprint 1 — Tasks

**Project 1: E-Commerce MVC**

**Duration:** Weeks 1–2

---

# 📌 Overview

In this sprint, you will transform a basic ASP.NET Core MVC application into a well-structured N-Tier application while implementing a complete authentication and authorization system using ASP.NET Core Identity.

By the end of this sprint, your application should follow proper separation of concerns, use the Repository & Unit of Work patterns, and provide secure role-based access for administrators and customers.

---

# 🎯 Learning Objectives

After completing this sprint, you should be able to:

- Understand N-Tier Architecture.
- Apply Repository Pattern.
- Apply Unit of Work Pattern.
- Build reusable Business Logic.
- Configure Dependency Injection.
- Work with DTOs.
- Configure AutoMapper.
- Implement ASP.NET Core Identity.
- Manage Roles & Policies.
- Secure MVC Applications.

---

# 📝 Task 1 — N-Tier Architecture

## 🎯 Objective

Refactor the project into a maintainable layered architecture by separating responsibilities across multiple layers.

---

## 📚 Concepts

- N-Tier Architecture
- Repository Pattern
- Unit of Work
- Dependency Injection
- DTOs
- AutoMapper

---

## ✅ Requirements

### Solution Structure

Refactor the solution into the following layers:

- Presentation Layer (MVC)
- Business Logic Layer (BLL)
- Data Access Layer (DAL)

---

### Repository Pattern

Implement repositories for your business entities.

At minimum:

- Product Repository
- Category Repository

Repositories should encapsulate all database operations.

---

### Unit of Work

Implement a Unit of Work that exposes all repositories.

Responsibilities:

- Coordinate repository access.
- Save all pending changes using a single transaction.

---

### Business Layer

Move business logic out of Controllers.

Examples include:

- Product management
- Category management

Controllers should communicate only with the Business Layer.

---

### Dependency Injection

Register all repositories and services inside `Program.cs`.

Use appropriate service lifetimes.

---

### DTOs

Create DTOs for:

- Product
- Category

Expose only the data required by the presentation layer.

---

### AutoMapper

Configure AutoMapper profiles.

Map:

- Entity → DTO
- DTO → Entity

---

### Controller Refactoring

Refactor controllers so they:

- Never communicate directly with DbContext.
- Never contain business logic.
- Only coordinate requests and responses.

---

## ✔️ Acceptance Criteria

Your solution is considered complete when:

- Controllers never access DbContext directly.
- All CRUD operations still work.
- Repository Pattern is implemented.
- Unit of Work is implemented.
- DTOs are used correctly.
- AutoMapper is configured.
- Application builds without errors.

---

## 🎁 Bonus Challenge

Implement a Generic Repository to reduce duplicated CRUD code.

---

# 📝 Task 2 — Authentication & Authorization

## 🎯 Objective

Secure the application using ASP.NET Core Identity and role-based authorization.

---

## 📚 Concepts

- ASP.NET Core Identity
- Authentication
- Authorization
- Roles
- Claims
- Policies

---

## ✅ Requirements

### Identity

Configure ASP.NET Core Identity.

Create an `ApplicationUser` that extends `IdentityUser`.

Add at least one custom property.

Example:

- Full Name

---

### Roles

Create the following roles:

- Admin
- Customer

Seed them automatically when the application starts.

---

### Registration

Implement user registration.

Requirements:

- Validate user input.
- Assign the Customer role automatically.
- Redirect to Login after successful registration.

---

### Login

Implement user login.

Requirements:

- Authenticate using Identity.
- Redirect authenticated users correctly.
- Display validation messages for invalid credentials.

---

### Logout

Allow authenticated users to sign out securely.

---

### Authorization

Protect administrative pages.

Only administrators should be able to access:

- Product Management
- Category Management
- User Management

Customers should not access these pages.

---

### Policy-Based Authorization

Create at least one custom Authorization Policy.

Use it in one or more controller actions.

---

## ✔️ Acceptance Criteria

The task is complete when:

- Users can register.
- Users can login.
- Users can logout.
- Roles are seeded automatically.
- Customers receive the Customer role.
- Admin pages are protected.
- Unauthorized users are redirected correctly.

---

## 🎁 Bonus Challenge

Implement Email Confirmation before allowing users to login.

---

# 📝 Task 3 — User Management

## 🎯 Objective

Allow administrators to manage application users.

---

## 📚 Concepts

- UserManager
- RoleManager
- Identity Services

---

## ✅ Requirements

Build a User Management page for administrators.

The page should allow administrators to:

### View Users

Display:

- Username
- Email
- Current Role
- Lock Status

---

### Role Management

Allow administrators to:

- Promote Customer → Admin
- Demote Admin → Customer

---

### Lock / Unlock Accounts

Allow administrators to:

- Lock accounts
- Unlock accounts

---

### Delete Users (Optional)

Allow administrators to delete users safely.

Prevent administrators from deleting their own accounts.

---

## ✔️ Acceptance Criteria

The task is complete when:

- All users are listed.
- Roles can be changed.
- Accounts can be locked.
- Accounts can be unlocked.
- Proper authorization is enforced.

---

## 🎁 Bonus Challenge

Add searching and pagination to the User Management page.

---

# 📋 Sprint Checklist

Before moving to Sprint 2, make sure your project satisfies all the following requirements.

## Architecture

- [ ] N-Tier Architecture implemented.
- [ ] Repository Pattern implemented.
- [ ] Unit of Work implemented.
- [ ] DTOs implemented.
- [ ] AutoMapper configured.
- [ ] Dependency Injection configured.

---

## Identity

- [ ] Registration works.
- [ ] Login works.
- [ ] Logout works.
- [ ] Roles seeded.
- [ ] Authorization implemented.
- [ ] Policy-based Authorization implemented.

---

## User Management

- [ ] Users can be listed.
- [ ] Roles can be assigned.
- [ ] Users can be locked.
- [ ] Admin pages are protected.

---

# 🚀 Submission Requirements

Each trainee must submit:

- GitHub Repository.
- SQL Server Database Backup (.bak or SQL Script).
- Updated README.
- Screenshots of:
  - Login
  - Register
  - User Management
  - Product Management
- A short demo video (Optional).

---

# 🎯 Sprint Outcome

By completing this sprint, you will have built a secure, maintainable MVC application following N-Tier Architecture and ASP.NET Core Identity best practices.

You are now ready to implement state management, file handling, and shopping cart features in Sprint 2.