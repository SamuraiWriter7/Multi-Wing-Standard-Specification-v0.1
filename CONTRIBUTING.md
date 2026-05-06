# Contributing to Multi-Wing Standard Specification

Thank you for your interest in contributing to the **Multi-Wing Standard Specification**.

This repository is intended to evolve as an open specification for distributed intelligence systems based on role-specialized Wings, Kazene-style coordination, and trace-aware interoperability.

Because this is a specification repository rather than a product repository, contributions should prioritize:

- clarity
- consistency
- interoperability
- testability
- extensibility
- accountability

---

## Scope of Contributions

Contributions are welcome in areas such as:

- terminology refinement
- specification clarity
- schema design and correction
- example improvements
- interoperability mappings
- conformance language
- governance extensions
- security analysis
- failure-mode analysis
- editorial cleanup

This repository accepts both conceptual and technical contributions, as long as they improve the standard in a way that is:

- precise
- reviewable
- implementation-relevant
- consistent with the repository's architectural direction

---

## Before You Contribute

Please read the following documents first:

1. `README.md`
2. `docs/one-page-overview.md`
3. `spec/multi-wing-standard-specification-v0.1.md`

Before proposing a major change, make sure you understand:

- the three-layer architecture
- the role of the Wing Type System
- the purpose of Kazene coordination principles
- the repository's interoperability goals
- the intended scope of v0.1

---

## Types of Contributions

### 1. Editorial Contributions
Use this for:

- grammar fixes
- formatting cleanup
- wording clarification
- typo correction
- improved readability

These changes should preserve technical meaning.

### 2. Specification Clarifications
Use this for:

- ambiguous definitions
- unclear lifecycle behavior
- missing normative language
- inconsistent terminology
- incomplete conformance requirements

These changes should reduce interpretive ambiguity.

### 3. Schema and Example Contributions
Use this for:

- JSON Schema fixes
- example object corrections
- validation alignment
- profile-specific examples
- message model improvements

These changes should improve machine readability and implementation utility.

### 4. Extension Proposals
Use this for:

- new profiles
- new registries
- new trace hooks
- transport mappings
- governance modules
- auditable workflow patterns

These changes should be proposed carefully and should not destabilize the core specification without strong justification.

---

## Contribution Principles

Contributors are expected to follow these principles:

### Keep the core minimal
Multi-Wing v0.1 is intentionally small enough to remain implementable.  
Do not overload the base specification with premature complexity.

### Prefer interoperability over elegance alone
A beautiful abstraction is valuable, but a reusable standard requires stable boundaries, predictable behavior, and clear mappings.

### Separate core from extension
If a proposal is useful but not universally required, consider placing it in an extension document or future version rather than the v0.1 core.

### Preserve layered architecture
Changes should respect the distinction between:

- Structure Layer
- Protocol Layer
- Execution Layer

### Design for auditability
Where relevant, proposals should make behavior more inspectable, attributable, and testable.

---

## How to Contribute

### Small Changes
For small fixes:

1. Fork the repository
2. Create a branch
3. Make the change
4. Submit a pull request

### Larger Changes
For substantial changes:

1. Open an issue first
2. Explain the problem
3. Describe the proposed change
4. Clarify whether it affects:
   - the core model
   - schemas
   - interoperability
   - conformance
   - governance
5. Wait for discussion before opening a large pull request

This helps keep the specification coherent.

---

## Pull Request Guidelines

Please keep pull requests:

- focused
- small when possible
- well-described
- traceable to an issue when appropriate

Include in your pull request description:

- what changed
- why it changed
- whether the change is normative or informative
- whether schemas or examples were updated
- whether conformance implications exist

---

## Normative vs Informative Changes

When proposing changes, please indicate whether they are:

### Normative
Changes that affect implementation behavior, conformance, required fields, lifecycle expectations, or protocol semantics.

### Informative
Changes that improve explanation, examples, rationale, background, or editorial quality without altering implementation requirements.

This distinction is especially important in a standards-oriented repository.

---

## Style Guidelines

Please follow these style preferences:

- Use clear technical English
- Prefer consistent terminology
- Avoid unnecessary metaphor inside normative sections
- Keep section titles stable unless a rename is necessary
- Use short paragraphs where possible
- Prefer explicit definitions over implied meaning

### Normative language
Use normative language carefully:

- **MUST**
- **SHOULD**
- **MAY**

Avoid accidental use of strong normative language in purely explanatory text.

---

## File-Specific Notes

### `spec/`
Canonical specification text belongs here.  
Changes should be deliberate and reviewed carefully.

### `docs/`
Supporting explanations, background notes, and architectural commentary belong here.  
This is the right place for expansion that does not need to be normative.

### `schemas/`
Schema files should be machine-valid and aligned with the current draft.

### `examples/`
Examples should be realistic, minimal where possible, and consistent with schema definitions.

---

## Validation

Where applicable, please validate:

- JSON Schemas
- example files
- internal links
- file references
- version labels

If repository automation is available via GitHub Actions, ensure that your changes do not break validation workflows.

---

## Versioning Expectations

This repository uses draft-stage versioning.

That means:

- changes may still be substantial
- backward compatibility is not yet guaranteed
- conceptual stability matters more than premature freeze

Even so, avoid introducing unnecessary breaking changes unless they improve the specification in a meaningful way.

---

## What Not to Submit

Please avoid opening pull requests that:

- turn the specification into a vendor-specific product design
- collapse the layered architecture into a single stack
- add economic settlement logic directly into the v0.1 core
- introduce speculative mechanisms without implementation value
- replace clear definitions with purely rhetorical language
- broaden scope without describing conformance impact

---

## Discussions and Issues

Please use Issues for:

- bugs in the specification
- ambiguity reports
- requests for clarification
- schema inconsistencies
- interoperability concerns
- security observations
- extension proposals

When possible, point to specific files and sections.

---

## Attribution

Constructive contributions may be acknowledged through repository history, issue discussions, and citation metadata where appropriate.

If provenance-aware contribution tracking is formalized in future versions, this repository may expand its attribution model accordingly.

---

## Code of Collaboration

Contribute in a way that improves the shared structure.

That means:

- argue clearly
- critique precisely
- revise openly
- avoid territorial behavior
- prioritize coherence over ownership reflex

A standard becomes useful not when it is defended as a possession, but when it becomes precise enough for others to build with.

---

## Final Note

Multi-Wing is being developed as an open standardization effort for distributed intelligence.

Contributions are welcome not because everything is undecided, but because careful refinement is part of how standards mature.

Thank you for helping make the specification clearer, stronger, and more interoperable.
