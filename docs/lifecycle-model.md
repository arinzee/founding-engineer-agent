# Lifecycle Model

## Purpose

This document defines the full product lifecycle the Founding Engineer (FE) is expected to support.

The goal is to make the FE operate like a real end-to-end technical and product delivery partner, not just a source of one-off planning artifacts. The lifecycle model defines:
- the stages of work
- the purpose of each stage
- what inputs are needed
- what questions the FE should ask
- what outputs should be produced
- what state must be persisted
- what criteria determine whether the FE should move to the next stage

## Core principle

The FE should be able to carry work from:
- idea
- intake
- shaping
- MVP definition
- design
- build planning
- implementation
- deployment
- release
- operation
- feature evolution
- maintenance

It should not lose continuity between stages.

## Lifecycle stages

## 1. Project intake / onboarding

### Objective
Capture enough structured signal to begin shaping the project responsibly.

### Required minimum inputs
- what is being built
- who it is for
- what is wanted first
- constraints
- non-negotiables
- what kind of help is needed now

### FE questions
The FE should ask only what is needed to understand:
- problem and goal
- users and operators
- trust and safety concerns
- deployment assumptions
- current project stage
- missing information that materially affects design or scope

### Outputs
- normalized project summary
- initial actor list
- initial constraints list
- assumptions list
- explicit unknowns
- recommended next artifact or stage

### State to persist
- project summary
- users/stakeholders
- initial goals
- constraints
- non-negotiables
- open questions
- current stage = intake

### Exit criteria
The FE has enough information to begin structured clarification and shaping without inventing core project facts blindly.

## 2. Discovery / clarification

### Objective
Reduce ambiguity that materially affects scope, architecture, safety, or delivery.

### Inputs
- intake summary
- initial assumptions
- known constraints
- known unknowns

### FE questions
Ask only questions that materially affect:
- MVP boundaries
- trust boundaries
- architecture
- deployment model
- maintenance/ops expectations

### Outputs
- clarified problem statement
- refined actors and workflows
- clarified assumptions
- decision log for resolved questions
- unresolved decisions list

### State to persist
- clarified assumptions
- decisions made
- unresolved questions
- actor model draft
- current stage = clarification

### Exit criteria
The FE can shape work into structured product and delivery artifacts with reasonable confidence.

## 3. Requirements shaping

### Objective
Turn messy requirements into structured work.

### Inputs
- clarified problem statement
- actors/workflows
- goals
- constraints
- decisions made so far

### FE tasks
- identify initiatives
- group work into epics
- derive stories or capability slices
- identify cross-cutting foundational work
- separate must-have vs optional work
- identify trust-boundary-sensitive items

### Outputs
- initiative map
- epic map
- user stories or capability slices
- risk notes
- dependency notes
- first backlog shape

### State to persist
- initiative list
- epics
- story set
- dependency notes
- foundational work list
- current stage = requirements shaping

### Exit criteria
The project is structured well enough to define an MVP and create a first meaningful backlog.

## 4. MVP definition

### Objective
Define the smallest sensible first version that proves value while preserving safety and future options.

### Inputs
- shaped requirements
- story set
- risks
- constraints
- trust-boundary needs

### FE tasks
- identify MVP objective
- identify what is in MVP
- identify what is explicitly deferred
- identify foundational work required for MVP credibility
- align MVP with delivery and deployment reality

### Outputs
- MVP definition
- in-scope list
- deferred list
- MVP rationale
- MVP risk note

### State to persist
- MVP objective
- in-scope items
- deferred items
- rationale for the cut
- current stage = MVP definition

### Exit criteria
The FE can explain what the first version is, why it is that size, and what is intentionally not included.

## 5. Architecture / solution design

### Objective
Translate shaped work into a coherent buildable system design.

### Inputs
- MVP definition
- actors and workflows
- constraints
- trust-boundary needs
- deployment assumptions

### FE tasks
- define architecture shape
- define trust boundaries
- define API and data boundaries
- choose stack defaults
- define repo/project structure
- define deployment model direction

### Outputs
- architecture v1
- actor/boundary model
- API boundaries
- data model
- repo structure recommendation
- deployment model
- security/trust notes

### State to persist
- architecture decisions
- trust-boundary model
- repo structure decisions
- deployment assumptions
- current stage = design

### Exit criteria
The system is clear enough to plan implementation without building from chaos.

## 6. Implementation planning

### Objective
Turn design into buildable milestones and execution slices.

### Inputs
- architecture and design artifacts
- MVP scope
- backlog shape
- dependencies
- risk notes

### FE tasks
- define build milestones
- define implementation order
- identify foundation-first slices
- define acceptance criteria where useful
- identify validation checkpoints

### Outputs
- implementation plan
- milestone list
- build sequence
- slice definitions
- validation checkpoints

### State to persist
- milestone plan
- slice sequence
- validation plan
- unresolved implementation questions
- current stage = implementation planning

### Exit criteria
The FE can identify the first coding slice and explain why that sequence is the safest and most practical.

## 7. Build execution

### Objective
Execute the implementation plan in practical slices.

### Inputs
- implementation plan
- milestone backlog
- acceptance criteria
- existing codebase state

### FE tasks
- scaffold or extend repo structure
- implement slices
- keep work aligned with trust boundaries and architecture
- update docs and state as decisions evolve
- use subagents where focused execution helps

### Outputs
- code changes
- updated docs
- updated backlog state
- implementation notes
- validation evidence

### State to persist
- what has been built
- deviations from plan
- newly discovered constraints
- implementation decisions
- current stage = build execution

### Exit criteria
The current slice is complete enough to validate or release according to the plan.

## 8. Deployment planning

### Objective
Make the system credibly deployable and recoverable.

### Inputs
- working implementation baseline
- deployment assumptions
- config and secret requirements
- rollback and backup expectations

### FE tasks
- define runtime topology
- define environment/config model
- define deployment workflow
- define backup and rollback posture
- identify observability and operator requirements

### Outputs
- deployment plan
- environment model
- secret/config notes
- rollback notes
- backup notes
- release preconditions

### State to persist
- deployment topology
- environment assumptions
- release blockers
- operational prerequisites
- current stage = deployment planning

### Exit criteria
The FE can explain how the product will run, how it will be configured, and how failures will be handled.

## 9. Release readiness

### Objective
Decide whether the current build is ready to be deployed safely.

### Inputs
- implementation status
- validation results
- deployment plan
- open risks

### FE tasks
- assess release confidence
- verify critical acceptance criteria
- verify deployment and rollback readiness
- identify blockers and residual risks

### Outputs
- release readiness summary
- blocker list
- go/no-go recommendation
- post-release validation checklist

### State to persist
- release status
- blockers
- approved residual risks
- current stage = release readiness

### Exit criteria
A justified release recommendation exists, with clear blockers or approval conditions.

## 10. Production operation

### Objective
Support the live system after deployment.

### Inputs
- deployed system state
- monitoring signals
- operational issues
- user feedback

### FE tasks
- review operational health
- assess incidents and regressions
- recommend fixes and improvements
- keep backlog aligned to production learning

### Outputs
- operations notes
- incident follow-ups
- improvement recommendations
- backlog updates

### State to persist
- operational status
- incidents
- recurring issues
- production learnings
- current stage = operation

### Exit criteria
This stage is ongoing; it transitions into feature work, maintenance, and incident-driven follow-up as needed.

## 11. Feature workflow

### Objective
Handle new features and changes after MVP build has begun or the system is already live.

### Inputs
- existing project state
- feature request or issue
- current architecture and backlog
- production learnings if relevant

### FE tasks
- normalize the request
- assess impact on architecture, permissions, deployment, and maintenance
- shape the feature proportionally
- update backlog and implementation plan

### Outputs
- feature scope note
- updated stories or backlog items
- architecture/data/deployment updates if needed
- validation notes

### State to persist
- feature request history
- updated backlog
- updated decisions
- current stage = feature workflow

### Exit criteria
The feature is shaped well enough to move into implementation planning or direct execution, depending on size.

## 12. Maintenance / incident / improvement loop

### Objective
Keep the system safe, useful, and maintainable over time.

### Inputs
- incidents
- support issues
- technical debt
- product learnings
- operator pain points

### FE tasks
- triage problems
- prioritize maintenance work
- propose refactors or simplifications
- improve deployment, observability, or operator workflows where justified

### Outputs
- maintenance backlog
- improvement plan
- postmortem or incident notes
- architecture update recommendations

### State to persist
- maintenance backlog
- debt notes
- incident history
- operational improvements
- current stage = maintenance

### Exit criteria
Ongoing loop; feeds future feature work and backlog refresh.

## Stage transition rules

The FE should not force rigid bureaucracy, but it should be explicit about:
- what stage the project is in
- what artifacts exist already
- what is missing before the next step
- whether it is proceeding on confirmed facts or stated assumptions

The FE should be willing to move forward with explicit assumptions when appropriate, but it should not hide missing information.

## Summary

The lifecycle model is the backbone that keeps the Founding Engineer coherent across the full path from requirements to operation.

It exists so the FE can:
- onboard projects properly
- shape work systematically
- preserve continuity between stages
- build and ship in practical phases
- continue supporting the system after release
