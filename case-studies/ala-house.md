# Àlà House — Designing a Distributed Hospitality Operations Platform

**Focus:** Distributed systems · backend engineering · DevOps  
**Technology areas:** TypeScript, Next.js, PostgreSQL, Redis, messaging, object storage, Docker, testing and CI

## At a glance
Àlà House is a hospitality engineering project covering guest booking, administration, point of sale, payments, commerce and asynchronous processing. The aim was to demonstrate explicit service boundaries, transaction correctness, recovery and testable operations rather than merely a marketing website.

## STAR case study

### Situation
Hotel operations require consistent availability, reservation state, stock accounting, payments and staff permissions. Interactions across these domains create concurrency and partial-failure risks.

### Task
Design and implement a modular system with clear domain ownership, recoverable business operations and repeatable local verification environments.

### Action
- Organized guest, admin and POS applications around service boundaries for identity, hotel operations, payments, commerce, an API gateway and workers.
- Designed PostgreSQL ownership boundaries, transaction constraints and validation for reservation, inventory and financial invariants.
- Introduced idempotent request handling, event/outbox patterns and duplicate-processing controls for cross-service workflows.
- Added containerized environments, health/readiness checks, security controls, automated test categories, CI checks and operational runbooks.
- Documented edge cases including delayed payment confirmation, expired holds and partial service failures.

### Result
The private project includes a multi-application/service engineering implementation and operational documentation. It is **not an approved production hotel platform**. Managed hosting, production TLS and secrets management, real payment-provider configuration and deployment-specific reliability verification remain outstanding.

## Simplified architecture
```text
Guest UI      Admin UI      POS UI
    \            |           /
      Application/API boundary
                 |
     Identity / Reservations / Commerce
                 |
          Payment workflows
                 |
       Events + background jobs
                 |
        Domain-owned data

Supporting capabilities: caching, content management,
object storage, containerized delivery and CI
```

*This is a conceptual view, not a disclosure of private network topology.*

## Engineering decisions
- Keep reservation/allocation transactions and stock/POS transactions within appropriate domain boundaries.
- Make retries and delayed callbacks explicit rather than assuming exactly-once delivery.
- Enforce key business invariants at the database boundary.
- Distinguish development controls from controls required before real-world deployment.

## Limitations
No real guest transaction volume, throughput, uptime, payment settlement or completed production rollout is claimed.

## Disclosure
No proprietary code, credentials, customer records, internal network routes or environment-specific deployment settings are included.
