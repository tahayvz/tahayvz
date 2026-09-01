## Taha Yavuz

**Senior Software Engineer · Java & Spring** — İstanbul, Türkiye

I build enterprise backend systems: scalable REST APIs, Spring Boot services, and
event-driven architectures. 4+ years in the Java & Spring ecosystem, 6+ years in software.

I work as a senior engineer at **ebebek**, on enterprise e-commerce backend systems —
leading a small team, running code reviews, and owning services in production.

I started out writing C/C++ drivers for LCD/TFT panels and programming ARM microcontrollers.
That background still shapes how I work: I care about what actually runs in production —
latency, memory, failure modes — not just what compiles.

---

### Selected work

#### [Yavuz Collection](https://yavuzcollection.com) — e-commerce platform, live in production
*Sole engineer: architecture, implementation, deployment and operations.*

- **Microservices on Spring Boot** — API gateway, catalog, contact, image and notification services
- **Event-driven with Kafka** — retry topics and dead-letter queues for failure isolation
- **PostgreSQL** with per-service Flyway migrations
- **Defense in depth** — JWT + BCrypt, gateway-level RBAC, TOTP 2FA, brute-force lockout, IP rate limiting, audit logging, Resilience4j circuit breakers
- **Full observability** — Prometheus + Grafana, Loki, Zipkin tracing
- **CI/CD to a VPS** — Docker Compose, GHCR auto-deploy, nginx with TLS 1.3
- **Next.js 16 / React 19 / TypeScript** frontend

Source is private (it runs a live business), but I'm glad to walk through the architecture.

#### [classified-lifecycle-api](https://github.com/tahayvz/classified-lifecycle-api)
Hexagonal architecture (ports & adapters) keeping a listing lifecycle state machine
independent of Spring, JPA and HTTP — and proving it: **ArchUnit rules fail the build**
when a dependency points the wrong way. 112 unit tests plus end-to-end integration tests
on a real PostgreSQL container, behind a coverage gate rather than a badge.
`Java 17` `Spring Boot 3.5` `JPA` `Testcontainers` `ArchUnit` `JaCoCo` `Docker` `GitHub Actions`

---

### How I work

- **Domain-first architecture** — business rules stay independent of frameworks, so they can be tested without HTTP or a database
- **Event-driven where it earns its place** — Kafka with retry and DLQ, not events for their own sake
- **Tests as design pressure** — fast unit tests on pure domain logic, Testcontainers at the integration boundary
- **Measured performance work** — query and endpoint optimisation judged by before/after numbers, not by guesswork
- **End-to-end ownership** — I operate what I build, including deployment and monitoring

---

### Experience

| | | |
| --- | --- | --- |
| **2022 – present** | Senior Full-Stack Developer | **ebebek Mağazacılık A.Ş.**, İstanbul |
| **2021 – 2022** | Full-Stack Java Developer | **Etstur**, İstanbul |
| **2019 – 2021** | Embedded Software Engineer | **Sisel Elektronik**, İstanbul |

B.Sc. Electrical & Electronics Engineering — Marmara University (English-medium)

---

### Tech

**Languages** Java · TypeScript · JavaScript · SQL · C / C++

**Backend** Spring Boot · Spring MVC · Spring Cloud Gateway · Spring Data JPA · Spring Security · Hibernate · REST · OpenAPI · Resilience4j

**Data & messaging** PostgreSQL · MS SQL Server · Oracle · MySQL · Elasticsearch · Apache Kafka · Caffeine

**Observability** Prometheus · Grafana · Loki · Zipkin

**DevOps & testing** Docker · Docker Compose · CI/CD · nginx · Maven · Git · JUnit 5 · Testcontainers

**Frontend** React · Next.js · Angular

**Integrations** SAP Cloud (REST)

---

### Contact

[LinkedIn](https://linkedin.com/in/tahayavuz) · [tahayavuz5@gmail.com](mailto:tahayavuz5@gmail.com)
