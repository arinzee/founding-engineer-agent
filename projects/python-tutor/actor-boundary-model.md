# Python Tutor Platform — Actor and Boundary Model

## Core actors

### Learner / Child
**Goals**
- learn Python safely and progressively
- interact through an age-appropriate tutoring interface
- receive lessons, explanations, prompts, exercises, and feedback

**Allowed interfaces**
- child-safe custom UI only

**Visible data**
- their own lessons
- their own exercises
- their own progress view appropriate to child level
- child-safe tutoring interactions

**Allowed actions**
- engage in lessons
- answer questions
- submit exercises
- request help
- resume their own learning sessions

**Restricted actions**
- no raw OpenClaw interface
- no direct access to parent UI
- no direct access to operator/super-agent controls
- no access to parent notes, admin data, or system settings
- no unrestricted channel access

### Parent / Guardian
**Goals**
- monitor progress
- understand engagement and learning trajectory
- guide goals/preferences
- communicate with the parent-facing agent

**Allowed interfaces**
- parent dashboard
- WhatsApp in MVP or early phase

**Visible data**
- child progress summaries
- learning milestones
- selected session insights
- alerts / recommendations / next steps
- parent-relevant controls

**Allowed actions**
- view progress dashboard
- communicate with parent-facing agent
- adjust selected preferences/goals
- receive summaries and updates

**Restricted actions**
- should not access operator/super-agent internals directly
- should not access unsafe/raw learner-agent internals if that breaks product boundaries
- should not see system implementation details unless explicitly intended

### Operator / Platform Owner
**Goals**
- configure and supervise the tutor system
- manage learner/client setup
- oversee agents
- customize per-client experience
- intervene when needed

**Allowed interfaces**
- operator/admin interface
- OpenClaw-level control surfaces
- infrastructure/runtime controls

**Visible data**
- client configuration
- agent-level state as needed
- operational metrics
- safety issues
- audit logs
- curriculum/tutoring config

**Allowed actions**
- provision client/family instances
- configure super agent behavior
- manage parent/learner setup
- review incidents
- adjust orchestrations/configs

## Agent actors

### Learner Agent
Role: deliver the learner tutoring experience through the child-safe UI only.
Must not access parent-private information, operator-only data, or unrestricted supervisory context.

### Parent Agent
Role: explain learner progress, answer parent questions, and provide parent-facing summaries.
Must not expose operator-only or super-agent-only context.

### Curriculum Agent
Role: determine or adapt lesson pathway and recommend what the learner should do next.
This should be a backend/orchestration actor, not a directly user-facing one.

### Super Agent
Role: per-client supervisory orchestration agent that can tailor learner-agent and parent-agent behavior, coordinate curriculum direction, and shape tutoring behavior within allowed boundaries.

Important: the super agent must not be the true security boundary. Backend/platform policy remains authoritative for permissions, data access, and forbidden paths.

## Trust boundaries

### Learner boundary
The child must only access:
- child-safe custom UI
- learner-scoped content
- learner-agent outputs filtered for that learner and age band

### Parent boundary
The parent can see:
- learner progress summaries
- selected oversight information
- communication designed for the parent role

The parent should not automatically receive every raw tutoring interaction or operator/supervisor internals.

### Operator boundary
Operator access is fundamentally different and should be audited.

### Agent-context boundary
Each agent must have a different allowed context envelope:
- learner agent
- parent agent
- curriculum agent
- super agent

No agent should infer permissions from conversation alone.

### OpenClaw boundary
OpenClaw should be behind the product layer and not directly exposed to the learner. Preferably it should not be directly exposed to the parent either.

## Shared vs private data

### Shared
- learner progress summary
- high-level lesson state
- approved parent-facing updates
- client/family configuration relevant to both parent and learner

### Learner-private / learner-scoped
- active lesson flow
- child-facing tutoring history
- age-appropriate feedback
- exercise attempts

### Parent-private
- parent notes/preferences/goals
- communications with parent agent
- tutoring style preferences or concerns

### Operator / admin-private
- orchestration settings
- logs
- agent internals
- incident/debug information
- deployment/runtime config

### Restricted / derived
- agent-generated summaries
- risk/flag signals
- curriculum decisions
- internal tutor analysis

## AI context eligibility rules

### Learner agent may receive
- learner profile appropriate to child role
- lesson state
- exercise state
- approved curriculum context
- child-safe tutoring memory

### Learner agent must never receive
- parent-private notes unless explicitly allowed through policy
- operator-only controls or logs
- unrestricted super-agent context
- admin/debug/runtime information

### Parent agent may receive
- parent-visible progress summary
- parent-facing interpretation of learning status
- approved recommendations
- selected family/client preferences

### Parent agent must not receive
- unsafe raw child context if not intended
- operator-only internals
- unrestricted super-agent context
- hidden moderation/control logic unless deliberately surfaced

### Super agent may receive
- broader supervisory context
- but still should be bounded by policy and auditability

## Forbidden paths
- learner cannot access raw OpenClaw UI
- learner cannot switch to unrestricted channel access
- learner cannot interact directly with parent or super-agent surfaces
- parent cannot access operator/super-agent control surfaces directly
- no agent can bypass backend policy enforcement
- no AI context should be widened based only on conversational inference

## MVP product surfaces
- child: custom learner web UI only
- parent: parent dashboard + likely WhatsApp support
- operator: internal operator/admin control plane

## System principle
- backend platform remains the policy and orchestration authority
- OpenClaw provides runtime/orchestration support
- custom UI remains the only child-facing surface
