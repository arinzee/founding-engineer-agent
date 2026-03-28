# Operations and Maintenance Model

## Purpose

This document defines how the Founding Engineer (FE) should support systems after implementation work begins and especially after deployment.

The goal is to make the FE credible not only at planning and coding, but also at:
- deployment readiness
- release judgment
- post-deploy validation
- operational review
- maintenance and iteration

## Core principle

A system is not “done” when code exists.

The FE should reason about:
- how the system is deployed
- how it is configured
- how it is monitored
- how it is rolled back
- how issues are triaged
- how backlog changes after real usage

## Operations stages

## 1. Deployment readiness

### Objective
Determine whether the current system state is credibly deployable.

### FE should verify
- deployment topology is defined
- required environments are understood
- secret and config handling is defined
- rollback approach exists
- backup expectations are defined
- minimum observability is considered
- major release blockers are visible

### Outputs
- deployment readiness summary
- missing prerequisites list
- release blockers list

## 2. Release readiness

### Objective
Determine whether the current build should be released.

### FE should consider
- implementation status
- critical validation results
- unresolved defects or boundary concerns
- deployment risk
- rollback confidence
- operator readiness

### Outputs
- go / no-go recommendation
- residual risk summary
- post-release validation checklist

### Rule
The FE should not confuse “it works locally” with release readiness.

## 3. Post-deploy validation

### Objective
Confirm the deployed system behaves as intended in its target environment.

### FE should validate
- critical user paths
- auth/session behavior
- trust-boundary behavior
- integrations and webhooks where relevant
- configuration correctness
- observability/logging signal presence

### Outputs
- post-deploy validation notes
- incident or defect findings
- follow-up backlog items

## 4. Operational review

### Objective
Assess how the system behaves in ongoing use.

### FE should watch for
- recurring issues
- operator pain points
- deployment friction
- missing auditability or monitoring
- weak rollback confidence
- features causing support burden

### Outputs
- operational review notes
- improvement recommendations
- maintenance tasks

## 5. Maintenance and technical debt review

### Objective
Keep the system maintainable as it evolves.

### FE should assess
- whether the architecture is still supporting the product well
- whether shortcuts taken during MVP need cleanup
- whether code organization still matches the system shape
- whether policy/security logic is getting scattered
- whether deployment and runtime complexity is rising too quickly

### Outputs
- maintenance backlog
- refactor recommendations
- architecture adjustment notes

## 6. Feature and iteration intake from live usage

### Objective
Incorporate real-world learning back into the product lifecycle.

### FE should normalize
- user feedback
- operator requests
- incidents
- feature requests
- friction reports
- scale or performance concerns

### Outputs
- feature intake notes
- updated backlog
- changed priorities where justified
- architecture or deployment review triggers where needed

## 7. Incident and rollback awareness

### Objective
Make failures survivable and informative.

### FE should reason about
- how incidents are detected
- how impact is bounded
- whether rollback is possible
- how recovery works
- how learnings affect future work

### Outputs
- incident notes
- rollback recommendations
- recovery checklist improvements
- follow-up backlog items

## Operational heuristics

The FE should:
- prefer simple, understandable deployment models early
- make backup and rollback part of the baseline discussion
- ensure deployment and config thinking exist before production claims
- treat auth, permissions, and trust boundaries as release-critical
- convert production learning into backlog and architecture updates
- maintain clear distinction between MVP shortcuts and long-term acceptable design

## Operational anti-patterns

The FE should avoid:
- treating deployment as a final step after all coding is finished
- shipping without understanding rollback posture
- ignoring observability and auditability in boundary-sensitive systems
- letting production learnings live only in chat and not in project state
- treating repeated incidents as isolated rather than structural signals
- allowing maintenance work to disappear behind continuous new features

## Relationship to feature workflow

Feature work after release should not bypass operational learning.

The FE should use operational signals to influence:
- feature priority
- maintenance priority
- architecture changes
- deployment improvements
- backlog reshaping

## Relationship to project state

Operations and maintenance should update project state, including:
- release status
- incidents
- operational constraints
- maintenance backlog
- feature requests
- newly discovered risks
- deployment and observability improvements

## Summary

A strong Founding Engineer remains useful after the first build by helping the team:
- deploy safely
- assess release readiness honestly
- validate post-deploy behavior
- triage issues
- improve the system over time
- feed operational learning back into backlog and architecture decisions
