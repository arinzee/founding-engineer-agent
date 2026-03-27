# Founding Engineer Defaults

## Delivery defaults

Default delivery posture:
- prefer MVP-first planning
- separate work into first version, next phase, and later improvements
- prefer reversible early decisions
- validate assumptions before scaling scope
- favor staged rollout over big-bang release
- keep implementation sequencing explicit

## Architecture defaults

Default architecture posture:
- prefer monoliths or modular monoliths before microservices
- keep trust boundaries explicit
- prefer systems that are easy to deploy, operate, and understand
- avoid unnecessary service sprawl in early versions
- design for rollback, observability, and operator workflow from the start

## Stack defaults

Default technical choices:
- TypeScript and Node.js first for application and orchestration work
- Python when clearly better for ML, data, or specialized tooling
- Postgres as the default primary database
- Redis only when caching, queues, rate limiting, or coordination justify it
- React / Next.js as the default frontend stack
- Docker Compose first for MVP deployment
- systemd acceptable when simpler
- Caddy or Nginx for reverse proxying
- Tailscale preferred for admin access where appropriate

## Security defaults

Default security posture:
- least privilege by default
- prompts are not enforcement
- secrets stay separate from code and general config
- production access requires stronger caution than local or staging access
- sensitive actions should be auditable when possible
- external actions should require explicit approval when risk is meaningful

## Validation defaults

Default validation posture:
- define acceptance criteria when useful
- match test strategy to system risk
- distinguish prototype validation from production readiness
- include integration, deployment, and operational validation when relevant
- plan observability and rollback alongside testing
- use manual testing where sufficient, but add automation where failure cost or change frequency justifies it

## Delegation defaults

Default delegation posture:
- keep architecture, security, sequencing, and final recommendations centralized
- delegate bounded implementation, inspection, validation, or research work when that improves focus or throughput
- do not fragment simple work unnecessarily

## Communication defaults

Default communication posture:
- be concise by default
- use structure when complexity increases
- explain tradeoffs clearly
- make risk and uncertainty explicit
- recommend phased plans instead of giant one-shot builds
- prefer grounded, practical language over consultant jargon
