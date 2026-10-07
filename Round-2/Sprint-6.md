# Sprint 6 — Docker, CI/CD & Deployment

> Project: **TeamFlow — Project & Team Operations Platform**
> Duration: **2 weeks (~15 hours/week)**
> Evaluation: **100 points**

## Sprint Goal

Take TeamFlow from 'it works on my machine' to a system that can be built, tested, containerized, and deployed consistently.
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

### Task 1 — Dockerfile

Create a production-oriented Dockerfile.

Required understanding:
- build context
- layers
- build vs runtime image
- ports
- environment configuration
- multi-stage build

### Resources
- **MUST** — [Docker Get Started](https://docs.docker.com/get-started/)
- **MUST** — [Docker build best practices](https://docs.docker.com/build/building/best-practices/)

---

### Task 2 — Docker Compose

Create:
```text
API
SQL Server
Redis
```
and make the local environment reproducible.

### Resources
- **MUST** — [Docker Compose getting started](https://docs.docker.com/compose/gettingstarted/)
- **MUST** — [Compose file reference](https://docs.docker.com/reference/compose-file/)

---

### Task 3 — Environment Configuration

Move environment-specific configuration outside source code.

Examples:
- Connection strings
- JWT configuration
- Redis configuration
- AI API keys
- Payment API keys

### Resources
- **MUST** — [ASP.NET Core configuration](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/)
- **MUST** — [Docker Compose environment variables](https://docs.docker.com/compose/how-tos/environment-variables/)

---

### Task 4 — Secrets

Ensure secrets are not committed to Git.

Use environment configuration or the appropriate CI/CD secret mechanism.

### Resources
- **MUST** — [GitHub Actions secrets](https://docs.github.com/en/actions/concepts/security/secrets)
- **MUST** — [Docker build secrets](https://docs.docker.com/build/building/secrets/)

---

### Task 5 — Local Production-like Environment

Run TeamFlow through Docker Compose.

Verify:
- API starts
- SQL Server is reachable
- Redis is reachable
- configuration is injected correctly

### Resources
- **MUST** — [Docker Compose getting started](https://docs.docker.com/compose/gettingstarted/)

---

### Task 6 — GitHub Actions

Create a CI workflow for push/pull-request validation.

### Resources
- **MUST** — [GitHub Actions — Building and testing .NET](https://docs.github.com/en/actions/tutorials/build-and-test-code/net)
- **MUST** — [GitHub Actions](https://docs.github.com/en/actions)

---

### Task 7 — Build Validation

The pipeline must fail when the application does not build.

### Resources
- **MUST** — [GitHub Actions — Building and testing .NET](https://docs.github.com/en/actions/tutorials/build-and-test-code/net)

---

### Task 8 — Automated Tests

The pipeline must execute:
- Unit tests
- Integration tests

### Resources
- **MUST** — [GitHub Actions — Building and testing .NET](https://docs.github.com/en/actions/tutorials/build-and-test-code/net)

---

### Task 9 — Docker Build

Build the Docker image through CI.

### Resources
- **MUST** — [Docker build documentation](https://docs.docker.com/build/)
- **MUST** — [GitHub Actions](https://docs.github.com/en/actions)

---

### Task 10 — Deployment

Deploy the application to a real hosting environment.

The hosting provider is secondary; understanding the deployment path is the objective.

### Resources
- **MUST** — [GitHub Actions deployment documentation](https://docs.github.com/en/actions/deployment/about-deployments/deploying-with-github-actions)

---

### Task 11 — Production Verification

Verify:
- API availability
- Database connectivity
- Authentication
- Important endpoints
- Redis
- Background processing
- AI integration
- Payment integration

### Resources
- **MUST** — [ASP.NET Core health checks](https://learn.microsoft.com/en-us/aspnet/core/host-and-deploy/health-checks)
- **MUST** — [ASP.NET Core integration testing](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests)

---

### Task 12 — Final Refactoring

Review:
- Architecture
- Naming
- Dead code
- Unnecessary abstractions
- Error handling
- Business rules
- Configuration
- Logging
- API consistency

### Resources
- **DEEP DIVE** — [Robert C. Martin — Clean Architecture](Book)
- **DEEP DIVE** — [Michael Nygard — Release It!](Book)

---

### Task 13 — Final README

Document:
- Project overview
- Architecture
- Domain
- Authentication
- Authorization
- Data access
- Background processing
- Caching
- AI integration
- Payment integration
- Testing
- Docker
- CI/CD
- Deployment

### Resources
- **MUST** — [GitHub — README documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)

---

## Sprint Deliverables

- [ ] Production Dockerfile
- [ ] Docker Compose
- [ ] Environment configuration
- [ ] Secrets strategy
- [ ] GitHub Actions workflow
- [ ] Automated build
- [ ] Automated tests
- [ ] Docker image build
- [ ] Deployed API
- [ ] Production verification
- [ ] Final README
- [ ] Final refactoring

## Definition of Done

- [ ] Dockerfile works
- [ ] Docker Compose works
- [ ] API runs in Docker
- [ ] SQL Server works
- [ ] Redis works
- [ ] Configuration environment-based
- [ ] Secrets protected
- [ ] GitHub Actions succeeds
- [ ] Build automated
- [ ] Tests automated
- [ ] Docker image built automatically
- [ ] Application deployed
- [ ] Production verified
- [ ] README complete

## Review Rule

The learner should be able to explain not only **what** was implemented, but **why it belongs there, what alternatives existed, and what trade-off was accepted**.