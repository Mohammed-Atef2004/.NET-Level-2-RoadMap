# Sprint 5 — Testing, AI & Payment Integration

> Project: **TeamFlow — Project & Team Operations Platform**
> Duration: **2 weeks (~15 hours/week)**
> Evaluation: **100 points**

## Sprint Goal

Verify important backend behavior and safely integrate an AI assistant and one payment provider.
## How to use this sprint plan

For every task:

1. Read the **MUST** resources before implementation.
2. Read **DEEP DIVE** only when the concept is unclear or the learner wants deeper understanding.
3. Implement the requested TeamFlow change.
4. Verify the behavior manually.
5. Add/update tests when the task naturally requires them.
6. Commit the work in small, meaningful commits.
7. Be able to explain the architectural decision during review.

**Important:** This document does not change the original Sprint scope. It expands the original tasks into an executable checklist.

## Sprint Tasks

### Task 1 — Unit Test Strategy

Identify the most important business logic and use cases that require unit tests.

Do not chase arbitrary coverage percentages.

### Resources
- **MUST** — [xUnit](https://xunit.net/)
- **MUST** — [Microsoft — Testing in .NET](https://learn.microsoft.com/en-us/dotnet/core/testing/)
- **DEEP DIVE** — [Vladimir Khorikov — Unit Testing Principles, Practices, and Patterns](Book)

---

### Task 2 — Business Rule Unit Tests

Test:
- Task assignment rules
- Task completion
- Task reopening
- Project membership rules
- Important invalid operations

### Resources
- **MUST** — [xUnit](https://xunit.net/)
- **DEEP DIVE** — [Vladimir Khorikov — Enterprise Craftsmanship](https://enterprisecraftsmanship.com/)

---

### Task 3 — Application Unit Tests

Test important application use cases. Prefer behavior-focused tests over tests coupled to implementation details.

### Resources
- **MUST** — [Microsoft — Testing in .NET](https://learn.microsoft.com/en-us/dotnet/core/testing/)

---

### Task 4 — Integration Test Infrastructure

Create the infrastructure required to run integration tests.

### Resources
- **MUST** — [ASP.NET Core integration tests](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests)
- **RECOMMENDED** — [Testcontainers for .NET](https://dotnet.testcontainers.org/)

---

### Task 5 — Critical API Integration Tests

Test a small number of important HTTP workflows:
- Register → Login
- Create Project
- Create Task → Assign Task
- Complete Task

### Resources
- **MUST** — [ASP.NET Core integration tests](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests)

---

### Task 6 — AI Provider Abstraction

Create an abstraction around the AI provider. Avoid spreading provider-specific implementation across the application.

### Resources
- **MUST** — [OpenAI .NET SDK](https://github.com/openai/openai-dotnet)
- **DEEP DIVE** — [Microsoft — Dependency inversion / architecture](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures)

---

### Task 7 — AI Assistant

Implement project-related AI queries such as:
- overdue tasks
- incomplete tasks
- project status summary
- important unfinished tasks

### Resources
- **MUST** — [OpenAI API documentation](https://developers.openai.com/api/docs/)
- **MUST** — [Structured model outputs](https://developers.openai.com/api/docs/guides/structured-outputs)

---

### Task 8 — AI Authorization

Ensure users cannot ask the AI about project data they cannot access.

Authorization must happen before unauthorized project data is supplied to the provider.

### Resources
- **MUST** — [ASP.NET Core resource-based authorization](https://learn.microsoft.com/en-us/aspnet/core/security/authorization/resource-based)
- **MUST** — [OpenAI safety best practices](https://developers.openai.com/api/docs/guides/safety-best-practices)

---

### Task 9 — AI Failure Handling

Handle:
- Timeout
- Provider failure
- Rate limiting
- Invalid responses

### Resources
- **MUST** — [OpenAI rate limits](https://developers.openai.com/api/docs/guides/rate-limits)
- **MUST** — [Structured model outputs](https://developers.openai.com/api/docs/guides/structured-outputs)
- **MUST** — [OpenAI safety best practices](https://developers.openai.com/api/docs/guides/safety-best-practices)

---

### Task 10 — Payment Gateway Integration

Integrate one payment provider in test mode.

### Resources
- **MUST** — [Stripe PaymentIntents](https://docs.stripe.com/api/payment_intents)

---

### Task 11 — Payment Status

Track payment status and update the appropriate TeamFlow entitlement.

### Resources
- **MUST** — [Stripe PaymentIntents](https://docs.stripe.com/api/payment_intents)

---

### Task 12 — Payment Webhook

Implement the payment webhook endpoint.

### Resources
- **MUST** — [Stripe webhooks](https://docs.stripe.com/webhooks)

---

### Task 13 — Signature Verification

Verify that webhook notifications are authentic.

### Resources
- **MUST** — [Stripe webhook signature verification](https://docs.stripe.com/webhooks/signature)

---

### Task 14 — Webhook Idempotency

Ensure duplicate webhook delivery cannot process the same event twice.

### Resources
- **MUST** — [Stripe idempotency](https://docs.stripe.com/api/idempotent_requests)
- **MUST** — [Stripe webhooks](https://docs.stripe.com/webhooks)

---

## Sprint Deliverables

- [ ] Unit tests
- [ ] Important integration tests
- [ ] Business-rule coverage
- [ ] Application-flow coverage
- [ ] AI provider abstraction
- [ ] Project AI assistant
- [ ] Authorization
- [ ] AI failure handling
- [ ] Payment integration
- [ ] Payment status
- [ ] Webhook
- [ ] Signature verification
- [ ] Idempotent webhook processing

## Definition of Done

- [ ] Important business rules tested
- [ ] Critical flows integration-tested
- [ ] AI access authorized
- [ ] AI failures handled
- [ ] Payment works in test mode
- [ ] Webhook verified
- [ ] Duplicate webhook safe

## Review Rule

The learner should be able to explain not only **what** was implemented, but **why it belongs there, what alternatives existed, and what trade-off was accepted**.