# Kart-Me P00 — Service Boundary and Ownership Proposal

## Boundary rules
1. A service owns its business invariants and authoritative data.
2. Other services never write directly to its database.
3. Cross-service operations use API contracts or events.
4. Every service has an owner, threat model, SLO, data classification, migrations, tests, dashboards, runbook, and event/API compatibility policy.
5. Service boundaries are approved before code generation. A service catalog is not an instruction to generate every service in one batch.

## Proposed ownership matrix

| Service | Owns | Must not own |
|---|---|---|
| Gateway/BFF | Routing, aggregation, rate limiting, correlation | Core business invariants; sole authorization enforcement |
| Tenant & Organization | Tenant lifecycle, org/store membership, plans | User credentials/passwords managed by Keycloak |
| Identity Integration/Policy | Claims mapping, authorization policy contracts | Duplicate identity store |
| Merchant & Partner | Merchant/partner profile and onboarding | Product source-of-truth beyond submissions/ownership metadata |
| Catalog | Product, variant, category and publication state | Inventory availability as sole authority |
| Search | Search documents and query API | Authoritative product/order state |
| Pricing & Promotions | Price rules, coupon and promotion eligibility | Final browser-supplied totals |
| Inventory | Stock balances, reservations, movements | Payment state |
| Cart | Cart and item selection | Authoritative order total after checkout |
| Checkout | Quote and orchestration; final validation | Payment provider ledger or inventory source of truth |
| Order | Order aggregate, line snapshots, state transitions | Direct provider charge execution |
| Payment | Payment attempts, webhook receipts, provider refs, refund execution status | Raw card storage; seller settlement policy as sole owner |
| Fulfillment/Shipping | Shipment packages, carrier and fulfillment state | Delivery-agent identity |
| Delivery | Agent availability/assignment, proof and delivery exceptions | Order aggregate ownership |
| Returns & Refund Workflow | Return eligibility/case and orchestration | Provider-specific payment execution |
| Support | Cases, notes, escalation, approvals | Unrestricted access to all tenant/customer data |
| Finance/Settlement | Commission calculation records, settlement batches and reconciliation | Unaudited manual ledger edits |
| Notification | Templates, dispatch attempts and delivery status | Business transaction state |
| Review & Reputation | Reviews, moderation and rating projection | Payment/order source of truth |
| Audit & Compliance | Audit event access, retention and review workflows | Mutable business records |
| Reporting/Analytics | Derived read models and reporting | Authoritative writes to source services |
| Configuration/Feature Policy | Feature flags and tenant configuration | Secrets or authorization bypasses |
| Media/Asset | Upload metadata, scan status, object references | Unrestricted public file access |
| Tax/Compliance Rules | Tax rule versions/calculation contracts | Unreviewed legal/tax interpretations |
| Warehouse Operations | Location/warehouse task operations if separated from fulfillment | Inventory authoritative movement without Inventory service |
| QA/Test Operations | Test runs, synthetic data metadata and evidence | Unrestricted production customer data access |

## Required event/API contracts for P01 design
- `TenantCreated`, `TenantSuspended`, `MembershipChanged`
- `ProductPublished`, `ProductUpdated`, `ProductArchived`
- `InventoryReserved`, `InventoryReservationExpired`, `InventoryAdjusted`
- `CheckoutQuoteCreated` / quote invalidation contract
- `OrderPlaced`, `OrderCancelled`, `OrderConfirmed`
- `PaymentInitiated`, `PaymentSucceeded`, `PaymentFailed`, `PaymentOutcomeUnknown`, `RefundStatusChanged`
- `ShipmentCreated`, `DeliveryAssigned`, `DeliveryCompleted`, `DeliveryFailed`
- `ReturnRequested`, `ReturnApproved`, `SettlementCalculated`
- `SupportCaseOpened`, `SupportCaseEscalated`
- `NotificationRequested`, `NotificationDeliveryUpdated`

Names are illustrative; schema, ownership, compatibility and event timing require detailed contract design. Include event ID, event type, schema version, occurred-at, producer, aggregate ID, tenant context where applicable, correlation ID, causation ID, and payload.

## Decisions that block service implementation
- Marketplace order vs seller sub-order relationship and cancellation/refund allocation.
- Inventory reservation expiry and oversell policy.
- Payment ownership, split payments, refunds, chargebacks and reconciliation.
- Settlement ledger model and commission/tax responsibility.
- Tenant isolation tiers and tenant-aware uniqueness.
- Whether Tax, Warehouse, Returns, QA and Identity Policy are standalone services or modules within an owner service.
