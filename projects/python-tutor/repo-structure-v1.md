# Python Tutor Platform — Repo Structure v1

## Purpose

This document proposes the first repository structure for building the Python Tutor Platform MVP.

The goal is to support:
- custom learner and parent product surfaces
- backend-enforced permissions and orchestration control
- OpenClaw integration behind the product layer
- a deployable VPS/container setup
- room to evolve without premature service sprawl

## Recommendation

For MVP, use a **single product repository** with a modular internal structure.

Do not begin with multiple repositories or many deployable services.

The system is already complex enough because of:
- role boundaries
- child-safe requirements
- agent orchestration
- progress tracking
- parent channel integration

A single repo will make it easier to:
- keep boundaries coherent
- change interfaces quickly
- evolve the data model safely
- deploy and rollback consistently

## Proposed top-level structure

```text
python-tutor/
├── README.md
├── docs/
│   ├── product/
│   ├── architecture/
│   ├── operations/
│   └── decisions/
├── apps/
│   ├── learner-web/
│   ├── parent-web/
│   ├── operator-web/         # optional early, can start as internal admin pages in backend
│   └── backend-api/
├── packages/
│   ├── auth/
│   ├── policy/
│   ├── domain/
│   ├── agent-orchestration/
│   ├── progress/
│   ├── summaries/
│   ├── channels/
│   ├── curriculum/
│   ├── audit/
│   └── shared-types/
├── infra/
│   ├── docker/
│   ├── caddy/
│   ├── scripts/
│   └── env/
├── openclaw/
│   ├── agents/
│   ├── configs/
│   └── references/
├── tests/
│   ├── integration/
│   ├── policy/
│   ├── orchestration/
│   └── e2e/
└── tools/
```

## Structure rationale

## `apps/`
Holds deployable application surfaces.

### `apps/learner-web/`
Learner-facing web UI.

Responsibilities:
- child-safe tutoring interface
- lesson and exercise interaction
- learner progress view
- learner authentication/session handling via backend APIs

### `apps/parent-web/`
Parent-facing web UI.

Responsibilities:
- parent dashboard
- parent summaries
- parent-agent interaction
- future parent settings/preferences

### `apps/operator-web/`
Optional early dedicated operator surface.

For MVP, this can start smaller or be embedded into backend-admin routes.
If separated later, it should support:
- client provisioning
- super-agent configuration
- operational review
- audit/incident visibility

### `apps/backend-api/`
The core product backend.

Responsibilities:
- auth and identity
- permissions and policy enforcement
- data access
- learner/parent/session/progress APIs
- agent context filtering
- OpenClaw orchestration control
- WhatsApp integration hooks
- summaries and audit/event handling

This is the most important deployable unit.

## `packages/`
Holds reusable internal modules used by the backend and possibly by multiple apps.

### `packages/auth/`
- authentication helpers
- identity/session logic
- role resolution

### `packages/policy/`
- visibility rules
- action authorization
- forbidden path checks
- agent context eligibility

### `packages/domain/`
- core domain models
- client/family
- learner/parent
- sessions
- lessons
- exercises

### `packages/agent-orchestration/`
- learner agent invocation rules
- parent agent invocation rules
- curriculum-agent integration
- super-agent supervision control
- orchestration contracts with OpenClaw

### `packages/progress/`
- progress records
- learner state
- progress summarization inputs

### `packages/summaries/`
- parent-facing summary generation
- derived content rules
- safe transformation logic

### `packages/channels/`
- WhatsApp integration logic
- parent identity mapping
- channel-specific policy enforcement

### `packages/curriculum/`
- curriculum-agent integration
- lesson sequencing helpers
- curriculum state mapping

### `packages/audit/`
- audit event creation
- operational and sensitive-action logging helpers

### `packages/shared-types/`
- shared DTOs
- enums
- visibility classifications
- role and agent type definitions

## `openclaw/`
Keeps product-controlled OpenClaw integration artifacts together.

### `openclaw/agents/`
- learner-agent definitions or references
- parent-agent definitions or references
- curriculum-agent definitions or references
- super-agent definitions or references

### `openclaw/configs/`
- environment-specific OpenClaw integration config
- policy-related references where appropriate

### `openclaw/references/`
- notes about how the product uses OpenClaw
- integration decisions
- runtime assumptions

Important: this folder should support the product’s integration with OpenClaw, not become the primary user-facing product surface.

## `infra/`
Infrastructure and deployment material.

### `infra/docker/`
- Dockerfiles
- Compose files
- local/prod variants if needed

### `infra/caddy/`
- reverse proxy configuration

### `infra/scripts/`
- operational helper scripts
- deploy/backup/restore helpers as they mature

### `infra/env/`
- environment variable references
- example config templates
- secret naming references (not raw secrets)

## `tests/`
A product like this needs more than unit tests.

### `tests/policy/`
- role enforcement tests
- visibility tests
- forbidden path tests
- context eligibility tests

### `tests/orchestration/`
- learner/parent/super-agent context flow tests
- policy-boundary tests on orchestration

### `tests/integration/`
- backend/data/channel/invocation flow tests

### `tests/e2e/`
- learner UI flows
- parent UI flows
- key bounded interaction flows

## `docs/`
Project docs that support actual product delivery.

Recommended substructure:

### `docs/product/`
- problem framing
- actor boundaries
- MVP docs
- user stories

### `docs/architecture/`
- architecture v1
- data model
- request flows
- security notes

### `docs/operations/`
- deployment model
- rollback notes
- backups
- incident procedures later

### `docs/decisions/`
- ADR-style decisions
- tradeoffs
- major scope calls

## Suggested implementation simplification for early MVP

To avoid overbuilding:
- `learner-web` and `parent-web` can initially live in one frontend codebase with role-separated routes if that is simpler
- `operator-web` can initially be lightweight or embedded in backend-admin tools
- many `packages/` can begin as internal modules inside `backend-api` before being split cleanly

The important thing is not premature package extraction.
The important thing is keeping the boundaries conceptually clear from day one.

## What not to do in v1

Do not begin with:
- multiple repos
- separate microservices for each agent type
- a standalone workflow service
- a standalone summary service
- a standalone policy service
- deeply coupled vendor-specific structure spread across the codebase

That would add complexity before the product proves itself.

## Recommended next artifact

The next useful artifact after repo structure is:
- `deployment-model-v1.md`
or
- `api-boundaries-v1.md`

My recommendation: do `deployment-model-v1.md` next, because the product is explicitly intended for VPS/container deployment and that operational shape should be made concrete early.
