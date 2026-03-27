# Python Tutor Platform — Architecture v1

## Purpose

This document describes the first architecture pass for the Python Tutor Platform MVP.

The goal is to define a deployable system that:
- provides a child-safe learner experience
- provides a parent progress and communication experience
- uses OpenClaw behind the scenes as the agent runtime/orchestration substrate
- enforces role, data, and AI context boundaries in the backend
- can run on a VPS in containers

## Architectural principles

1. **Custom product surfaces, not raw OpenClaw UI**
   - learners and parents interact with custom product interfaces
   - OpenClaw is not the user-facing product surface

2. **Backend is the authority**
   - permissions, data access, and forbidden paths are enforced in the backend
   - prompts and agent behavior do not define the security boundary

3. **OpenClaw is the agent runtime, not the policy engine**
   - OpenClaw runs and coordinates agents
   - the application backend decides what context, actions, and surfaces are allowed

4. **Child safety is a first-class design concern**
   - the learner experience is restricted by system design, not only by prompt tone

5. **Start as a modular monolith**
   - one backend service for product logic, policy, orchestration control, and data access
   - avoid premature service splitting in MVP

## High-level system shape

### Frontend surfaces

#### 1. Learner web app
Custom child-safe UI for:
- lesson interaction
- tutoring conversations
- exercises
- age-appropriate progress display

This is the only learner-facing interaction surface.

#### 2. Parent web app
Custom parent UI for:
- progress dashboard
- learner activity summaries
- parent-agent interaction
- future parent controls/preferences

#### 3. Parent WhatsApp channel
Optional MVP extension or early follow-on surface for parent-agent interaction.

#### 4. Operator/admin surface
Internal operator-facing control plane for:
- client provisioning
- super-agent configuration
- operational visibility
- incident handling

This should not be exposed to learners or parents.

## Backend platform

The backend should be a single modular application responsible for:
- authentication and identity
- role and permission enforcement
- client/family relationship model
- learner/parent/session/progress data access
- AI context filtering
- orchestration control over OpenClaw agents
- audit logging
- parent summary generation
- policy enforcement for all sensitive actions

### Suggested internal modules
- auth and identity
- client/family management
- learner session management
- progress and reporting
- policy and authorization
- agent orchestration control
- channel integration (WhatsApp)
- audit and operations

## OpenClaw role in the system

OpenClaw should sit behind the backend and provide:
- learner agent runtime
- parent agent runtime
- curriculum agent runtime/integration
- super-agent runtime
- channel integration support where appropriate
- agent session/state handling under backend control

### Important boundary
The backend should decide:
- which agent is invoked
- what context is passed
- what the agent is allowed to do
- what response is returned to which surface

OpenClaw should not be allowed to define user-visible authorization policy on its own.

## Agent model

### Learner agent
- child-facing tutoring behavior
- receives only learner-safe and learner-relevant context
- cannot access parent-private or operator-private context
- communicates only through the learner web app

### Parent agent
- parent-facing explanation and summary behavior
- receives parent-visible progress and approved learner insights
- may communicate via parent dashboard and WhatsApp

### Curriculum agent
- determines lesson progression and next-step recommendations
- not directly user-facing
- accessed through backend-supervised orchestration

### Super agent
- supervises per-client tutoring behavior
- can steer learner and parent agents
- can adapt behavior and coordination for the family/client
- operates inside backend-enforced boundaries
- should not itself become the true security or permission authority

## Identity and permission model

### Primary roles
- learner
- parent
- operator/admin

### Enforcement rules
- role enforcement happens in the backend
- UI restrictions must be backed by backend checks
- agent context eligibility is derived from backend policy
- forbidden paths are blocked at routing, API, and orchestration boundaries

### Key permission distinctions
- visibility vs action authority
- child-safe shared content vs parent-private content
- operator operational access vs household-private access
- agent-allowed context vs backend-held full context

## Data model — first-pass concepts

The initial data model should likely include:

### Core entities
- client / family
- learner
- parent
- operator relationship (internal)
- learner session
- lesson / curriculum unit
- exercise / task
- learner progress record
- parent-visible summary
- agent interaction record
- policy / visibility classification metadata
- audit event

### Visibility concepts
Each relevant object should have enough metadata or policy derivation to support:
- learner-scoped visibility
- parent-visible visibility
- operator-only visibility
- restricted / derived content handling

### Important rule
Derived summaries must not silently become less restricted than the source data they depend on.

## Request/response flow — example

### Learner interaction flow
1. learner uses child-safe web UI
2. backend authenticates learner and resolves client/family context
3. backend fetches learner-safe lesson/session context
4. backend chooses learner agent path in OpenClaw
5. backend sends filtered context only
6. OpenClaw returns agent output
7. backend validates/formats output for learner UI
8. response is shown to learner
9. relevant progress/audit/session data is recorded

### Parent interaction flow
1. parent uses dashboard or WhatsApp
2. backend authenticates/maps parent identity
3. backend fetches parent-visible learner progress context
4. backend invokes parent agent
5. backend returns parent-safe summary/response
6. interaction is logged where appropriate

## Deployment model

### Recommended MVP stack
- reverse proxy: Caddy
- frontend app (could be a single web app with role-separated experiences or separate frontend apps)
- backend API/application service
- OpenClaw service
- Postgres
- optional Redis later only if justified

### Deployment form
- Docker Compose on a VPS
- runtime-injected secrets
- persistent database volume
- backup strategy from day one

## Operational model

### Minimum operational requirements
- environment-specific config
- runtime secret management
- audit logs for sensitive actions and role-sensitive access
- application logs
- versioned deployment process
- documented rollback path
- database backup and restore basics

### Recommended MVP production posture
- one production environment
- optional staging if feasible
- strict separation of production credentials from local/dev
- operator-only access to admin/control surfaces

## WhatsApp integration boundary

If WhatsApp is included in MVP or shortly after:
- it should be parent-only
- parent identity must be mapped explicitly
- parent channel messages should go through backend policy checks before agent invocation
- the channel should not become a bypass around dashboard restrictions

## What is intentionally not in v1 architecture
- microservice decomposition
- broad multi-client control plane sophistication
- raw user-facing OpenClaw UI
- unrestricted learner channel access
- advanced analytics platform
- autonomous super-agent authority over safety boundaries
- coding sandbox unless explicitly added later

## Main architectural risks
- role/context leakage between learner, parent, operator, and agent layers
- overloading the super agent with too much authority
- treating OpenClaw as the policy layer instead of runtime substrate
- letting WhatsApp become a policy bypass
- scope creep into a much larger education platform before the tutoring loop is proven

## Recommended next artifact

The next architecture-level artifact should be either:
- `implementation-plan.md`
or
- `data-model-v1.md`

My recommendation is to do the implementation plan next, because the MVP shape is now clear enough to sequence work.
