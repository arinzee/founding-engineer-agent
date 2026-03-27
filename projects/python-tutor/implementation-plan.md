# Python Tutor Platform — Implementation Plan

## Goal

Build the MVP of a personal Python tutor platform that:
- provides a child-safe learner experience
- provides a parent progress experience
- uses OpenClaw behind the scenes
- enforces strong role and context boundaries
- can run on a VPS in containers

## Delivery approach

Use a staged delivery plan with a working product baseline first, then layer in orchestration and parent-channel complexity.

The first version should optimize for:
- correctness of boundaries
- learner experience usefulness
- parent visibility
- operational simplicity
- deployability

## Phase 0 — foundation and repo setup

### Objective
Create the initial project structure and define the implementation baseline.

### Work
- decide repository structure for the actual product
- define stack choices for frontend, backend, database, and OpenClaw integration
- define local development workflow
- define environment and secret strategy
- define deployment target assumptions for the VPS

### Output
- implementation repo structure
- stack decision record
- local/dev setup plan

## Phase 1 — backend and role foundation

### Objective
Establish the system of record and the trust-boundary foundation.

### Work
- implement core backend service
- implement learner / parent / operator identity model
- implement client/family relationship model
- implement policy and permission layer
- define data visibility classifications
- implement core persistence for learners, parents, sessions, and progress records
- implement audit logging baseline

### Output
- working backend baseline
- role and permission enforcement baseline
- persisted core entities

## Phase 2 — learner experience MVP

### Objective
Deliver the first child-safe learner product surface.

### Work
- implement learner web UI
- implement learner authentication/access path
- implement bounded tutoring session flow
- integrate learner agent through backend orchestration
- implement learner-safe context filtering
- implement basic progress recording
- implement age-appropriate learner progress display

### Output
- learner can enter the product safely
- learner can interact with tutoring sessions
- learner session data is persisted

## Phase 3 — parent experience MVP

### Objective
Deliver the first parent-facing experience.

### Work
- implement parent dashboard
- implement parent authentication/access path
- implement parent-visible progress summaries
- integrate parent agent through backend orchestration
- ensure parent-visible data is policy-filtered

### Output
- parent can log in
- parent can view learner progress
- parent can ask parent-facing questions in the dashboard

## Phase 4 — agent orchestration baseline

### Objective
Introduce the multi-agent orchestration model required for the product.

### Work
- integrate curriculum agent flow into tutoring logic
- implement super-agent supervision at basic orchestration level
- define context handoff rules between learner, parent, curriculum, and super agents
- ensure orchestration remains backend-controlled and auditable

### Output
- learner, parent, curriculum, and super-agent roles are functioning in bounded orchestration

## Phase 5 — deployment and operational baseline

### Objective
Make the MVP deployable and recoverable on a VPS.

### Work
- containerize frontend, backend, OpenClaw, and database
- set up reverse proxy
- configure runtime secrets
- define backups and restore basics
- define rollback procedure
- implement application and operational logging

### Output
- working VPS deployment baseline
- basic operational safety model

## Phase 6 — parent WhatsApp integration

### Objective
Add the first external parent channel, if included in MVP timing.

### Work
- integrate WhatsApp channel path through backend
- map parent identity to approved channel access
- route parent-safe context to the parent agent
- ensure auditability and policy enforcement for channel interactions

### Output
- parent can interact with the system through WhatsApp without bypassing product boundaries

## Suggested implementation order

Recommended order of execution:
1. backend and role foundation
2. learner experience MVP
3. parent experience MVP
4. deployment and operational baseline
5. agent orchestration baseline
6. parent WhatsApp integration

### Why this order
- trust boundaries come first
- learner and parent product value comes before deeper orchestration sophistication
- deployment baseline should exist before external channel complexity expands the surface area
- WhatsApp is valuable, but should not delay the safer core loop unless product validation depends heavily on it

## Risks to manage during implementation

- backend policy layer arriving too late
- OpenClaw agent wiring happening before context boundaries are defined
- child-safe UI being treated as just a frontend concern instead of a system boundary
- parent channel integration becoming a bypass path
- super-agent logic expanding faster than enforcement and auditability
- trying to solve multi-client scaling before one-client/family flow works well

## Validation checkpoints

### Checkpoint 1 — role and boundary foundation
Validate:
- role enforcement works
- learner cannot access parent/operator surfaces
- forbidden paths are blocked
- core data model supports visibility rules

### Checkpoint 2 — learner experience
Validate:
- learner sessions are bounded and useful
- learner-safe context filtering works
- progress is recorded correctly

### Checkpoint 3 — parent experience
Validate:
- parent sees only parent-allowed data
- progress summaries are useful
- parent agent responses stay within policy limits

### Checkpoint 4 — orchestration
Validate:
- learner/parent/curriculum/super-agent context routing is bounded
- super-agent does not bypass policy controls
- orchestration behavior is auditable

### Checkpoint 5 — deployment
Validate:
- VPS deployment is repeatable
- backups exist
- rollback path is documented and tested enough for MVP confidence

### Checkpoint 6 — WhatsApp
Validate:
- parent identity is mapped correctly
- channel messages do not bypass policy
- sensitive outputs are handled correctly

## Suggested near-term next artifact

The next useful artifact after this plan is likely:
- `data-model-v1.md`
or
- `repo-structure-v1.md`

My recommendation: do `data-model-v1.md` next, because permissions, visibility, progress, and agent-context boundaries all depend on it.
