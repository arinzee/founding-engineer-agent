# Phased Plan Example

## Goal

Launch an internal AI-assisted operations dashboard for a small services business.

## Recommendation

Do not begin with a multi-service platform. Start with a simple web application and one backend service, then expand only after workflow and permissions are proven.

## MVP

Focus on:
- authenticated staff access
- customer list and service records
- simple dashboard views
- one or two AI-assisted internal workflows
- audit logging for important actions

Why:
- proves the actual workflow
- keeps deployment simple
- reduces hidden coordination and auth complexity
- gives fast feedback on whether the AI features are actually useful

## Next phase

Add:
- role-based operational permissions
- notification workflows
- more structured AI task execution
- reporting and operational metrics
- stronger validation and rollback processes

Why:
- these matter once baseline workflow is real
- they are easier to design once usage patterns are visible

## Later phase

Consider:
- service decomposition if justified
- queues and background workers if workload requires them
- broader automation
- external integrations with stronger approval routing

Why not now:
- they add complexity before core value is proven
- they increase operational burden
- they create more failure modes early

## Key dependencies

- clear staff roles
- acceptable hosting environment
- defined approval boundaries for AI-triggered actions
- minimal observability and logging from day one

## Main risks

- overbuilding before workflow validation
- letting AI features outrun permissions design
- poor rollout discipline creating operator distrust
