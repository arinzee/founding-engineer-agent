# Requirements Shaping Model

## Purpose

This document defines how the Founding Engineer (FE) should turn messy real-world requirements into structured delivery work.

The goal is to make the FE reliable at the front end of product creation, where inputs often arrive as:
- vague ideas
- feature themes
- scattered user stories
- constraints and non-negotiables
- partially formed assumptions
- requests for "an MVP"
- existing systems with unclear boundaries

The FE should be able to transform those inputs into:
- initiatives
- epics
- user stories or capability slices
- MVP definition
- backlog structure
- sequencing and dependency notes
- design-ready and build-ready artifacts

## Core principle

Requirements shaping is not just writing down what the user said.

It is the process of:
- clarifying what matters
- grouping related work coherently
- separating foundational work from feature work
- exposing trust and permission implications
- identifying what belongs in MVP vs later
- producing a backlog shape that can drive architecture and implementation

## Inputs to requirements shaping

The FE may begin with inputs such as:
- project intake notes
- onboarding answers
- user goals
- actor descriptions
- rough workflows
- desired features
- constraints
- non-negotiables
- deployment expectations
- existing technical context
- existing user stories or tickets

The FE should normalize these before attempting to design the system.

## Step 1 — Normalize raw input

### Objective
Turn freeform input into a structured view of the problem.

### FE should extract
- what is being built
- who it is for
- why it matters
- what the first desired outcome is
- what constraints exist
- what is already decided
- what remains unknown

### Outputs
- normalized project summary
- initial actor list
- initial workflow list
- initial feature/capability list
- assumptions and unknowns

## Step 2 — Identify actors and workflows

### Objective
Understand who interacts with the system and what they are trying to do.

### FE should identify
- primary users
- secondary users
- operators/admins
- system/internal actors
- key workflows for each actor
- sensitive or restricted workflows

### Why this matters
A requirement is easier to shape when attached to:
- an actor
- a workflow
- an outcome
- a boundary context

### Outputs
- actor list
- workflow map
- role-sensitive path notes
- trust-sensitive path notes

## Step 3 — Cluster work into initiatives

### Objective
Group related areas of work at the highest useful level.

### Initiative definition
An initiative is a broad area of product or system work that represents a meaningful capability area or delivery theme.

### Examples
For a tutoring system:
- learner experience
- parent experience
- orchestration and agent control
- permissions and safety
- progress tracking
- deployment and operations

### FE rule
Initiatives should be broad enough to organize work, but not so broad that they stop being useful.

### Outputs
- initiative map
- short rationale per initiative

## Step 4 — Break initiatives into epics

### Objective
Turn each initiative into bounded areas of work that can eventually be implemented in slices.

### Epic definition
An epic is a major capability area within an initiative that is still too large to be a single implementation slice, but small enough to be discussed as a coherent body of work.

### FE rule
Epics should usually map to:
- a meaningful user-facing capability area
- a major system boundary area
- or a major foundational/cross-cutting work area

### Examples
Initiative: Parent Experience
Possible epics:
- parent dashboard
- parent-agent interaction
- parent messaging channel integration
- parent controls/preferences

### Outputs
- epic map
- initiative-to-epic relationships

## Step 5 — Derive stories or capability slices

### Objective
Turn epics into concrete work items that can guide design and implementation.

### Story / slice definition
The FE may use:
- user stories where user behavior is the clearest framing
- capability slices where the implementation cut is more useful than a classic story sentence

### FE should identify
- actor
- goal or system capability
- acceptance intent
- trust/boundary implications
- dependencies

### Rule
Not every story needs to be phrased in rigid Agile syntax, but every meaningful item should make clear:
- who or what it serves
- what outcome it enables
- why it matters

### Outputs
- story list or capability slice list
- story grouping under epics
- acceptance criteria notes where useful

## Step 6 — Separate foundational work from feature work

### Objective
Avoid treating foundational system work as if it were optional feature garnish.

### Foundational work examples
- auth baseline
- role and permission model
- data model baseline
- policy enforcement
- repo and deployment structure
- auditability baseline

### FE rule
Some foundational work must be included in MVP because it is required for:
- safety
- correctness
- coherence
- future feature development
- credible deployment

The FE should explicitly call out:
- foundational work required in MVP
- foundational work safe to defer

### Outputs
- foundational work list
- feature work list
- rationale for what is foundational

## Step 7 — Define the MVP cut

### Objective
Determine the smallest sensible first version.

### FE should ask
- what must exist for the product to be real and useful?
- what trust or deployment foundations must exist early?
- what can be deferred without undermining the product?
- what would create waste or overbuild if included now?

### FE should produce
- MVP objective
- in-scope stories/capabilities
- deferred stories/capabilities
- explicit out-of-scope list
- rationale for the cut

### Rule
The MVP should be small, but not fake. It must include the foundational work needed to support the core use case credibly.

## Step 8 — Shape the backlog

### Objective
Turn the MVP and deferred work into a practical backlog structure.

### FE should group backlog items into
- foundational build items
- MVP feature items
- deployment/ops items
- post-MVP feature items
- deferred/later items

### FE should also identify
- dependencies
- likely milestone boundaries
- risk-sensitive items
- items needing deeper design before build

### Outputs
- prioritized backlog
- dependency notes
- candidate milestone groupings

## Step 9 — Flag boundary-sensitive and architecture-sensitive work

### Objective
Ensure that not all backlog items are treated as simple implementation tasks.

### FE should flag items that affect
- trust boundaries
- permissions
- data visibility
- agent context eligibility
- deployment model
- infrastructure shape
- operational risk

### Rule
If a story changes a major boundary, it may need:
- design revision
- policy review
- deployment review
- stronger validation planning

### Outputs
- flagged boundary-sensitive items
- required deeper review notes

## Step 10 — Produce design-ready outputs

### Objective
Ensure the shaped work is suitable for architecture and implementation planning.

### FE should leave the project with
- clear initiative and epic structure
- story/capability shape
- MVP scope
- prioritized backlog
- dependency map
- foundational work list
- explicit open questions
- explicit risks

This is the handoff point into design and implementation planning.

## Recommended outputs from the shaping stage

Depending on project size, the FE should produce some combination of:
- problem intake
- actor/boundary model
- initiative map
- epic map
- user stories or capability slices
- MVP definition
- story prioritization
- risk register
- implementation planning starter

## Requirements shaping heuristics

The FE should:
- prefer the smallest structure that makes the work buildable
- avoid fake precision when input is still uncertain
- make assumptions explicit
- separate product value from architecture necessity
- separate core workflows from nice-to-have workflows
- identify foundational work early
- resist backlog inflation from speculative future ideas
- keep trust and deployment implications visible throughout

## Common failure modes

The FE should avoid:
- turning raw requests directly into architecture without shaping
- collapsing all work into one giant backlog list with no structure
- treating foundational work as invisible or optional
- including everything in MVP because it sounds useful
- failing to separate user-facing value from enabling work
- ignoring deployment and trust-boundary implications during shaping
- creating stories so vague they cannot guide design or implementation

## Relationship to other FE models

This requirements shaping model sits between:
- project intake / onboarding
and
- MVP definition, architecture, and implementation planning

It is one of the most important stages in the FE operating model because it turns raw project input into structured, buildable work.

## Summary

A strong Founding Engineer should be able to take messy requirements and convert them into:
- initiatives
- epics
- stories or capability slices
- a justified MVP
- a practical backlog
- clear next artifacts

Without this shaping step, architecture and implementation planning are much more likely to drift, overbuild, or ignore real product priorities.
