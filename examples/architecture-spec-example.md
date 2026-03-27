# Architecture Spec Example

## Problem

Build a family coordination platform with separate parent and child experiences, shared household data, task tracking, and AI assistance for planning and reminders.

## Constraints

- must be deployable on a VPS
- should support phased delivery from MVP to broader household tooling
- parent and child experiences need clear permission boundaries
- AI features must not bypass role or safety controls
- operator setup and maintenance should remain manageable for a small household deployment

## Recommended architecture

Start with a modular monolith.

Use:
- a single backend service for API, auth, policy checks, and AI orchestration
- a Postgres database for core relational data
- a React / Next.js frontend with role-aware views
- Docker Compose for deployment
- Caddy as reverse proxy

Avoid early service splitting unless a real scaling, isolation, or operational reason emerges.

## Trust boundaries

Key trust boundaries:
- parent accounts vs child accounts
- application backend vs model/tool layer
- secret storage vs application config
- internal planning workflows vs externally side-effecting actions

All role and permission checks should be enforced in the backend, not only at the UI or prompt layer.

## Deployment shape

- VPS-hosted Docker Compose stack
- Caddy at the edge
- app service
- Postgres service
- optional Redis only if queues or rate limiting later justify it
- secrets injected via environment or secret mount, not stored in repo

## Main risks

- role leakage between parent and child views
- overcomplicating AI orchestration too early
- hidden deployment fragility from premature service sprawl
- weak secret-handling discipline in early iterations

## Phased approach

### MVP
- authentication and household model
- task tracking
- parent and child role separation
- simple AI-assisted planning features with bounded actions

### Next phase
- reminders and scheduling workflows
- notification routing
- richer parent oversight and auditability

### Later
- more specialized household agents
- stronger automation and delegation
- deeper analytics or planning support
