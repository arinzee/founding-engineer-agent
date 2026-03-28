# Environment Readiness Model

## Purpose

This document defines how the Founding Engineer (FE) should assess whether the current environment is capable of supporting the planned work.

The goal is to prevent a common failure mode:
- the project is well shaped
- the architecture is sensible
- implementation starts
- but the actual environment cannot build, test, run, or validate the chosen stack reliably

A real-world founding engineer should not only shape the product and stack. It should also verify that the working environment is capable of supporting build execution, validation, and deployment activities.

## Core principle

A good plan is not enough if the current environment cannot execute it.

The FE should explicitly assess environment readiness before or during the transition from planning into active implementation and runtime validation.

## Environment readiness categories

## 1. Build environment readiness

### Objective
Verify that the environment can actually build and iterate on the chosen stack.

### FE should check
- required runtimes are installed
- required package managers are available
- compiler/toolchain commands are available
- repo bootstrap commands can run
- writable cache/home assumptions are satisfied
- local file permissions do not block common tooling

### Examples
- Node available
- pnpm or npm available as expected
- TypeScript build/typecheck commands runnable
- Python tooling available if the project needs it
- workspace install can complete

## 2. Test and validation environment readiness

### Objective
Verify that the environment can support the intended validation loop.

### FE should check
- typecheck/test commands can run
- smoke or integration scripts can run
- local dependencies needed for tests can be started
- browser or API test assumptions are realistic for the environment
- permission/network constraints do not block validation tooling

### Examples
- typecheck can run without cache/permission failure
- curl/shell-based smoke scripts can run
- database-backed tests can access a DB when required
- UI test tools are available if expected

## 3. Runtime and local/dev readiness

### Objective
Verify that the environment can run the local/dev version of the stack.

### FE should check
- container runtime exists if the stack depends on Docker/Compose
- required ports can be bound
- local services can start
- environment variable model is usable
- service-to-service assumptions are realistic

### Examples
- Docker available
- docker compose available
- backend can bind expected port
- database can run locally or in containers
- reverse proxy can be exercised if part of the active loop

## 4. Deployment-readiness assumptions

### Objective
Verify that the environment and planned target support the deployment path being proposed.

### FE should check
- deployment tool assumptions are valid
- VPS/container model is realistic for the target
- reverse proxy/runtime assumptions are realistic
- secrets/config flow is workable
- the team has a path to validate or execute deployment later

### Important distinction
An environment may be:
- ready for coding
- but not ready for local runtime validation
- or ready for local validation
- but not ready for real deployment work

The FE should distinguish these cases explicitly.

## Readiness decision levels

The FE should summarize environment readiness using one of these outcomes.

### Ready
The current environment supports build, test, and active runtime work for the current stage.

### Ready with caveats
Most work can proceed, but some validation or deployment activities are constrained.

### Blocked for runtime validation
Design and some code work may proceed, but testing or local runtime validation is blocked by missing tooling or environment constraints.

### Blocked for implementation
The environment is missing critical prerequisites for the intended build workflow.

## FE behavior rules

The FE should:
- check environment assumptions early enough that blockers are found before confidence is overstated
- distinguish environment limitations from design flaws
- record readiness findings as durable project state
- avoid pretending that a stack is validated if the environment could not actually run the validation path
- propose the smallest remediation needed to restore confidence

## Typical environment blockers

Examples of blockers the FE should surface explicitly:
- package manager not installed
- compiler/toolchain unavailable
- unwritable cache or home directory for required tooling
- Docker/Compose unavailable where containerized dev is expected
- required ports or network paths blocked
- database/runtime dependency unavailable
- secrets/config path undefined for planned validation

## Relationship to build execution

Environment readiness should be treated as an explicit precondition or early check inside build execution.

The FE should not move from planning into confident implementation and validation claims without checking whether the environment can actually support the chosen workflow.

## Summary

The environment-readiness model exists to keep the Founding Engineer honest.

It ensures the FE checks not only:
- what should be built
but also:
- whether the current environment can actually build, test, run, and validate it
