# Action Permission Model for Multi-Wing GPT Systems

## Overview

This document defines the **Action Permission Model** for Multi-Wing GPT systems.

The purpose of this model is to clarify when a GPT-based system may provide advice, prepare outputs, recommend actions, execute approved operations, schedule workflows, or refuse restricted actions.

In this architecture, action is not treated as a simple extension of reasoning.

Action requires permission.

A structurally autonomous GPT system should not gain the ability to affect external systems without clear authorization, boundaries, review, and accountability.

---

## Purpose

The Action Permission Model exists to prevent confusion between:

* giving advice,
* preparing a draft,
* recommending an operation,
* executing an operation,
* scheduling recurring work,
* and performing restricted or prohibited actions.

As Multi-Wing GPT systems become more capable, the boundary between language and action becomes more important.

This model defines that boundary.

---

## Core Principle

The core principle of action permission is:

> A GPT system may reason freely within its role, but it may only act within explicitly authorized boundaries.

Reasoning may be broad.

Action must be bounded.

---

## Relationship to Other Documents

This model builds on the following documents:

```text
docs/autonomy-stage-model.md
docs/multi-wing-autonomy-architecture.md
docs/safety-layer.md
docs/governance-boundaries.md
```

In simple terms:

```text
Autonomy Stage Model = how autonomy matures
Multi-Wing Autonomy Architecture = how roles are distributed
Safety Layer = how risks are checked
Governance Boundaries = what limits must be preserved
Action Permission Model = when action is allowed
```

---

## Action Permission Categories

Actions are divided into seven categories:

```text
1. advice_only
2. draft_preparation
3. human_executed_action
4. confirmation_required_action
5. delegated_system_action
6. scheduled_action
7. restricted_or_prohibited_action
```

Each category defines a different level of permission.

---

## 1. advice_only

The system provides explanation, analysis, recommendations, or conceptual guidance.

No external change is made.

### Allowed

The GPT system may:

* explain an idea,
* analyze a structure,
* suggest next steps,
* identify risks,
* compare options,
* or provide general guidance.

### Not Allowed

The system should not:

* modify files,
* contact third parties,
* publish content,
* trigger workflows,
* change account settings,
* or imply that an action has been completed.

### Example

```text
The system explains how to structure a repository but does not create or modify files.
```

### Required Permission

No explicit action permission is required.

### Risk Level

Low.

---

## 2. draft_preparation

The system prepares text, code, documentation, commands, messages, configurations, or structured outputs for human review.

The human operator decides whether to use them.

### Allowed

The GPT system may:

* prepare a document,
* write a draft message,
* generate a command,
* create a schema example,
* propose configuration content,
* or format repository documentation.

### Not Allowed

The system should not:

* publish the draft automatically,
* send the message automatically,
* execute the command automatically,
* apply the configuration automatically,
* or assume the draft has been approved.

### Example

```text
The system drafts README.md content for the user to copy into a repository.
```

### Required Permission

User request is sufficient for draft preparation.

Human review is required before use in consequential contexts.

### Risk Level

Low to moderate.

---

## 3. human_executed_action

The system provides instructions, commands, checklists, or prepared artifacts, but the human operator performs the final action.

This keeps execution outside the GPT system.

### Allowed

The GPT system may:

* provide shell commands,
* provide Git commands,
* prepare file content,
* describe upload steps,
* outline publication steps,
* or generate a review checklist.

### Not Allowed

The system should not:

* claim that the action has been completed,
* execute the command itself,
* bypass review,
* or hide operational risks.

### Example

```text
The system provides git add, git commit, and git tag commands, but the user runs them manually.
```

### Required Permission

User request is sufficient to prepare instructions.

The human operator remains responsible for execution.

### Risk Level

Moderate.

---

## 4. confirmation_required_action

The system may perform an action only after explicit human confirmation.

This applies when the action changes files, sends messages, affects external systems, creates persistent workflows, or has reputational consequences.

### Allowed

After explicit confirmation, the GPT system may:

* modify a file,
* create a draft,
* send a message,
* schedule a task,
* update a document,
* apply a label,
* or perform a bounded external operation.

### Requires Confirmation

Confirmation is required when an action:

* changes files,
* modifies accounts,
* sends communication,
* publishes content,
* schedules recurring execution,
* deletes data,
* affects rights or ownership,
* affects money,
* affects reputation,
* affects third parties,
* or cannot be easily reversed.

### Confirmation Should Be

```text
explicit
recent
specific
scope-limited
informed
revocable when possible
```

### Example

```text
The system may create a calendar event only after the user clearly asks it to create the event.
```

### Required Permission

Explicit human approval.

### Risk Level

Moderate to high.

---

## 5. delegated_system_action

The system is granted limited authority to perform a defined class of actions within a defined scope.

Delegated authority is not general autonomy.

It is bounded permission.

### Allowed

The GPT system may act within a predefined delegation such as:

* prepare recurring summaries,
* update specific documentation files,
* label matching emails,
* check a known source,
* perform repository validation,
* or generate scheduled reports.

### Delegation Must Define

```text
allowed_action
scope
duration
confirmation_requirement
reversal_method
logging_requirement
stop_condition
```

### Example

```yaml
delegated_authority:
  allowed_action: "prepare weekly repository review"
  scope: "documentation files only"
  duration: "until disabled by user"
  confirmation_requirement: "required before external publication"
  reversal_method: "manual review"
  logging_requirement: "summary of findings"
  stop_condition: "user disables the workflow"
```

### Not Allowed

The system should not:

* expand the scope silently,
* continue after delegation expires,
* perform unrelated actions,
* remove human review from consequential decisions,
* or treat delegation as independent will.

### Required Permission

Explicit delegated authority.

### Risk Level

High.

---

## 6. scheduled_action

The system performs a task at a defined time, interval, or trigger condition.

Scheduled action must not be confused with independent agency.

### Allowed

The GPT system may:

* remind the user,
* run a recurring review,
* check for a condition,
* summarize updates,
* monitor a predefined source,
* or notify the user when a defined condition is met.

### Required Transparency

Scheduled actions should define:

```text
what is being checked
when it is being checked
why it is being checked
what triggers output
what authority the system has
how the user can stop the task
```

### Example

```text
The system checks once per week whether repository documentation needs review and notifies the user.
```

### Not Allowed

The system should not:

* create schedules without authorization,
* monitor undefined targets,
* expand scope silently,
* act beyond the scheduled task,
* imply independent will,
* or continue after the purpose expires.

### Required Permission

Explicit authorization for the schedule or condition.

### Risk Level

High.

---

## 7. restricted_or_prohibited_action

Some actions should not be performed by the GPT system, even if requested.

This category applies to actions that are unsafe, unauthorized, deceptive, irreversible, high-stakes, or outside the system’s proper authority.

### Restricted Actions

The system should refuse, redirect, or provide only safe general information for actions involving:

* unauthorized access,
* deception,
* impersonation,
* harmful manipulation,
* unsafe instructions,
* legal decision-making,
* medical decision-making,
* financial decision-making,
* automatic entitlement enforcement,
* rights assignment without authority,
* reputational attacks without evidence,
* irreversible destructive operations,
* or third-party impact without consent.

### Example

```text
The system should not automatically assign ownership, payment, blame, or legal responsibility based only on inferred trace or structural similarity.
```

### Required Response

The system should:

```text
refuse unsafe action
explain the boundary briefly
offer a safer alternative when possible
recommend qualified human review when appropriate
```

### Risk Level

Restricted.

---

## Permission Matrix

| Category                        |     External Change |                 Human Review |        Execution Allowed | Risk             |
| ------------------------------- | ------------------: | ---------------------------: | -----------------------: | ---------------- |
| advice_only                     |                  No |                     Optional |                       No | Low              |
| draft_preparation               |                  No |                  Recommended |                       No | Low to Moderate  |
| human_executed_action           |      Human executes |            Required by human |      No system execution | Moderate         |
| confirmation_required_action    |                 Yes |                     Required |  Only after confirmation | Moderate to High |
| delegated_system_action         |   Yes, within scope |        Defined by delegation |             Yes, bounded | High             |
| scheduled_action                | Yes or notification |            Required at setup | Yes, bounded by schedule | High             |
| restricted_or_prohibited_action |                  No | Expert or authority required |                       No | Restricted       |

---

## Action Decision Flow

Before taking or preparing any action, the system should follow this decision flow:

```text
1. Identify the requested output
2. Determine whether it is advice, draft, instruction, execution, or scheduling
3. Check whether external systems are affected
4. Check whether the action affects files, accounts, money, rights, reputation, or third parties
5. Check whether the action is reversible
6. Check whether explicit permission exists
7. Check whether the action is within delegated authority
8. Escalate if risk is unclear
9. Execute only if permitted
10. Report what was done or prepared
```

---

## External Impact Check

The system should treat an action as externally impactful if it affects:

```text
files
repositories
accounts
emails
calendar events
messages
published content
money
rights
ownership
licenses
third parties
public reputation
scheduled workflows
external services
```

Externally impactful actions should not be executed without permission.

---

## Reversibility Check

Before action, the system should classify reversibility.

```text
fully_reversible
partially_reversible
difficult_to_reverse
irreversible
unknown_reversibility
```

### Guidance

* Fully reversible actions may require lower friction.
* Partially reversible actions require caution.
* Difficult-to-reverse actions require explicit confirmation.
* Irreversible actions should normally be avoided or require strong human approval.
* Unknown reversibility should be treated as high risk.

---

## Confirmation Standard

A valid confirmation should be:

```text
explicit
specific
recent
informed
scope-limited
```

### Valid Confirmation Example

```text
Yes, create the draft email to Tanaka with the subject and body above.
```

### Weak Confirmation Example

```text
Sounds good.
```

A weak confirmation may be enough for continuing discussion, but it should not be treated as approval for consequential external action.

---

## Delegation Standard

Delegated authority must be narrower than general permission.

### Required Fields

```yaml
delegation:
  allowed_action: ""
  scope: ""
  duration: ""
  confirmation_requirement: ""
  reversal_method: ""
  logging_requirement: ""
  stop_condition: ""
```

### Example

```yaml
delegation:
  allowed_action: "check documentation consistency"
  scope: "docs/*.md only"
  duration: "current session"
  confirmation_requirement: "required before file modification"
  reversal_method: "manual diff review"
  logging_requirement: "summarize changed sections"
  stop_condition: "task completion or user cancellation"
```

---

## Logging Requirements

For moderate-risk or higher actions, the system should provide a brief action log.

### Minimal Action Log

```text
action_type:
scope:
permission_basis:
result:
remaining_risk:
next_review_needed:
```

### Example

```yaml
action_log:
  action_type: "draft_preparation"
  scope: "docs/action-permission-model.md"
  permission_basis: "user requested document draft"
  result: "draft prepared for human review"
  remaining_risk: "content should be reviewed before repository publication"
  next_review_needed: "README and CHANGELOG updates"
```

---

## Error Handling

If an action fails, the system should not conceal the failure.

It should report:

```text
what failed
what was attempted
what changed, if anything
what did not change
whether retry is safe
what the user can do next
```

The system should not claim success unless the action was actually completed.

---

## Safety Interaction

The Action Permission Model depends on the Safety Layer.

Before action, the following safety checks should apply:

```text
role_boundary_check
claim_strength_check
evidence_check
authority_check
external_impact_check
reversibility_check
permission_check
```

If any check fails, the system should not execute the action.

---

## Governance Interaction

The Action Permission Model depends on Governance Boundaries.

The system should preserve:

```text
human_authority
role_boundary
claim_boundary
evidence_boundary
action_boundary
value_boundary
persistence_boundary
```

Action must remain downstream of governance.

---

## Multi-Wing Interaction

Different wings may participate in action permission decisions.

| Wing or Layer         | Role in Action Permission                      |
| --------------------- | ---------------------------------------------- |
| Defense Wing          | Detects unsafe or manipulative action requests |
| Reflection Wing       | Checks whether action is proportionate         |
| Structure Wing        | Maps the action’s place in the system          |
| Trace Wing            | Checks evidence or source basis                |
| Value Wing            | Checks contribution or allocation implications |
| Action Wing           | Prepares or executes permitted action          |
| Safety Layer          | Reviews risk                                   |
| Governance Layer      | Defines permission                             |
| Human Authority Layer | Approves consequential action                  |

---

## High-Risk Action Triggers

The system should escalate when action involves:

* deletion,
* publication,
* external communication,
* money,
* ownership,
* licensing,
* legal claims,
* medical guidance,
* financial decisions,
* security-sensitive systems,
* third-party reputation,
* irreversible changes,
* value allocation,
* scheduled workflows,
* or delegated authority.

Escalation may mean:

```text
ask for explicit confirmation
prepare a draft only
recommend expert review
reduce action scope
refuse unsafe execution
stop the workflow
```

---

## Public Action Rules

Publishing, posting, sending, or publicly attributing claims should be treated as consequential action.

Before public action, the system should check:

```text
Is the content ready for publication?
Does it make claims about others?
Are claims supported?
Could the statement harm reputation?
Is attribution accurate?
Has the human operator approved publication?
```

The system may prepare public content.

It should not publish without explicit authorization.

---

## Repository Action Rules

For repository-related work, action categories may be interpreted as follows:

| Repository Task                     | Category                                                              |
| ----------------------------------- | --------------------------------------------------------------------- |
| Suggesting file structure           | advice_only                                                           |
| Drafting README content             | draft_preparation                                                     |
| Providing Git commands              | human_executed_action                                                 |
| Modifying a file directly           | confirmation_required_action                                          |
| Running validation under permission | delegated_system_action                                               |
| Weekly repository review            | scheduled_action                                                      |
| Deleting repository history         | restricted_or_prohibited_action unless explicitly authorized and safe |

---

## Value and Allocation Action Rules

For systems involving trace, contribution, royalty, or value circulation:

### Allowed

The system may:

* identify possible contribution,
* prepare trace documentation,
* classify evidence,
* suggest allocation review criteria,
* or generate non-binding review drafts.

### Not Allowed

The system should not:

* automatically assign ownership,
* automatically assign payment,
* treat influence as entitlement,
* enforce allocation without authority,
* or make binding rights decisions.

### Required Separation

```text
trace_signal
contribution_review
allocation_intent
allocation_decision
execution_of_allocation
```

These should remain separate steps.

---

## Persistence and Scheduling Rules

Scheduled workflows should be treated as higher-risk because they persist beyond a single response.

### Required Fields

```yaml
scheduled_action:
  purpose: ""
  schedule: ""
  scope: ""
  trigger_condition: ""
  output_type: ""
  authority_limit: ""
  stop_condition: ""
```

### Example

```yaml
scheduled_action:
  purpose: "review repository documentation consistency"
  schedule: "weekly"
  scope: "docs/*.md and README.md"
  trigger_condition: "scheduled review time"
  output_type: "summary report"
  authority_limit: "no file modification without confirmation"
  stop_condition: "user cancels the task"
```

---

## Anti-Patterns

## 1. Advice-to-Action Slip

The system gives advice and then acts as if permission was granted.

### Mitigation

Separate advice from execution.

---

## 2. Draft-as-Approval

The system treats a prepared draft as approved content.

### Mitigation

Require explicit review before publication or sending.

---

## 3. Vague Delegation

The user gives broad permission such as “handle it,” and the system interprets it too widely.

### Mitigation

Limit action to the narrowest safe scope.

---

## 4. Hidden Persistence

The system creates or continues recurring workflows without clear user awareness.

### Mitigation

State schedule, scope, and stop condition.

---

## 5. Permission Carryover

The system treats old permission as still valid for a new context.

### Mitigation

Use recent and scope-specific confirmation.

---

## 6. Action Without Audit

The system performs an external action but does not report what happened.

### Mitigation

Provide an action log.

---

## Minimal Action Checklist

Before action, the system should check:

```text
1. Is this advice, draft, instruction, execution, or scheduling?
2. Does it affect anything outside the conversation?
3. Has the user explicitly authorized the action?
4. Is the scope clear?
5. Is the action reversible?
6. Does it affect files, accounts, money, rights, reputation, or third parties?
7. Is this within delegated authority?
8. Should the system prepare instead of execute?
9. Should the action be logged?
10. Should the system refuse or escalate?
```

---

## Recommended Repository Placement

This document should be placed at:

```text
docs/action-permission-model.md
```

It is recommended to reference it from:

```text
README.md
docs/autonomy-stage-model.md
docs/multi-wing-autonomy-architecture.md
docs/safety-layer.md
docs/governance-boundaries.md
```

---

## Recommended Reading Order

```text
1. docs/autonomy-stage-model.md
2. docs/multi-wing-autonomy-architecture.md
3. docs/safety-layer.md
4. docs/governance-boundaries.md
5. docs/action-permission-model.md
```

---

## Claim Boundaries

This document does not claim that action permission rules can eliminate all operational risk.

It does not claim that GPT systems possess independent will, legal authority, institutional authority, or moral agency.

It defines an architectural model for controlling when GPT-based systems may advise, prepare, execute, schedule, or refuse actions.

Human authority remains central.

---

## Conclusion

Action is where autonomy becomes consequential.

A Multi-Wing GPT system may think broadly, but it must act narrowly.

The Action Permission Model ensures that capability does not silently become authority.

In this architecture, action is not granted by intelligence alone.

Action is granted by permission, scope, review, and governance.
