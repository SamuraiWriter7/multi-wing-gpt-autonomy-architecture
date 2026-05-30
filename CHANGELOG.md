# Changelog

All notable changes to this project will be documented in this file.

This project follows a simple release history format focused on architectural additions, documentation updates, governance-related changes, and standardization-oriented development.

---

## [0.2.0-candidate] - 2026-05-31

### Added

* Added `docs/standardization-readiness.md`

  * Defines how the Multi-Wing GPT Autonomy Architecture can be positioned for future standardization-oriented development.
  * Translates the architecture into standardization-facing language, including purpose, scope, terminology, architecture model, requirements structure, conformance model, and readiness assessment.
  * Clarifies that the repository is not an official ISO, IEC, IEEE, regulatory, or institutional standard.

* Added `docs/glossary.md`

  * Defines key terms used across the repository.
  * Stabilizes terminology such as Wing, Structural Autonomy, Governance Layer, Human Authority Layer, Action Boundary, Traceability, Claim Boundary, Value Boundary, and Action Permission categories.
  * Provides the terminology foundation for requirements, conformance, use cases, alignment mapping, and working draft preparation.

* Added `docs/requirements-table.md`

  * Converts the architecture into standardization-oriented requirements using `shall`, `should`, and `may`.
  * Organizes requirements into role separation, self-checking, boundary control, traceability, action permission, human authority, governance and escalation, persistence and scheduling, value and allocation boundaries, and auditability.
  * Establishes a requirements framework that can support future conformance review.

* Added `docs/conformance-guide.md`

  * Defines repository-level conformance guidance for the Multi-Wing GPT Autonomy Architecture.
  * Introduces three candidate conformance levels:

    * Level 1 — Basic Conformance
    * Level 2 — Structured Conformance
    * Level 3 — Governed Conformance
  * Provides evidence types, assessment process, gap assessment template, conformance self-assessment template, and conformance statement templates.
  * Clarifies that conformance does not imply official certification, regulatory approval, legal compliance, or complete AI safety.

* Added `docs/use-cases.md`

  * Defines representative use cases for the architecture.
  * Covers documentation and repository support, research and analysis support, tool-using assistants, scheduled review workflows, multi-agent reasoning systems, public-facing publication assistants, trace-aware attribution review, value and contribution review, human-in-the-loop operational assistants, and high-risk boundary examples.
  * Maps each use case to relevant Wings, control layers, risks, required controls, action permission categories, and likely conformance levels.

* Added `docs/alignment-matrix.md`

  * Provides conceptual and architectural alignment mapping with AI management, AI risk management, system and software quality, transparency of autonomous systems, fail-safe design, human-in-the-loop governance, AI agent governance, accountability, and auditability areas.
  * Positions Multi-Wing as a complementary structural architecture, not as a replacement for existing standards.
  * Clarifies that the repository does not claim formal compliance, certification, endorsement, or equivalence with any ISO, IEC, IEEE, regulatory, or institutional standard.

* Added `docs/working-draft-wd0.md`

  * Provides a Working Draft 0 version of the architecture.
  * Consolidates the repository into a formal specification-style structure, including scope, terms and definitions, normative language, core principles, architecture model, autonomy stages, Wing requirements, governance boundary requirements, action permission requirements, human authority requirements, traceability, auditability, escalation, conformance, use cases, implementation guidance, and annexes.
  * Clarifies that WD0 is an internal candidate working draft for architectural review and standardization-oriented development.

### Updated

* Updated `README.md`

  * Added the standardization readiness documents to `Repository Structure`.
  * Divided documents into:

    * Core Architecture Documents
    * Standardization Readiness Documents
  * Added descriptions for all standardization readiness documents under `Key Documents`.
  * Added a two-path recommended reading order:

    * Path 1: Architecture Understanding
    * Path 2: Standardization Readiness
  * Added a Standardization Readiness Flow.
  * Added a Conformance Summary.
  * Added a Standardization Position section.
  * Updated the project status to reflect foundational architecture plus standardization-oriented readiness documentation.

### Core Concepts Added

* Standardization readiness
* Working Draft 0
* Normative language
* Requirements table
* Conformance levels
* Conformance evidence
* Gap assessment
* Use case profiles
* Alignment matrix
* Conceptual alignment
* Complementary standardization mapping
* Basic Conformance
* Structured Conformance
* Governed Conformance
* Role separation requirements
* Self-checking requirements
* Boundary control requirements
* Traceability requirements
* Action permission requirements
* Human authority requirements
* Persistence and scheduling requirements
* Value and allocation boundary requirements
* Auditability requirements

### Notes

This candidate release extends the repository from a core architectural specification into a standardization-oriented documentation set.

The project remains a candidate structural architecture for governed autonomy in GPT-based and agentic AI systems.

This release does not claim:

```text
ISO status
IEC status
IEEE status
regulatory status
institutional certification
formal compliance with any existing standard
legal authority
complete AI safety
```

The core standardization principle introduced in this release is:

```text
Capability requires boundaries.
Autonomy requires governance.
Conformance requires evidence.
```

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
