# Python Tutor Platform — Execution Handoff v1

## Purpose

This document is the handoff bridge from the Python Tutor project pack into actual implementation work.

It is meant to answer:
- what has already been established
- what should be treated as canonical
- what should happen next
- how the implementation should begin without reinterpreting the whole project from scratch

## What has already been established

The project pack already defines:

### Product framing
- the product goal
- primary users and operators
- key constraints
- non-negotiables
- child-safety and trust-boundary requirements

### Structured project shape
- actor and boundary model
- initiative and epic structure
- MVP definition
- MVP story prioritization

### Solution design
- architecture direction
- API boundary direction
- data model direction
- repo structure direction

### Delivery and operations direction
- implementation sequencing
- deployment model
- operational baseline expectations

## Canonical documents to use during implementation

### Use these as the primary source of truth
- `project-state-v1.md`
- `mvp-definition.md`
- `architecture-v1.md`
- `api-boundaries-v1.md`
- `data-model-v1.md`
- `repo-structure-v1.md`
- `implementation-plan.md`
- `deployment-model-v1.md`
- `first-build-milestone-v1.md`

## Core implementation principles that should not be re-decided casually

- backend is the authority for auth, policy, context eligibility, and forbidden paths
- OpenClaw is behind the product layer, not the user-facing product surface
- learner and parent experiences are separate product surfaces
- family/client is the core scoping boundary
- start as a modular monolith
- deploy on a VPS in containers
- child-safe and parent/learner boundary rules must be system-enforced
- super agent must not become the real security boundary

## Immediate implementation objective

Complete Milestone 1 — Product foundation baseline.

That means creating:
- the implementation repo/workspace baseline
- backend control-plane scaffold
- shared role/domain/policy contracts
- first learner and parent protected paths
- family/client context loading baseline

## Recommended order of execution

1. bootstrap the implementation repo/workspace
2. create shared types/domain/policy baseline
3. scaffold backend protected route structure
4. add demo session and current-user/current-family loading helper
5. connect learner and parent product-surface baselines
6. validate install/typecheck and role/family flow behavior

## What to avoid during initial execution

Do not:
- start with WhatsApp integration
- let frontend routing become the real security boundary
- expose raw OpenClaw UI to users
- implement orchestration complexity before backend context boundaries are clear
- prematurely split into many services
- add advanced operator tooling before the core family flow works

## Expected output of the handoff stage

At the end of the first implementation handoff and build milestone, there should be:
- a real implementation repo baseline
- a first meaningful set of protected product paths
- family-scoped domain types in code
- backend control-plane behavior starting to exist in implementation form
- enough structure to continue MVP development without architectural confusion

## Next decision after Milestone 1

After Milestone 1, reassess:
- whether learner and parent product baselines are sufficient to deepen into real MVP flows
- whether the current repo structure is holding cleanly
- whether orchestration integration should begin now or after learner/parent product flows are stronger
- whether WhatsApp remains in MVP timing or should move to the first post-core milestone

## Summary

This handoff exists to prevent implementation drift.

The Python Tutor pack is already strong enough to guide real build work. The next job is not to re-plan the product from zero, but to begin implementation in a controlled way using the established trust boundaries, MVP scope, architecture direction, and first milestone definition.
