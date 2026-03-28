# Founding Engineer Agent Template

A documentation-first OpenClaw agent package for a startup-caliber Founding Engineer: an agent that can take messy requirements and carry work through onboarding, requirements shaping, MVP definition, architecture, implementation planning, build execution, deployment, and ongoing iteration.

## Purpose

This repo is the foundation for a reusable OpenClaw-based Founding Engineer agent.

The goal is to create an agent that can:
- onboard real projects without requiring a perfect spec
- turn vague requirements into structured work such as initiatives, epics, stories, MVP scope, and backlog
- design systems, trust boundaries, and deployment models
- guide or perform implementation across backend, frontend, orchestration, infra, and operations
- deploy safely and maintainably
- preserve project continuity across the full lifecycle
- use subagents deliberately as part of a compressed real-world team model

## What the repo now contains

### Core documentation
- persona, principles, operating model, security, and agent spec
- lifecycle, project-state, requirements-shaping, subagent, build-execution, and operations models

### Runtime-facing agent artifacts
- `agent/identity.md`
- `agent/behavior.md`
- `agent/defaults.md`
- `agent/prompt.md`

### Templates
Reusable scaffolds for:
- project onboarding
- project state
- decision logs
- milestone planning
- release readiness
- maintenance review
- implementation and system design work

### Reference project work
- `projects/python-tutor/` as a concrete end-to-end FE test case spanning intake through execution handoff

## Intended use

This package is meant to become:
- a reusable Founding Engineer persona and operating system for OpenClaw
- a reference model for turning real project input into design, build, deploy, and maintain workflows
- a practical testbed for validating FE behavior on real project packs such as Python Tutor

## Current status

The package now has a much stronger lifecycle and operating backbone.

It is strongest in:
- onboarding and shaping
- MVP and architecture definition
- trust-boundary and deployment thinking
- implementation planning and execution modeling

Remaining hardening work is mostly operational polish and repeated-use scaffolding, not core concept formation.

## Best starting points

If you are new to the repo, start with:
- `README.md`
- `PACKAGE.md`
- `USAGE.md`
- `docs/agent-spec.md`
- `docs/lifecycle-model.md`
- `docs/project-workflow.md`
