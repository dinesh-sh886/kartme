# Kart-Me P00 — Decisions Register

Statuses: `PROPOSED`, `ACCEPTED`, `REJECTED`, `DEFERRED`, `BLOCKED`. No proposal becomes accepted by inclusion in this file.

| ID | Decision | Proposal | Status | Rationale / consequence | Required owner action |
|---|---|---|---|---|---|
| KME-DEC-001 | Project identity | New standalone Kart-Me repository; no inherited WeKart/QEVANO/RASA state | PROPOSED | Prevents accidental coupling and false assumptions | Accept |
| KME-DEC-002 | Business model | Hybrid marketplace + merchant-owned commerce SaaS | PROPOSED | Supports both marketplace and branded storefronts | Confirm transaction/merchant ownership |
| KME-DEC-003 | Tenancy | Multi-tenant from inception with explicit tenant scope | PROPOSED | Core product model; isolation is release blocker | Choose logical/physical isolation tiers |
| KME-DEC-004 | Identity provider | Keycloak using OIDC/OAuth 2.0 | PROPOSED | Central identity; services still enforce authorization | Define realm/client strategy and MFA policy |
| KME-DEC-005 | Backend baseline | Java 21 + Spring Boot; exact Boot version selected after compatibility check | PROPOSED | Stable Java baseline without prematurely pinning dependencies | Approve version policy in P01 |
| KME-DEC-006 | Frontend | Angular/TypeScript portals | PROPOSED | Shared component and API contract approach | Decide monorepo frontend structure |
| KME-DEC-007 | Deployment style | Independently deployable domain microservices | PROPOSED | Independent scaling/release boundaries; higher ops cost | Accept service decomposition and operating capacity |
| KME-DEC-008 | API protocol | REST/OpenAPI default; Kafka events; gRPC/GraphQL only by ADR | PROPOSED | Minimize unnecessary protocol sprawl | Accept |
| KME-DEC-009 | Persistence | PostgreSQL for transactions; MongoDB selectively; Redis for cache/ephemeral state | PROPOSED | Match storage to invariants and access patterns | Approve service-level ownership map |
| KME-DEC-010 | Event reliability | Transactional outbox, idempotent consumers, DLQ and reconciliation | PROPOSED | Handles DB/event dual-write and duplicate delivery | Accept |
| KME-DEC-011 | Deployment platform | Docker and OpenShift/Kubernetes | PROPOSED | Standardized container orchestration | Confirm target environment/provider |
| KME-DEC-012 | CI/CD and quality | Jenkins, PMD, SonarQube, automated tests and security scans | PROPOSED | Enforce repeatable quality gates | Define quality thresholds |
| KME-DEC-013 | Observability | Prometheus, Grafana, structured logs, traces and runbooks | PROPOSED | Production diagnostics and SLO tracking | Choose log/trace storage |
| KME-DEC-014 | Delivery scope | Broad release with all named portals and advanced operations | PROPOSED | Full intended product scope; rollout may be staged | Confirm MVP/release slicing without deleting scope |
| KME-DEC-015 | SLO baseline | 99.9% proposed availability; initial RTO 4h/RPO 15m | PROPOSED | Starting point only; impacts cost and architecture | Approve or replace targets |
| KME-DEC-016 | Payment integration | Provider adapter, no raw card storage, webhook verification, idempotency | PROPOSED | Limits sensitive data and duplicate effects | Select providers and payment ownership |
| KME-DEC-017 | Tax/finance | India-first GST/INR readiness; provider/legal validation required | PROPOSED | Important for Indian commerce | Confirm invoicing, tax and settlement requirements |
| KME-DEC-018 | AI agent governance | OpenCode follows `AGENTS.md`, no automatic phase progression/deploys | PROPOSED | Prevents unsanctioned changes | Accept agent permissions policy |
| KME-DEC-019 | Repository workflow | Public GitHub repo, default branch `main`; review before first push | PROPOSED | Transparent project history | Confirm branch protection and secret scanning |
| KME-DEC-020 | Sharding | Do not shard until workload evidence justifies it | PROPOSED | Avoid premature operational complexity | Accept trigger-based decision |
| KME-DEC-021 | Multi-region | No active-active writes in initial architecture absent explicit need | PROPOSED | Simplifies consistency/recovery | Confirm geographic requirements |
| KME-DEC-022 | Service count | Service catalog is provisional; final boundaries based on ownership and operations | PROPOSED | Prevents service-count-driven design | Review each boundary |
| KME-DEC-023 | Data isolation tiers | Shared DB/schema with tenant keys initially as a candidate; premium isolation tiers undecided | BLOCKED | Affects cost, schema, migrations, backups and isolation | Select isolation model and upgrade path |
| KME-DEC-024 | Merchant/order model | Define marketplace order vs seller sub-order, payments, refunds and settlement semantics | BLOCKED | Foundational for order, payment, fulfillment and finance services | Approve domain model |
| KME-DEC-025 | Expected scale | Tenant/SKU/session/order/event growth and peak factors not yet specified | BLOCKED | Needed for capacity, partitions, indexes and load targets | Provide initial workload assumptions |
| KME-DEC-026 | Regions and DR | Hosting region, data residency, failover topology and recovery budget undecided | BLOCKED | Impacts privacy, latency, DR and cost | Select target region and DR stance |

## Approval record

- P00 status: `IN_PROGRESS`
- Authorized approver: project owner (to be recorded)
- Approval date: not yet recorded
- Evidence: pending
- P01 status: `BLOCKED_PENDING_P00_ACCEPTANCE`
