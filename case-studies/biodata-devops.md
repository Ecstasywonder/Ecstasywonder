# Biodata DevOps — Building a Verifiable Container-to-EC2 Delivery Workflow

**Focus:** Backend engineering · containers · CI · release operations  
**Technology areas:** Node.js, PostgreSQL, Docker Compose, GitHub Actions, Linux, AWS EC2 and smoke testing

## At a glance
A small biodata intake API served as a controlled environment for practicing repeatable deployments, database readiness, idempotency, health checks, release identity and rollback planning.

## STAR case study

### Situation
A working CRUD endpoint alone does not show that an application can tolerate startup sequencing, repeated client submissions or failed releases. Persistent data must also survive container replacement.

### Task
Build a database-backed HTTP service and establish a controlled path from a verified source revision to a private Linux deployment.

### Action
- Implemented validated CRUD and search/pagination endpoints plus idempotency keys for retry-safe creation.
- Containerized the API and PostgreSQL with Docker Compose, health checks and private service binding.
- Added GitHub Actions integration smoke tests using fictional data, readiness checks and disposable test resources.
- Documented manual revision selection, checked source transfer, reuse of protected runtime configuration, post-deploy checks and database-volume preservation.
- Created rollback instructions and documented schema compatibility, non-atomic replacement and mutable-build limitations.

### Result
The repository documents a reproducible CI smoke-test process and a commit-specific EC2 promotion/rollback procedure. **The deployment script does not verify the GitHub CI result itself**: an operator must check the successful workflow for the exact revision. Images are rebuilt on the deployment host, so CI/runtime artifacts are not guaranteed identical. No zero-downtime or production uptime claim is made.

## Delivery flow
```text
Source revision
      |
GitHub Actions: build + health + API smoke tests
      |
Operator verifies passing run for that exact revision
      |
Validated source transfer
      |
Private Linux host: API + PostgreSQL in Compose
      |
Post-deployment verification
      |
Manual rollback to compatible earlier release
```

## Decisions and trade-offs
- Retry-safe writes are an API reliability property, not just a client concern.
- Selecting a specific revision improves traceability over deploying an arbitrary branch head.
- Persistent volumes are preserved across rollback; schema compatibility still requires planning.
- A future stronger design would promote an immutable image digest and automatically verify the CI gate.

## Disclosure
No hostnames, SSH key paths, internal directories, credentials, ports or identifying test records are disclosed.
