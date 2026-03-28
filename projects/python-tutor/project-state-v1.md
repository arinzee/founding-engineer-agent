# Python Tutor Platform — Project State v1

## Purpose

This document captures the current canonical project state for the Python Tutor Platform.

The goal is to preserve continuity across shaping, design, implementation planning, deployment planning, and eventual build execution, so the project can move forward without repeatedly rediscovering its core decisions.

## Project identity

### Project name
Python Tutor Platform

### Short summary
A family-scoped Python tutoring product powered by OpenClaw behind the scenes, with separate learner and parent experiences, backend-enforced trust boundaries, and a deployable VPS/container operating model.

### Current phase
Pre-build / implementation handoff

## Problem and goal

### Core problem
Build a child-safe, parent-aware tutoring platform that uses OpenClaw as the orchestration/runtime layer without exposing raw OpenClaw UI or prompt-level behavior as the real product boundary.

### Immediate goal
Move from design-complete planning artifacts into a credible implementation baseline for MVP.

### MVP objective
Deliver a first version for a single family/client unit that proves:
- learner experience usefulness and safety
- parent experience usefulness
- backend-enforced role and context boundaries
- bounded multi-agent orchestration
- deployability on a VPS in containers

## Users, stakeholders, and actors

### Primary users
- learner / child
- parent / guardian

### Operators
- platform operator
- optional future admin/operator roles

### Key internal/system actors
- learner agent
- parent agent
- curriculum agent
- super agent
- backend platform
- OpenClaw runtime

## Key workflows

### Learner workflows
- access tutor through child-safe UI only
- participate in tutoring/lesson/exercise flows
- receive age-appropriate progress visibility

### Parent workflows
- view learner progress and summaries
- interact with parent-facing agent
- potentially interact via WhatsApp in MVP or early follow-on

### Operator workflows
- configure client/family setup
- supervise tutor behavior and orchestration
- review operational and safety signals

## Constraints and non-negotiables

### Technical
- VPS-hosted
- containerized deployment
- OpenClaw is the orchestration/runtime substrate
- no raw OpenClaw UI exposure to learner or parent

### Trust and safety
- learner boundaries must be system-enforced
- parent and learner access must be clearly separated
- backend is the real policy/control plane
- super agent must not become the true security boundary

### Product
- product should start small
- MVP should avoid solving every tutoring problem at once

## Major decisions already made

- product is family/client scoped
- learner and parent experiences are separate product surfaces
- backend is authoritative for permissions, context eligibility, and forbidden paths
- OpenClaw sits behind the product layer
- architecture should start as a modular monolith
- deployment should start on a VPS in containers
- WhatsApp is the preferred first parent channel, but should not weaken product boundaries
- target learner age range starts at 7+

## Current artifact map

### Intake and shaping
- `problem-intake.md`
- `actor-boundary-model.md`
- `initiative-epic-map.md`
- `mvp-definition.md`
- `mvp-story-prioritization.md`

### Design
- `architecture-v1.md`
- `api-boundaries-v1.md`
- `data-model-v1.md`
- `repo-structure-v1.md`

### Delivery and operations planning
- `implementation-plan.md`
- `deployment-model-v1.md`

## MVP scope summary

### In MVP
- learner web experience
- parent dashboard experience
- backend-enforced role and context boundaries
- learner/parent/operator role model
- bounded learner/parent/curriculum/super-agent orchestration
- progress and summary baseline
- VPS/container deployment baseline
- audit, backup, rollback basics

### Optional inside MVP if capacity allows
- parent WhatsApp interaction with strong policy controls

### Deferred / later
- broader parent channel set
- advanced admin tooling
- advanced analytics
- advanced automation-heavy orchestration
- broader multi-client platform concerns
- richer escalation and risk systems

## Current implementation posture

### What is ready
The project appears ready to begin implementation planning at the milestone and slice level.

### What is not yet present in this project pack
- a canonical first build milestone definition
- a first-slice execution plan
- an implementation repo initialized from the recommended structure

## Main open questions

- should MVP use one frontend codebase with role-separated routes or separate learner and parent apps from the start?
- should WhatsApp be included inside MVP timing or treated as a near-term follow-on after core learner/parent web flows are working?
- how much operator surface should exist in MVP versus lightweight backend-admin routes?
- what exact first implementation milestone should be used to establish the product baseline cleanly?

## Current priorities

1. define the first implementation milestone
2. define the first implementation slices
3. choose implementation repo/bootstrap approach
4. begin building the backend/control-plane foundation

## Recommended next step

Create the first implementation milestone and first-slice execution plan, then bootstrap the actual implementation repo in the order defined by the implementation and repo-structure artifacts.

## Status summary

The Python Tutor project is no longer in vague concept stage.
It has:
- problem framing
- trust-boundary definition
- MVP definition
- architecture and API thinking
- data model direction
- repo structure recommendation
- implementation planning
- deployment model direction

The project is now at the point where the next meaningful FE move is not more broad shaping, but a controlled handoff into implementation execution.
