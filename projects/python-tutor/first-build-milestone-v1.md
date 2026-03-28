# Python Tutor Platform — First Build Milestone v1

## Purpose

This document defines the first implementation milestone for the Python Tutor Platform MVP.

The goal is to establish the minimum credible product and architecture baseline needed to begin real implementation without drifting into throwaway scaffolding or premature complexity.

## Milestone name
Milestone 1 — Product foundation baseline

## Milestone objective
Create the initial implementation baseline for the Python Tutor Platform as a modular monolith with:
- repo structure and app/package scaffolding
- backend control-plane foundation
- role and family/client domain baseline
- policy and permission baseline
- first protected learner and parent product paths
- demo or mocked session flow sufficient to exercise boundaries without requiring full production auth on day one

## Why this milestone comes first

This milestone creates the foundation required for later MVP slices without trying to ship the whole product at once.

It prioritizes:
- trust-boundary correctness
- family/client scoping
- backend authority
- product-surface separation
- implementation structure that can grow cleanly

It intentionally does not try to complete:
- rich learner tutoring flows
- full parent dashboard sophistication
- production-grade auth
- full orchestration complexity
- WhatsApp integration
- full operator tooling

## In scope

### Repo and code structure
- initialize the actual product repository structure
- scaffold deployable apps and reusable packages
- establish basic TypeScript workspace/tooling baseline

### Backend foundation
- create backend API application baseline
- create basic protected route structure for learner and parent flows
- centralize role/family/client context loading path early

### Domain foundation
- establish initial domain types for:
  - client family
  - user
  - learner profile
  - parent profile
  - family relationship
- create demo or mocked domain state helpers where useful for early product flow validation

### Policy foundation
- establish role and visibility model baseline
- create policy helper or authorization baseline
- ensure forbidden path enforcement starts in backend structure, not just UI routing

### Product surface baseline
- create first learner-facing protected path
- create first parent-facing protected path
- ensure each path resolves the correct role/family context
- ensure backend returns role-shaped data rather than only generic role labels

### Shared types / contracts baseline
- create shared DTO/type baseline for roles, identities, and early route outputs

## Explicitly out of scope for this milestone

- full production auth system
- rich curriculum sequencing
- full tutoring loop quality
- parent WhatsApp support
- advanced operator/admin experience
- advanced multi-agent supervision logic
- deployment hardening beyond initial repo/config baseline

## First implementation slices

## Slice 1 — Monorepo / workspace bootstrap
### Objective
Create the implementation repository baseline and top-level structure.

### Deliverables
- root workspace setup
- app/package directories aligned to repo structure recommendation
- package manager / TypeScript baseline
- basic run and typecheck commands

### Acceptance intent
- project installs cleanly
- workspace resolves packages correctly
- basic typecheck runs successfully

## Slice 2 — Shared role/domain/policy types baseline
### Objective
Create shared types and simple policy primitives needed across backend and frontend.

### Deliverables
- role types
- visibility/policy enums or equivalent
- base domain types for family/user/profile relationships
- initial policy helper shape

### Acceptance intent
- backend and frontend can share core role/domain contracts
- type boundaries reflect the intended product roles

## Slice 3 — Backend API scaffold and protected route baseline
### Objective
Establish the backend as the initial control plane.

### Deliverables
- backend app scaffold
- protected learner route baseline
- protected parent route baseline
- placeholder session or request identity handling

### Acceptance intent
- learner and parent paths are distinct
- role checks happen in backend structure
- backend returns role-aware responses

## Slice 4 — Demo session and family-context loading baseline
### Objective
Create the first current-user/current-family resolution flow for development and design validation.

### Deliverables
- mock or demo session model
- central helper for current user/context loading
- family/client scoping baseline
- role-aware route consumption of shared context

### Acceptance intent
- routes do not reconstruct session/family context ad hoc
- family-scoped domain resolution works consistently across protected paths

## Slice 5 — Learner and parent product-surface baseline
### Objective
Create the first usable web/app-facing baseline for learner and parent experiences.

### Deliverables
- learner surface scaffold
- parent surface scaffold
- route-level integration with backend protected paths
- domain-shaped demo data rendering

### Acceptance intent
- learner and parent surfaces are visibly distinct
- each surface receives only role-appropriate shaped data
- product starts to resemble a family-scoped tutoring system instead of a generic role shell

## Dependencies

- slice 1 before all others
- slice 2 before slices 3–5
- slice 3 before slice 5
- slice 4 should land by or during slice 3–5, but before route logic spreads too far

## Milestone validation

Before calling Milestone 1 complete, validate:
- workspace installs and typechecks
- learner and parent protected flows exist
- role/family context is resolved centrally enough to avoid ad hoc sprawl
- core domain baseline reflects family-scoped product logic
- backend is clearly acting as the control plane
- the implementation direction still matches architecture and repo-structure decisions

## Milestone result

If this milestone succeeds, the project should have:
- a real implementation repo baseline
- family-scoped domain structure
- backend-authoritative role/product flow baseline
- enough structure to begin learner and parent MVP feature development cleanly

## Recommended next milestone after this

Milestone 2 should deepen the learner and parent MVP experiences by building:
- real learner session flow
- basic progress recording
- parent progress summary baseline
- stronger orchestration integration where required by those flows
