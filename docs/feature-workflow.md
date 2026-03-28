# Feature Workflow

## Purpose

This document defines how the Founding Engineer should handle new features, changes, and improvements after the MVP has started or shipped.

The goal is to reuse the same core project-shaping logic without forcing every post-MVP change through the full weight of a greenfield project workflow.

## Core principle

New features should follow the same reasoning pattern as MVP work:
- intake
- clarification
- shaping
- design
- delivery planning
- execution and release thinking
- deployment and maintenance thinking

But the depth should be proportional to the size, risk, and architectural impact of the change.

## Feature workflow overview

The intended feature workflow is:
1. feature intake
2. impact clarification
3. scoped feature shaping
4. design/update decision
5. implementation and deployment planning
6. execution and release handling as needed
7. post-release review when needed

Feature work should be understood as an extension of the lifecycle and project-state models, not a separate disconnected process.

## Stage 1 — Feature intake

### Goal
Capture enough detail to understand the requested change.

### Typical input
A feature request should usually include:
- what is changing
- who it affects
- why it matters
- whether it is net-new, an extension, a fix, or a refactor
- any constraints or non-negotiables

The input can still be messy. The Founding Engineer should normalize it and relate it back to the existing project state, backlog, architecture decisions, and operational context.

## Stage 2 — Impact clarification

### Goal
Determine what kind of feature or change this is.

The Founding Engineer should assess whether the feature affects:
- user experience only
- data model
- trust boundaries or permissions
- agent context rules
- deployment/infrastructure
- integrations
- auditability or operations

### Rule
The more the feature affects boundaries, infrastructure, or safety, the more rigor it needs.

## Stage 3 — Scoped feature shaping

### Goal
Turn the feature into a bounded delivery slice.

Depending on complexity, the Founding Engineer may produce:
- a small problem intake
- one or more user stories or capability slices
- updated acceptance criteria
- an MVP-vs-later feature cut
- an updated risk note
- backlog updates and dependency notes

Not every feature needs a full initiative/epic breakdown.

## Stage 4 — Design/update decision

### Goal
Decide whether the feature can fit into the existing architecture or requires broader design updates.

### The Founding Engineer should determine whether the feature requires:
- no architectural change
- a small architecture extension
- a data model update
- a trust-boundary or permission update
- an infrastructure/deployment update
- a broader refactor before implementation

### Rule
Do not assume every feature is “just implementation.”
Some features are actually architecture or boundary changes and should be treated accordingly.

## Stage 5 — Implementation and deployment planning

### Goal
Define how the feature should be built and released.

The Founding Engineer should produce enough guidance to answer:
- what is being implemented now
- what dependencies exist
- what validation is needed
- whether rollout should be staged
- whether infra or deployment changes are required
- what is explicitly deferred
- how project state and backlog priority should be updated

## Stage 6 — Execution and release handling as needed

### Goal
Carry the feature through implementation, validation, and release activity at the level of rigor justified by the change.

This may include:
- bounded implementation planning
- subagent use for focused execution or review
- release-readiness checks
- deployment review
- rollback notes for risky changes

## Stage 7 — Post-release review when needed

### Goal
Ensure the feature behaves as intended and does not create hidden issues.

This may include:
- feature-specific validation notes
- maintenance review notes
- incident or rollback notes if something went wrong
- follow-up improvements

## Feature categories and expected rigor

### 1. Small product feature
Examples:
- simple UI addition
- small parent dashboard enhancement
- low-risk workflow improvement

Expected rigor:
- light intake
- scoped stories
- implementation plan
- validation notes

### 2. Boundary-sensitive feature
Examples:
- new parent/child visibility path
- new channel access
- new agent context source
- role-based action expansion

Expected rigor:
- intake
- trust-boundary check
- policy and data visibility review
- validation and rollout thinking

### 3. Data or architecture-impacting feature
Examples:
- new progress model
- new orchestration layer
- new lesson-state structure
- major reporting change

Expected rigor:
- intake
- scope shaping
- architecture or data-model update
- implementation sequencing
- migration or rollout notes if needed

### 4. Infrastructure-affecting feature
Examples:
- new queue
- new service
- channel/webhook addition
- deployment topology change

Expected rigor:
- intake
- architecture/deployment review
- secret/config implications
- rollback and ops implications

## Decision rule for feature work

The Founding Engineer should recommend the lightest process that still preserves:
- safety
- clarity
- architecture coherence
- deployability
- maintainability

That means:
- not every feature needs full-project depth
- but no feature should bypass boundary, deployment, or maintenance thinking when those are materially affected

## Relationship to the MVP workflow

### Before MVP build
Use the full project workflow to get to MVP readiness.

### After MVP build starts or ships
Use the feature workflow for incremental work, while pulling in deeper artifacts only when the feature meaningfully affects:
- architecture
- data model
- permissions and trust boundaries
- deployment or operations

## Expected FE output for a feature request

A good Founding Engineer response to a feature request should usually clarify:
- what the feature really is
- who it affects
- whether it changes trust boundaries, architecture, or deployment
- what level of process/rigor is needed
- what the next artifact or implementation step should be
- how backlog and project state should change

## Summary

The feature workflow reuses the same Founding Engineer thinking as MVP work, but with proportional depth.

This allows the agent to support the full lifecycle of a product:
- MVP creation
- feature expansion
- architecture evolution
- deployment changes
- ongoing maintenance

without treating every new feature like a brand-new greenfield project.
