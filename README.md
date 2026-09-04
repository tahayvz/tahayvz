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
- **Next.js / React / TypeScript** frontend

Source is private (it runs a live business), but I'm glad to walk through the architecture.

#### [kervan](https://github.com/tahayvz/kervan) — event-driven commerce platform
Spring Boot microservices with a **Transactional Outbox**: an order and its event are
written in one database transaction, and a separate publisher moves the event to Kafka.
Writing to a database and publishing to a broker are two systems with no shared
transaction — a crash between them either loses the event or invents one, and no retry
can tell you which happened. Putting the event in the same transaction removes the
question.

Hexagonal architecture, **6 ADRs** recording why each choice was made, polyglot
persistence (MongoDB for catalog, PostgreSQL for orders), and 78 tests — the end-to-end
one runs against real PostgreSQL and Kafka containers.
`Java 21` `Spring Boot` `Kafka` `PostgreSQL` `MongoDB` `Flyway` `Testcontainers` `Docker` `GitHub Actions`

#### [anadolu-flight-system](https://github.com/tahayvz/anadolu-flight-system)
Four services behind a gateway — booking, flight operations and external feed integration
— coordinated by a **Saga orchestrator** with a transactional outbox, Redis-backed saga
state, circuit breakers and a dead-letter queue. Helm charts included. The booking rules
were extracted out of the Spring service into a plain class with an injected `Clock`, so
"is a 12-year-old an adult?" is answered in 80 ms instead of a 40-second context boot.
The airline is fictional.
`Java 17` `Spring Cloud Gateway` `Kafka` `Redis` `Saga` `Testcontainers` `Helm`

#### [anadolu-flight-web](https://github.com/tahayvz/anadolu-flight-web)
The React client for the platform above, and the part I find more interesting than the
booking forms: an **operations panel for distributed-system failures**. It reads the
backend's saga state — which step a booking is stuck on, what has been compensated — and
lets an operator retry a saga or reprocess a message sitting in the dead-letter queue.
Live flight status runs over a native `WebSocket` with hand-written STOMP frames rather
than a 50 kB client library. No `any` in the codebase, including `catch` blocks: the
error narrowing lives in one tested helper, covering the case that actually breaks — a
network failure with no response object at all.
`React 19` `TypeScript` `Vite` `Zustand` `Tailwind` `STOMP` `Vitest`

#### [spring-reactive-streaming](https://github.com/tahayvz/spring-reactive-streaming)
WebFlux backpressure, stream composition and R2DBC, built around one question: virtual
threads made blocking cheap, so what is reactive still for? The answer is **backpressure**
— a fast producer being told to slow down, which virtual threads have no way to signal.
The three overflow strategies are measured, not asserted: `BUFFER` fails loudly at
capacity, `DROP_LATEST` keeps the oldest values, `DROP_OLDEST` keeps the newest. Includes
an honest section on when *not* to reach for reactive.
`Java 21` `Spring WebFlux` `Project Reactor` `R2DBC` `Testcontainers`

#### [java-concurrency-benchmarks](https://github.com/tahayvz/java-concurrency-benchmarks)
Virtual threads, platform pools and parallel streams measured with JMH against the same
workload. Two findings the usual summary gets wrong: on CPU-bound work virtual threads
give **no speedup at all** — identical to a fixed pool, because there is no blocking to
unmount from; and a `synchronized` block around a wait costs **7.7× on 14 cores, 24× on
4** by pinning the carrier thread. Measured, reproduced in CI, and the arithmetic matches
the mechanism.
`Java 21` `Virtual Threads` `JMH` `JUnit 5`

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

**DevOps & testing** Docker · Docker Compose · CI/CD · nginx · Maven · Git · JUnit 5 · Testcontainers · Vitest

**Frontend** React · Next.js · Angular

**Integrations** SAP Cloud (REST)

---

### Contact

[LinkedIn](https://linkedin.com/in/tahayavuz) · [tahayavuz5@gmail.com](mailto:tahayavuz5@gmail.com)
