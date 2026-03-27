# Architecture

## Purpose

This document describes how the Founding Engineer concept should become a real OpenClaw artifact.

The goal is not just to describe ideas in layers, but to define how this repository evolves from documentation into a reusable agent package.

## Packaging model

This project should eventually ship as a documentation-backed OpenClaw agent package.

That package should include:
- a clear persona and behavioral definition
- a consolidated agent specification
- runtime prompt and default behavior artifacts
- security and approval boundary guidance
- optional supporting skills, examples, and templates

The documentation is the source of truth for the agent’s intended behavior. Runtime artifacts should be derived from it, not invented separately.

## Source-of-truth layers

The project should evolve through four layers.

### 1. Concept layer
Defines the intent of the agent.

Primary artifacts:
- `docs/vision.md`
- `docs/persona.md`
- `docs/principles.md`

This layer answers:
- who the agent is
- what it is trying to optimize for
- how it should think and make decisions

### 2. Operating layer
Defines how the agent works in practice.

Primary artifacts:
- `docs/operating-model.md`
- `docs/security.md`

This layer answers:
- how the agent approaches tasks
- when it asks for approval
- how it handles validation, risk, delegation, and secrets

### 3. Specification layer
Defines the implementation contract for the packaged agent.

Primary artifacts:
- `docs/agent-spec.md` (planned)

This layer should answer:
- what the actual packaged agent must do
- what outputs it is expected to produce
- what guardrails it must follow
- what runtime defaults it should carry

### 4. Runtime layer
Defines the concrete packaged artifacts used by OpenClaw.

Planned artifacts:
- `agent/prompt.md`
- `agent/identity.md`
- `agent/behavior.md`
- `agent/defaults.md`

This layer should contain the actual agent-facing runtime content, derived from the documentation and specification layers.

## Proposed repository layout

A likely future structure for this project is:

```text
founding-engineer-agent/
├── README.md
├── docs/
│   ├── persona.md
│   ├── principles.md
│   ├── operating-model.md
│   ├── vision.md
│   ├── architecture.md
│   ├── security.md
│   ├── roadmap.md
│   └── agent-spec.md
├── agent/
│   ├── prompt.md
│   ├── identity.md
│   ├── behavior.md
│   └── defaults.md
├── skills/        # optional, later
├── examples/      # optional, later
└── templates/     # optional, later
```

This keeps concept documentation separate from runtime artifacts.

## Document-to-artifact mapping

The current docs should eventually map into packaged artifacts roughly like this:

- `docs/persona.md` → agent identity, tone, temperament, and boundaries
- `docs/principles.md` → decision rules and tradeoff behavior
- `docs/operating-model.md` → workflow behavior, delegation model, and execution style
- `docs/security.md` → approval boundaries, secret handling model, and safety expectations
- `docs/vision.md` → project intent and success criteria
- `docs/roadmap.md` → staged implementation plan for the agent itself
- `docs/agent-spec.md` → consolidated implementation contract
- `agent/prompt.md` → final runtime prompt text
- `agent/defaults.md` → stack defaults, output expectations, and runtime assumptions

## Implementation progression

The recommended progression for this repository is:

### Phase 1 — documentation foundation
Create and refine the concept and operating docs until the agent behaves coherently on paper.

### Phase 2 — implementation specification
Write `docs/agent-spec.md` to consolidate the intended behavior into a practical implementation contract.

### Phase 3 — runtime packaging
Create the `agent/` artifacts that translate the specification into a usable OpenClaw agent package.

### Phase 4 — optional extensions
Add optional supporting artifacts such as:
- reusable skills
- examples of expected outputs
- templates for common deliverables

### Phase 5 — validation on real work
Test the packaged agent on real system-design, planning, implementation, deployment, and review tasks, then refine based on observed failure modes.

## Design rule

This repository should remain documentation-led until the behavior is clear enough to package cleanly.

The goal is not to rush into prompt tuning. The goal is to build a reusable agent whose runtime behavior is grounded in explicit design, operating, and security decisions.
