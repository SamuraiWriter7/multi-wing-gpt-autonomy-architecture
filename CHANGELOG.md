# Changelog

All notable changes to this project will be documented in this file.

This project follows a simple release history format focused on architectural additions, documentation updates, and governance-related changes.

---

## [0.1.0] - 2026-05-30

### Added

* Added `docs/autonomy-stage-model.md`

  * Defines the staged development model of structural autonomy for Multi-Wing GPT systems.
  * Distinguishes between single-response GPT behavior, role-fixed operation, self-checking, multi-wing coordination, external action capability, scheduled workflows, and governed structural autonomy.
  * Establishes the developmental map for the repository.

* Added `docs/multi-wing-autonomy-architecture.md`

  * Defines the structural arrangement of role-based GPTs, reasoning modules, and functional layers.
  * Introduces the Defense Wing, Reflection Wing, Structure Wing, Trace Wing, Value Wing, Action Wing, Balance Layer, Governance Layer, and Human Authority Layer.
  * Provides the core architecture for distributed, governed GPT autonomy.

* Added `docs/safety-layer.md`

  * Defines the Safety Layer for keeping structural autonomy bounded, stable, and reviewable.
  * Covers defensive review, reflection review, boundary control, claim control, and action permission checks.
  * Clarifies how safety prevents unsafe compliance, role drift, overclaim, and unauthorized action.

* Added `docs/governance-boundaries.md`

  * Defines governance boundaries for role, claim, evidence, action, authority, value, and persistence.
  * Clarifies the distinction between advice and action, trace and proof, contribution and entitlement, scheduling and independent agency.
  * Preserves human authority as system capability increases.

* Added `docs/action-permission-model.md`

  * Defines when a GPT-based system may advise, prepare drafts, provide instructions, perform confirmed actions, operate under delegated authority, run scheduled workflows, or refuse restricted actions.
  * Separates reasoning from execution.
  * Establishes permission-based action control for Multi-Wing GPT systems.

### Updated

* Updated `README.md`

  * Added the five core documents to `Repository Structure`.
  * Added descriptions for each document under `Key Documents`.
  * Added a recommended reading order.
  * Added a document relationship section explaining how the five documents work together.

### Core Concepts Introduced

* Structural autonomy
* Multi-Wing GPT systems
* Role-fixed GPT operation
* Self-checking GPT behavior
* Multi-wing coordination
* Governed structural autonomy
* Defense Layer
* Reflection Layer
* Safety Layer
* Governance Boundaries
* Action Permission Model
* Human Authority Layer
* Claim Boundary
* Evidence Boundary
* Action Boundary
* Value Boundary
* Persistence Boundary

### Notes

This initial release defines the conceptual and architectural foundation for governed structural autonomy in Multi-Wing GPT systems.

The project does not claim that GPT systems possess consciousness, independent will, legal authority, or self-directed moral agency.

The core principle remains:

```text
Autonomy is not freedom from structure.
Autonomy is structure refined into governed operation.
```
