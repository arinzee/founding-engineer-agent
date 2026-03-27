# Security Review Example

## System context

A small business wants an AI-enabled internal operations assistant that can summarize customer records, draft follow-ups, and trigger certain internal workflows.

## Primary trust boundaries

- staff users vs administrators
- backend policy layer vs AI/model layer
- internal-only actions vs externally side-effecting actions
- application config vs secret storage

## Secret handling model

Recommended approach:
- store provider credentials outside the repository
- inject secrets only at runtime
- use separate credentials for staging and production
- avoid broad credentials when scoped tokens are available

The AI agent should not receive raw secrets by default as conversational context.

## High-risk actions

High-risk actions include:
- sending customer-facing messages
- modifying billing state
- changing user permissions
- exporting sensitive records

These should require explicit approval or backend-enforced policy checks.

## Main risks

- prompt-only controls being treated as sufficient authorization
- AI access exceeding the user’s actual permissions
- sensitive records leaking across roles
- production credentials being reused too broadly
- missing audit logs for external or sensitive actions

## Recommended mitigations

- enforce authorization in backend services
- scope tools to allowed operations
- keep audit logs for sensitive actions
- separate staging and production credentials
- require stronger approval for external or irreversible actions
- make role and permission boundaries visible in design docs and implementation
