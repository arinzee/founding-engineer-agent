# Python Tutor Platform — MVP Definition

## MVP objective
Deliver a personal Python tutor for a single family/client unit with:
- a child-safe learner experience
- a parent progress experience
- backend-enforced boundaries
- supervised multi-agent orchestration
- deployable on a VPS in containers

The MVP should prove:
- the learner experience is useful and safe
- the parent experience is valuable
- the role/agent boundaries are enforceable
- the system can run reliably as a product, not just a demo

## MVP in

### Learner experience
- custom learner web UI only
- age-restricted child-safe interaction model
- learner tutoring sessions for Python
- lesson/help/exercise interaction in a bounded format
- learner progress view at an age-appropriate level

### Parent experience
- parent dashboard
- learner progress summary
- high-level activity/session summary
- parent-facing agent interaction in the dashboard

### Basic parent channel support
- one parent messaging channel only
- recommendation: WhatsApp first

### Agent orchestration
- learner agent
- parent agent
- curriculum-agent integration
- super-agent supervision at a basic orchestration level

### Safety, permissions, and trust boundaries
- learner / parent / operator role model
- shared vs private vs restricted data model
- backend-enforced permissions
- AI context eligibility rules
- no raw OpenClaw UI for learner or parent
- forbidden path enforcement

### Progress and learning intelligence
- learner session history
- lesson/exercise progress records
- parent-facing progress summaries
- basic operator visibility into learner progress

### Deployment and operations baseline
- VPS deployment
- containerized stack
- backend + frontend + OpenClaw + Postgres + reverse proxy
- runtime secret handling
- basic audit logging
- backup / rollback basics

## Next phase
- richer parent channel workflows
- stronger super-agent controls
- broader parent controls
- better learning intelligence
- more polished curriculum integration

## Later
- advanced operator/admin tooling
- advanced risk/escalation systems
- more sophisticated workflow automation
- expanded learning modalities
- broader communication surfaces

## Explicit exclusions for MVP
- raw OpenClaw UI exposure to learner
- raw OpenClaw UI exposure to parent
- unrestricted learner access to messaging channels
- super agent acting as the true security boundary
- broad multi-client admin platform
- sophisticated analytics/reporting suite
- advanced automation-heavy orchestration
- multiple parent channels at once
- full-featured coding sandbox
- solving all tutoring problems in the first version
