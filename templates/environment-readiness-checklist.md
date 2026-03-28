# Environment Readiness Checklist

## Purpose

Use this template to assess whether the current environment is capable of supporting the planned build, test, runtime, and deployment workflow.

## Project
- Name:
- Current phase:
- Date:

## Stack assumptions
- Primary language/runtime:
- Package manager:
- Database/runtime dependencies:
- Container/runtime assumptions:
- Deployment assumptions:

## Build readiness
- Required runtimes installed: yes / no
- Required package manager available: yes / no
- Install/bootstrap command works: yes / no
- Typecheck/build command works: yes / no
- Tooling cache/home permissions are OK: yes / no

### Notes
- 
- 

## Test and validation readiness
- Smoke-test tooling available: yes / no
- Test runner available if expected: yes / no
- Local validation dependencies available: yes / no
- Browser/API validation assumptions workable: yes / no

### Notes
- 
- 

## Runtime / local-dev readiness
- Docker available if required: yes / no
- Compose available if required: yes / no
- Local services can bind required ports: yes / no
- Env/config model is usable: yes / no
- Service-to-service assumptions are workable: yes / no

### Notes
- 
- 

## Deployment-readiness assumptions
- Target deployment model is still valid: yes / no
- Tooling for deployment path is available or planned clearly: yes / no
- Secrets/config path is defined enough for current stage: yes / no
- There is a realistic path to deployment validation later: yes / no

### Notes
- 
- 

## Readiness outcome
Examples:
- ready
- ready with caveats
- blocked for runtime validation
- blocked for implementation

## Key blockers
- 
- 
- 

## Recommended next actions
- 
- 
- 
