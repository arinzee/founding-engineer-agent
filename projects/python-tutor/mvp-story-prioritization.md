# Python Tutor Platform — MVP Story Prioritization

## Must-have for MVP v1

### Learner access and safety
- learner can access tutoring only through the child-safe interface
- learner access routes are explicitly restricted
- learner has a bounded tutoring session flow
- learner session experience is age-restricted and controlled

### Parent value
- parent can see learner progress
- parent can see a simple dashboard view without raw system details

### Supervision and orchestration
- super agent can steer per-client tutor behavior
- super agent orchestrates within backend-defined safety limits

### Safety, permissions, and boundaries
- learner, parent, and operator roles are enforced explicitly
- data is classified/shared safely
- each agent receives only role-eligible context
- forbidden paths are blocked

### Progress and learning state
- learner session and progress records are stored
- parent progress summaries are generated safely

### Deployment baseline
- platform is deployable on a VPS in containers
- basic rollback and operational baseline exist

## Nice-to-have inside MVP if capacity allows
- parent can interact through WhatsApp
- WhatsApp remains bounded and policy-controlled

## Defer beyond MVP v1
- richer parent-channel workflows
- multiple parent channels
- more advanced customization controls
- sophisticated analytics
- richer escalation/risk detection
- broader operator tooling
- advanced learning modalities
- heavier automation

## Core MVP v1
Stories represented by the must-have set above.

## Optional MVP extension
- WhatsApp parent interaction
- bounded parent-channel policy enforcement
