# Project Onboarding Template

## Purpose

Use this template to capture the minimum structured input the Founding Engineer (FE) needs to start shaping a real project.

The goal is not to force a full specification up front. The goal is to gather enough signal to begin:
- clarification
- requirements shaping
- MVP definition
- architecture and implementation planning
- deployment and operational thinking

## Project identity

### Project name

### One-line summary
What are we building, in one sentence?

### Current stage
Examples:
- raw idea
- early shaping
- MVP definition
- architecture
- implementation planning
- active build
- deployment prep
- live system / maintenance

## Problem and goal

### What problem are we trying to solve?

### Why does it matter?

### What do we want first?
Examples:
- clearer problem framing
- MVP definition
- architecture
- implementation plan
- deployment plan
- feature shaping
- maintenance review

## Users, stakeholders, and actors

### Primary users

### Secondary users

### Operators / admins

### Other stakeholders

### Important internal/system actors
Examples:
- background jobs
- AI agents
- external providers
- admins
- internal reviewers

## Workflows and product expectations

### Main user workflows
What are the most important things the system must let people do?

### Sensitive or restricted workflows
What actions, information, or paths need stronger control?

### What should be explicitly out of bounds?
Examples:
- no direct learner access to admin surfaces
- no raw OpenClaw UI
- no external messaging without approval

## Constraints and non-negotiables

### Technical constraints
Examples:
- required stack
- required integrations
- existing systems that must be used

### Deployment constraints
Examples:
- must run on a VPS
- must be containerized
- must support staging/production separation

### Safety, privacy, or trust constraints
Examples:
- child-safe interface only
- backend-enforced permissions
- no cross-role data leakage

### Non-negotiables
What absolutely must be true?

## Success criteria

### What would make the first version successful?

### What are the most important risks or failure modes?

## Existing context

### What decisions have already been made?

### What assumptions are we currently making?

### What is still unclear or undecided?

### Are there existing docs, repos, or systems involved?

## Delivery and operations context

### Expected deployment environment
Examples:
- local app
- VPS
- cloud VM
- container platform

### Operational expectations
Examples:
- backups required
- rollback required
- operator visibility needed
- audit logging needed

### External integrations
Examples:
- messaging providers
- payment systems
- identity providers
- OpenClaw

## Help needed right now

### What should the Founding Engineer do next?
Examples:
- ask clarifying questions
- shape requirements into epics/stories
- define MVP
- design architecture
- propose repo structure
- define build plan
- define deployment model

## Minimum viable onboarding complete checklist

Before moving on, the FE should usually be able to answer:
- what is being built?
- who is it for?
- what is wanted first?
- what constraints matter?
- what non-negotiables exist?
- what trust or safety concerns matter?
- what environment is this expected to run in?
- what is already known vs unknown?

If not, the FE should ask targeted follow-up questions before proceeding.
