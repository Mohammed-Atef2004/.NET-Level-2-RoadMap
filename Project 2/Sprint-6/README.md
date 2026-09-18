# 🏃 Sprint 6 — Advanced API Features

**Duration:** Weeks 11–12

---

## 🎯 Sprint Goal

Add a small set of practical backend features that make the API more complete without introducing unnecessary production complexity.

---

## Task 1 — Advanced Querying

### Requirements

Extend:

```
GET /api/v1/events
```

with:

#### Pagination

```
pageNumber
pageSize
```

#### Searching

- Title
- Description

#### Filtering

- Status
- Venue
- Date

#### Sorting

- Title
- StartDate
- CreatedDate

Use:

```
IQueryable
```

and apply:

```
Filter
→ Search
→ Sort
→ Pagination
```

### Deliverable

A flexible event listing endpoint.

---

## Task 2 — QR Check-in

### Requirements

Generate a QR code for confirmed registrations.

Implement:

```
Get Registration QR
Check-in Registration
```

### Rules

- Cancelled registration → reject
- Already checked-in → reject
- Valid registration → check in

### Deliverable

A complete workflow:

```
Registration
      ↓
QR
      ↓
Check-in
```

---

## Task 3 — Background Email

### Requirements

Create a simple:

```
IEmailQueue
BackgroundService
```

Send an email when:

- Registration is confirmed
- Registration is cancelled

That's it.

> ❌ No RabbitMQ.
> ❌ No Kafka.
> ❌ No distributed messaging.

### Deliverable

A simple background email-processing workflow.

---

## Task 4 — Logging

### Requirements

Configure **Serilog**.

Log:

- HTTP Method
- Request Path
- Status Code
- Execution Time
- Exceptions

And important actions:

- Event Created
- Registration Created
- Registration Cancelled
- Check-in Completed

### Deliverable

Structured application logging.

---

## Task 5 — Testing & Documentation


### Testing


#### Unit Tests

- Event validation
- Registration rules
- Check-in rules

#### Integration Tests

- Login
- Create Event
- Register
- Check-in

### Swagger

Document:

- Endpoints
- Request/Response
- Status Codes
- JWT Authentication

### API Versioning

```
/api/v1/events
/api/v1/registrations
```
