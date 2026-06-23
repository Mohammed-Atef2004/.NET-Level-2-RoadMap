# 🗺️ .NET Developer Roadmap — 3 Months / 6 Sprints

> **Goal:** Graduate a Junior .NET Developer with two complete projects, solid architectural knowledge, and interview-ready patterns.

> **Sprint structure:** Each sprint = 2 weeks. Each sprint has 2–3 tasks. Each task has detailed bullet points.

---

## 📋 Prior Knowledge (Starting Point)

|Topic|Level|
|---|---|
|C#|✅ Solid|
|LINQ|✅ Solid|
|Entity Framework Core|✅ Intermediate|
|SQL + Database|✅ Intermediate|
|MVC|✅ Intermediate|
|Web API|✅ Basic|
|Basic Authentication|✅ Basic|

---

## 🏗️ Project 1 — MVC E-Commerce System

---

### Sprint 1 — Weeks 1–2

**Architecture + Authentication**

---

#### Task 1 — Restructure the Project into Layers

Migrate from a flat Controller → DbContext structure to a proper layered architecture.

- Create a `Core` project (or folder) with two sub-folders: `Interfaces` and `Services`
- Create an `Infrastructure` project with two sub-folders: `Repositories` and `Data`
- Define `IProductRepository` in `Core/Interfaces` with methods: `GetAllAsync`, `GetByIdAsync`, `AddAsync`, `UpdateAsync`, `DeleteAsync`
- Define `IUnitOfWork` in `Core/Interfaces` with a `SaveChangesAsync()` method and a property per repository (e.g. `IProductRepository Products`)
- Implement `ProductRepository` in `Infrastructure/Repositories` — it takes `AppDbContext` via constructor injection and implements every method from the interface
- Implement `UnitOfWork` in `Infrastructure/Repositories` — it wraps `AppDbContext` and exposes all repositories
- Register `IProductRepository → ProductRepository` and `IUnitOfWork → UnitOfWork` as **Scoped** in `Program.cs`
- Create `ProductDto` and `CategoryDto` — only expose the fields the UI actually needs (no navigation properties)
- Add an AutoMapper Profile that maps `Product → ProductDto` and `Category → CategoryDto`
- Refactor `ProductsController` to inject `IUnitOfWork` and use AutoMapper — zero direct `DbContext` usage in the controller

---

#### Task 2 — Authentication & Authorization

Set up Identity, roles, and an admin user management page.

- Install and configure ASP.NET Core Identity; create `ApplicationUser : IdentityUser` with any extra fields (e.g. `FullName`)
- Add `IdentityDbContext` (or merge with existing `AppDbContext`) and run a migration
- In `Program.cs` seed two roles on startup: `"Admin"` and `"Customer"` — use `RoleManager`, only seed if roles don't exist yet
- On the Register page, auto-assign the `"Customer"` role to every new user after successful registration
- Protect every admin controller/action with `[Authorize(Roles = "Admin")]`
- Configure `AccessDeniedPath` and `LoginPath` in the cookie options so unauthenticated users are redirected to Login — no raw 403 pages
- Build a **User Management** page (admin only):
    - List all users in a table: username, email, current role, lock status
    - "Promote to Admin" / "Demote to Customer" buttons — use `UserManager.AddToRoleAsync` / `RemoveFromRoleAsync`
    - "Lock" / "Unlock" buttons — use `UserManager.SetLockoutEndDateAsync`

---

### Sprint 2 — Weeks 3–4

**File Management + Session Cart + Caching**

---

#### Task 1 — File Upload & Image Management

Handle product images professionally with full validation and lifecycle control.

- Create `IFileService` in `Core/Interfaces` with two methods: `Task<string> UploadAsync(IFormFile file, string folder)` and `Task DeleteAsync(string filePath)`
- Implement `LocalFileService` in `Infrastructure`:
    - Save files inside `wwwroot/uploads/{folder}/`
    - Generate the filename as `{Guid.NewGuid()}{Path.GetExtension(file.FileName)}` to avoid collisions
    - Return the relative path (e.g. `/uploads/products/abc123.jpg`) to store in the database
- Add validation inside `UploadAsync`:
    - Allowed extensions: `.jpg`, `.jpeg`, `.png`, `.webp`
    - Max file size: 2 MB — throw a descriptive exception if exceeded
- Register `IFileService → LocalFileService` as **Scoped** in `Program.cs`
- In the "Create Product" action: call `UploadAsync` and store the returned path in `Product.ImageUrl`
- In the "Edit Product" action: if a new file is provided, call `DeleteAsync` on the old path first, then `UploadAsync` the new one
- In the "Delete Product" action: call `DeleteAsync` before removing the database record
- In product list and detail views: use `<img src="@product.ImageUrl">` and a `?? "/images/placeholder.png"` fallback if `ImageUrl` is null

---

#### Task 2 — Session-based Shopping Cart

Build a fully functional cart stored in the user's session.

- Create a `CartItem` model with: `ProductId`, `ProductName`, `Price`, `Quantity`, `ImageUrl`
- Create `ICartService` in `Core/Interfaces` with methods: `GetCart()`, `AddItem(CartItem)`, `UpdateQuantity(productId, qty)`, `RemoveItem(productId)`, `ClearCart()`
- Implement `SessionCartService`:
    - Inject `IHttpContextAccessor`
    - Serialize/deserialize the cart list as JSON using `HttpContext.Session.GetString` / `SetString`
    - Register session in `Program.cs`: `AddSession()` + `AddDistributedMemoryCache()` + `UseSession()`
- Register `ICartService → SessionCartService` as **Scoped**
- Add an "Add to Cart" button on the Product Details page that POSTs to `CartController.AddItem`
- Build the Cart page:
    - Display each item: image, name, unit price, quantity input, line total
    - "Update" button per row to change quantity
    - "Remove" button per row to delete the item
    - Order total at the bottom
    - "Clear Cart" button at the top

---

#### Task 3 — Caching Categories

Cache the Category list so it isn't re-queried on every page load.

- Inject `IMemoryCache` into `CategoryService` (or wherever categories are fetched)
- On every call to `GetAllCategoriesAsync`:
    - Try `_cache.TryGetValue("categories", out List<CategoryDto> cached)` — return `cached` if found
    - If not found, query the database, then `_cache.Set("categories", result, TimeSpan.FromMinutes(30))`
- On every **Create**, **Update**, or **Delete** category operation, call `_cache.Remove("categories")` to invalidate immediately
- Display the active cache source visually in the admin UI (optional but useful for learning): add a `[FromCache]` label next to the category list heading that only shows when data came from cache

---

### Sprint 3 — Weeks 5–6

**Advanced EF Core + Email & Payment**

---

#### Task 1 — Soft Delete + Advanced EF Core

Take full control of queries and implement safe deletion.

- Add two columns to `Product` and `Category`: `bool IsDeleted` (default `false`) and `DateTime? DeletedAt`
- In `AppDbContext.OnModelCreating`, add a Global Query Filter on both entities:
    
    ```csharp
    modelBuilder.Entity<Product>().HasQueryFilter(p => !p.IsDeleted);modelBuilder.Entity<Category>().HasQueryFilter(c => !c.IsDeleted);
    ```
    
- Replace every hard-delete in repositories with a soft-delete: set `IsDeleted = true` and `DeletedAt = DateTime.UtcNow`, then call `SaveChangesAsync`
- Add an **Archived Products** page (admin only) that calls `.IgnoreQueryFilters()` to fetch soft-deleted products
- Add a **Restore** button on the Archived page that sets `IsDeleted = false` and `DeletedAt = null`
- Configure entities with Fluent API in separate `IEntityTypeConfiguration<T>` classes:
    - Set `MaxLength` on string columns (e.g. `Name` max 200, `Description` max 2000)
    - Mark required fields with `.IsRequired()`
    - Add an index on `Product.CategoryId`
- Add `CreatedAt` and `UpdatedAt` as Shadow Properties:
    - Declare them in `OnModelCreating`: `modelBuilder.Entity<Product>().Property<DateTime>("CreatedAt")`
    - Populate them automatically in `SaveChanges` override: set `CreatedAt` on `EntityState.Added`, set `UpdatedAt` on both `Added` and `Modified`

---

#### Task 2 — Email & Payment Integration

Send transactional emails and accept payments.

- Create `IEmailService` in `Core/Interfaces` with one method: `Task SendAsync(string to, string subject, string htmlBody)`
- Implement `MailKitEmailService` in `Infrastructure`:
    - Install `MailKit` NuGet package
    - Read SMTP settings (`Host`, `Port`, `Username`, `Password`) from `appsettings.json` via the Options Pattern
    - Build and send a `MimeMessage` using `SmtpClient`
- Create two HTML email templates as `.html` files in `Infrastructure/EmailTemplates`:
    - **Welcome Email**: greets the user by name and includes a confirmation link
    - **Order Confirmation Email**: lists ordered products (name, qty, price), subtotal, and delivery details
- Add `Order` and `OrderItem` entities:
    - `Order`: `Id`, `UserId`, `CreatedAt`, `Status` (enum: `Pending / Paid / Cancelled`), `TotalAmount`
    - `OrderItem`: `Id`, `OrderId`, `ProductId`, `ProductName`, `UnitPrice`, `Quantity`
    - Run a migration
- Build the **Checkout** page:
    - Show a summary of cart items and the total
    - A form for delivery details (name, address, phone)
    - A "Pay Now" button
- On Checkout submit (Fake Payment):
    - Create the `Order` + `OrderItems` in the database
    - Set `Status = Paid`
    - Call `ClearCart()`
    - Send the Order Confirmation Email
    - Redirect to a "Thank You" page
- Integrate **Stripe Sandbox** (replace the fake payment):
    - Install `Stripe.net`
    - On Checkout POST: create a `PaymentIntent` via Stripe API and return the `client_secret` to the view
    - Use Stripe.js on the frontend to confirm the card payment
    - On success callback: finalize the order in the database and send the email
- Add a **My Orders** page for customers: list all their orders with date, total, and status badge

---

## 🚀 Project 2 — Task Management System (REST API)

---

### Sprint 4 — Weeks 7–8

**Clean Architecture + CQRS + MediatR**

---

#### Task 1 — Clean Architecture Setup

Build the solution skeleton with proper layer separation.

- Create a new solution with 4 projects and configure project references:
    - `TaskManager.Domain` — no references to other projects
    - `TaskManager.Application` — references `Domain` only
    - `TaskManager.Infrastructure` — references `Application` and `Domain`
    - `TaskManager.API` — references `Application` only (never `Infrastructure` directly)
- In `Domain`, create a `BaseEntity` class with: `Guid Id`, `DateTime CreatedAt`, `DateTime UpdatedAt`
- In `Domain`, create three entities (all inheriting `BaseEntity`): `AppTask`, `Project`, `Comment`
    - `AppTask`: `Title`, `Description`, `Status` (enum), `Priority` (enum), `DueDate`, `ProjectId`, `UserId`
    - `Project`: `Name`, `Description`, `OwnerId`, `IList<AppTask> Tasks`
    - `Comment`: `Content`, `TaskId`, `UserId`
- In `Application`, declare interfaces:
    - `ITaskRepository` with `GetAllAsync`, `GetByIdAsync`, `AddAsync`, `UpdateAsync`, `DeleteAsync`
    - `IProjectRepository` with the same methods
    - `IUnitOfWork` with `SaveChangesAsync()` and repository properties
    - `IEmailService` and `IFileService` (signatures only — no implementation)
- In `Infrastructure`:
    - Implement `AppDbContext` with EF Core
    - Implement all repositories
    - Add a static `DependencyInjection.cs` with an `AddInfrastructure(IServiceCollection services)` extension method that registers everything
- In `API/Program.cs`, call `services.AddInfrastructure(configuration)` — the API never references Infrastructure types directly
- Verify: build the solution and confirm `Domain` has 0 external references

---

#### Task 2 — CQRS + MediatR

Implement all task operations as Commands and Queries.

- Install `MediatR` and `MediatR.Extensions.Microsoft.DependencyInjection` in the `Application` project; register with `services.AddMediatR(typeof(ApplicationAssemblyMarker))`
- Write the following **Commands** (each in its own file under `Application/Tasks/Commands/`):
    - `CreateTaskCommand` — properties: `Title`, `Description`, `Priority`, `DueDate`, `ProjectId`; handler creates the entity, calls `UnitOfWork.SaveChangesAsync`, returns the new `TaskDto`
    - `UpdateTaskCommand` — properties: `Id` + updatable fields; handler fetches the entity, updates fields, saves, returns updated `TaskDto`
    - `DeleteTaskCommand` — property: `Id`; handler fetches, soft-deletes or hard-deletes, saves, returns `bool`
- Write the following **Queries** (each in its own file under `Application/Tasks/Queries/`):
    - `GetTasksQuery` — no parameters for now; handler returns `List<TaskDto>`
    - `GetTaskByIdQuery` — property: `Id`; handler returns `TaskDto` or `null`
- Create `TaskDto` in `Application/Tasks/DTOs/` with only the fields the API consumer needs
- In `TasksController`, inject `IMediator` and send every request through it:
    
    ```csharp
    var result = await _mediator.Send(new GetTasksQuery());
    ```
    
- Add two **Pipeline Behaviors** in `Application/Behaviors/`:
    - `LoggingBehavior<TRequest, TResponse>` — logs request name and elapsed time in milliseconds
    - `ValidationBehavior<TRequest, TResponse>` — runs FluentValidation validators; throws `ValidationException` if any fail
- Register behaviors in the correct order in DI: `LoggingBehavior` first, then `ValidationBehavior`

---

### Sprint 5 — Weeks 9–10

**JWT Auth + Exception Handling & Logging**

---

#### Task 1 — JWT Authentication + Refresh Tokens

Secure the API with a professional token-based auth flow.

- Add JWT config to `appsettings.json`:
    
    ```json
    "Jwt": { "SecretKey": "...", "Issuer": "TaskManager", "Audience": "TaskManagerUsers", "AccessTokenExpiryMinutes": 15, "RefreshTokenExpiryDays": 7 }
    ```
    
- Bind to a `JwtOptions` class via the Options Pattern and register in DI
- Create `ITokenService` in `Application` with: `string GenerateAccessToken(ApplicationUser user)` and `string GenerateRefreshToken()`
- Implement `TokenService` in `Infrastructure`:
    - Access token: use `JwtSecurityTokenHandler`, include Claims `sub` (userId), `email`, `role`; sign with `HmacSha256`
    - Refresh token: generate a cryptographically random base64 string via `RandomNumberGenerator`
- Add a `RefreshToken` entity: `Id`, `Token`, `UserId`, `ExpiresAt`, `IsRevoked`, `CreatedAt` — run a migration
- Implement the auth endpoints in `AuthController`:
    - `POST /api/auth/register` — create user, assign `"User"` role, send welcome email, return 201
    - `POST /api/auth/login` — validate credentials, generate both tokens, store refresh token in DB, return `{ accessToken, refreshToken, expiresAt }`
    - `POST /api/auth/refresh` — validate the incoming refresh token (exists in DB, not expired, not revoked), generate new access token, return it
    - `POST /api/auth/logout` — find the refresh token in DB, set `IsRevoked = true`, return 204
- Add `[Authorize]` to all Task and Project controllers
- In every handler that creates or fetches tasks, extract `userId` from `IHttpContextAccessor` Claims — a user can only see and modify their own tasks

---

#### Task 2 — Global Exception Handling, Result Pattern & Logging

Make the API production-grade in terms of error handling and observability.

- Create `Result<T>` in `Application/Common/`:
    
    ```csharp
    public class Result<T> {    public bool IsSuccess { get; }    public T? Value { get; }    public string? Error { get; }    public string? ErrorCode { get; }    public static Result<T> Success(T value) => ...;    public static Result<T> Failure(string error, string errorCode) => ...;}
    ```
    
- Create a static `ErrorCodes` class with string constants: `NotFound`, `Unauthorized`, `ValidationFailed`, `Conflict`, `BusinessRuleViolation`
- Refactor all handlers to return `Result<TaskDto>` (or `Result<bool>`) instead of throwing exceptions for business errors
- Create custom exception classes in `Application/Exceptions/`:
    - `NotFoundException(string entityName, object key)`
    - `ValidationException(IEnumerable<ValidationFailure> failures)`
    - `UnauthorizedException(string message)`
- Write `GlobalExceptionMiddleware` in `API/Middleware/`:
    - Wrap the entire `next(context)` call in a try/catch
    - Map exception types to HTTP status codes and `ProblemDetails` responses:
        - `NotFoundException` → 404
        - `ValidationException` → 400 with a `errors` dictionary (field → message list)
        - `UnauthorizedException` → 401
        - Any other `Exception` → 500 with a generic message (never expose the stack trace in production)
    - Register the middleware as the **first** middleware in `Program.cs`
- Install **Serilog** and configure two sinks:
    - Console sink with `outputTemplate` showing timestamp, level, and message
    - File sink writing to `logs/log-.txt` with daily rolling (`rollingInterval: RollingInterval.Day`)
- Set log levels in `appsettings.json`:
    - `Information` for normal request flow
    - `Warning` for business-rule failures (e.g. task not found)
    - `Error` for unhandled exceptions
- Apply the **Options Pattern** for all external config sections: `JwtOptions`, `EmailOptions`; bind in `DependencyInjection.cs`

---

### Sprint 6 — Weeks 11–12

**Pagination & Filtering + Background Services + Deployment**

---

#### Task 1 — Pagination, Filtering, Sorting & FluentValidation

Build professional, query-rich endpoints.

- Create `PaginationParams` in `Application/Common/`:
    - `int Page` (default 1), `int PageSize` (default 10, max 50)
    - `string? SortBy`, `string? SortOrder` (default `"asc"`)
- Create `PaginatedResult<T>` in `Application/Common/`:
    - `IEnumerable<T> Data`
    - `int CurrentPage`, `int PageSize`, `int TotalCount`, `int TotalPages`
- Update `GetTasksQuery` to include `PaginationParams` plus filter fields: `string? Search`, `TaskStatus? Status`, `Priority? Priority`, `Guid? ProjectId`
- Update `GetTasksQueryHandler`:
    - Build the EF Core query step by step — first filter, then search, then sort, then paginate
    - Search: `Where(t => t.Title.Contains(search) || t.Description.Contains(search))`
    - Sort: use a `switch` on `SortBy` to apply `.OrderBy` / `.OrderByDescending` on the correct column
    - Paginate: `.Skip((page - 1) * pageSize).Take(pageSize)` — run `CountAsync()` before skipping for `TotalCount`
    - Return `PaginatedResult<TaskDto>`
- The API response for `GET /api/tasks` should look like:
    
    ```json
    {  "data": [...],  "pagination": { "currentPage": 1, "pageSize": 10, "totalCount": 47, "totalPages": 5 }}
    ```
    
- Install **FluentValidation** (`FluentValidation.DependencyInjectionExtensions`) and write validators:
    - `CreateTaskCommandValidator`: `Title` required, 3–100 chars; `DueDate` must be in the future; `Priority` must be a valid enum value
    - `UpdateTaskCommandValidator`: same rules on provided fields
    - `RegisterCommandValidator`: valid email format, password min 8 chars
- The existing `ValidationBehavior` in MediatR picks up all registered validators automatically
- The error response for a validation failure must be structured:
    
    ```json
    { "errors": [{ "field": "Title", "message": "Title must be at least 3 characters" }] }
    ```
    

---

#### Task 2 — Background Services, API Docs & Deployment

Finalize and ship the project.

- Create `EmailBackgroundService` in `Infrastructure/BackgroundServices/` inheriting `BackgroundService`:
    - Inject a thread-safe `Channel<EmailMessage>` (from `System.Threading.Channels`) as a singleton queue
    - In `ExecuteAsync`, loop with `await _channel.Reader.ReadAsync(stoppingToken)` and call `IEmailService.SendAsync` for each message
    - Expose a method `EnqueueEmail(EmailMessage msg)` that other services call instead of sending directly
    - Register the service with `services.AddHostedService<EmailBackgroundService>()`
- Set up **Swagger / OpenAPI**:
    - Install `Swashbuckle.AspNetCore`
    - Enable XML documentation comments on the `API` project (project properties → enable XML doc file)
    - Add `/// <summary>` comments on every controller action
    - Configure Swagger to include the XML file and add a JWT `Bearer` security definition so you can authorize from the Swagger UI
- Add **API Versioning**:
    - Install `Microsoft.AspNetCore.Mvc.Versioning`
    - Register with `services.AddApiVersioning(options => { options.DefaultApiVersion = new ApiVersion(1, 0); options.AssumeDefaultVersionWhenUnspecified = true; })`
    - Prefix all current routes with `/api/v1/` and mark controllers with `[ApiVersion("1.0")]`
- **Deploy**:
    - Add `appsettings.Production.json` with production connection string, JWT secret (via environment variable), and `Serilog` writing to a file path accessible on the server
    - Publish to IIS: run `dotnet publish -c Release`, configure an IIS Application Pool (No Managed Code), point to the publish folder
    - Or deploy to **Azure App Service**: push from VS or GitHub Actions, set environment variables in App Service → Configuration → Application Settings

---

## 📊 Skills Progression

```
Sprint 1–3 (Project 1)           Sprint 4–6 (Project 2)
──────────────────────────        ─────────────────────────────
N-Tier → Layered Architecture     Clean Architecture (4 layers)
Repository + Unit of Work         CQRS + MediatR
ASP.NET Core Identity             Pipeline Behaviors
Role & Policy Authorization       JWT + Refresh Tokens
File Upload & Management          Global Exception Handling
Session Cart                      Result Pattern
Memory Cache                      Serilog Logging
Soft Delete + EF Core Fluent API  FluentValidation
Email + Stripe Payments           Pagination + Filtering
                                  Background Services
                                  Swagger + API Versioning
                                  Deployment (IIS / Azure)
```
