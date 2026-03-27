# Package Guide

## Purpose

This repository defines a documentation-backed Founding Engineer agent package for OpenClaw.

It is intended to capture not just a persona, but a reusable operating model for an agent that can turn ambiguous product and technical ideas into secure, maintainable, deployable systems.

## What this repo contains

### `docs/`
Source-of-truth concept and specification documents.

These define:
- who the agent is
- how it should think
- how it should work
- how it should handle security, validation, and delegation
- what the packaged agent must be

### `agent/`
Runtime-facing package artifacts.

These define:
- `identity.md` — who the agent is meant to feel like
- `behavior.md` — the operational habits it should exhibit
- `defaults.md` — the standard choices it should prefer
- `prompt.md` — the distilled runtime directive for agent behavior

### `examples/`
Representative example outputs that show the style and shape of work this agent should produce.

### `templates/`
Reusable scaffolds for common Founding Engineer deliverables.

## Source of truth

The intended source-of-truth order is:
1. `docs/`
2. `docs/agent-spec.md`
3. `agent/`
4. `examples/` and `templates/`

That means runtime artifacts should be derived from the documentation and specification layers, not invented independently.

## How to use this package

Use this repository when you want to:
- define or refine a Founding Engineer-style agent
- package a strong engineering persona for OpenClaw
- create reusable planning, design, and review scaffolds
- evaluate whether an agent is behaving like a dependable end-to-end technical partner

## Design intent

This package is designed to emphasize:
- practical system thinking
- phased delivery
- strong security and trust boundaries
- deployment and operational realism
- validation and delivery confidence
- responsible use of delegation and automation

## Not yet included

This repository does not yet include:
- a finalized OpenClaw-native packaging manifest
- executable skill implementations
- automated tests for the package itself
- a library of domain-specific examples

Those can be added later once the behavioral core is stable.

## Maintenance rule

If the runtime artifacts and the docs diverge, update the docs and spec first, then reconcile the runtime package.

The goal is to keep the package grounded in explicit design decisions rather than letting the prompt drift independently.
