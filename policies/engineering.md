# Engineering Policy

1. Java 21 baseline; choose Spring Boot version in P01 after dependency compatibility review.
2. Angular/TypeScript frontend; Maven multi-module backend with explicit module/service boundaries.
3. Follow SOLID, domain-driven design, clean architecture and dependency inversion.
4. Controllers remain thin; business invariants live in domain/application layers.
5. Never expose persistence entities directly through APIs; use validated DTOs.
6. REST/OpenAPI is the default API style; Kafka for asynchronous events; GraphQL/gRPC require a concrete use case and approved design.
7. Use Flyway migrations; applied migrations are immutable. Use expand/migrate/contract for rolling changes.
8. Test from empty database and supported upgrade path. Use constraints and indexes justified by query plans.
9. Use unit, integration, contract, security, migration and end-to-end tests appropriate to risk.
10. PMD, SonarQube, dependency/image scanning and secret scanning are CI quality gates.
11. Do not suppress findings without a documented reason and reviewer approval.
12. API and event contracts require compatibility policy, versioning and ownership.
13. No merge with failing required checks or unresolved release-blocking security findings.
14. Document commands and actual results; never fabricate test or deployment success.
