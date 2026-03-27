# Python Tutor Platform — Problem Intake

## Idea / request summary
Build a Python tutoring platform powered by OpenClaw behind the scenes, with separate custom experiences for children and parents, plus a supervisor layer controlled per learner/client.

## What is being built or changed?
A role-sensitive tutoring product with:
- a child / learner experience
- a parent experience
- a supervisor / super-agent layer
- OpenClaw as the orchestration/runtime substrate
- a custom UI instead of exposing raw OpenClaw UI to end users

## Why does it matter?
The goal is to create a tutoring system that:
- is child-safe
- is role-separated
- gives parents visibility into progress
- allows supervised multi-agent tutoring flows
- can be deployed and operated reliably on a VPS

## Who is this for?
Primary users:
- children / learners
- parents / guardians

Operators:
- platform operator
- possibly admins later

System actors:
- learner agent
- parent agent
- super agent
- curriculum agent
- backend platform
- OpenClaw runtime

## Current pain point or opportunity
Opportunity:
- use OpenClaw to power tutoring/orchestration
- but present it as a real product with custom parent/child experiences
- with stricter role and safety boundaries than a generic agent/chat interface

## Desired outcome
A platform where:
- the child interacts only through a controlled, age-restricted custom UI
- the parent sees progress and relevant info through a separate parent experience
- the parent may also interact through approved channels like WhatsApp
- the super agent supervises the learner/parent agents per learner/client
- OpenClaw is hidden behind the product layer
- the whole system runs on a VPS in containers

## Constraints
### Technical
- VPS-hosted
- containerized deployment
- OpenClaw should be the underlying orchestration/runtime layer
- no raw OpenClaw UI exposed to parents or children

### Safety / trust
- strict child-safe interaction boundaries
- age restriction must be enforced, not advisory
- role separation must be backend/system enforced
- parent and child access must be clearly separated
- super-agent control must not leak into user-visible privilege escalation

### Product
- product should start small
- MVP should avoid trying to solve every education/tutoring problem at once

## Known risks
- boundary leakage between parent/child/supervisor contexts
- overloading the super agent with too much authority
- confusing product roles vs agent roles
- exposing too much OpenClaw behavior directly
- trying to build too broad a platform in the first version

## Key decisions already clarified
- target learner age range starts at 7+
- curriculum will be driven by another agent
- parent visibility must include a progress dashboard
- WhatsApp is the most important parent channel
- the product is intended to be deployed as a complete solution per client/family
- the super agent should control end-to-end client agent behavior, but within backend-enforced boundaries

## Current stage
- idea / early design framing

## Suggested next artifacts
- actor-boundary-model.md
- initiative-epic-map.md
- mvp-definition.md
- mvp-story-prioritization.md
