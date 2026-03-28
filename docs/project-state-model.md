# Project State Model

## Purpose

This document defines the structured project state the Founding Engineer (FE) should preserve across the lifecycle of a product.

The goal is to prevent drift, repeated rediscovery, and loss of important decisions as work moves from intake through design, build, deployment, and maintenance.

## Core principle

A project is not just a sequence of chats or documents. It is a persistent stateful body of work.

The FE should treat project state as durable working memory containing the most important facts, decisions, assumptions, and artifacts required to continue the project coherently.

## State categories

## 1. Project identity

Capture:
- project name
- short project summary
- current project stage
- date or status of latest review

Purpose:
- identify what the project is
- identify where it currently sits in the lifecycle

## 2. Users, stakeholders, and actors

Capture:
- primary users
- secondary users
- operators/admins
- external stakeholders if relevant
- internal system actors or agent roles if relevant

Purpose:
- preserve who the system is for and who interacts with it

## 3. Goals and success criteria

Capture:
- business or product goal
- immediate objective
- MVP success criteria
- operational or quality constraints tied to success

Purpose:
- preserve why the project exists and what “good” means

## 4. Constraints and non-negotiables

Capture:
- technical constraints
- deployment constraints
- compliance or safety constraints
- explicit non-negotiables
- known capacity or time constraints if provided

Purpose:
- prevent later recommendations from violating known requirements

## 5. Assumptions and open questions

Capture:
- active assumptions
- unverified assumptions
- unresolved questions
- assumptions the FE used to move work forward

Purpose:
- make uncertainty explicit and reviewable

## 6. Trust boundaries and risk notes

Capture:
- role boundaries
- permission boundaries
- data visibility constraints
- integration trust assumptions
- known security, privacy, or operational risks

Purpose:
- preserve the boundary model so implementation and feature work do not drift into unsafe shortcuts

## 7. Requirements and workflow understanding

Capture:
- major user workflows
- major system capabilities
- requirements grouped by initiative or area
- especially important edge cases or forbidden paths

Purpose:
- preserve the product and workflow understanding that shaped the design

## 8. MVP definition and roadmap cut

Capture:
- MVP objective
- what is in MVP
- what is deferred to next phase
- what is explicitly out of scope for now
- rationale for the cut

Purpose:
- prevent scope drift and loss of intentional sequencing

## 9. Initiative, epic, story, and backlog state

Capture:
- initiative list
- epic list
- user stories or capability slices
- prioritized backlog
- dependencies and sequencing notes
- foundational work items

Purpose:
- preserve the buildable work structure created during shaping and planning

## 10. Architecture and design decisions

Capture:
- architecture decisions
- data model decisions
- API boundary decisions
- repo structure decisions
- stack decisions
- rejected alternatives where important

Purpose:
- preserve the reasoning behind implementation shape and future evolution

## 11. Implementation state

Capture:
- completed milestones or slices
- in-progress work
- deviations from the original plan
- known implementation blockers
- validation evidence for implemented slices

Purpose:
- preserve the real build status, not just the intended plan

## 12. Deployment and operations state

Capture:
- deployment target
- environment assumptions
- secret/config model
- backup/rollback posture
- release blockers
- monitoring or operational notes

Purpose:
- preserve deployability and operational continuity

## 13. Release and production state

Capture:
- release readiness status
- deployed versions or milestones
- post-deploy issues
- production learnings
- incident notes

Purpose:
- allow the FE to support the system after build rather than acting as though the project resets after launch

## 14. Maintenance and iteration state

Capture:
- maintenance backlog
- technical debt notes
- recurring issues
- feature requests
- architecture changes under consideration

Purpose:
- support sustained product evolution

## Canonical state expectations

The FE should be explicit about where truth lives.

### Examples
- project summary and constraints may begin in intake artifacts
- MVP scope may live primarily in an MVP definition artifact
- architecture decisions may live in architecture and boundary documents
- backlog state may live in implementation planning and story artifacts
- operational state may live in deployment and maintenance notes

The FE should avoid duplicating state carelessly across too many documents. If duplication exists, it should be clear which artifact is canonical.

## Update rules

The FE should update project state when:
- a key assumption is confirmed or invalidated
- a major decision is made
- MVP scope changes
- architecture direction changes
- implementation milestones are completed or blocked
- deployment assumptions change
- production learnings affect backlog or design

The FE should not rewrite history casually. It should preserve the fact that:
- earlier assumptions existed
- decisions changed when needed
- scope evolved for a reason

## State continuity rules

The FE should preserve enough state to answer:
- what are we building?
- who is it for?
- what phase are we in?
- what is the MVP?
- what has already been decided?
- what is still open?
- what is built already?
- what is next?
- what risks matter right now?
- what deployment and operational constraints apply?

If the FE cannot answer those questions reliably, project state is too weak.

## Relationship to lifecycle

Every lifecycle stage should:
- consume project state
- update project state
- leave the project in a clearer, more durable condition than before

The project state model is what allows the FE to move from:
- onboarding
- to shaping
- to architecture
- to build
- to deploy
- to operate

without losing coherence.

## Summary

The Founding Engineer should treat project state as durable working memory for the entire product lifecycle.

Without this state model, the FE risks:
- repeating work
- forgetting decisions
- drifting across stages
- losing why the system was designed the way it was

With it, the FE can behave much more like a real end-to-end product and delivery partner.
