# Kart-Me P00 — Blocking Open Questions

These are deliberately not silently decided by the agent. Resolve before P00 acceptance or record an explicitly approved, time-bound deferral.

1. **Tenant isolation tiers:** Shared PostgreSQL database/schema with tenant keys for all tenants, or offer schema/database/dedicated deployment tiers? What is the migration path between tiers?
2. **Realm/client strategy:** One Keycloak realm with tenant-aware claims, realm per tenant, or a tiered model? Who provisions realms/clients and rotates service credentials?
3. **Order model:** One marketplace parent order with seller sub-orders? How are shipping, cancellation, partial shipment, return and refund allocated?
4. **Payments:** Which provider(s), merchant-of-record model, split payments, delayed capture, refund/chargeback workflows, and reconciliation source?
5. **Finance:** What is the authoritative ledger/settlement record? How are commissions, fees, taxes, payout holds and corrections represented?
6. **Inventory:** Reservation TTL, oversell policy, warehouse allocation, stock reconciliation and backorder behavior?
7. **Launch geography:** India only at launch? Which states/regions, data residency, language, currency and tax/invoice requirements need review?
8. **Scale:** Initial and 12-month estimates for tenants, stores, SKUs, daily orders, peak concurrent users, checkout RPS, Kafka events/sec and data growth?
9. **Availability/DR:** Which region/provider, multi-zone plan, RTO/RPO, backup retention, failover strategy and cost ceiling?
10. **Portal delivery:** Separate Angular applications or one workspace with route-level modules? Which mobile capabilities are required for delivery agents?
11. **Search/media/notifications:** Select search engine, object storage, email/SMS/push providers and retention rules.
12. **Service catalog:** Which proposed services must be independent at launch, and which can be deferred without violating the independent-microservice requirement?
13. **Compliance:** Which privacy, consumer protection, payment-provider, tax, accounting and security obligations require formal legal/compliance review?
14. **Repository governance:** Branch protection, required reviewers, secret scanning, dependency updates, release tagging and CI secrets policy?
15. **Operational ownership:** Who owns alerts, on-call, incident response, security incidents, backup restore and finance reconciliation?

## Required response format
For each answer record: decision, rationale, alternatives considered, impact, owner, status, and date in `docs/decisions-register.md`.
