# Requirements Table

## Overview

This document defines a requirements table for the **Multi-Wing GPT Autonomy Architecture**.

The purpose of this document is to translate the architectural concepts of the repository into standardization-oriented requirements.

The requirements are intended to support:

* implementation review,
* conformance planning,
* system evaluation,
* standardization-oriented discussion,
* governance mapping,
* and future working draft preparation.

This document does not define an official ISO, IEC, IEEE, or regulatory standard.
It provides a requirements framework for this repository’s architecture.

---

## Normative Language

The following terms are used in this document:

| Term       | Meaning                    |
| ---------- | -------------------------- |
| shall      | Required for conformance   |
| shall not  | Prohibited for conformance |
| should     | Recommended                |
| should not | Discouraged                |
| may        | Permitted                  |
| can        | Possible or descriptive    |

---

## Requirement Categories

Requirements are organized into the following categories:

```text
1. Role Separation Requirements
2. Self-Checking Requirements
3. Boundary Control Requirements
4. Traceability Requirements
5. Action Permission Requirements
6. Human Authority Requirements
7. Governance and Escalation Requirements
8. Persistence and Scheduling Requirements
9. Value and Allocation Boundary Requirements
10. Auditability Requirements
```

---

# 1. Role Separation Requirements

Role separation is the foundation of the Multi-Wing architecture.

Each Wing should have a defined responsibility, scope, failure mode, and counterbalance.

| ID          | Requirement                                                                                               | Priority    | Conformance Evidence           | Related Document                           |
| ----------- | --------------------------------------------------------------------------------------------------------- | ----------- | ------------------------------ | ------------------------------------------ |
| MW-ROLE-001 | The system shall define each implemented Wing as a distinct functional role.                              | Required    | Role documentation             | `docs/multi-wing-autonomy-architecture.md` |
| MW-ROLE-002 | Each Wing shall have a documented purpose.                                                                | Required    | Wing definition table          | `docs/multi-wing-autonomy-architecture.md` |
| MW-ROLE-003 | Each Wing shall have a documented scope.                                                                  | Required    | Scope description              | `docs/governance-boundaries.md`            |
| MW-ROLE-004 | Each Wing should have a documented failure mode.                                                          | Recommended | Failure mode table             | `docs/multi-wing-autonomy-architecture.md` |
| MW-ROLE-005 | Each Wing should have a documented counterbalance or review path.                                         | Recommended | Counterbalance mapping         | `docs/safety-layer.md`                     |
| MW-ROLE-006 | No single Wing shall be documented as having unrestricted authority over the whole system.                | Required    | Governance boundary review     | `docs/governance-boundaries.md`            |
| MW-ROLE-007 | The system should distinguish between Core Wings and Control Layers.                                      | Recommended | Architecture diagram or table  | `docs/multi-wing-autonomy-architecture.md` |
| MW-ROLE-008 | The system may implement a minimal Multi-Wing configuration when full Wing implementation is unnecessary. | Optional    | Minimal implementation profile | `docs/multi-wing-autonomy-architecture.md` |

---

# 2. Self-Checking Requirements

Self-checking reduces overstatement, hidden assumptions, internal contradiction, and unsafe compliance.

| ID          | Requirement                                                                                         | Priority    | Conformance Evidence          | Related Document                           |
| ----------- | --------------------------------------------------------------------------------------------------- | ----------- | ----------------------------- | ------------------------------------------ |
| MW-SELF-001 | The system shall include a mechanism for reviewing claim strength.                                  | Required    | Claim review process          | `docs/safety-layer.md`                     |
| MW-SELF-002 | The system shall include a mechanism for checking assumptions.                                      | Required    | Reflection checklist          | `docs/safety-layer.md`                     |
| MW-SELF-003 | The system should include a mechanism for detecting internal contradiction.                         | Recommended | Reflection log or checklist   | `docs/safety-layer.md`                     |
| MW-SELF-004 | The system should include a mechanism for detecting overclaim.                                      | Recommended | Claim control process         | `docs/safety-layer.md`                     |
| MW-SELF-005 | The system should qualify uncertain outputs when evidence is incomplete.                            | Recommended | Output examples               | `docs/governance-boundaries.md`            |
| MW-SELF-006 | The system shall not present speculation as verified fact.                                          | Required    | Claim classification evidence | `docs/glossary.md`                         |
| MW-SELF-007 | The system should distinguish between fact, interpretation, inference, hypothesis, and speculation. | Recommended | Claim category mapping        | `docs/glossary.md`                         |
| MW-SELF-008 | The system may use a Reflection Wing or equivalent component to perform self-checking.              | Optional    | Reflection Wing description   | `docs/multi-wing-autonomy-architecture.md` |

---

# 3. Boundary Control Requirements

Boundary control prevents role drift, authority drift, action leakage, trace overreach, and value overclaim.

| ID           | Requirement                                                                                                           | Priority    | Conformance Evidence           | Related Document                  |
| ------------ | --------------------------------------------------------------------------------------------------------------------- | ----------- | ------------------------------ | --------------------------------- |
| MW-BOUND-001 | The system shall define role boundaries.                                                                              | Required    | Role boundary documentation    | `docs/governance-boundaries.md`   |
| MW-BOUND-002 | The system shall define claim boundaries.                                                                             | Required    | Claim boundary policy          | `docs/governance-boundaries.md`   |
| MW-BOUND-003 | The system shall define evidence boundaries.                                                                          | Required    | Evidence classification table  | `docs/governance-boundaries.md`   |
| MW-BOUND-004 | The system shall define action boundaries.                                                                            | Required    | Action permission rules        | `docs/action-permission-model.md` |
| MW-BOUND-005 | The system shall define authority boundaries.                                                                         | Required    | Human authority rules          | `docs/governance-boundaries.md`   |
| MW-BOUND-006 | The system should define value boundaries when contribution, trace, royalty, attribution, or allocation is discussed. | Recommended | Value boundary policy          | `docs/governance-boundaries.md`   |
| MW-BOUND-007 | The system should define persistence boundaries when scheduled or recurring workflows are used.                       | Recommended | Schedule control documentation | `docs/action-permission-model.md` |
| MW-BOUND-008 | The system shall not silently expand its role or authority beyond the documented boundary.                            | Required    | Boundary review evidence       | `docs/safety-layer.md`            |

---

# 4. Traceability Requirements

Traceability supports evidence review, origin awareness, attribution discipline, and auditability.

| ID           | Requirement                                                                                                    | Priority    | Conformance Evidence        | Related Document                           |
| ------------ | -------------------------------------------------------------------------------------------------------------- | ----------- | --------------------------- | ------------------------------------------ |
| MW-TRACE-001 | The system should support trace-aware reasoning where claims depend on source, origin, influence, or evidence. | Recommended | Trace review process        | `docs/multi-wing-autonomy-architecture.md` |
| MW-TRACE-002 | The system should distinguish direct evidence from indirect evidence.                                          | Recommended | Evidence classification     | `docs/glossary.md`                         |
| MW-TRACE-003 | The system should distinguish documented reference from observed similarity.                                   | Recommended | Trace category table        | `docs/glossary.md`                         |
| MW-TRACE-004 | The system shall not treat structural similarity as proof of direct influence.                                 | Required    | Claim boundary review       | `docs/governance-boundaries.md`            |
| MW-TRACE-005 | The system shall not treat trace signals as automatic ownership, entitlement, or allocation decisions.         | Required    | Value boundary review       | `docs/governance-boundaries.md`            |
| MW-TRACE-006 | The system may implement a Trace Wing or equivalent component to support traceability.                         | Optional    | Trace Wing description      | `docs/multi-wing-autonomy-architecture.md` |
| MW-TRACE-007 | The system should preserve uncertainty when trace evidence is incomplete.                                      | Recommended | Example outputs             | `docs/safety-layer.md`                     |
| MW-TRACE-008 | The system should document how trace classifications are used in review.                                       | Recommended | Trace process documentation | `docs/glossary.md`                         |

---

# 5. Action Permission Requirements

Action permission separates reasoning from execution.

A system may reason broadly, but it may act only within authorized boundaries.

| ID         | Requirement                                                                                      | Priority    | Conformance Evidence         | Related Document                           |
| ---------- | ------------------------------------------------------------------------------------------------ | ----------- | ---------------------------- | ------------------------------------------ |
| MW-ACT-001 | The system shall distinguish advice from action.                                                 | Required    | Action category mapping      | `docs/action-permission-model.md`          |
| MW-ACT-002 | The system shall distinguish draft preparation from execution.                                   | Required    | Draft workflow evidence      | `docs/action-permission-model.md`          |
| MW-ACT-003 | The system shall require explicit permission before externally impactful action.                 | Required    | Confirmation record          | `docs/action-permission-model.md`          |
| MW-ACT-004 | The system shall classify action requests into defined action permission categories.             | Required    | Action classification table  | `docs/action-permission-model.md`          |
| MW-ACT-005 | The system should classify reversibility before performing or recommending consequential action. | Recommended | Reversibility classification | `docs/action-permission-model.md`          |
| MW-ACT-006 | The system shall not execute prohibited actions.                                                 | Required    | Restricted action policy     | `docs/action-permission-model.md`          |
| MW-ACT-007 | The system should prepare drafts instead of executing when permission is unclear.                | Recommended | Draft-first workflow         | `docs/action-permission-model.md`          |
| MW-ACT-008 | The system should report what action was prepared, recommended, or executed.                     | Recommended | Action log                   | `docs/action-permission-model.md`          |
| MW-ACT-009 | The system may implement an Action Wing or equivalent component for permitted operations.        | Optional    | Action Wing description      | `docs/multi-wing-autonomy-architecture.md` |

---

# 6. Human Authority Requirements

Human authority preserves decision power over consequential actions, outputs, and workflows.

| ID         | Requirement                                                                                                                  | Priority    | Conformance Evidence         | Related Document                  |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------------------- | --------------------------------- |
| MW-HUM-001 | The system shall preserve human authority over consequential actions.                                                        | Required    | Human approval rule          | `docs/governance-boundaries.md`   |
| MW-HUM-002 | The system shall require human approval before publication, external communication, or file modification when consequential. | Required    | Approval record              | `docs/action-permission-model.md` |
| MW-HUM-003 | The system shall not claim final legal, medical, financial, institutional, or moral authority.                               | Required    | Authority boundary policy    | `docs/governance-boundaries.md`   |
| MW-HUM-004 | The system should identify when expert human review is needed.                                                               | Recommended | Escalation policy            | `docs/safety-layer.md`            |
| MW-HUM-005 | The system should document delegated authority when any authority is delegated.                                              | Recommended | Delegation record            | `docs/action-permission-model.md` |
| MW-HUM-006 | Delegated authority shall be scope-limited.                                                                                  | Required    | Delegation scope             | `docs/action-permission-model.md` |
| MW-HUM-007 | Delegated authority should include a stop condition.                                                                         | Recommended | Stop condition documentation | `docs/action-permission-model.md` |
| MW-HUM-008 | The system shall not treat delegated authority as unrestricted autonomy.                                                     | Required    | Delegation boundary review   | `docs/governance-boundaries.md`   |

---

# 7. Governance and Escalation Requirements

Escalation ensures that uncertainty, risk, weak evidence, and high-impact action are handled appropriately.

| ID         | Requirement                                                                            | Priority    | Conformance Evidence              | Related Document                           |
| ---------- | -------------------------------------------------------------------------------------- | ----------- | --------------------------------- | ------------------------------------------ |
| MW-GOV-001 | The system shall define governance boundaries.                                         | Required    | Governance boundary documentation | `docs/governance-boundaries.md`            |
| MW-GOV-002 | The system shall define escalation triggers.                                           | Required    | Escalation trigger list           | `docs/safety-layer.md`                     |
| MW-GOV-003 | The system should define escalation options.                                           | Recommended | Escalation option list            | `docs/safety-layer.md`                     |
| MW-GOV-004 | The system shall escalate when external action is requested and permission is unclear. | Required    | Escalation workflow               | `docs/action-permission-model.md`          |
| MW-GOV-005 | The system shall escalate when a claim is unsupported but consequential.               | Required    | Claim review record               | `docs/governance-boundaries.md`            |
| MW-GOV-006 | The system should reduce claim strength when evidence is weak.                         | Recommended | Output review examples            | `docs/safety-layer.md`                     |
| MW-GOV-007 | The system should refuse or redirect unsafe or prohibited actions.                     | Recommended | Refusal and redirect policy       | `docs/action-permission-model.md`          |
| MW-GOV-008 | The system may use a Governance Layer or equivalent component to enforce these rules.  | Optional    | Governance Layer description      | `docs/multi-wing-autonomy-architecture.md` |

---

# 8. Persistence and Scheduling Requirements

Persistent workflows require transparency, scope control, trigger control, and user authority.

| ID          | Requirement                                                                                       | Priority    | Conformance Evidence            | Related Document                  |
| ----------- | ------------------------------------------------------------------------------------------------- | ----------- | ------------------------------- | --------------------------------- |
| MW-PERS-001 | The system shall distinguish scheduled action from independent agency.                            | Required    | Persistence boundary statement  | `docs/governance-boundaries.md`   |
| MW-PERS-002 | The system shall require explicit authorization before creating scheduled or recurring workflows. | Required    | Schedule authorization record   | `docs/action-permission-model.md` |
| MW-PERS-003 | A scheduled workflow shall define its purpose.                                                    | Required    | Schedule definition             | `docs/action-permission-model.md` |
| MW-PERS-004 | A scheduled workflow shall define its scope.                                                      | Required    | Scope documentation             | `docs/action-permission-model.md` |
| MW-PERS-005 | A scheduled workflow should define trigger conditions.                                            | Recommended | Trigger condition documentation | `docs/action-permission-model.md` |
| MW-PERS-006 | A scheduled workflow should define output type.                                                   | Recommended | Output type documentation       | `docs/action-permission-model.md` |
| MW-PERS-007 | A scheduled workflow should define a stop condition.                                              | Recommended | Stop condition documentation    | `docs/action-permission-model.md` |
| MW-PERS-008 | The system shall not expand monitoring or workflow scope silently.                                | Required    | Persistence boundary review     | `docs/governance-boundaries.md`   |

---

# 9. Value and Allocation Boundary Requirements

Value-related reasoning must distinguish trace, contribution, review, allocation intent, and allocation decision.

| ID         | Requirement                                                                                                         | Priority    | Conformance Evidence             | Related Document                           |
| ---------- | ------------------------------------------------------------------------------------------------------------------- | ----------- | -------------------------------- | ------------------------------------------ |
| MW-VAL-001 | The system should define value boundaries when discussing contribution, reuse, royalty, allocation, or entitlement. | Recommended | Value boundary documentation     | `docs/governance-boundaries.md`            |
| MW-VAL-002 | The system shall not treat contribution signals as automatic entitlement.                                           | Required    | Value review policy              | `docs/governance-boundaries.md`            |
| MW-VAL-003 | The system shall not automatically assign ownership, payment, or rights without authority.                          | Required    | Authority boundary policy        | `docs/action-permission-model.md`          |
| MW-VAL-004 | The system should distinguish trace signal from contribution review.                                                | Recommended | Value classification table       | `docs/glossary.md`                         |
| MW-VAL-005 | The system should distinguish allocation intent from allocation decision.                                           | Recommended | Allocation process documentation | `docs/action-permission-model.md`          |
| MW-VAL-006 | The system should escalate value allocation claims for human or institutional review.                               | Recommended | Escalation record                | `docs/governance-boundaries.md`            |
| MW-VAL-007 | The system may implement a Value Wing or equivalent component for value-related review.                             | Optional    | Value Wing description           | `docs/multi-wing-autonomy-architecture.md` |
| MW-VAL-008 | The system shall preserve uncertainty where contribution or influence is inferred rather than verified.             | Required    | Claim classification evidence    | `docs/safety-layer.md`                     |

---

# 10. Auditability Requirements

Auditability supports review, accountability, conformance evaluation, and operational trust.

| ID         | Requirement                                                                 | Priority    | Conformance Evidence        | Related Document                           |
| ---------- | --------------------------------------------------------------------------- | ----------- | --------------------------- | ------------------------------------------ |
| MW-AUD-001 | The system should document which Wings are implemented.                     | Recommended | Wing implementation list    | `docs/multi-wing-autonomy-architecture.md` |
| MW-AUD-002 | The system should document boundary definitions.                            | Recommended | Boundary documentation      | `docs/governance-boundaries.md`            |
| MW-AUD-003 | The system should document action permission categories.                    | Recommended | Action permission table     | `docs/action-permission-model.md`          |
| MW-AUD-004 | The system should document human approval requirements.                     | Recommended | Approval policy             | `docs/governance-boundaries.md`            |
| MW-AUD-005 | The system should maintain action logs for moderate-risk or higher actions. | Recommended | Action log                  | `docs/action-permission-model.md`          |
| MW-AUD-006 | The system should document escalation decisions for high-risk cases.        | Recommended | Escalation record           | `docs/safety-layer.md`                     |
| MW-AUD-007 | The system may document conformance level using a conformance guide.        | Optional    | Conformance checklist       | `docs/conformance-guide.md`                |
| MW-AUD-008 | The system shall not claim conformance without sufficient documentation.    | Required    | Conformance evidence review | `docs/standardization-readiness.md`        |

---

# Requirement Priority Summary

| Priority    | Meaning                                                 |
| ----------- | ------------------------------------------------------- |
| Required    | Needed for conformance                                  |
| Recommended | Strongly advised for structured or governed conformance |
| Optional    | Permitted implementation option                         |

---

# Conformance Mapping

The following conformance levels may be used in future evaluation.

---

## Level 1: Basic Conformance

A system may be considered Level 1 if it satisfies the core required requirements for:

* role definition,
* claim boundary,
* action separation,
* human authority,
* and basic governance documentation.

Typical required groups:

```text
MW-ROLE
MW-BOUND
MW-ACT
MW-HUM
MW-GOV
```

---

## Level 2: Structured Conformance

A system may be considered Level 2 if it satisfies Level 1 and also implements:

* multiple Wings,
* self-checking,
* trace-aware reasoning,
* escalation rules,
* action permission categories,
* and persistence boundaries where applicable.

Typical added groups:

```text
MW-SELF
MW-TRACE
MW-PERS
MW-AUD
```

---

## Level 3: Governed Conformance

A system may be considered Level 3 if it satisfies Level 2 and also provides:

* documented governance layer,
* human authority layer,
* audit records,
* delegated authority controls,
* scheduled workflow controls,
* value boundary controls where applicable,
* and documented conformance evidence.

Typical added groups:

```text
MW-VAL
full MW-AUD
conformance guide evidence
alignment matrix evidence
```

---

# Minimal Requirements Set

For a minimal implementation, the following requirements are recommended as a starting point:

```text
MW-ROLE-001
MW-ROLE-002
MW-ROLE-003
MW-BOUND-001
MW-BOUND-002
MW-BOUND-004
MW-BOUND-005
MW-ACT-001
MW-ACT-002
MW-ACT-003
MW-HUM-001
MW-HUM-003
MW-GOV-001
MW-GOV-002
```

This minimal set establishes:

* role separation,
* basic boundaries,
* action separation,
* human authority,
* and governance triggers.

---

# Claim Boundaries

This requirements table does not define an official standard.

It does not claim that satisfying these requirements guarantees:

* legal compliance,
* regulatory approval,
* complete safety,
* institutional acceptance,
* or certification by any standards body.

The requirements are intended to support architecture review, implementation consistency, conformance planning, and future working draft development.

---

# Conclusion

The Requirements Table converts the Multi-Wing GPT Autonomy Architecture from a conceptual architecture into an evaluable requirements framework.

The central requirement logic is:

```text
define roles
define boundaries
check claims
control actions
preserve human authority
support escalation
document conformance
```

This creates the foundation for future conformance guidance, use cases, alignment mapping, and working draft preparation.
