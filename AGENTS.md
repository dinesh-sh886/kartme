# Kart-Me — OpenCode Agent Instructions

## Project identity
This repository is Kart-Me, a new standalone project. Do not mix it with WeKart, QEVANO, RASA, or any other project. Keycloak is the selected identity provider. OpenCode is the development agent.

## Mandatory startup
1. Read `README.md`, `docs/prd.md`, `docs/architecture.md`, `docs/decisions-register.md`, `docs/service-boundaries.md`, `docs/risk-register.md`, `docs/acceptance-criteria.md`, and all policies.
2. Inspect repository state, current branch, existing instructions, and uncommitted changes before acting.
3. Identify the current phase and explicitly requested task.
4. If phase is P00, only prepare/review documentation and governance artifacts. Do not generate application code or start P01.
5. If a decision affects tenant isolation, security, payments, data consistency, public APIs, or architecture boundaries and is unresolved, ask for a decision rather than silently inventing one.

## Execution restrictions
- No automatic phase progression, implementation, publishing, deployment, or background work.
- Do not overwrite user work, delete files/data, force-push, reset branches, or run destructive commands without explicit authorization.
- Do not claim repository changes, tests, reviews, or approvals unless directly verified.
- Never import code, decisions, secrets, or status from WeKart, QEVANO, or RASA.
- Use Keycloak/OIDC for identity; do not substitute RASA.
- Keep secrets out of source control. Review staged changes before commits.
- Treat `PROPOSED` decisions as unapproved until the authorized owner accepts them.

## Documentation rules
- Record each material decision in `docs/decisions-register.md` with ID, status, rationale, consequences, owner, and date.
- Architecture changes require an ADR or decision-register entry.
- Every service must have an explicit owner, data boundary, API/event contract, security model, SLO, and operational runbook before implementation.
- Record assumptions separately from facts.
- Use stable requirement IDs and link acceptance evidence.

## P00 completion
P00 may be marked `ACCEPTED` only after all blocking decisions are resolved, the checklist is completed, architecture and policies are reviewed, and the authorized project owner explicitly approves. Until then, keep P01 blocked.
