# Kart-Me P00 — Risk Register

Scales: Probability (P) and Impact (I) 1–5. Score = P × I. Ratings are initial qualitative estimates; review them during P00.

| ID | Risk | P | I | Score | Mitigation / control | Trigger / evidence |
|---|---|---:|---:|---:|---|---|
| KME-R-001 | Too many microservices create high operational overhead | 4 | 5 | 20 | Confirm boundaries, ownership, platform automation and on-call capacity; release in controlled waves | Repeated deploy failures, missing runbooks, high cross-service latency |
| KME-R-002 | Cross-tenant data leakage | 3 | 5 | 15 | Tenant context derived from identity, scoped queries, cache/event tenant keys, automated negative tests | Any cross-tenant access test failure is release blocker |
| KME-R-003 | Ambiguous marketplace vs storefront order/settlement model | 4 | 5 | 20 | Decide order/sub-order, payment, cancellation, refund, tax and settlement semantics in P00 | Service contracts cannot be approved |
| KME-R-004 | Payment duplicate/unknown outcomes cause financial errors | 3 | 5 | 15 | Idempotency, signed webhooks, provider reconciliation, immutable payment attempt history | Reconciliation gap or duplicate effect |
| KME-R-005 | Overselling due to concurrent checkout | 3 | 5 | 15 | Atomic reservations/conditional writes, expiry policy, concurrency tests | Inventory drift or negative availability |
| KME-R-006 | Keycloak role/tenant claims are trusted incorrectly | 3 | 5 | 15 | Validate issuer/audience/signature/expiry; server-side membership; service authorization tests | Any bypass or stale membership acceptance |
| KME-R-007 | Performance assumptions are absent | 4 | 4 | 16 | Define tenants, concurrency, peak ratio, SKU/order/event growth; benchmark before SLO sign-off | No agreed workload model by P00 gate |
| KME-R-008 | Database-per-service complexity and migration drift | 4 | 4 | 16 | Standard migration pipeline, ownership, compatibility tests, expand/contract | Incompatible rollout or migration failure |
| KME-R-009 | Kafka duplicates, lag or poison messages stall workflows | 3 | 4 | 12 | Idempotent consumers, bounded retries, DLQ, lag/age alerts, replay procedure | Consumer lag exceeds agreed threshold |
| KME-R-010 | DR objectives not achievable within budget | 3 | 5 | 15 | Costed RTO/RPO, isolated backups, restore/failover drills | Restore test misses target |
| KME-R-011 | AI agent makes unauthorized or broad changes | 3 | 5 | 15 | AGENTS.md, explicit task scope, human approvals, protected branches, no autonomous deployment | Unreviewed destructive command or scope creep |
| KME-R-012 | Public repository accidentally exposes secrets | 2 | 5 | 10 | Secret scanning, `.gitignore`, staged diff review, secret rotation runbook | Secret detected in staged/committed history |
| KME-R-013 | Finance/tax rules incorrect or incomplete | 3 | 5 | 15 | Confirm provider/accounting/tax requirements with qualified stakeholders; version rules and audit changes | Unreconciled settlement or incorrect invoice |
| KME-R-014 | Privileged portal exposes production PII | 3 | 5 | 15 | Least privilege, masked data, purpose limitation, audit, approvals | Unauthorized access/export |
| KME-R-015 | Cache invalidation creates stale price/stock decisions | 3 | 4 | 12 | Cache only non-authoritative data for checkout decisions; revalidate transactionally | Checkout accepts stale price/stock |
| KME-R-016 | Multi-region active-active adds conflict complexity prematurely | 2 | 4 | 8 | Start with explicit primary/DR design; ADR required before active-active | New region requirement |
| KME-R-017 | API/event contract drift breaks consumers | 3 | 4 | 12 | Schema versioning, compatibility checks, contract tests, ownership | Consumer errors after rollout |
| KME-R-018 | Support/QA/database access exceeds need-to-know | 3 | 5 | 15 | Separate roles, scoped workflows, masking, time-bound elevation and audit | Excessive role grants or sensitive export |
| KME-R-019 | Observability cost and cardinality grow without bounds | 3 | 3 | 9 | Bounded labels, sampling/retention policy, budgets and dashboards | Prometheus cardinality or storage spike |
| KME-R-020 | Compliance obligations are assumed without validation | 3 | 5 | 15 | Legal/privacy/security review of applicable Indian and target-market requirements | Launch market or data flow changes |

## Risk acceptance rule
No critical data-integrity, tenant-isolation, payment, or privileged-access risk may be silently accepted. Any exception needs named owner, rationale, compensating controls, expiry/review date, and explicit approval.
