# P00 Review Checklist

Mark each item only after reviewing its supporting evidence.

## Product
- [ ] Hybrid marketplace + merchant SaaS model is explicit.
- [ ] All portals and personas are in scope.
- [ ] Marketplace and merchant-owned storefront behavior is distinguished.
- [ ] Broad release scope and staged delivery order are clear.
- [ ] Success metrics and workload assumptions are agreed.

## Architecture
- [ ] Independent microservices are accepted with operating cost understood.
- [ ] Service responsibilities and data ownership are reviewed.
- [ ] Order/sub-order/payment/refund/settlement model is resolved.
- [ ] PostgreSQL, MongoDB, Redis and Kafka boundaries are explicit.
- [ ] REST/Kafka/gRPC/GraphQL policies are clear.
- [ ] CAP, consistency, idempotency, outbox, deadlocks, caching, indexing and sharding policies are covered.
- [ ] DR, redundancy, failover, backup/restore and RTO/RPO are approved.

## Identity and security
- [ ] Keycloak OIDC/OAuth strategy is reviewed.
- [ ] Tenant isolation model and tiering decision are approved.
- [ ] Role/permission matrix covers every portal.
- [ ] Admin/support/QA/finance/DB operator privileges are separated.
- [ ] Secrets, audit, PII, data retention and exports are covered.

## Reliability and delivery
- [ ] SLOs, latency and capacity assumptions are approved.
- [ ] Retry/timeout/circuit-breaker/bulkhead/backpressure behavior is defined.
- [ ] Outbox, consumer dedupe, DLQ and reconciliation are required.
- [ ] Prometheus/Grafana/logging/tracing/runbooks are planned.
- [ ] Jenkins, SonarQube, PMD, contract/security tests and branch protection are defined.

## Governance
- [ ] Risks have owners/mitigations or explicit accepted treatment.
- [ ] Open questions are resolved or approved as time-bound deferrals.
- [ ] OpenCode policy is accepted.
- [ ] No implementation started prematurely.
- [ ] Project owner explicitly records P00 acceptance with date and evidence.

**Disposition:** PENDING REVIEW. Checking this list in a UI or editing the document does not by itself constitute formal acceptance.
