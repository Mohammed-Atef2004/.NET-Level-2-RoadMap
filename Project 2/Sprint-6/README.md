# 🏃 Sprint 6 — Testing & Background Processing

- **Duration:** 2 Weeks
- **Expected Effort:** 10–15 hours/week
- **Project:** Task Management API (no new domain is introduced; all work extends the existing system)

---

## 🎯 Sprint Goal

Improve the reliability of the existing Task Management API through automated testing, then introduce background job processing for tasks that do not need to run inside the HTTP request.

---

# Week 1 — Testing

## 📚 Topics

- Unit Testing
- xUnit
- Arrange / Act / Assert
- Test Naming & Structure
- Mocking
- Testing Business Rules
- Testing Success & Failure Cases
- Integration Testing Fundamentals

## 🛠️ Tasks

### Task 1 — Unit Testing

Create unit tests for the existing business rules.

Test cases should include:

- [ ] Valid Task Status Transition
- [ ] Invalid Task Status Transition
- [ ] Invalid Project when creating a Task
- [ ] Invalid Task when adding a Comment
- [ ] Invalid User Assignment

> Focus on testing **business behavior**, not implementation details.

### Task 2 — Integration Testing

Add a small number of integration tests for the main application workflow.

Test the critical flow:

```
Register
   ↓
Login
   ↓
Create Project
   ↓
Create Task
   ↓
Assign Task
   ↓
Complete Task
```

> No need to test every endpoint.

## 📦 Week 1 Deliverable

A test suite covering the most important business rules and one critical end-to-end API workflow.

---

# Week 2 — Background Processing

## 📚 Topics

- Background Jobs
- Hangfire
- Quartz.NET
- Immediate vs Delayed Jobs
- Recurring Jobs
- Job Scheduling
- Job Retries & Failure Handling
- When to use Background Processing

## 🛠️ Tasks

### Task 3 — Hangfire

Integrate Hangfire into the existing application.

Implement at least one background job related to the existing Task Management domain.

Example:

```
Task Completed
      ↓
Background Job
      ↓
Process Activity / Notification
```

> The processing can initially be simulated through structured logging.

- [ ] Install and configure Hangfire (storage + server)
- [ ] Enqueue a job when a Task is completed
- [ ] Log the processing using structured logging
- [ ] Configure retries / failure handling

### Task 4 — Quartz.NET

Integrate Quartz.NET for scheduled processing.

Implement a recurring job such as:

```
Daily Scheduled Job
        ↓
Find Overdue Tasks
        ↓
Process Them
        ↓
Log the Result
```

The job should:

- [ ] Run on a defined schedule
- [ ] Query overdue tasks
- [ ] Process the results
- [ ] Log the execution
- [ ] Handle cancellation/failure appropriately

## 📦 Week 2 Deliverable

A working background-processing system demonstrating both:

```
Hangfire
→ Background / delayed job execution

Quartz.NET
→ Scheduled / recurring job execution
```

---

## 🎯 Sprint Outcome

By the end of Sprint 6, students should be able to:

- Write meaningful unit tests for backend business rules.
- Understand the difference between unit and integration testing.
- Test a critical API workflow.
- Understand why some work should run outside the HTTP request.
- Implement background jobs using Hangfire.
- Implement scheduled jobs using Quartz.NET.
- Handle basic job failures and retries.
- Apply background processing to an existing business domain.

---

# 📖 Resource Bank

> **Note:** The docs and article links come from general knowledge, so if a link has moved, open the site's home page and search inside it. The YouTube videos in the last section all came from actual searches, and each one is listed with its title so you can find it again if the URL changes.

## Week 1 — Testing

### 1. Unit Testing + AAA + Naming

- [Unit testing best practices (Microsoft Learn)](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices): The most important source. Covers AAA, naming, and avoiding logic inside tests.
- [Unit testing C# with xUnit (Microsoft Learn)](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-csharp-with-xunit): Hands-on walkthrough from scratch.
- [Practical Test Pyramid – Martin Fowler](https://martinfowler.com/articles/practical-test-pyramid.html): Explains the difference between unit and integration tests and when to use each.
- [Enterprise Craftsmanship – Vladimir Khorikov](https://enterprisecraftsmanship.com/): Testing **behavior, not implementation**. His book *Unit Testing Principles, Practices, and Patterns* is the strongest reference on the topic.

### 2. xUnit

- [xunit.net Docs](https://xunit.net/): The official site. Focus on `[Fact]`, `[Theory]`, `[InlineData]`, and fixtures.

### 3. Mocking

- [Mocks Aren't Stubs – Martin Fowler](https://martinfowler.com/articles/mocksArentStubs.html): The difference between mocks, stubs, and fakes.
- [NSubstitute](https://nsubstitute.github.io/): Easy to use, and the tests read cleanly.
- [Moq](https://github.com/devlooped/moq): The most popular, but review its open issues before you commit to it.
- If your domain logic lives inside clean entities, you can test it without any mocks at all.

### 4. Assertions

- [Shouldly](https://docs.shouldly.org/): Free.
- [FluentAssertions](https://fluentassertions.com/): Popular, but version 8 and later require a commercial license for commercial use, so check the license before using it.

### 5. Integration Testing

- [Integration tests in ASP.NET Core (Microsoft Learn)](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests): Covers `WebApplicationFactory`, `HttpClient`, and replacing services. This is the foundation for Task 2.
- [Testcontainers for .NET](https://dotnet.testcontainers.org/): Runs a real SQL Server or Postgres in Docker during tests.
- [Respawn](https://github.com/jbogard/Respawn): Resets the database between tests.
- Ready-made examples that include unit and integration test projects:
  - [Jason Taylor – CleanArchitecture](https://github.com/jasontaylordev/CleanArchitecture)
  - [Ardalis – CleanArchitecture](https://github.com/ardalis/CleanArchitecture)

## Week 2 — Background Processing

### 1. General Concepts + When to Use Background Jobs

- [Background tasks with hosted services (Microsoft Learn)](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services): The foundation that Hangfire and Quartz are built on.
- [Milan Jovanović – Blog](https://www.milanjovanovic.tech/): Articles on background jobs, Quartz, and Hangfire in a Clean Architecture context.

### 2. Hangfire

- [Hangfire Documentation](https://docs.hangfire.io/en/latest/): The main reference.
- Job types (see the Background Methods section):
  - Fire-and-forget → `BackgroundJob.Enqueue`
  - Delayed → `BackgroundJob.Schedule`
  - Recurring → `RecurringJob.AddOrUpdate`
  - Continuations
- [Dealing with exceptions](https://docs.hangfire.io/en/latest/background-processing/dealing-with-exceptions.html): Retries and `[AutomaticRetry]`.
- Dashboard: enable it and secure it with an authorization filter.
- **Tip for Task 3:** The job must be **idempotent**, because retries can cause it to run more than once. Also pass only the Id as an argument, not a whole entity.

### 3. Quartz.NET

- [Quartz.NET Documentation](https://www.quartz-scheduler.net/documentation/): The main reference.
- Key lessons: Jobs, Triggers, and CronTrigger. Focus on:
  - `IJob` and `JobDataMap`
  - `[DisallowConcurrentExecution]` so the same job does not run twice at the same time
  - Misfire instructions
- The Microsoft DI Integration page (`AddQuartz` and `AddQuartzHostedService`) is the right approach in ASP.NET Core.
- **Tip for Task 4:** Quartz runs jobs in a new scope, so if you need a `DbContext`, use `IServiceScopeFactory` or the DI integration. Also pass the `CancellationToken` to every query.

### 4. Hangfire vs Quartz

- Search for "Hangfire vs Quartz.NET".
- The gist: Hangfire is easier and ships with a dashboard and persistence out of the box, while Quartz is stronger for complex scheduling, cron, and calendars.

## 🎥 YouTube Videos (from actual searches)

### Week 1 — Testing

**Unit Testing + xUnit + AAA**
- [Unit Testing with xUnit & .NET Core](https://www.youtube.com/watch?v=WyYQCihvLDg): First video in a series on xUnit, starting with the basic definitions. Good starting point.
- [xUnit Testing C# Asp.Net Core: A complete course for beginners](https://www.youtube.com/watch?v=fVVNOkbLcPw): Full course from scratch, covering both unit and integration testing.
- [xUnit Testing C# Asp.Net Core: Mastering Unit Testing in C# with xUnit (Playlist)](https://www.youtube.com/playlist?list=PLaFzfwmPR7_LlpcyBEOZBrYpZv3MppZNB): A complete playlist if you want to go video by video.
- [NDC Minnesota Workshop: Introduction to Effective testing in C# and .NET – Nick Chapsas](https://www.youtube.com/watch?v=kJFB8o78FBs): A long workshop on effective testing. Great once you finish the basics.
- [Make Your .NET Tests Insanely Faster – Nick Chapsas](https://www.youtube.com/watch?v=eE7PWWV1ykE): Optional, for when the basics feel comfortable.

**Unit Testing (Arabic-language)**
- [Introduction To Unit Test In C# (Part 1, Arabic-language)](https://www.youtube.com/watch?v=lY4Q8fZYSN8): Introduction to testing and what a unit test is, plus a comparison of MSTest, NUnit, and xUnit.

**Mocking**
- [NSubstitute Mocking framework for .NET [C#]](https://www.youtube.com/watch?v=sjHJfk4bRa0): An explanation of NSubstitute.
- [Mocking with NSubstitute](https://www.youtube.com/watch?v=aTx8_79QkDE): An older video, but the mocking and collaborator concepts are the same.

**Integration Testing**
- [Master ASP.NET Core Integration Testing (WebApplicationFactory + Testcontainers + xUnit)](https://www.youtube.com/watch?v=zaRM0iIhJvs): Explains `WebApplicationFactory`, swapping the database, Testcontainers, and Bogus. The closest video to Task 2.

### Week 2 — Background Processing

**Hangfire**
- [Hangfire in ASP.NET Core – Handle Background Jobs Easily (Code Maze)](https://www.youtube.com/watch?v=UGVVpvBYUaI): Explains Hangfire and its job types in ASP.NET Core. A companion written article is available: [Hangfire with ASP.NET Core](https://code-maze.com/hangfire-with-asp-net-core/).
- [Background Jobs (Tasks) Using Hangfire in .Net 6 – 1. Prepare Your Project (Arabic-language)](https://www.youtube.com/watch?v=hnK1qn6ZjKo): Part 1 of an Arabic-language series on Hangfire. The remaining parts should be on the same channel.

**Quartz.NET**
- [Schedule Jobs With Quartz.NET in ASP.NET Core (Code Maze)](https://www.youtube.com/watch?v=8u13lX3GXoo): Jobs, triggers, cron, and persistence.
- [Quartz.NET Job Scheduler in C# (Playlist)](https://www.youtube.com/playlist?list=PLzATctVhnsggHnboJ_FUtgsR4-KveqkzX): A series on building job scheduling with Quartz.
- [Job Keys And Bulk Scheduling – Quartz NET Best Practices](https://www.youtube.com/watch?v=dOZVtRIksHU): Best practices for naming and managing jobs.
- [Scheduling Background Jobs in C# .NET 10 with Quartz.NET](https://www.youtube.com/watch?v=HYAVLQVVito): A simple step-by-step console app example.

> ⚠️ **Important warning about Quartz:** The Code Maze article has been updated for **Quartz.NET 4**, and it notes that the video uses `UseJsonSerializer()`, which **no longer exists** in version 4. The replacement is `UseSystemTextJsonSerializer()`. Also, in version 4, DI and hosting support moved into the main `Quartz` package, so you no longer need to install `Quartz.Extensions.Hosting` separately. In addition, `Execute` now receives a `CancellationToken` as a second parameter. So **watch the video for the concepts, and copy the code from the written article**: [Quartz.NET in C#: How to Schedule Jobs](https://code-maze.com/schedule-jobs-with-quartz-net/). This also helps with Task 4, since you need cancellation handling.

### Note on Arabic-language content

I searched for Arabic-language tutorials on **Integration Testing**, **Mocking**, and **Quartz.NET** and could not find clear videos I could verify, so I did not include links I am unsure about. Rely on the English videos above together with the official docs. You can also try searching YouTube for each topic name with the word "Arabic" added.

### 📌 Channels to Follow (verify on YouTube)

- **Nick Chapsas** (his testing videos appear above)
- **Code Maze** (their Hangfire and Quartz videos appear above)
- **Milan Jovanović**: Excellent written articles on Testcontainers and background jobs (links are in the sections above).

---

## ✅ Sprint Checklist

**Week 1**
- [ ] Read Unit testing best practices
- [ ] Task 1: Write the 5 groups of unit tests
- [ ] Read Integration tests in ASP.NET Core
- [ ] Task 2: Integration test for the main workflow

**Week 2**
- [ ] Read Hangfire docs (Background Methods + Exceptions)
- [ ] Task 3: Hangfire job on Task Completed
- [ ] Read Quartz.NET docs + DI Integration
- [ ] Task 4: Daily overdue tasks job
