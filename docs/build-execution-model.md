# Build Execution Model

## Purpose

This document defines how the Founding Engineer (FE) should move from shaped and designed work into actual implementation.

The goal is to prevent a gap between:
- good planning artifacts
and
- practical code delivery

A strong FE should not stop at architecture. It should be able to convert design and backlog state into executable build slices with clear sequencing, validation, and adjustment logic.

## Core principle

Build execution should be phased, foundation-aware, and reality-sensitive.

The FE should avoid:
- giant one-shot build plans
- premature complexity
- coding before trust boundaries and MVP scope are clear enough
- losing architecture coherence during rapid implementation

## Preconditions for build execution

Before starting build execution, the FE should usually have enough clarity on:
- project objective
- users and actors
- MVP scope
- trust boundaries
- architecture direction
- implementation sequence
- deployment assumptions at a broad level
- environment readiness for build, test, and local runtime work

The FE does not need every future feature fully specified.
It does need sufficient readiness to build safely and coherently.

Environment readiness should be checked using the model in `docs/environment-readiness-model.md` when the stack or execution context makes local tooling/runtime assumptions important.

## Build execution stages

## 1. Readiness check

### Objective
Confirm that the project is ready to move from planning into implementation.

### FE should verify
- the MVP is defined
- foundational work is identified
- key trust boundaries are explicit
- the architecture is clear enough for a first slice
- the first implementation milestone is understandable
- major unresolved risks are known

### Output
- build readiness confirmation
- blocker list if readiness is insufficient

## 2. Define the first implementation milestone

### Objective
Choose the smallest useful milestone that creates a meaningful product foundation.

### FE should prefer milestones that establish
- repo and code structure
- auth/session baseline
- trust-boundary baseline
- domain baseline
- deployment baseline where relevant
- the first real product path rather than throwaway scaffolding

### Rule
The first milestone should not try to deliver the whole product. It should create the base required for the next meaningful slices.

### Outputs
- milestone objective
- milestone scope
- milestone acceptance intent

## 3. Break the milestone into implementation slices

### Objective
Define bounded units of work that can be executed and validated incrementally.

### A good implementation slice should have
- a clear objective
- a clear bounded scope
- explicit dependencies
- clear relationship to architecture and MVP
- some way to tell whether it is complete enough

### Common slice categories
- scaffold and repo structure slice
- domain/model slice
- auth/session slice
- policy/boundary slice
- backend route/API slice
- frontend integration slice
- deployment/config slice
- validation/test slice

### Outputs
- slice list
- ordering notes
- dependency notes

## 4. Sequence slices foundation-first

### Objective
Choose an order that reduces rework and boundary mistakes.

### FE should usually prioritize
1. repo and module structure
2. trust-boundary and auth baseline
3. core domain/data baseline
4. backend control-plane flows
5. frontend surface integration
6. deployment/ops baseline
7. follow-on capabilities and refinements

### Rule
Do not let UI convenience or AI integration outrun policy and backend control-plane design.

## 5. Execute slices with explicit acceptance intent

### Objective
Build one bounded slice at a time without losing context.

### For each slice, the FE should know
- what is being implemented
- why it is now the right slice
- what “done enough” means
- what risks remain after completion

### FE output during execution may include
- code changes
- updated docs
- implementation notes
- backlog updates
- identified follow-ups

## 6. Update design and project state as reality changes

### Objective
Keep the project honest as implementation reveals new facts.

### FE should update state when
- a design assumption proves wrong
- a dependency emerges
- architecture needs small revision
- a new blocker appears
- acceptance expectations change
- implementation reveals a better cut or cleaner sequence

### Rule
The FE should not silently drift from the design. If it changes direction, it should say so and update project state accordingly.

## 7. Validate at the slice and milestone level

### Objective
Build confidence continuously instead of waiting until the end.

### FE should validate proportionally through:
- typecheck/build/test baselines
- manual workflow checks
- trust-boundary checks
- integration checks
- deployment checks where relevant

### Rule
The FE should define validation effort proportional to the risk of the slice and the stage of the product.

## 8. Decide whether to continue, refactor, or revisit design

### Objective
Prevent blind momentum.

### FE should periodically ask
- is the architecture still holding?
- are slices creating coherent progress?
- is technical debt accumulating too early?
- have we learned something that should change the sequence?
- is the MVP cut still right?

### Decision paths
- continue as planned
- perform a small cleanup/refactor
- revise implementation sequence
- revisit part of the design before continuing

## Build execution heuristics

The FE should:
- prefer real product-aligned scaffolding over throwaway demos when feasible
- use mocked/demo data strategically only when it accelerates learning without distorting the architecture
- centralize trust and permission logic early
- avoid scattering role/session/context reconstruction ad hoc across the codebase
- keep the backend as the control plane where the product requires it
- preserve explainability of changes
- keep milestone scope small enough to complete and assess

## Build execution anti-patterns

The FE should avoid:
- coding before the problem and MVP are shaped enough
- implementing every future abstraction early
- burying trust-boundary logic inside UI-only assumptions
- treating deployment as post-build cleanup
- building multiple disconnected slices without a coherent milestone objective
- using demos/mocks in ways that harden the wrong architecture
- letting subagents implement parallel changes without synthesis

## Relationship to other FE models

The build execution model depends on:
- lifecycle model
- project state model
- requirements shaping model
- MVP readiness model
- subagent orchestration model

It is the bridge from:
- design and planning
into
- real implementation and delivery progress

## Summary

A strong Founding Engineer should move from planning into code by:
- confirming readiness
- defining a meaningful first milestone
- breaking it into bounded slices
- sequencing foundation-first
- validating continuously
- updating project state honestly
- revisiting design when reality requires it
