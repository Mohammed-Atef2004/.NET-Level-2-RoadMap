# 🏃 Sprint 1 — Foundation & Architecture

**Weeks 1–2 · Project 1: E-Commerce MVC**

---

## 🎯 Goal

Build a maintainable MVC application by introducing layered architecture, authentication, authorization and clean application structure.

---

## 📚 Concepts

| # | Concept |
|---|---------|
| 1 | N-Tier Architecture |
| 2 | Repository Pattern |
| 3 | Unit of Work |
| 4 | Dependency Injection |
| 5 | DTOs |
| 6 | AutoMapper |
| 7 | ASP.NET Core Identity |
| 8 | Authentication & Authorization |
| 9 | Roles & Policies |

---

## 📝 Features

### 🏗️ Application Architecture

Refactor the project into a clean N-Tier architecture.

- Separate Presentation, Business Logic and Data Access layers
- Implement Repository Pattern
- Implement Unit of Work
- Register services using Dependency Injection
- Remove direct DbContext usage from controllers
- Introduce DTOs and AutoMapper

---

### 🔐 Authentication & Authorization

Secure the application using ASP.NET Core Identity.

- User Registration
- User Login / Logout
- Role Management
- Admin & Customer roles
- Authorization using Roles
- Policy-based Authorization

---

### 👥 User Management

Build an administration panel for managing users.

- View all users
- Create users
- Assign or remove roles
- Lock / Unlock accounts
- Delete users *(optional)*

---

## ✅ Deliverable

A well-structured N-Tier MVC application with secure authentication, authorization, role management and clean separation of concerns.

---

## 🔗 Resource Hub

---

### 🏗️ N-Tier Architecture & Project Structure

| Source | Type | Link |
|--------|------|------|
| **Passionate Coders (Mohamed El-Mehdi)** — Full Arabic ASP.NET Core course covering architecture from the ground up | 🇪🇬 Arabic Playlist | [ASP.NET Core For Beginners](https://www.youtube.com/playlist?list=PLsV97AQt78NQ8E7cEqovH0zLYRJgJahGh) |
| **Khalid Essaadani** — Microsoft MVP, ASP.NET Core from scratch in Arabic | 🇲🇦 Arabic Playlist | [ASP.NET Core Fundamentals](https://www.youtube.com/user/EssaadaniTV/playlists) |
| **Microsoft Docs** — Common web app architectures including N-Tier | 📄 Docs | [App Architecture Guide](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures) |

---

### 🗃️ Repository Pattern & Unit of Work

| Source | Type | Link |
|--------|------|------|
| **DevCreed (محمد الهلالي)** — Repository Pattern With Unit Of Work in .Net 6 (Core) | 🇪🇬 Arabic Playlist | [Repository Pattern With Unit Of Work](https://youtube.com/playlist?list=PL62tSREI9C-e6nQ47brLj00iSGddiee73&si=nLuqqnNJJj4Qrp4K) |
| **Mohamad Lawand** — Step-by-step Repository Pattern + Unit of Work with EF Core | 🇬🇧 Video | [Repository Pattern & Unit of Work](https://www.youtube.com/watch?v=-jcf1Qq8A-4) |
| **Milan Jovanović** — Generic Repository & Unit of Work in .NET 7 | 🇬🇧 Video | [Generic Repository & UoW](https://www.youtube.com/watch?v=xdibesoH8zE) |
| **Microsoft Docs** — Implementing Repository & Unit of Work in ASP.NET MVC | 📄 Docs | [Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application) |

---

### 💉 Dependency Injection

| Source | Type | Link |
|--------|------|------|
| **Passionate Coders (Mohamed El-Mehdi)** — DI explained within the ASP.NET Core for Beginners series | 🇪🇬 Arabic Video | [DI — Episode 3](https://www.youtube.com/watch?v=6j3Nzr84dqo) |
| **Nick Chapsas** — DI and clean service registration in ASP.NET Core | 🇬🇧 Video | [DI & Clean Service Registration](https://www.youtube.com/watch?v=ESdvXlrG9zQ) |
| **Milan Jovanović** — Structuring DI in ASP.NET Core the right way | 🇬🇧 Video | [Structuring DI](https://www.youtube.com/watch?v=tKEF6xaeoig) |
| **Microsoft Docs** — Dependency Injection in ASP.NET Core | 📄 Docs | [DI Official Docs](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection) |

---

### 🗺️ DTOs & AutoMapper

| Source | Type | Link |
|--------|------|------|
| **Mohamad Lawand** — AutoMapper + DTOs in .NET 6, full walkthrough | 🇬🇧 Video | [AutoMapper & DTOs](https://youtu.be/Wm7hN0S-AdU?si=eXoKVTDHGpTArD9V) |
| **Nick Chapsas** — Comparing the best .NET mappers (AutoMapper vs Mapster) | 🇬🇧 Video | [Best .NET Mapper in 2023](https://www.youtube.com/watch?v=U8gSdQN2jWI) |
| **AutoMapper Docs** — Official getting started guide | 📄 Docs | [automapper.org](https://docs.automapper.org/en/stable/Getting-started.html) |

---

### 🔐 ASP.NET Core Identity

| Source | Type | Link |
|--------|------|------|
| **Khalid Essaadani** — Complete ASP.NET Identity playlist in Arabic | 🇲🇦 Arabic Playlist | [ASP.NET Identity Arabic](https://www.youtube.com/playlist?list=PLwj1YcMhLRN1T3fIb-JDa4xNFfVQoljGI) |
| **Milan Jovanović** — ASP.NET Core Identity from scratch: DbContext, Roles, Registration | 🇬🇧 Video | [Identity from Scratch](https://www.youtube.com/watch?v=5WCUZ8NX8Do) |
| **Microsoft Docs** — Introduction to ASP.NET Core Identity | 📄 Docs | [Identity Official Docs](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/identity) |

---

### 🛡️ Authorization — Roles & Policies

| Source | Type | Link |
|--------|------|------|
| **Milan Jovanović** — Building a simple role-based auth system in .NET from scratch | 🇬🇧 Video | [Role-Based Auth System](https://www.youtube.com/watch?v=24r7UmuRh0A) |
| **Milan Jovanović** — Full Authentication & Authorization playlist | 🇬🇧 Playlist | [Auth Playlist](https://www.youtube.com/playlist?list=PLYpjLpq5ZDGtJOHUbv7KHuxtYLk1nJPw5) |
| **Microsoft Docs** — Introduction to Authorization | 📄 Docs | [Authorization Docs](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/introduction) |
| **Microsoft Docs** — Role-based Authorization | 📄 Docs | [Role-based Auth Docs](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/roles) |
| **Microsoft Docs** — Policy-based Authorization | 📄 Docs | [Policy-based Auth Docs](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/policies) |

