# 🗺️ .NET Developer Roadmap — 3 Months / 6 Sprints

> **Goal:** Graduate a Junior .NET Developer with two complete projects, solid architectural knowledge, and interview-ready patterns.

> **Sprint structure:** Each sprint = 2 weeks. Each sprint has 2–3 tasks. Each task has detailed bullet points.


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
**File Management + Session Cart + Pagination & Caching**

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

#### Task 3 — Pagination, Search, Sorting & Caching

Make the product list scalable and fast — skills that apply to almost every CRUD screen.

**Pagination**
- Add `PageNumber` and `PageSize` query parameters to the product list action (defaults: page 1, size 10)
- Use `.Skip((page - 1) * pageSize).Take(pageSize)` in the repository to fetch only the current page
- Create a `PaginatedResult<T>` wrapper: `Items`, `TotalCount`, `PageNumber`, `PageSize`, `TotalPages`
- Render a pagination control in the view: Previous / Next buttons and page number links, disabled appropriately at boundaries

**Search**
- Add a `search` query parameter; filter products with `.Where(p => p.Name.Contains(search) || p.Description.Contains(search))` before applying pagination
- Preserve the search term across page navigations by including it in every pagination link
- Display the active search term in the search input so the user always sees what they filtered by

**Sorting**
- Add a `sortBy` query parameter accepting values: `name_asc`, `name_desc`, `price_asc`, `price_desc`
- Apply the correct `.OrderBy` / `.OrderByDescending` before pagination
- Highlight the active sort option in the UI (e.g. bold or an arrow indicator on the column header)

**Caching**
- Inject `IMemoryCache` into `CategoryService` (or wherever categories are fetched)
- On every call to `GetAllCategoriesAsync`:
  - Try `_cache.TryGetValue("categories", out List<CategoryDto> cached)` — return `cached` if found
  - If not found, query the database, then `_cache.Set("categories", result, TimeSpan.FromMinutes(30))`
- On every **Create**, **Update**, or **Delete** category operation, call `_cache.Remove("categories")` to invalidate immediately
- Display the active cache source visually in the admin UI (optional but useful for learning): add a `[FromCache]` label next to the category list heading that only shows when data came from cache

---

### Sprint 3 — Weeks 5–6
**Advanced EF Core + Email, Orders & Reviews**

---

#### Task 1 — Soft Delete + Advanced EF Core

Take full control of queries and implement safe deletion.

- Add two columns to `Product` and `Category`: `bool IsDeleted` (default `false`) and `DateTime? DeletedAt`
- Add `CreatedAt` and `UpdatedAt` as regular properties on `Product` and `Category`:
  - Declare them directly on the entity class: `public DateTime CreatedAt { get; set; }` and `public DateTime UpdatedAt { get; set; }`
  - Populate them automatically by overriding `SaveChanges` / `SaveChangesAsync` in `AppDbContext`: set `CreatedAt` on `EntityState.Added`, set `UpdatedAt` on both `Added` and `Modified`
- In `AppDbContext.OnModelCreating`, add a Global Query Filter on both entities:
  ```csharp
  modelBuilder.Entity<Product>().HasQueryFilter(p => !p.IsDeleted);
  modelBuilder.Entity<Category>().HasQueryFilter(c => !c.IsDeleted);
  ```
- Replace every hard-delete in repositories with a soft-delete: set `IsDeleted = true` and `DeletedAt = DateTime.UtcNow`, then call `SaveChangesAsync`
- Add an **Archived Products** page (admin only) that calls `.IgnoreQueryFilters()` to fetch soft-deleted products
- Add a **Restore** button on the Archived page that sets `IsDeleted = false` and `DeletedAt = null`
- Configure entities with Fluent API in separate `IEntityTypeConfiguration<T>` classes:
  - Set `MaxLength` on string columns (e.g. `Name` max 200, `Description` max 2000)
  - Mark required fields with `.IsRequired()`
  - Add an index on `Product.CategoryId`

---

#### Task 2 — Email, Orders & Checkout

Send transactional emails and build a complete order flow with fake payment.

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
  - Set `Status = Paid`, call `ClearCart()`, send the Order Confirmation Email
  - Redirect to a "Thank You" page
- Add a **My Orders** page for customers: list all their orders with date, total, and status badge

---

#### Task 3 — Product Reviews

Let customers rate and review products — a small feature with high teaching value.

- Add a `Review` entity: `Id`, `ProductId`, `UserId`, `Rating` (1–5), `Comment`, `CreatedAt`
  - Configure the relationship in Fluent API: one `Product` has many `Reviews`
  - Run a migration
- On the Product Details page:
  - Display all approved reviews: reviewer name, star rating, comment, date
  - Show the average rating (use `.Average(r => r.Rating)`) next to the product title
  - Render a "Write a Review" form below (visible to logged-in customers only)
- On Review submit:
  - Validate that `Rating` is between 1 and 5
  - Prevent a user from submitting more than one review per product — check for an existing review before saving
  - Save the review and redirect back to the product page
- Allow a user to **Edit** or **Delete** their own review:
  - Protect these actions with an ownership check: `review.UserId == currentUserId` — return `403` otherwise
- Add an **admin moderation panel**: list all reviews with an "Approve / Reject" toggle; only approved reviews appear on the product page
## 🚀 Project 2 — Event Management System (REST API)

> **Domain:** A platform where organizers create and publish events, attendees register and pay for tickets, and admins get full reporting. Think Eventbrite, but as a backend API.

> **Entities:** `Event`, `Category`, `Ticket`, `Registration`, `Attendee`, `Speaker`, `Venue`, `Payment`, `Notification`

> **Roles:** `Admin`, `Organizer`, `Attendee`

---

### Sprint 4 — Weeks 7–8
**Clean Architecture + CQRS + MediatR**

---

#### Task 1 — Clean Architecture Setup

Build the solution skeleton with the correct layer separation and the full domain model.

- Create a new solution with 4 projects and configure project references:
  - `EventHub.Domain` — no references to other projects
  - `EventHub.Application` — references `Domain` only
  - `EventHub.Infrastructure` — references `Application` and `Domain`
  - `EventHub.API` — references `Application` only (never `Infrastructure` directly)
- In `Domain`, create a `BaseEntity` with: `Guid Id`, `DateTime CreatedAt`, `DateTime UpdatedAt`
- In `Domain`, create the following entities (all inherit `BaseEntity`):
  - `Event`: `Title`, `Description`, `StartDate`, `EndDate`, `Venue`, `MaxAttendees`, `Status` (enum: `Draft / Published / Cancelled / Completed`), `OrganizerId`, `CategoryId`, `CoverImageUrl`
  - `Ticket`: `EventId`, `Name` (e.g. "VIP", "General"), `Price`, `TotalQuantity`, `SoldQuantity`
  - `Registration`: `EventId`, `AttendeeId`, `TicketId`, `RegisteredAt`, `Status` (enum: `Pending / Confirmed / Cancelled`), `QRCodeUrl`
  - `Speaker`: `FullName`, `Bio`, `PhotoUrl`, `EventId`
  - `Venue`: `Name`, `Address`, `City`, `Country`, `Capacity`, `Latitude`, `Longitude`
  - `Payment`: `RegistrationId`, `Amount`, `Status` (enum: `Pending / Paid / Refunded`), `StripePaymentIntentId`, `PaidAt`
- In `Application`, declare interfaces:
  - `IEventRepository`, `IRegistrationRepository`, `ITicketRepository`, `IVenueRepository` — each with standard CRUD methods
  - `IUnitOfWork` with `SaveChangesAsync()` and a property per repository
  - `IEmailService`, `IFileService`, `IQRCodeService`, `INotificationService` — signatures only
- In `Infrastructure`:
  - Implement `AppDbContext` with EF Core and all entity configurations
  - Implement all repositories
  - Add `DependencyInjection.cs` with `AddInfrastructure(IServiceCollection, IConfiguration)` that registers everything
- In `API/Program.cs`, call `services.AddInfrastructure(configuration)` — never reference Infrastructure types directly in the API project
- Verify: build the solution and confirm `Domain` has 0 external package references

---

#### Task 2 — CQRS + MediatR

Implement all event and registration operations as Commands and Queries.

- Install `MediatR` in `Application` and register with `services.AddMediatR(typeof(ApplicationAssemblyMarker))`
- Write the following **Commands** (each in its own file under `Application/Events/Commands/`):
  - `CreateEventCommand`: `Title`, `Description`, `StartDate`, `EndDate`, `VenueId`, `CategoryId`, `MaxAttendees`; handler creates the entity with `Status = Draft`, saves, returns `EventDto`
  - `PublishEventCommand`: `EventId`; handler validates the event has at least one ticket defined, changes `Status` to `Published`, saves, returns `EventDto`
  - `CancelEventCommand`: `EventId`, `Reason`; handler sets `Status = Cancelled`, sends cancellation notifications to all registered attendees, returns `bool`
  - `RegisterForEventCommand`: `EventId`, `TicketId`, `AttendeeId`; handler checks `SoldQuantity < TotalQuantity`, creates a `Registration` with `Status = Pending`, increments `SoldQuantity`, saves, returns `RegistrationDto`
- Write the following **Queries** (each in its own file under `Application/Events/Queries/`):
  - `GetEventsQuery`: returns `List<EventSummaryDto>` (no heavy navigation properties)
  - `GetEventByIdQuery`: returns full `EventDetailDto` including tickets, speakers, and venue
  - `GetMyRegistrationsQuery`: returns all registrations for the current attendee
- Add two **Pipeline Behaviors** in `Application/Behaviors/`:
  - `LoggingBehavior<TRequest, TResponse>`: logs request name and elapsed time in milliseconds
  - `ValidationBehavior<TRequest, TResponse>`: runs FluentValidation validators; throws `ValidationException` if any fail
- Register behaviors in the correct order: `LoggingBehavior` first, then `ValidationBehavior`
- Wire up `EventsController` and `RegistrationsController` in the API — every action sends through `IMediator` only

---

### Sprint 5 — Weeks 9–10
**JWT Auth + Exception Handling + File & QR Code Management**

---

#### Task 1 — JWT Authentication + Refresh Tokens

Secure the API with role-based JWT auth.

- Add JWT config to `appsettings.json`:
  ```json
  "Jwt": { "SecretKey": "...", "Issuer": "EventHub", "Audience": "EventHubUsers", "AccessTokenExpiryMinutes": 15, "RefreshTokenExpiryDays": 7 }
  ```
- Bind to a `JwtOptions` class via the Options Pattern and register in DI
- Create `ITokenService` in `Application` with: `string GenerateAccessToken(ApplicationUser user)` and `string GenerateRefreshToken()`
- Implement `TokenService` in `Infrastructure`:
  - Access token: use `JwtSecurityTokenHandler`, include Claims `sub` (userId), `email`, `role`; sign with `HmacSha256`
  - Refresh token: generate a cryptographically random base64 string via `RandomNumberGenerator`
- Add a `RefreshToken` entity: `Id`, `Token`, `UserId`, `ExpiresAt`, `IsRevoked`, `CreatedAt` — run a migration
- Implement the auth endpoints in `AuthController`:
  - `POST /api/auth/register` — create user, assign role (`Organizer` or `Attendee` based on request), send welcome email, return 201
  - `POST /api/auth/login` — validate credentials, generate both tokens, store refresh token in DB, return `{ accessToken, refreshToken, expiresAt }`
  - `POST /api/auth/refresh` — validate the incoming refresh token (exists, not expired, not revoked), return a new access token
  - `POST /api/auth/logout` — set the refresh token `IsRevoked = true`, return 204
- Apply role-based authorization:
  - `[Authorize(Roles = "Organizer")]` on Create, Publish, Cancel Event endpoints
  - `[Authorize(Roles = "Attendee")]` on Register for Event endpoint
  - `[Authorize(Roles = "Admin")]` on reporting endpoints
- In every handler, extract `userId` from Claims via `IHttpContextAccessor` — organizers can only manage their own events

---

#### Task 2 — File Management, QR Code Generation & Exception Handling

Handle event cover images, speaker photos, and attendee QR codes, plus make the API production-grade on errors.

- **File Management:**
  - Reuse the `IFileService` / `LocalFileService` pattern from Project 1
  - Add an `UploadEventCoverAsync` endpoint: `PUT /api/events/{id}/cover` — validate image (jpg/png/webp, max 5 MB), delete old cover if it exists, save new one, update `Event.CoverImageUrl`
  - Add an `UploadSpeakerPhotoAsync` endpoint: `PUT /api/speakers/{id}/photo` — same validation, max 2 MB

- **QR Code Generation:**
  - Install `QRCoder` NuGet package
  - Create `IQRCodeService` in `Application` with: `Task<string> GenerateAsync(string content, string folder)`
  - Implement `QRCodeService` in `Infrastructure`:
    - Generate a QR code PNG from the content string using `QRCoder`
    - Save the PNG to `wwwroot/qrcodes/` with a GUID filename
    - Return the relative path to store in `Registration.QRCodeUrl`
  - After a registration is `Confirmed`, call `IQRCodeService.GenerateAsync($"REG-{registrationId}")` and update `Registration.QRCodeUrl`
  - Add a `GET /api/registrations/{id}/qrcode` endpoint that returns the QR code image file

- **Global Exception Handling & Result Pattern:**
  - Create `Result<T>` in `Application/Common/` with: `IsSuccess`, `Value`, `Error`, `ErrorCode`; static `Success(T)` and `Failure(string, string)` factory methods
  - Create a static `ErrorCodes` class: `NotFound`, `Unauthorized`, `ValidationFailed`, `Conflict`, `EventFull`, `EventNotPublished`, `AlreadyRegistered`
  - Refactor all handlers to return `Result<T>` instead of throwing for business errors (e.g. event full → `Result.Failure("No tickets left", ErrorCodes.EventFull)`)
  - Write `GlobalExceptionMiddleware` in `API/Middleware/`:
    - `NotFoundException` → 404 ProblemDetails
    - `ValidationException` → 400 with field-level errors dictionary
    - `UnauthorizedException` → 401
    - Any other `Exception` → 500 with a safe generic message (no stack trace in production)
  - Install **Serilog** with Console + daily-rolling File sinks; set `Information` / `Warning` / `Error` levels in `appsettings.json`

---

### Sprint 6 — Weeks 11–12
**Payments + Real-time Notifications + Reporting + Deployment**

---

#### Task 1 — Stripe Payments, Real-time Notifications & Reporting

Integrate payment, push live updates to clients, and give admins data they can act on.

- **Stripe Payment Integration:**
  - Install `Stripe.net` and bind `StripeOptions` (`SecretKey`, `WebhookSecret`) from `appsettings.json`
  - Add `POST /api/payments/create-intent`:
    - Receive `RegistrationId`
    - Look up the registration and its ticket price
    - Create a Stripe `PaymentIntent` with the amount in cents
    - Return `{ clientSecret }` to the frontend
  - Add `POST /api/payments/webhook` (Stripe webhook endpoint):
    - Verify the Stripe signature using `WebhookSecret`
    - On `payment_intent.succeeded`: find the matching `Payment` record by `StripePaymentIntentId`, set `Status = Paid`, set the linked `Registration.Status = Confirmed`, trigger QR code generation
    - On `payment_intent.payment_failed`: set `Payment.Status` and `Registration.Status` to `Cancelled`, release the ticket slot (decrement `SoldQuantity`)
  - Add `GET /api/payments/{registrationId}` to check payment status

- **Real-time Notifications with SignalR:**
  - Install `Microsoft.AspNetCore.SignalR` and add `services.AddSignalR()` in `Program.cs`
  - Create `NotificationHub : Hub` in `API/Hubs/` — clients connect and join a group by their `userId`
  - Create `INotificationService` in `Application` with: `Task SendToUserAsync(string userId, string message, string type)` and `Task SendToAllAsync(string message, string type)`
  - Implement `SignalRNotificationService` in `Infrastructure` — inject `IHubContext<NotificationHub>` and call `Clients.Group(userId).SendAsync("ReceiveNotification", payload)`
  - Trigger notifications from handlers:
    - When an organizer publishes an event → notify all users who follow that organizer (or all users for now)
    - When a registration is confirmed → notify the attendee: "Your ticket for {EventTitle} is confirmed!"
    - When an event is cancelled → notify all registered attendees: "{EventTitle} has been cancelled"
  - Map the hub in `Program.cs`: `app.MapHub<NotificationHub>("/hubs/notifications")`

- **Reporting & Analytics (Admin only):**
  - Add `GET /api/reports/events-summary`:
    - Return per-event stats: total registrations, confirmed count, cancelled count, total revenue
    - Use EF Core projections (`.Select(...)`) — never load full entities for reports
  - Add `GET /api/reports/revenue`:
    - Accept `?from=` and `?to=` date filters
    - Return total revenue per day grouped by date
    - Return overall totals: gross revenue, refunded amount, net revenue
  - Add `GET /api/reports/top-events`:
    - Return the top 10 events by registration count with fill rate (`SoldQuantity / TotalQuantity * 100`)
  - All report endpoints are `[Authorize(Roles = "Admin")]` and return lightweight projection DTOs (no AutoMapper — use `.Select()` directly for performance)

---

#### Task 2 — Pagination & Filtering, API Docs & Deployment

Finalize the API and ship it.

- **Pagination, Filtering & Sorting:**
  - Create `PaginationParams` in `Application/Common/`: `Page` (default 1), `PageSize` (default 10, max 50), `SortBy`, `SortOrder`
  - Create `PaginatedResult<T>`: `Data`, `CurrentPage`, `PageSize`, `TotalCount`, `TotalPages`
  - Update `GetEventsQuery` with filter fields: `string? Search` (on title/description), `Guid? CategoryId`, `string? City`, `DateTime? From`, `DateTime? To`, `EventStatus? Status`
  - Build the EF Core query step by step in the handler: filter → search → sort → paginate → `CountAsync()` for total
  - Install **FluentValidation** and write validators:
    - `CreateEventCommandValidator`: `Title` required 5–200 chars, `StartDate` must be in the future, `EndDate` must be after `StartDate`, `MaxAttendees` must be > 0
    - `RegisterForEventCommandValidator`: `EventId` and `TicketId` required
    - `CreateTicketCommandValidator`: `Price` must be ≥ 0, `TotalQuantity` must be > 0
  - The `ValidationBehavior` picks up all validators automatically and returns a structured 400

- **Swagger & API Versioning:**
  - Install `Swashbuckle.AspNetCore` and enable XML doc comments on the API project
  - Add `/// <summary>` comments on every controller action
  - Configure Swagger to include the JWT Bearer security definition so you can authorize from the Swagger UI
  - Install `Microsoft.AspNetCore.Mvc.Versioning`, register with default version `1.0`, prefix all routes `/api/v1/`

- **Deployment:**
  - Add `appsettings.Production.json` with production connection string and Stripe keys loaded from environment variables
  - Configure Serilog to write to a file path accessible on the server in production
  - Publish to **IIS**: `dotnet publish -c Release`, create an Application Pool (No Managed Code), point the site to the publish folder
  - Or deploy to **Azure App Service**: set all secrets in App Service → Configuration → Application Settings (never commit secrets to source control)

---

## 📊 Skills Progression

```
Sprint 1–3 (Project 1 — MVC)        Sprint 4–6 (Project 2 — API)
──────────────────────────────       ──────────────────────────────────
N-Tier → Layered Architecture        Clean Architecture (4 layers)
Repository + Unit of Work            CQRS + MediatR + Pipeline Behaviors
ASP.NET Core Identity                JWT + Refresh Tokens + Role-based Auth
Role & Policy Authorization          Global Exception Handling + Result Pattern
File Upload & Lifecycle Mgmt         File Management + QR Code Generation
Session Cart + Memory Cache          Stripe Webhooks + Payment Flow
Soft Delete + EF Core Fluent API     Real-time Notifications (SignalR)
Email Integration (MailKit)          Reporting & Analytics (EF Projections)
Stripe Sandbox Payments              Pagination + Filtering + FluentValidation
                                     Swagger + API Versioning + Deployment
```
## Keep Shining Up
