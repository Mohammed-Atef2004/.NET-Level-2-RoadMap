# 🗺️ .NET Developer Roadmap — 3 Months

> **Goal:** Graduate job-ready Junior .NET Developers equipped with hands-on experience from two complete projects and a solid understanding of industry-standard patterns discussed in technical interviews.

---

## 📋 Prior Knowledge (Starting Point)

Trainees are entering this level with the following baseline:

| Topic | Level |
|---|---|
| C# | ✅ Solid |
| LINQ | ✅ Solid |
| Entity Framework Core | ✅ Intermediate |
| SQL + Database | ✅ Intermediate |
| MVC | ✅ Intermediate |
| Web API | ✅ Basic |
| Basic Authentication | ✅ Basic |

---

## 🗓️ Overview

| Sprint | Weeks | Focus |
|---|---|---|
| Sprint 1 | 1–2 | Foundation & Security |
| Sprint 2 | 3–4 | State Management & Media |
| Sprint 3 | 5–6 | Data Mastery & Integrations |
| Sprint 4 | 7–8 | Enterprise Architecture |
| Sprint 5 | 9–10 | API Security & Resilience |
| Sprint 6 | 11–12 | Production Readiness & Go-Live |

---

## 🏃 Sprint 1: Foundation & Security
### Weeks 1 & 2 · Project 1: E-Commerce — Structure & Access Control

**🎯 Goal:** Establish a robust N-Tier architecture and implement a complete identity & access management system.

### 📚 Concepts

- N-Tier Architecture, Repository Pattern, Unit of Work
- Dependency Injection (Lifetimes), DTOs, AutoMapper
- ASP.NET Core Identity (In-depth)
- Roles, Claims, Policy-based Authorization

### 📝 Tasks

- [ ] Refactor the template from `Controller → DbContext` to `Controller → Service → Repository → DbContext`
- [ ] Implement `Admin` and `Customer` roles
- [ ] Secure admin pages using `[Authorize(Roles="Admin")]` and Policies
- [ ] Build a User Management dashboard for the Admin (View, Delete, Assign Roles)

### ✅ Deliverable

A perfectly structured N-Tier MVC app with bulletproof authentication and role management.

### 🔗 Resource Hub

**🇪🇬 Egyptian Creators**
- [Hosam Kamel — Clean Architecture & SOLID](https://www.youtube.com/@HosamKamel) — Look for his ASP.NET Core Clean Architecture playlist
- [Mohamed El-Zohairy — Repository & UoW](https://www.youtube.com/@MohamedElZohairy) — Excellent practical implementation of generic repositories

**🇬🇧 English Creators**
- [Milan Jovanović — DI & Best Practices](https://www.youtube.com/@MilanJovanovicTech) — Search for his "ASP.NET Core Services Lifetime" video
- [Tim Corey — ASP.NET Core Identity](https://www.youtube.com/@IAmTimCorey) — His Identity series is the gold standard for beginners

**📄 Official Docs**
- [Microsoft Docs: Dependency Injection in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection)
- [Microsoft Docs: Introduction to Identity](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/identity)

---

## 🏃 Sprint 2: State Management & Media
### Weeks 3 & 4 · Project 1: E-Commerce — Cart & Media Handling

**🎯 Goal:** Handle files securely and manage application state using caching and sessions for a smooth user experience.

### 📚 Concepts

- `IFormFile`, Image Validation (Type, Size), GUID naming
- HTTP Statelessness, Session vs. Cookies
- `IMemoryCache` & `IDistributedCache`, Cache Invalidation

### 📝 Tasks

- [ ] Implement product image uploads with validation and automatic deletion of old images on update
- [ ] Build a Shopping Cart completely driven by Session state
- [ ] Cache the Categories list in memory
- [ ] Implement Cache Invalidation (clear the category cache when an admin adds/edits a category)

### ✅ Deliverable

A fully functional Session-based Shopping Cart with optimized image and data caching.

### 🔗 Resource Hub

**🇪🇬 Egyptian Creators**
- [Islam El-Mohammady — File Upload](https://www.youtube.com/@IslamElMohammady) — Great practical examples on uploading files in MVC
- [Ahmed Rabie — Caching & Session](https://www.youtube.com/@AhmedRabie) — Look for his ASP.NET Core performance videos

**🇬🇧 English Creators**
- [Nick Chapsas — Caching Strategies](https://www.youtube.com/@nickchapsas) — Deep dives into why and how to cache
- [Julio Casal — Practical MVC](https://www.youtube.com/@juliocasal) — Very clean code examples for file handling

**📄 Official Docs**
- [Microsoft Docs: File Uploads in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/mvc/models/file-uploads)
- [Microsoft Docs: Caching in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/performance/caching/overview)

---

## 🏃 Sprint 3: Data Mastery & Integrations
### Weeks 5 & 6 · Project 1: E-Commerce — Advanced Data & External Services

**🎯 Goal:** Optimize database queries and integrate real-world third-party services (Emails & Payments).

### 📚 Concepts

- Eager / Lazy / Explicit Loading, Global Query Filters, Fluent API
- Soft Delete Pattern (Shadow Properties)
- MailKit, HTML Email Templates
- Payment Gateways, Stripe Sandbox, Webhooks

### 📝 Tasks

- [ ] Implement Soft Delete for Products/Categories using a Global Query Filter (`IsDeleted = false`)
- [ ] Create an "Archived Products" view for admins
- [ ] Integrate MailKit to send Registration and Order Confirmation HTML emails
- [ ] Integrate Stripe Sandbox (or a fake payment service) to handle the Checkout flow

### ✅ Deliverable

A production-like MVP E-commerce system with Stripe payments, transactional emails, and soft-deleted data. **Project 1 Complete 🎉**

### 🔗 Resource Hub

**🇪🇬 Egyptian Creators**
- [Mohamed El-Zohairy — EF Core Advanced](https://www.youtube.com/@MohamedElZohairy) — His EF Core series covers Global Filters and Loading perfectly
- [Mustafa Salem — Stripe Integration](https://www.youtube.com/@MustafaSalem) — Has specific videos on integrating Stripe in .NET

**🇬🇧 English Creators**
- [Tim Corey — EF Core Deep Dive](https://www.youtube.com/@IAmTimCorey) — Look for "EF Core Querying" and "Shadow Properties"
- [Nick Chapsas — Stripe Best Practices](https://www.youtube.com/@nickchapsas) — Great architectural advice on handling payments

**📄 Official Docs**
- [Microsoft Docs: Global Query Filters](https://learn.microsoft.com/en-us/ef/core/querying/filters)
- [Stripe Docs: .NET Integration](https://stripe.com/docs/development/quickstart?lang=dotnet)

---

## 🏃 Sprint 4: Enterprise Architecture
### Weeks 7 & 8 · Project 2: Task Management API — Clean Arch & CQRS

**🎯 Goal:** Shift from N-Tier to Clean Architecture and implement the CQRS pattern to separate reads from writes.

### 📚 Concepts

- Clean Architecture (Domain, Application, Infrastructure, Presentation)
- Dependency Inversion Principle (DIP), Rich Domain Entities
- CQRS Pattern, MediatR (`IRequest`, `IRequestHandler`)
- Pipeline Behaviors (Validation, Logging, Performance)

### 📝 Tasks

- [ ] Setup the API solution with 4 strictly separated projects
- [ ] Create `Task`, `Project`, `User` entities in the Domain
- [ ] Implement MediatR for all CRUD operations (e.g., `CreateTaskCommand`, `GetTasksQuery`)
- [ ] Setup a `ValidationBehavior` pipeline so all commands are validated automatically before hitting the database

### ✅ Deliverable

A strictly structured Clean Architecture API where all data flow is handled via MediatR CQRS.

### 🔗 Resource Hub

**🇪🇬 Egyptian Creators**
- [Hosam Kamel — Clean Architecture](https://www.youtube.com/@HosamKamel) — His explanation of Domain vs Infrastructure is top-tier
- [Mohamed El-Zohairy — MediatR](https://www.youtube.com/@MohamedElZohairy) — Has a dedicated CQRS + MediatR playlist

**🇬🇧 English Creators**
- [Nick Chapsas — CQRS & MediatR](https://www.youtube.com/@nickchapsas) — Absolute masterclass on why to use MediatR and how to build Pipeline Behaviors
- [Milan Jovanović — Clean Architecture](https://www.youtube.com/@MilanJovanovicTech) — His "Modular Monolith" and Clean Arch videos are industry standard

**📄 Official Docs**
- [MediatR GitHub Wiki](https://github.com/jbogard/MediatR/wiki)

---

## 🏃 Sprint 5: API Security & Resilience
### Weeks 9 & 10 · Project 2: Task Management API — JWT & Error Handling

**🎯 Goal:** Secure the API using stateless tokens and ensure the API never crashes ungracefully using global exception handling.

### 📚 Concepts

- JWT Structure, Access vs. Refresh Tokens, Token Revocation
- Middleware Pipeline, Global Exception Handling
- Problem Details (RFC 7807)
- Result Pattern (Returning `Result<T>` instead of throwing exceptions)
- Serilog (Structured Logging), Sinks

### 📝 Tasks

- [ ] Build Auth endpoints (`/login`, `/refresh`, `/revoke`) returning JWTs
- [ ] Create a `Result<T>` class and refactor all MediatR handlers to use it
- [ ] Build a Global Exception Middleware that catches errors and returns standardized `ProblemDetails`
- [ ] Integrate Serilog to log all errors and requests to a file sink

### ✅ Deliverable

A highly secure, resilient API that handles failures gracefully and logs everything structurally.

### 🔗 Resource Hub

**🇪🇬 Egyptian Creators**
- [Mohamed El-Zohairy — JWT](https://www.youtube.com/@MohamedElZohairy) — Very clear step-by-step JWT implementation
- [Islam El-Mohammady — Serilog & Exceptions](https://www.youtube.com/@IslamElMohammady) — Good coverage of middleware and logging

**🇬🇧 English Creators**
- [Milan Jovanović — Global Error Handling](https://www.youtube.com/@MilanJovanovicTech) — His "Problem Details" implementation video is exactly what you need
- [Julio Casal — JWT in .NET 6/7/8](https://www.youtube.com/@juliocasal) — Clean, up-to-date JWT guides

**📄 Official Docs**
- [Microsoft Docs: JWT Bearer Authentication](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/jwt-authn)
- [Serilog Documentation](https://serilog.net/)

---

## 🏃 Sprint 6: Production Readiness & Go-Live
### Weeks 11 & 12 · Project 2: Task Management API — Advanced Features & Deployment

**🎯 Goal:** Add the final polish required by companies (filtering, validation) and deploy the application to a live server.

### 📚 Concepts

- Offset-based Pagination, Dynamic Filtering, Generic Sorting
- FluentValidation (Integrating with MediatR Pipeline)
- `IHostedService` / `BackgroundService` (Email Queues)
- Swagger / OpenAPI, XML Comments, API Versioning
- Deployment (IIS / Azure App Service), Environment Variables

### 📝 Tasks

- [ ] Implement a generic `PaginatedResult<T>` and apply dynamic filtering/sorting to the `GET /api/tasks` endpoint
- [ ] Replace all Data Annotations with FluentValidation rules linked to the MediatR pipeline
- [ ] Create a Background Service to process an email queue asynchronously
- [ ] Setup Swagger with XML comments and API Versioning (`/api/v1/tasks`)
- [ ] Publish and deploy the API + Angular frontend to IIS or Azure

### ✅ Deliverable

A fully documented, production-ready, deployed full-stack application. **Project 2 Complete 🎉**

### 🔗 Resource Hub

**🇪🇬 Egyptian Creators**
- [Mohamed El-Zohairy — FluentValidation & Swagger](https://www.youtube.com/@MohamedElZohairy) — Covers the integration perfectly
- [Code With Ahmed — Azure Deployment](https://www.youtube.com/@CodeWithAhmed) — Simple, straightforward deployment guides

**🇬🇧 English Creators**
- [Nick Chapsas — FluentValidation](https://www.youtube.com/@nickchapsas) — Why you should ditch Data Annotations
- [Tim Corey — Swagger & Deployment](https://www.youtube.com/@IAmTimCorey) — Very beginner-friendly deployment tutorials

**📄 Official Docs**
- [Microsoft Docs: Background Tasks](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services)
- [Microsoft Docs: Swagger / OpenAPI](https://learn.microsoft.com/en-us/aspnet/core/tutorials/web-api-help-pages-using-swagger)
- [FluentValidation Documentation](https://docs.fluentvalidation.net/en/latest/)

---

*Built to produce job-ready .NET developers in 12 weeks.*
