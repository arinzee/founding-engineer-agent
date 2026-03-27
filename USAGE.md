# Usage Guide

## What this repo is right now

This repository is currently a documentation-backed Founding Engineer agent package.

It provides:
- source-of-truth concept and specification docs
- runtime-facing agent artifacts
- representative examples
- reusable templates

It does not yet provide a fully automated OpenClaw-native installation flow or a finalized packaging manifest.

## Who this is for

This repo is useful for people who want to:
- define a strong Founding Engineer-style agent
- reuse the persona and operating model in OpenClaw or related systems
- evaluate whether an agent behaves like a dependable end-to-end technical partner
- use the examples and templates to support real planning, design, and review work

## How to use the repo

### 1. Understand the design intent
Start with:
- `README.md`
- `PACKAGE.md`
- `docs/vision.md`

These explain what the project is for and how the package is intended to evolve.

### 2. Read the behavioral source of truth
Then read:
- `docs/persona.md`
- `docs/principles.md`
- `docs/operating-model.md`
- `docs/security.md`
- `docs/agent-spec.md`

These define who the Founding Engineer is, how it should think, how it should operate, and what the packaged agent must do.

### 3. Use the runtime-facing artifacts
Use:
- `agent/identity.md`
- `agent/behavior.md`
- `agent/defaults.md`
- `agent/prompt.md`

These are the most relevant files when you want to adapt the package into a real runtime agent configuration.

### 4. Study examples
Use:
- `examples/architecture-spec-example.md`
- `examples/phased-plan-example.md`
- `examples/security-review-example.md`

These show the shape of outputs the Founding Engineer should produce.

### 5. Reuse templates
Use:
- `templates/system-design-template.md`
- `templates/implementation-plan-template.md`
- `templates/risk-register-template.md`

These are reusable scaffolds for real Founding Engineer work.

## Suggested workflow for using this package

A practical workflow is:
1. use the docs to understand and refine the persona
2. use the `agent/` files to define runtime behavior
3. use the examples to evaluate output quality
4. use the templates in real project work
5. refine the package based on failure modes observed in real usage

## How to evaluate whether it is working

A good Founding Engineer output should:
- clarify ambiguity instead of hiding it
- recommend practical, phased plans
- make trust and permission boundaries explicit
- design with deployment and rollback in mind
- include validation and delivery confidence thinking
- avoid unnecessary complexity
- feel like dependable technical judgment, not generic code generation

## Current limitations

Right now this repo does not yet include:
- a finalized OpenClaw packaging manifest
- executable skills or code-backed automation
- automated evaluation harnesses
- a broad library of examples

## Recommended next additions

The next useful additions are likely:
- `examples/response-style-example.md`
- `templates/deployment-plan-template.md`
- `docs/evaluation.md`

These would make the package easier to evaluate and use in real delivery work.
