# Usage Guide

## What this repo is now

This repository is a documentation-backed Founding Engineer agent package with a much clearer end-to-end operating model.

It provides:
- source-of-truth concept and specification docs
- runtime-facing agent artifacts
- lifecycle, shaping, execution, and operations models
- reusable templates for real project work
- a realistic reference project pack in `projects/python-tutor/`

## Who this is for

This repo is useful for people who want to:
- define or refine a Founding Engineer-style agent
- use an FE operating model inside OpenClaw
- evaluate whether an agent behaves like a dependable end-to-end product and technical partner
- shape real projects from messy requirements into MVP, backlog, design, and execution

## How to use the repo

### 1. Understand the package intent
Start with:
- `README.md`
- `PACKAGE.md`
- `docs/agent-spec.md`

These explain what the package is for and what the Founding Engineer is expected to do.

### 2. Understand the lifecycle backbone
Then read:
- `docs/lifecycle-model.md`
- `docs/project-workflow.md`
- `docs/project-state-model.md`
- `docs/requirements-shaping-model.md`

These define how the FE moves from intake through shaping, design, build, deploy, and maintenance.

### 3. Understand the runtime behavior
Then read:
- `agent/identity.md`
- `agent/behavior.md`
- `agent/defaults.md`
- `agent/prompt.md`

These are the most relevant files when adapting the package into a real runtime agent configuration.

### 4. Use the templates in real work
Use templates such as:
- `templates/project-onboarding-template.md`
- `templates/project-state-template.md`
- `templates/decision-log-template.md`
- `templates/milestone-plan-template.md`
- `templates/release-readiness-template.md`
- `templates/maintenance-review-template.md`

These help operationalize the FE lifecycle model.

### 5. Validate the package against a real project
Use:
- `projects/python-tutor/`

This project pack shows how the FE can be exercised across:
- intake
- boundary modeling
- MVP definition
- architecture
- implementation planning
- deployment modeling
- execution handoff

## Practical usage pattern

A practical workflow for using the package is:
1. onboard a project using the onboarding template
2. shape requirements into initiatives, epics, stories, MVP, and backlog
3. define architecture and trust boundaries
4. define implementation milestones and slices
5. guide or perform build execution
6. assess deployment and release readiness
7. continue with maintenance and feature workflow

## How to evaluate whether it is working

A good Founding Engineer output should:
- clarify ambiguity instead of hiding it
- ask for the right minimum input
- turn messy requirements into structured work
- preserve continuity across lifecycle stages
- make trust and permission boundaries explicit
- design with deployment, rollback, and maintenance in mind
- avoid unnecessary complexity
- feel like dependable technical judgment, not generic code generation

## Current limitations

This repo still does not yet include:
- a finalized OpenClaw packaging manifest
- automated evaluation harnesses
- executable FE skills or automation
- a broad set of project packs beyond the Python Tutor reference

## Recommended next use

The package is now strong enough to:
- continue validation against real project work
- guide a real implementation repo bootstrap
- support a project like Python Tutor moving from planning into build execution
