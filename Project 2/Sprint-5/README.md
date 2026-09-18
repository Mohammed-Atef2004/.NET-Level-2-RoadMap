# 🏃 Sprint 5 — Core Event Management & Security

**Duration:** Weeks 9–10

---

## 🎯 Sprint Goal

Build the core Event Management API on top of the Light Clean Architecture established in Sprint 4.

Focus on event management, ticketing, registration, authentication, authorization, and validation.

---

## Task 1 — Event Management

### Requirements

Create:

- `Event`
- `Venue`
- `Speaker`

Implement:

- Create Event
- Get Event
- Get Events
- Update Event
- Delete Event
- Publish Event
- Cancel Event

### Basic Rules

- Start date < End date
- Registration deadline < Start date
- Cancelled events cannot accept registrations
- Only the organizer can modify their event

### Concepts

- CQRS
- MediatR
- DTOs
- EF Core Relationships
- Business Validation

### Deliverable

A functional Event Management module.

---

## Task 2 — Tickets & Registration

### Requirements

Create:

**`TicketType`**

- `Name`
- `Price`
- `Quantity`
- `EventId`

**`Registration`**

- `EventId`
- `TicketTypeId`
- `UserId`
- `RegisteredAt`
- `Status`

Implement:

```
Register
Get My Registrations
Get Registration
Cancel Registration
```

### Rules

- Cannot register twice for the same event
- Cannot register after the registration deadline
- Cannot register for a cancelled event
- Cannot exceed ticket quantity
- User can cancel their own registration

### Deliverable

A complete **Event → Ticket → Registration** workflow.

---

## Task 3 — Authentication & Authorization

### Requirements

Implement:

- Register
- Login
- Refresh Token
- Logout

Roles:

```
Admin
Organizer
Attendee
```

Authorization:

| Role | Permissions |
|------|-------------|
| **Admin** | Manage system |
| **Organizer** | Manage own events |
| **Attendee** | Register for events |

Use:

- JWT
- Claims
- Role-based Authorization
- Policy-based Authorization

### Deliverable

A secured API with authentication and authorization.

---

## Task 4 — Validation & Error Handling

### Requirements

Use **FluentValidation** for:

- `CreateEvent`
- `UpdateEvent`
- `CreateTicket`
- `RegisterForEvent`

Use the existing Validation Pipeline.

Implement:

```
Result<T>
ProblemDetails
Global Exception Handling
```

Handle:

| Status Code | Meaning |
|-------------|---------|
| `400` | Bad Request |
| `401` | Unauthorized |
| `403` | Forbidden |
| `404` | Not Found |
| `409` | Conflict |
| `500` | Internal Server Error |

### Deliverable

Consistent validation and error responses.
