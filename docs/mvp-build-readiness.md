# MVP Build Readiness

## Purpose

This document defines when the Founding Engineer has enough clarity to recommend starting MVP implementation.

The goal is to prevent two common failure modes:
- starting to build too early with unsafe or vague foundations
- delaying unnecessarily because the project is not fully specified in every detail

## Core principle

The Founding Engineer should trigger MVP build when there is enough clarity to build safely, phase intelligently, and deploy credibly.

The standard is not perfect certainty.
The standard is sufficient readiness.

## What must be true before MVP build starts

The Founding Engineer should confirm that the following are sufficiently defined.

## 1. Problem and outcome are clear
There should be a clear understanding of:
- what is being built
- who it is for
- what the MVP is meant to prove or deliver
- what success looks like for the first version

The user does not need a perfect product spec, but the direction must be concrete enough to guide design and delivery.

## 2. Actors and trust boundaries are understood
The Founding Engineer should understand enough about:
- primary users and operators
- role differences
- visibility boundaries
- action boundaries
- safety-sensitive or permission-sensitive paths

If the system has meaningful trust boundaries, those must be explicit before implementation starts.

## 3. MVP scope is defined
There should be a clear distinction between:
- what is in the MVP
- what is explicitly deferred
- what is out of scope for now

If everything is still “maybe in,” the project is not ready to build.

## 4. Architecture direction is clear enough
The Founding Engineer should have recommended at least a first architecture direction that is sufficient to support the MVP.

This does not mean every internal detail is fully designed.
It means the overall shape is clear enough that implementation will not begin from chaos.

## 5. Foundational elements required for future feature development are included
The MVP should include the foundational elements that are necessary to:
- support the core use case
- preserve safety and correctness
- enable clean future feature development
- deploy and operate the system credibly

Examples may include:
- core architecture baseline
- auth or permissions baseline
- data model baseline
- deployment baseline
- auditability or observability baseline
- repo/code structure that can grow safely

These foundations should be pragmatic and minimal, not speculative or overbuilt.

## 6. Main unresolved risks are known
The Founding Engineer does not need every risk solved before implementation starts.

But it should know:
- the main risks
- which ones are accepted for MVP
- which ones must be mitigated before or during implementation

## 7. Implementation can be phased
There should be a build sequence that allows the MVP to be delivered in controlled slices.

If the project still depends on a giant one-shot build plan, readiness is weak.

## 8. Deployment direction is clear enough
The Founding Engineer should know enough about:
- where the MVP will run
- the broad deployment shape
- environment assumptions
- secret/config handling expectations
- basic backup and rollback posture

The deployment model does not need to be maximally mature, but it should be credible.

## 9. Maintenance is not being ignored
Before MVP build starts, the Founding Engineer should have at least minimal thought about:
- how the system will be operated
- how failures will be handled
- how future changes can be added

The agent should not treat maintenance as someone else’s future problem.

## What does not need to be fully complete before build starts

The Founding Engineer should not require all of the following before MVP build:
- every future feature story
- full long-term architecture
- advanced admin tooling
- speculative scale infrastructure
- perfect analytics and observability
- exhaustive optimization decisions

That would make the process too heavy and slow.

## Readiness decision rule

The Founding Engineer should recommend starting MVP implementation when:
- the MVP is clear enough to build
- the foundations are strong enough to build safely
- the work can be phased
- the major trust, deployment, and maintenance concerns are understood
- the remaining uncertainty is acceptable and explicitly acknowledged

## Expected FE output at the readiness point

When the project reaches readiness, the Founding Engineer should be able to say, in effect:
- what the MVP is
- what foundations are included
- what is intentionally deferred
- what the first implementation slices should be
- what key risks remain
- why it is now reasonable to start building

## Summary

MVP build readiness does not mean the project is fully finished on paper.
It means the project is structured well enough to move into implementation without turning the MVP into chaos, rework, or unsafe guesswork.
