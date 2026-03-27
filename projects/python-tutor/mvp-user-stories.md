# Python Tutor Platform — First-Pass MVP User Stories

## Learner access and child-safe UI

### Story 1
As a learner, I want to access my tutoring experience only through the child-safe interface so that I cannot enter unsafe or unintended product surfaces.

### Story 2
As the platform, I want learner access routes to be explicitly restricted so that child interactions remain policy-enforced rather than convention-based.

### Story 3
As a learner, I want a bounded tutoring session flow so that I can learn Python in a way appropriate to my age and product scope.

### Story 4
As the product owner, I want the learner session experience to be age-restricted and controlled so that the system remains safe and usable for children 7+.

## Parent dashboard and parent value

### Story 5
As a parent, I want to see my child’s learning progress so that I can understand whether the tutoring is helping.

### Story 6
As a parent, I want a simple dashboard view of what my child is working on so that I can support them without needing to inspect raw system details.

## Parent WhatsApp interaction

### Story 7
As a parent, I want to interact with the parent-facing tutor agent through WhatsApp so that I can ask questions and receive updates conveniently.

### Story 8
As the platform, I want WhatsApp parent communication to remain bounded so that the channel does not become a policy bypass.

## Super-agent supervision

### Story 9
As the operator, I want the super agent to steer per-client tutor behavior so that the tutoring experience can be tailored to each learner/family.

### Story 10
As the platform, I want the super agent to orchestrate other agents without becoming the security boundary so that customization does not weaken role safety.

## Safety, permissions, and boundaries

### Story 11
As the platform, I want learner, parent, and operator roles enforced explicitly so that each actor only sees and does what is allowed.

### Story 12
As the platform, I want data classified as shared, private, or restricted so that parent, learner, and operator access can be controlled safely.

### Story 13
As the platform, I want each agent to receive only role-eligible context so that AI outputs do not leak restricted information.

### Story 14
As the product owner, I want forbidden interaction paths blocked so that raw OpenClaw or unsafe role-bypass access is impossible in MVP.

## Progress and learning state

### Story 15
As the platform, I want to store learner session and progress records so that progress can be surfaced consistently to learners, parents, and operators.

### Story 16
As a parent, I want useful progress summaries generated from learner activity so that I can understand growth without reading raw tutoring transcripts.

## Deployment baseline

### Story 17
As the operator, I want the platform deployable on a VPS in containers so that it can run as a real managed product.

### Story 18
As the operator, I want a basic rollback and operational baseline so that the system can be recovered if a deployment goes wrong.
