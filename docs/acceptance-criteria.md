# Kart-Me P00 — Acceptance Criteria and Exit Gate

P00 is documentation and governance only. It does not include application coding.

## Gate A — Product definition
- [ ] Hybrid marketplace + merchant-owned commerce SaaS model documented.
- [ ] All portal personas and their permitted capabilities documented.
- [ ] Marketplace vs merchant-owned storefront differences documented.
- [ ] Customer, merchant, partner, delivery, support, finance, admin, staff, QA, audit and database-operations scope reviewed.
- [ ] MVP/release slicing preserves broad product scope while identifying rollout order.
- [ ] Success metrics and initial workload assumptions approved.

## Gate B — Architecture and service ownership
- [ ] Independent microservices explicitly selected and operational implications accepted.
- [ ] Each proposed service has responsibility, authoritative data, non-responsibilities and dependencies.
- [ ] PostgreSQL/MongoDB/Redis/Kafka usage policies reviewed.
- [ ] REST/Kafka/gRPC/GraphQL decision policy approved.
- [ ] Order/sub-order, inventory, payment/refund, settlement and tax ownership decisions resolved.
- [ ] CAP/consistency choices are operation-specific.
- [ ] Availability, scaling, replication, sharding and DR approach reviewed.

## Gate C — Security and tenancy
- [ ] Keycloak is the selected identity provider; OIDC/OAuth 2.0 integration boundary documented.
- [ ] Realm/client strategy, tenant membership, role/permission model and MFA for privileged users decided.
- [ ] Tenant isolation model and upgrade path selected.
- [ ] Cross-tenant tests are mandatory in P01+ CI.
- [ ] Support, QA, finance, admin, audit and database operator privileges are separated.
- [ ] Secrets, audit, data retention, masking and export controls documented.

## Gate D — Reliability and operations
- [ ] Initial SLO, latency targets, workload model, RTO/RPO approved or explicitly deferred with owner/date.
- [ ] Timeout/retry/circuit-breaker/bulkhead/backpressure policies approved.
- [ ] Outbox/inbox, idempotency, DLQ, replay and reconciliation policies approved.
- [ ] Monitoring, logs, traces, alerts, health checks and runbook requirements approved.
- [ ] Backup/restore, failover and return-to-primary expectations reviewed.
- [ ] Jenkins, PMD, SonarQube and security/contract test quality gates defined.

## Gate E — Governance and OpenCode
- [ ] Root `AGENTS.md` and policy files reviewed.
- [ ] OpenCode cannot autonomously advance phases, deploy, publish or perform destructive changes.
- [ ] Decisions register contains status, rationale, consequences and required owner actions.
- [ ] Risk register has mitigation and trigger/evidence for high risks.
- [ ] Review checklist completed and blocking questions resolved.
- [ ] Project owner explicitly records acceptance with date and evidence.

## Required evidence
- Final reviewed PRD, architecture and service boundary documents.
- Decisions register with no unresolved blocking items (or explicitly approved deferrals).
- Risk register review and accepted mitigations.
- Completed checklist and approval record.
- Repository baseline verified; no application code started before acceptance.

## Current disposition
`IN_PROGRESS`. P01 remains blocked until explicit P00 acceptance. No acceptance is inferred from document generation or checklist completion alone.
