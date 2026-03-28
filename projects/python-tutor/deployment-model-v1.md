# Python Tutor Platform — Deployment Model v1

## Purpose

This document defines the first deployment model for the Python Tutor Platform MVP.

The goal is to make the product deployable on a VPS in containers while preserving:
- backend-enforced trust boundaries
- safe OpenClaw integration
- parent/learner role separation
- operational simplicity
- backup and rollback viability

## Deployment principles

1. **One VPS, one stack, minimal moving parts**
   - start with a single VPS-hosted deployment
   - avoid premature distributed infrastructure

2. **Backend remains the control plane**
   - product traffic should flow through the application backend
   - OpenClaw should not be the user-facing control surface

3. **Separate exposure from internal runtime**
   - only the intended product surfaces should be internet-facing
   - internal services should remain on private Docker networks where possible

4. **Secrets are runtime inputs**
   - no secrets in repository files
   - no secrets embedded in agent prompts or docs

5. **Recovery matters from day one**
   - backups, rollback, and incident containment should exist in MVP form

## Recommended runtime shape

### Internet-facing surfaces
The VPS should expose only:
- learner web app
- parent web app
- backend API endpoints needed by the apps
- webhook endpoints needed for WhatsApp or related parent channel integration
- reverse proxy entrypoint (Caddy)

### Not internet-facing by default
- OpenClaw internal service endpoints
- Postgres
- operator/admin-only internal services unless intentionally exposed and protected
- internal audit and background components

## Recommended container set

### 1. `caddy`
Responsibilities:
- TLS termination
- reverse proxy routing
- public entrypoint for web apps and backend API
- webhook ingress routing if needed

### 2. `backend-api`
Responsibilities:
- authentication and identity
- policy enforcement
- data access
- learner/parent/product APIs
- OpenClaw orchestration control
- context filtering
- audit event generation
- parent WhatsApp integration logic

This is the central product service.

### 3. `learner-parent-web`
For MVP, this can be:
- one frontend app with role-separated routes
or
- separate learner and parent web apps if the implementation strongly benefits from that

Recommendation:
- start with one frontend codebase if simpler
- keep role boundaries enforced in the backend regardless

### 4. `openclaw`
Responsibilities:
- runtime for learner agent
- runtime for parent agent
- runtime for curriculum agent
- runtime for super agent
- supporting channel/runtime integrations where appropriate

Important:
- OpenClaw should sit behind the backend orchestration layer
- user-facing traffic should not directly rely on raw OpenClaw UI exposure

### 5. `postgres`
Responsibilities:
- persistent system of record
- users / family / learner / parent / session / progress / audit data

### 6. Optional future container: `redis`
Not required for MVP unless clearly justified.

Use later only if needed for:
- queues
- retries
- background job coordination
- rate-limiting support

## Docker network model

Recommended networks:

### `public`
Used by:
- caddy
- frontend
- backend-api

### `internal`
Used by:
- backend-api
- openclaw
- postgres
- optional future internal services

### Rule
- Postgres should not be on the public network
- OpenClaw should not be directly exposed publicly unless there is a very specific, intentional, and protected reason
- backend should mediate traffic to OpenClaw

## Request routing model

### Learner web flow
1. learner browser → Caddy
2. Caddy → learner/parent web app
3. frontend → backend-api
4. backend-api → Postgres and OpenClaw as needed
5. backend returns policy-filtered output to learner UI

### Parent dashboard flow
1. parent browser → Caddy
2. Caddy → learner/parent web app
3. frontend → backend-api
4. backend-api → Postgres and OpenClaw as needed
5. backend returns parent-visible progress and parent-agent output

### Parent WhatsApp flow
1. WhatsApp webhook/provider → Caddy
2. Caddy → backend-api webhook endpoint
3. backend-api authenticates/maps parent identity
4. backend-api applies policy and invokes parent-agent path through OpenClaw if needed
5. backend-api records audit and interaction state
6. backend-api sends response via approved channel path

## Environment model

Recommended environments:
- local/dev
- production

Preferred if feasible:
- local/dev
- staging
- production

### Environment rules
- separate secrets per environment
- separate database per environment
- separate channel/API credentials where possible
- no silent reuse of production secrets in development

## Secret model

Secrets likely required:
- database credentials
- session/auth secret
- OpenClaw config secrets
- model/provider API keys
- WhatsApp provider credentials
- any parent channel webhook/signing secrets

### Secret handling rules
- inject at runtime
- store outside the repository
- restrict access by environment
- rotate when needed
- never place secrets in prompts, docs, or code files

## Data persistence and backup model

### Persistence
- Postgres must use persistent storage
- any important OpenClaw state needed operationally should be understood and backed up appropriately if relevant to your install

### Backups
Minimum MVP backup expectation:
- scheduled Postgres backups
- off-host backup storage if possible
- documented restore procedure

### Restore expectation
The MVP should not be considered production-credible unless:
- backup creation is working
- restore steps are written down
- restore has been tested at least once in a realistic way

## Rollback model

### Application rollback
- versioned images
- previous known-good image retained
- documented Compose-based rollback process

### Configuration rollback
- environment/config changes tracked
- ability to restore previous working config state

### Data rollback / recovery
- backup-based restore for severe cases
- targeted repair or reconciliation steps for workflow/data issues when a full restore is too destructive

Important:
- rollback is not just “containers go back up”
- role-sensitive and learner-progress data must remain trustworthy after rollback decisions

## OpenClaw integration boundary

OpenClaw should be integrated as a protected internal runtime.

### Backend should control
- which agent is invoked
- what context is passed
- what role/visibility rules apply
- what outputs are returned to which user surface
- what actions are auditable

### OpenClaw should not control
- the primary authorization model
- direct learner-facing UI surface
- parent-facing UI surface
- final permission decisions

## Operational safeguards

Minimum safeguards for MVP:
- structured logs for backend and key runtime events
- audit logging for sensitive actions and role-sensitive access
- health checks for core services
- deployment notes/runbook
- rollback notes
- backup/restore notes
- operator-only access to privileged surfaces

## Security posture for deployment

### Required boundaries
- learner and parent access only through intended product surfaces
- no raw OpenClaw UI exposure to learner or parent
- backend-enforced role checks before agent invocation
- OpenClaw and Postgres on internal network only
- admin/operator access protected more strongly than normal user access

### WhatsApp-specific caution
If WhatsApp is enabled:
- parent identity must be mapped explicitly
- webhook verification must be correct
- responses must remain parent-scoped
- the channel must not become a visibility or action bypass

## Out of scope for MVP deployment

Do not include initially unless clearly justified:
- Kubernetes
- many independent services
- separate queue infrastructure
- public database exposure
- direct public OpenClaw runtime surface for learner or parent
- complex autoscaling logic

## Open questions

- whether frontend should be one app with role-separated routes or two deployable apps
- whether staging is affordable from day one
- what WhatsApp provider/runtime path is preferred in the actual implementation
- whether operator/admin UI is separate or embedded early on
- what exact OpenClaw container/config shape is best for the chosen stack

## Recommended next artifact

The next useful artifact is either:
- `api-boundaries-v1.md`
or
- `repo-bootstrap-plan.md`

My recommendation: do `api-boundaries-v1.md` next, because the deployment shape is now clear enough that the backend/OpenClaw/product boundaries should be made explicit before implementation starts.
