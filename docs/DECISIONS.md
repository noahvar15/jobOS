# JobOS Architecture Decisions

This document records important technical and architectural decisions made during development.

The purpose is to document the reasoning behind decisions rather than simply recording what technology was selected.

---

## ADR-001: React + TypeScript Frontend

### Decision

Use React with TypeScript for the frontend.

### Reasoning

React is widely used in professional software development and provides valuable experience for frontend engineering roles.

TypeScript adds static typing and improves maintainability for a larger application.

The project will use React as a way to gain practical experience building a real frontend rather than only small components or tutorials.

---

## ADR-002: ASP.NET Core Backend

### Decision

Use C# with ASP.NET Core for the backend.

### Reasoning

ASP.NET Core provides experience with:

- C#
- REST APIs
- Dependency injection
- Middleware
- Authentication
- Authorization
- Entity Framework Core
- Backend architecture

These are valuable skills for software engineering roles.

The backend should follow standard ASP.NET Core conventions rather than introducing unnecessary custom architecture.

---

## ADR-003: PostgreSQL

### Decision

Use PostgreSQL as the primary relational database.

### Reasoning

JobOS contains highly relational data.

Examples include:

- Users have applications
- Applications belong to jobs
- Jobs belong to companies
- Applications have interviews
- Applications have follow-ups
- Companies have contacts

A relational database is therefore a natural fit.

PostgreSQL also provides strong SQL capabilities and is widely used in production systems.

---

## ADR-004: Entity Framework Core

### Decision

Use Entity Framework Core for database access.

### Reasoning

Entity Framework Core provides practical experience with:

- ORM concepts
- Database modeling
- Relationships
- LINQ
- Migrations
- Transactions
- Query optimization

Raw SQL may still be used when it provides a meaningful advantage.

---

## ADR-005: REST API

### Decision

Use a REST API between the frontend and backend.

### Reasoning

A REST API creates a clear separation between the frontend and backend.

It also provides practical experience with:

- HTTP
- API design
- JSON
- HTTP status codes
- Authentication
- Validation
- Error handling

---

## ADR-006: Background Processing

### Decision

Long-running or asynchronous work should eventually be handled by background workers rather than blocking normal API requests.

### Reasoning

Operations such as email synchronization and job URL processing may take significant time.

The API should respond quickly and allow background workers to process tasks independently.

---

## ADR-007: Redis

### Decision

Redis will be introduced when the application has a real need for a background job queue.

### Reasoning

Redis provides useful experience with:

- In-memory data stores
- Queues
- Asynchronous processing
- Distributed systems concepts

However, Redis should not be added simply to increase the number of technologies in the project.

The application should first establish a real need for asynchronous processing.

---

## ADR-008: Docker

### Decision

Use Docker once the application has enough infrastructure to benefit from consistent environments.

### Reasoning

JobOS will eventually contain multiple services.

Potentially:

- Frontend
- Backend
- PostgreSQL
- Redis
- Background worker

Docker will make local development and deployment more reproducible.

Docker should not unnecessarily complicate the earliest stages of development.

---

## ADR-009: Monolithic Backend

### Decision

Start with a modular monolithic backend rather than microservices.

### Reasoning

JobOS is initially a single application with a relatively small user base.

A modular monolith provides:

- Simpler development
- Easier debugging
- Easier deployment
- Lower infrastructure complexity
- Clear separation of application domains

Microservices should only be considered if the application eventually develops a genuine need for them.

---

## ADR-010: Build Incrementally

### Decision

Build JobOS incrementally instead of implementing the entire architecture immediately.

### Reasoning

The primary purpose of the project is both to create a useful product and to develop software engineering skills.

Introducing technologies only when they solve a real problem makes it easier to understand why they exist and prevents unnecessary complexity.