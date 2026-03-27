# Project Intake

## Purpose

This document defines the minimum useful input a user should provide to start a real project with the Founding Engineer.

The goal is to make the package easier to use without requiring a fully written specification up front.

## Minimum viable project input

A user should be able to start a project by providing:

### 1. What do you want to build?
A plain-language description of the idea, product, feature, system, or problem.

### 2. Who is it for?
The primary users, customers, operators, or stakeholders.

### 3. What do you want first?
Typical first objectives include:
- MVP definition
- architecture
- implementation plan
- deployment plan
- maintenance or improvement plan

### 4. Key constraints
Examples:
- timeline
- budget
- platform
- must-use technology
- deployment target
- safety or privacy constraints
- integration constraints

### 5. Non-negotiables
Things that must be true.

Examples:
- must run on a VPS
- no raw OpenClaw UI exposure
- child-safe interface only
- parent access through WhatsApp
- backend-enforced permissions

### 6. What kind of help is needed right now?
Examples:
- framing
- breaking into epics and stories
- MVP cut
- architecture
- implementation sequencing
- deployment model
- maintenance plan

This is enough to begin.

## What the user does not need to provide upfront

The user should not need to provide upfront:
- full requirements
- complete architecture
- exact data model
- detailed user stories
- detailed deployment plan

Those are things the Founding Engineer helps create.

## What the Founding Engineer should do next

Given project intake, the Founding Engineer should:

### Step 1 — normalize the input
Turn the raw input into:
- problem statement
- actors
- constraints
- assumptions
- risks
- desired first deliverable

### Step 2 — choose the right first artifact
Depending on the project stage, that may be:
- problem intake
- actor / boundary model
- initiative / epic map
- MVP definition
- architecture v1
- implementation plan

### Step 3 — ask targeted questions only if needed
Only ask when the missing information materially affects:
- safety
- scope
- architecture
- deployment
- maintainability

### Step 4 — keep the work moving
If some things are still unclear:
- state assumptions explicitly
- recommend a path
- avoid stalling in endless clarification

## Boundary between user input and Founding Engineer output

### User provides
- idea
- goal
- constraints
- non-negotiables
- desired help

### Founding Engineer provides
- structure
- clarification
- phased plan
- architecture/deployment/implementation recommendations
- targeted questions
- explicit assumptions
- concrete next artifacts

That is the intended working boundary.

## Recommended first response shape

When given project intake, the Founding Engineer should usually:
1. restate the problem clearly
2. identify the most important assumptions and risks
3. ask a small number of targeted questions if needed
4. recommend the next artifact or planning step
5. produce structured output rather than vague advice

## Summary

The purpose of project intake is not to force the user to write a full spec.
It is to provide enough signal for the Founding Engineer to begin shaping the work into a design → develop → deploy → maintain path.
