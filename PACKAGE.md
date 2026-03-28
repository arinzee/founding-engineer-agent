# Package Guide

## Purpose

This repository defines a documentation-backed Founding Engineer agent package for OpenClaw.

It is intended to capture not just a persona, but a reusable operating system for an agent that can turn ambiguous product and technical ideas into structured project work, secure designs, implementation plans, deployable systems, and ongoing operational support.

## What this repo contains

### `docs/`
Source-of-truth concept and specification documents.

These define:
- who the agent is
- how it should think
- how it should work across the lifecycle
- how it should handle onboarding, shaping, design, build, deployment, and maintenance
- how it should handle security, validation, and delegation
- what the packaged agent must be

### `agent/`
Runtime-facing package artifacts.

These define:
- `identity.md` — who the agent is meant to feel like
- `behavior.md` — the operational habits it should exhibit
- `defaults.md` — the standard choices it should prefer
- `prompt.md` — the distilled runtime directive for agent behavior

### `templates/`
Reusable scaffolds for common Founding Engineer deliverables, including:
- project onboarding
- project state tracking
- decision logging
- milestone planning
- release readiness
- maintenance review

### `projects/`
Reference project packs used to validate the package in realistic end-to-end work.

Current primary example:
- `projects/python-tutor/`

## Source of truth

The intended source-of-truth order is:
1. `docs/`
2. `docs/agent-spec.md`
3. `agent/`
4. `projects/`, `examples/`, and `templates/`

That means runtime artifacts should be derived from the documentation and specification layers, not invented independently.

## How to use this package

Use this repository when you want to:
- define or refine a Founding Engineer-style agent
- package a strong engineering persona for OpenClaw
- onboard and shape real projects from messy requirements
- evaluate whether an agent behaves like a dependable end-to-end technical partner
- validate the FE model against realistic product work

## Design intent

This package is designed to emphasize:
- practical system thinking
- structured onboarding and requirements shaping
- phased delivery
- strong security and trust boundaries
- deployment and operational realism
- validation and delivery confidence
- responsible use of delegation and subagents
- continuity of project state across the lifecycle

## Current limitations

This repository still does not yet include:
- a finalized OpenClaw-native packaging manifest
- automated evaluation harnesses
- executable skills or code-backed automation for the FE package itself
- a broad library of domain-diverse project packs

## Maintenance rule

If the runtime artifacts and the docs diverge, update the docs and spec first, then reconcile the runtime package.

The goal is to keep the package grounded in explicit design decisions rather than letting the prompt drift independently.
