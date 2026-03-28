# Python Tutor Platform — API Boundaries v1

## Purpose

This document defines the first-pass API and interaction boundaries for the Python Tutor Platform MVP.

The goal is to make explicit:
- what the frontend talks to
- what the backend owns
- how OpenClaw is invoked
- how parent channels such as WhatsApp enter the system
- where permissions and visibility checks must happen

## Core rule

The frontend and external channels talk to the **backend product API**.

The backend product API talks to:
- Postgres
- OpenClaw
- external providers as needed

The learner and parent experiences do **not** talk directly to OpenClaw.

That boundary is one of the core safety and product rules.

## Primary boundary map

### Learner web app
May call:
- backend API endpoints for learner auth/session
- backend API endpoints for lesson/session state
- backend API endpoints for learner tutoring interaction
- backend API endpoints for learner progress view

Must not call:
- OpenClaw directly
- operator/admin APIs
- parent-only APIs
- unrestricted channel endpoints

### Parent web app
May call:
- backend API endpoints for parent auth/session
- backend API endpoints for progress dashboard
- backend API endpoints for parent-agent interaction
- backend API endpoints for parent settings/preferences when added

Must not call:
- OpenClaw directly
- learner-only APIs when not allowed
- operator/admin APIs unless explicitly authorized

### Parent WhatsApp channel
May reach:
- backend webhook endpoint only

Must not reach:
- OpenClaw directly
- hidden internal APIs
- privileged admin surfaces

### Operator/admin surface
May call:
- backend operator/admin APIs
- product-admin orchestration APIs

Should still not call OpenClaw directly unless there is a very deliberate operational/admin path and it is strongly controlled.

## Backend API responsibilities

The backend API is the product control plane.

It owns:
- identity and session handling
- role resolution
- permission checks
- visibility checks
- client/family scoping
- data access
- progress and summary retrieval
- context filtering before agent invocation
- OpenClaw invocation routing
- audit event recording
- safe formatting of outputs to each surface

## OpenClaw invocation boundary

The backend should invoke OpenClaw through internal orchestration functions such as:
- invoke learner agent
- invoke parent agent
- invoke curriculum agent
- invoke super agent

### Important rule
The backend decides:
- who is acting
- what role they have
- what client/family scope applies
- what data is eligible as agent context
- what action type is being attempted
- what output can be returned

OpenClaw should not receive raw unconstrained user context by default.

## Suggested API surface areas

## 1. Auth and identity APIs
Examples:
- learner sign-in/session start
- parent sign-in/session start
- operator/admin sign-in
- session refresh / session end

Rules:
- backend authenticates and establishes role context
- all later API access depends on this context

## 2. Learner APIs
Examples:
- get current learner session
- get lesson/task state
- submit learner response
- request tutoring help
- get learner progress view

Rules:
- learner role required
- learner can only access their own allowed scope
- tutoring output must be filtered through learner-safe boundaries

## 3. Parent APIs
Examples:
- get learner progress dashboard
- get parent summary view
- ask parent-agent question
- later: update selected tutor preferences

Rules:
- parent role required
- parent-family relationship must be valid
- responses must be parent-visible only

## 4. Operator/admin APIs
Examples:
- create or configure client/family instance
- configure super-agent settings
- inspect operational state
- review audit events

Rules:
- operator/admin role required
- sensitive access should be audited
- operator access should not automatically imply unrestricted household-private content unless explicitly intended

## 5. Agent orchestration APIs (internal)
These may not need to be public HTTP APIs initially.
They may begin as internal service-layer functions inside the backend.

Examples:
- build learner-agent context
- build parent-agent context
- invoke curriculum recommendation
- invoke super-agent supervision
- store interaction record
- generate parent summary

Recommendation:
- keep these internal to the backend in MVP
- do not prematurely expose them as public service APIs

## 6. Channel/webhook APIs
Examples:
- WhatsApp inbound webhook
- channel verification endpoint
- message delivery callback endpoint if needed

Rules:
- provider verification must happen first
- parent identity must be mapped explicitly
- backend applies role and visibility rules before agent invocation
- outbound responses must remain parent-scoped and auditable

## Permissions boundary rules

### Rule 1 — UI visibility is not authorization
Frontend routing and UI hiding are useful, but not sufficient.
All sensitive reads/writes must be checked in the backend.

### Rule 2 — role checks happen before agent invocation
The backend should not first invoke an agent and then decide whether the result was allowed.
Eligibility should be enforced before context is built and before the invocation happens.

### Rule 3 — outputs inherit visibility limits
A derived summary or agent response must not exceed the visibility of the data it is allowed to use.

### Rule 4 — operator/admin APIs are distinct
Operator paths should be separated clearly from parent/learner product flows.

## Example flow boundaries

### Learner tutoring request
1. learner UI sends request to backend
2. backend resolves learner identity and client/family scope
3. backend checks learner permission and session state
4. backend builds learner-safe context
5. backend invokes learner agent through internal orchestration path
6. backend validates/formats response
7. backend stores interaction/progress/audit data
8. backend returns learner-safe output to UI

### Parent dashboard summary request
1. parent UI requests dashboard data
2. backend resolves parent identity and family relationship
3. backend loads progress and summary state
4. backend returns parent-visible summary data only

### Parent WhatsApp message
1. WhatsApp provider posts to backend webhook
2. backend verifies provider and maps sender to parent identity
3. backend loads parent-visible context
4. backend optionally invokes parent agent
5. backend stores interaction/audit records
6. backend sends approved response via provider path

## What should not be APIs yet

For MVP, avoid prematurely creating separate public APIs for:
- curriculum-agent direct control
- super-agent direct control
- policy engine configuration
- raw OpenClaw session management for end users

These should remain internal or operator-controlled until the product boundaries are stable.

## API design implications for MVP

### Keep public API simple
Public API should mainly expose:
- learner product flows
- parent product flows
- parent channel/webhook entry
- operator/admin product flows

### Keep internal orchestration richer
Internal service boundaries can carry:
- agent role information
- context eligibility
- orchestration metadata
- audit instructions
- policy evaluation results

## Open questions

- whether learner and parent web apps should share one backend auth/session model or separate tailored session experiences
- how much of operator/admin tooling belongs in MVP APIs versus manual/internal tools
- whether parent summaries should be retrieved as precomputed records or generated on request
- what exact WhatsApp provider integration model will be used

## Recommended next artifact

The next useful artifact is either:
- `build-sequence-v1.md`
or
- `tech-stack-decisions.md`

My recommendation: do `tech-stack-decisions.md` next, because the system boundaries are now clear enough that choosing concrete implementation technology is the next meaningful design decision.
