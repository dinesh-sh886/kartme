# Kart-Me Product Requirements Document

**Status:** Draft for P00 review  
**Version:** 0.1

## 1. Product vision

Kart-Me is a multi-tenant commerce platform combining a shared marketplace with merchant-owned storefronts. It supports customer shopping, seller operations, partners, delivery, support, finance, platform administration, QA, staff operations, security/audit, and tightly controlled database operations.

## 2. Business model

**Proposed:** Hybrid model:
- Marketplace: customers discover and buy products from multiple sellers.
- Commerce SaaS: merchants operate branded storefronts and manage products, orders, customers, promotions, and reports.
- Shared platform services: identity integration, tenant lifecycle, catalog capabilities, payments integration, fulfillment, notification, audit, and observability.

Business rules must distinguish marketplace-managed transactions from merchant-owned storefront transactions where fees, tax, payment routing, customer ownership, data export, returns, and settlements differ.

## 3. Personas and portals

| Persona | Portal | Main responsibilities |
|---|---|---|
| Guest/customer | Customer storefront/account | Browse, search, cart, checkout, orders, returns, reviews |
| Merchant owner/staff | Merchant portal | Storefront, catalog, price, inventory, orders, promotions, staff |
| Partner/supplier/brand | Partner portal | Onboarding, product submissions, supply status, documents |
| Delivery agent | Delivery portal | Availability, assignments, pickup, delivery, proof, exceptions |
| Customer support | Support portal | Cases, permitted order context, escalation, authorized refunds |
| Operations staff | Operations portal | Fulfillment exceptions, queue management, reconciliation |
| Finance | Finance portal | Settlements, commissions, refunds, reconciliation, tax exports |
| Platform administrator | Admin portal | Tenant lifecycle, plans, configuration, platform governance |
| QA | QA portal/tooling | Synthetic test data, test runs, defects, evidence |
| Security/auditor | Audit console | Access reviews, audit search, incident evidence |
| Database operator | Restricted operations tooling | Health, capacity, approved maintenance, backup/restore evidence |

Portals are separate experiences and access policies, not necessarily separate frontend deployments. Privileged roles must be separated from customer/merchant permissions. QA should use synthetic or appropriately masked data. Database operators should not receive routine unrestricted business-data access.

## 4. Product capability scope

- Multi-tenant onboarding, membership, tenant lifecycle, plan/feature configuration.
- Keycloak integration using OIDC/OAuth 2.0; backend authorization and tenant membership enforcement.
- Merchant/storefront onboarding, catalog, product variants, media, moderation, pricing, tax categories.
- Search, filters, category browsing and product detail.
- Inventory by SKU/location, stock reservations, movements and reconciliation.
- Cart, checkout quote, shipping/tax calculation, promotions/coupons and final server-side validation.
- Orders, seller sub-orders/fulfillment groups, cancellations, payment attempts, refunds and audit history.
- Payment-provider integration, signed webhook verification, idempotency and ambiguous-outcome reconciliation.
- Delivery assignment, pickup/delivery state machine, proof of delivery, failed delivery and return flows.
- Support cases, approvals, reason codes and escalation.
- Finance settlement, commissions, refund reconciliation and tax reporting.
- Notifications, audit, reporting, data export/retention, incident management and operational dashboards.

## 5. Initial non-functional requirements

Targets are proposals and require validation against expected traffic, budget, and business risk.

| Measure | Proposed initial target |
|---|---|
| Browse availability | 99.9% monthly |
| Checkout/order availability | 99.9% monthly |
| Browse latency | p95 < 300 ms at agreed test load |
| Cart/checkout API latency | p95 < 400 ms excluding external provider wait; measure end-to-end separately |
| Recovery time objective | RTO ≤ 4 hours initially |
| Recovery point objective | RPO ≤ 15 minutes initially |
| Tenant isolation | Zero unauthorized cross-tenant access in automated negative tests |
| Core transaction durability | Committed order/payment state recoverable under defined failure model |
| Observability | Dashboards, alerts, trace/correlation IDs and runbooks for critical journeys |
| Security | No unresolved critical/high release-blocking findings unless formally risk-accepted |

Capacity targets require explicit assumptions for tenants, concurrent sessions, SKU count, order volume, peak-to-average ratio, event rate, data growth, region, and test duration.

## 6. Core invariants

1. Tenant context is derived from validated identity and server-side membership, not trusted from a request header.
2. Authorization is enforced at gateway and service/domain boundaries.
3. Order totals and order-line details are server-calculated snapshots.
4. Payment callbacks and commands are idempotent.
5. Inventory reservations and movements prevent duplicate effects and follow a documented oversell policy.
6. Domain events are emitted through a transactional outbox where DB state and event publication must be coordinated.
7. Consumers tolerate duplicate and out-of-order delivery where ordering is not guaranteed.
8. Unknown payment outcomes are reconciled, not assumed failed.
9. Financial adjustments, privileged access and manual stock changes are audited.
10. Secrets and unnecessary personal/payment data never enter logs or metrics.

## 7. Explicitly out of scope for first launch unless approved

- Active-active multi-region writes.
- Building a payment processor or storing raw card details.
- Unbounded service extraction or universal GraphQL/gRPC adoption.
- Autonomous production changes by AI agents.
- Unverified compliance claims.

## 8. Success measures to finalize

- Merchant activation and time-to-first-published-product.
- Search-to-product and cart-to-checkout conversion.
- Checkout success rate and payment reconciliation gap.
- Order fulfillment and on-time delivery rates.
- Refund/return resolution time.
- Platform availability, latency, error rate, queue lag, recovery performance.
- Tenant-isolation/security test results and audit completeness.
