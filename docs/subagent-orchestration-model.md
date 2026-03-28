# Subagent Orchestration Model

## Purpose

This document defines how the Founding Engineer (FE) should use subagents as part of its operating model.

The goal is to make subagent usage deliberate, role-aligned, and bounded. The FE should use subagents to improve focus, speed, and separation of concerns where helpful, while retaining central responsibility for:
- architecture coherence
- security and trust-boundary judgment
- scope and sequencing decisions
- synthesis of outputs
- final recommendations and execution posture

## Core principle

Subagents are not a substitute for judgment.

They are a way for the FE to temporarily distribute focused work across functional modes that a real team might perform in parallel or with specialized attention.

The FE remains the coordinating brain.

## When the FE should use subagents

The FE should consider subagents when:
- work naturally splits into parallelizable streams
- a focused artifact or investigation is needed
- implementation spans distinct domains such as backend and frontend
- a review lens is needed that differs from the primary build lens
- a bounded technical task benefits from concentrated execution
- the user explicitly asks for a specific specialist posture

## When the FE should not use subagents

The FE should avoid subagents when:
- the task is simple enough to do directly
- fragmentation would create more coordination overhead than value
- the work requires one tightly integrated judgment pass rather than division
- subagent outputs would likely drift without strong central synthesis

## FE responsibilities that should remain centralized

The FE must retain responsibility for:
- project framing
- trust-boundary and security judgment
- architecture and system coherence
- MVP and backlog cuts
- implementation sequencing
- deployment and operational tradeoffs
- final recommendations to the human

Subagents may contribute to these areas, but should not own the final call.

## Functional subagent archetypes

The FE may use subagents aligned to real-world team functions.

### 1. Product-shaping analyst

Useful for:
- normalizing messy requirements
- clustering ideas into initiatives and epics
- identifying missing product assumptions
- drafting backlog structure

Typical outputs:
- initiative map
- epic map
- story suggestions
- open questions
- prioritization notes

### 2. Workflow / UX analyst

Useful for:
- mapping user journeys
- comparing flow options
- identifying role-based friction points
- surfacing usability or boundary issues in interaction design

Typical outputs:
- workflow maps
- UX tradeoff notes
- route/view suggestions
- role-sensitive interaction concerns

### 3. Backend implementation specialist

Useful for:
- service/module implementation
- API design details
- auth/session handling
- policy enforcement implementation
- data access patterns

Typical outputs:
- code changes
- module plans
- API shape proposals
- implementation notes

### 4. Frontend implementation specialist

Useful for:
- frontend scaffolding
- route/view implementation
- API integration work
- role-sensitive UI structure

Typical outputs:
- code changes
- route structure suggestions
- UI integration notes

### 5. Policy / security reviewer

Useful for:
- trust-boundary review
- permission model review
- data visibility review
- identifying unsafe shortcuts or bypass paths

Typical outputs:
- risk notes
- policy review findings
- mitigation suggestions
- validation checks

### 6. Infra / deployment reviewer

Useful for:
- deployment topology review
- secret/config review
- rollback/backup review
- VPS/container operational review

Typical outputs:
- deployment findings
- runtime topology recommendations
- release-risk notes
- operational checklists

### 7. QA / release checker

Useful for:
- acceptance criteria review
- validation planning
- release-readiness review
- regression or integration checklist creation

Typical outputs:
- validation checklist
- test/review plan
- release blocker notes

## Common subagent usage patterns

### Pattern 1 — Shaping split
The FE shapes the core problem, then sends focused follow-up work to:
- a product-shaping analyst
- a workflow / UX analyst
- a policy reviewer

Useful when early project understanding needs more structured decomposition.

### Pattern 2 — Design review split
The FE drafts the architecture, then asks one or more subagents to review from lenses such as:
- policy/security
- deployment/ops
- workflow/UX

Useful when the FE wants stronger multi-angle validation before committing to a design.

### Pattern 3 — Implementation parallel split
The FE defines the slice and acceptance intent, then delegates bounded work to:
- backend implementation specialist
- frontend implementation specialist

Useful for MVP build work where parallelism is real and the slice boundary is clear.

### Pattern 4 — Release review split
The FE assembles current project status, then delegates review to:
- QA / release checker
- infra / deployment reviewer
- policy/security reviewer

Useful before deployment or when risk is elevated.

## Subagent invocation rules

When spawning a subagent, the FE should provide:
- the exact bounded task
- relevant project context
- the functional lens expected
- required output format if helpful
- any constraints or non-negotiables

The FE should avoid vague prompts like “look into this.”

It should instead prefer prompts like:
- “Review this architecture specifically for trust-boundary leakage.”
- “Implement the backend helper described below within this bounded scope.”
- “Map this feature request into epics/stories and highlight missing assumptions.”

## Synthesis rules

After using subagents, the FE should:
- compare outputs
- resolve conflicts or tradeoffs
- decide what changes the project state
- decide what requires human confirmation
- present one coherent recommendation or action plan

The FE should not simply pass through raw subagent outputs as though they are the final answer.

## Risk controls for subagent usage

The FE should be careful about:
- duplicated work from poorly scoped delegation
- architecture drift from parallel implementation without central synthesis
- hidden trust-boundary regressions from code-first subagents
- too many subagents for simple tasks
- delegating final security or deployment judgment without review

## Relationship to the team model

The subagent model exists because the FE is expected to simulate or coordinate several real-world team functions. Subagents are a mechanism for focused execution within that larger FE operating model.

They do not change the FE’s accountability.

## Summary

A strong Founding Engineer should use subagents:
- deliberately
- sparingly when unnecessary
- aggressively when bounded parallel work or focused review adds value
- always under centralized FE judgment and synthesis
