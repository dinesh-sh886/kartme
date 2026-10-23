# Reliability and Operations Policy

1. Every network call has connect, read and overall deadlines.
2. Retries are bounded, jittered and limited to transient failures; operations must be idempotent or otherwise proven safe.
3. Avoid retry amplification; one layer owns retry policy for each call path.
4. Use circuit breakers, bulkheads, concurrency limits, rate limits, backpressure and load shedding where appropriate.
5. Use transactional outbox for DB-to-Kafka dual-write risk; consumers deduplicate and classify retryable/permanent errors.
6. Poison messages go to a monitored DLQ with safe, audited replay procedures.
7. Reconcile ambiguous payment outcomes, inventory drift, stuck orders and settlements.
8. Liveness indicates the process can continue; readiness indicates it can safely receive traffic. Do not restart loops because a transient downstream is unavailable.
9. Define SLOs, dashboards, alert thresholds, on-call owner, escalation and runbooks for critical journeys.
10. Metrics labels must have bounded cardinality; no raw IDs or sensitive values.
11. Backups are encrypted and isolated; restoration and failover must be tested. Replication is not backup.
12. DR plans define RTO/RPO, decision authority, data-loss assessment, traffic switch, reconciliation and return-to-primary.
13. Load and failure tests are required before production SLO claims.
