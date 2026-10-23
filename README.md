# Kart-Me P00 — Product Definition and Governance

**Status:** IN_PROGRESS — review required  
**Version:** P00 Governance Pack v0.1  
**Product:** Kart-Me (standalone new project)  
**Target local path:** `~/workspace/gix/kartme/`  
**Target repository:** https://github.com/dinesh-sh886/kartme  
**Identity provider:** Keycloak (OAuth 2.0 / OpenID Connect)  
**Development agent:** OpenCode

## Scope and boundaries

This pack covers product definition, architecture decisions, service ownership, risks, policies, acceptance criteria, and review checklists. It does not implement application code and does not record P00 acceptance.

Kart-Me is a new project. Do not import or infer code, architecture decisions, acceptance state, credentials, or project history from WeKart, QEVANO, or RASA. Keycloak is the selected identity provider.

## Documents

- `docs/prd.md` — product definition and proposed launch scope
- `docs/architecture.md` — architecture principles and candidate service map
- `docs/decisions-register.md` — decisions, owners, status and open questions
- `docs/service-boundaries.md` — responsibilities, data ownership and communication
- `docs/risk-register.md` — risk register with mitigations and triggers
- `docs/acceptance-criteria.md` — P00 exit gates and evidence requirements
- `docs/policies.md` — policy index and enforcement requirements
- `review/review-checklist.md` — review checklist
- `review/open-questions.md` — decisions needing explicit resolution
- `AGENTS.md` — OpenCode operating instructions
- `policies/security.md`
- `policies/tenant-isolation.md`
- `policies/engineering.md`
- `policies/reliability-operations.md`
- `policies/ai-agent.md`

## Governance status

All decisions marked `PROPOSED` are recommendations, not approved decisions. The P00 phase remains `IN_PROGRESS` until the authorized project owner reviews the deliverables, resolves blocking decisions, and explicitly records acceptance. P01 implementation must not start before that acceptance.
