---
type: urn:open-specs:persona
title: Workspace Administrator Persona
description: Person responsible for protecting shared task access and supporting users in a workspace.
tags:
  - example
  - persona
  - administration
  - authentication
generated:
  by: agent:opencode
  at: 2026-08-25T00:00:00Z
status: draft
---

## Role

Person responsible for maintaining a safe shared workspace and helping users recover access or resolve access problems.

## Desired Outcomes

- Ensure only appropriate users can access shared task information.
- Understand account and access failures without exposing protected information.
- Support users without becoming the owner of their work.

## Triggers and Behaviors

- Reviews access concerns after a user reports a problem.
- Helps clarify ownership or authorization questions.
- Escalates repeated authentication failures or suspected unauthorized access.

## Constraints

- Must protect private task and account information.
- Needs auditable, understandable access behavior.
- May not have authority to inspect all user content.

## Pain Points

- Unclear access boundaries create security risk.
- Generic failures can make support diagnosis difficult.
- Manual recovery work consumes operational time.

## Success Criteria

- Can explain access boundaries and recovery responsibilities.
- Unauthorized access attempts are prevented and observable.
- Legitimate users can recover access without unnecessary exposure of account data.

## Evidence and Confidence

- Sources: discovery hypothesis based on shared-product operational needs.
- Confidence: low until validated with security and operations stakeholders.
- Review date: 2026-09-25.
