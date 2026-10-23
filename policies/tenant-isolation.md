# Tenant Isolation Policy

1. Every tenant-owned resource has a defined tenant scope and ownership model.
2. Resolve tenant context from verified identity and server-side membership/policy; never trust a raw tenant ID from the browser.
3. Enforce tenant authorization in gateway and owning service; never rely on frontend filtering.
4. Every query, mutation, export, background job and administrative action must apply tenant scope or explicitly document a platform-wide privilege.
5. Include tenant scope in cache keys, idempotency keys where business scope requires it, object-storage paths/policies, search filters, and event metadata.
6. Enforce tenant-aware uniqueness and foreign-key/invariant design where appropriate.
7. Prevent cross-tenant joins/writes between services. No direct access to another service's database.
8. Tenant context propagation across Kafka must be validated and preserved; consumers must not trust event metadata without producer/contract controls.
9. Audit tenant switching and privileged cross-tenant support access. Require reason and narrow scope.
10. QA uses synthetic or masked data. Production data access must be approved and audited.
11. CI must include negative tests for cross-tenant reads, writes, object IDs, caches, exports, async consumers and support/admin workflows.
12. Isolation tiers (shared schema, schema/database per tenant, dedicated deployment) must be explicitly decided with a migration/upgrade path before implementation.
