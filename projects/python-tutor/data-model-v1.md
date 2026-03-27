# Python Tutor Platform — Data Model v1

## Purpose

This document defines the first-pass data model for the Python Tutor Platform MVP.

The goal of this model is to support:
- learner / parent / operator role separation
- client/family scoping
- learner progress tracking
- parent-facing summaries
- agent orchestration boundaries
- data visibility and AI context eligibility rules

This is a product and trust-boundary model first, not only a database-schema draft.

## Modeling principles

1. **Client/family is the core ownership boundary**
   - most tutoring data belongs to a single client/family unit

2. **Visibility must be modelable, not implied**
   - parent-visible, learner-visible, operator-only, and restricted content must be representable explicitly or through clear policy derivation

3. **Derived content inherits constraints from source data**
   - summaries, agent-generated responses, and progress insights must not become less restricted than the data they are derived from

4. **Agent context eligibility is a data concern**
   - the model should support determining which records may be used as context by each agent role

5. **Progress, sessions, and curriculum state are first-class**
   - this is a tutoring product, not only a messaging product

## Core entity overview

### 1. ClientFamily
Represents the per-client/per-family boundary.

Suggested fields:
- id
- display_name
- status
- created_at
- updated_at

Purpose:
- top-level ownership scope for learners, parents, sessions, progress, and agent configuration

### 2. User
Represents a human user in the system.

Suggested fields:
- id
- client_family_id (nullable for operator/admin users if needed)
- role_type (`learner`, `parent`, `operator`)
- display_name
- contact_channel_info
- status
- created_at
- updated_at

Purpose:
- identity for learners, parents, and operators

### 3. LearnerProfile
Learner-specific tutoring and age-related state.

Suggested fields:
- id
- user_id
- client_family_id
- age_band
- learning_level
- tutor_preferences
- active_status
- created_at
- updated_at

Purpose:
- learner-specific configuration and product state

### 4. ParentProfile
Parent/guardian-specific state.

Suggested fields:
- id
- user_id
- client_family_id
- parent_preferences
- notification_preferences
- created_at
- updated_at

Purpose:
- parent-specific settings and relationship to the tutoring product

### 5. FamilyRelationship
Represents the relationship between parent(s) and learner(s).

Suggested fields:
- id
- client_family_id
- parent_user_id
- learner_user_id
- relationship_type
- status
- created_at

Purpose:
- explicit mapping of which parent can view/manage which learner

### 6. LessonUnit
Represents a curriculum or lesson unit.

Suggested fields:
- id
- client_family_id
- curriculum_source_type
- external_curriculum_ref
- title
- description
- level
- status
- created_at
- updated_at

Purpose:
- structure for the learner’s tutoring content and progression

### 7. LearnerSession
Represents a tutoring session instance.

Suggested fields:
- id
- client_family_id
- learner_id
- lesson_unit_id (nullable)
- session_status
- started_at
- ended_at
- session_summary_ref
- created_at
- updated_at

Purpose:
- top-level session boundary for tutoring interactions and progress events

### 8. ExerciseTask
Represents an exercise, task, or prompt inside a lesson/session.

Suggested fields:
- id
- client_family_id
- lesson_unit_id
- learner_session_id (nullable)
- task_type
- prompt_text
- expected_outcome
- status
- created_at
- updated_at

Purpose:
- supports structured learning interaction, not just free-form chat

### 9. LearnerProgressRecord
Represents learner progress over time.

Suggested fields:
- id
- client_family_id
- learner_id
- lesson_unit_id (nullable)
- learner_session_id (nullable)
- progress_type
- progress_value
- summary_text
- created_at

Purpose:
- persistent record of learning progress for learner, parent, and operator views

### 10. InteractionRecord
Represents a recorded interaction between a user and an agent-mediated surface.

Suggested fields:
- id
- client_family_id
- actor_user_id (nullable for system-generated entries)
- actor_role_type
- channel_type (`learner_ui`, `parent_ui`, `whatsapp`, `operator_ui`, etc.)
- agent_role_type (`learner_agent`, `parent_agent`, `curriculum_agent`, `super_agent`)
- learner_session_id (nullable)
- content_ref or content_body reference
- visibility_classification
- created_at

Purpose:
- auditable interaction tracking for learner, parent, and operator flows

### 11. ParentSummary
Represents a parent-facing derived summary.

Suggested fields:
- id
- client_family_id
- learner_id
- source_scope_ref
- summary_type
- summary_text
- visibility_classification
- created_at

Purpose:
- parent-appropriate summary surface derived from learner activity and progress

### 12. AgentConfiguration
Represents bounded configuration for agent behavior per client/family.

Suggested fields:
- id
- client_family_id
- agent_role_type
- configuration_scope
- config_payload_ref
- created_at
- updated_at

Purpose:
- store configuration that affects learner agent, parent agent, curriculum agent, and super-agent behavior

### 13. AgentContextPolicy
Represents context eligibility rules by agent role.

Suggested fields:
- id
- client_family_id (nullable if global defaults exist)
- agent_role_type
- allowed_visibility_classes
- forbidden_visibility_classes
- allowed_entity_types
- policy_version
- created_at

Purpose:
- make context filtering rule-driven and auditable

### 14. VisibilityClassification
A classification model applied to content-bearing records.

Suggested fields / values may include:
- `learner_visible`
- `parent_visible`
- `shared_family`
- `operator_only`
- `restricted`
- `derived_parent_summary`

Purpose:
- support policy evaluation and context filtering

### 15. AuditEvent
Represents an auditable system or user action.

Suggested fields:
- id
- client_family_id (nullable for operator-wide events)
- actor_user_id (nullable)
- actor_role_type
- event_type
- target_entity_type
- target_entity_id
- event_metadata
- created_at

Purpose:
- support sensitive action logging, operator review, and incident investigation

## First-pass relationship model

High-level relationships:
- `ClientFamily` has many `User`
- `User` may have one `LearnerProfile` or one `ParentProfile`
- `ClientFamily` has many `FamilyRelationship`
- `ClientFamily` has many `LessonUnit`
- `LearnerProfile` has many `LearnerSession`
- `LessonUnit` has many `ExerciseTask`
- `LearnerProfile` has many `LearnerProgressRecord`
- `LearnerSession` has many `InteractionRecord`
- `LearnerProfile` has many `ParentSummary`
- `ClientFamily` has many `AgentConfiguration`
- `ClientFamily` may have many `AgentContextPolicy`
- key actions create `AuditEvent`

## Visibility and access model

### Visibility concepts
Each content-bearing record should either:
- store a visibility classification directly
or
- derive it through policy and entity ownership

### Initial recommended visibility classes
- learner-visible
- parent-visible
- shared-family
- operator-only
- restricted
- derived-parent-summary

### Important rules
- parent-visible does not imply learner-visible
- operator-only does not imply parent-visible
- derived-parent-summary must be generated through approved transformation, not raw transcript leakage
- learner-agent context must not include parent-private or operator-only records

## Agent context eligibility model

The backend should determine context eligibility by combining:
- agent role type
- actor role type
- entity type
- visibility classification
- client/family scope
- explicit policy rules

### Example intent
- learner agent may use learner-visible and approved shared-family records
- parent agent may use parent-visible and approved derived summary records
- curriculum agent may use learner progress and curriculum state but not unrelated operator-only records
- super agent may use broader supervisory context but still inside audit and policy limits

## WhatsApp-specific modeling note

If parent WhatsApp is included:
- parent identity must map to a `User`
- channel-specific interaction should still create `InteractionRecord`
- visibility rules should be identical to dashboard parent access, not broader

## Data that should not be modeled as raw unrestricted text blobs only

Avoid relying only on undifferentiated transcript storage for:
- progress state
- parent summaries
- permissions decisions
- curriculum progression
- visibility control

Structured state is needed for safe summaries and supervision.

## First-pass implementation guidance

For MVP, not every policy detail must be represented as its own table. Some can begin as:
- typed fields
- enums
- backend policy code
- well-structured JSON fields where appropriate

But the model must still preserve:
- client/family boundary
- role boundary
- visibility boundary
- agent context boundary
- progress/session structure

## Open questions

- whether operators should live inside the same `User` model or a separate admin identity model
- whether learner age should be exact, banded, or policy-derived
- how much lesson/curriculum structure should be normalized in MVP
- whether parent summaries should be materialized records or generated-on-demand with caching
- whether `AgentContextPolicy` should be stored explicitly in MVP or implemented as code-first policy with limited persistence

## Recommended next artifact

The next useful artifact is:
- `repo-structure-v1.md`
or
- `deployment-model-v1.md`

If implementation planning is the priority, I would recommend `repo-structure-v1.md` next.
