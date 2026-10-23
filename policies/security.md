# Security Policy

1. Keycloak is the identity provider; use OIDC/OAuth 2.0 standards and approved flows.
2. Validate JWT signature, issuer, audience, expiry/not-before, required claims and key rotation.
3. Authentication does not imply authorization. Enforce permissions in every service and resource access path.
4. Tenant context is verified server-side; client headers alone never establish tenant identity.
5. Use least privilege, separate privileged personas, time-bound elevation, MFA/step-up for sensitive operations and approval workflows where required.
6. CORS allowlists are not authorization. Apply CSRF controls where cookie-based browser sessions require them.
7. Validate input, encode output, protect against injection, SSRF, mass assignment, replay and insecure direct object references.
8. Keep secrets out of source code, images, logs, test fixtures and repository history. Use approved secret management.
9. Encrypt traffic; define encryption-at-rest and key-management expectations for each data store.
10. Audit privileged access, financial adjustments, refunds, role changes, exports and tenant lifecycle actions.
11. Minimize PII and payment data; apply access control, retention and deletion rules.
12. Security scans and tests are required in CI; critical/high findings block release unless formally risk-accepted.
