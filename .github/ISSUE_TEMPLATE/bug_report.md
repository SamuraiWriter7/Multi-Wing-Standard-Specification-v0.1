---
name: Bug report
about: Report a bug, inconsistency, schema mismatch, or validation failure in the Multi-Wing specification repository
title: "[Bug] "
labels: bug
assignees: ""
---

# Bug Report

## Summary

Provide a short description of the problem.

Example:

- schema validation fails unexpectedly
- specification text contradicts the schema
- example file does not conform to the current draft
- terminology is inconsistent across documents

---

## Affected File(s)

List the relevant file(s), for example:

- `spec/multi-wing-standard-specification-v0.1.md`
- `schemas/message-envelope.schema.json`
- `examples/shared-context.sample.json`
- `docs/wing-type-system.md`

---

## Section / Object / Line Reference

If applicable, point to the exact section, field, or line area.

Example:

- Section 7.3 Message Types
- `trace_refs`
- `properties.review_state`
- lines around the definition of `composite`

---

## Type of Problem

Select one or more that apply:

- [ ] Specification text is unclear
- [ ] Specification text contradicts another file
- [ ] Schema is invalid
- [ ] Example does not validate
- [ ] Required field behavior is ambiguous
- [ ] Conformance language is inconsistent
- [ ] Version label mismatch
- [ ] Other

---

## Current Behavior

Describe what currently happens.

Example:

- validation fails with a missing required property
- the example uses a field not defined in the schema
- a required behavior is described differently in two documents

---

## Expected Behavior

Describe what you expected instead.

---

## Reproduction Steps

If relevant, describe how to reproduce the issue.

Example:

1. Open `schemas/trace-reference.schema.json`
2. Validate `examples/trace-reference.sample.json`
3. Observe the validation error

If this is a documentation inconsistency rather than a runtime issue, describe how the inconsistency appears.

---

## Validation Output / Error Message

Paste any relevant validation output, stack trace, or error message.

```text
Paste output here

Proposed Fix (Optional)

If you already have a suggestion, describe it here.

Examples:

rename a field
update an enum
clarify normative language
align example data with the current schema
Normative Impact

Does this issue affect the normative meaning of the specification?

 Yes
 No
 Not sure

If yes, briefly explain how.

Additional Context

Add any other context that may help review the issue.


---

## `.github/ISSUE_TEMPLATE/feature_request.md`

```md
---
name: Feature request
about: Propose a new capability, profile, example, schema improvement, or interoperability enhancement for the Multi-Wing specification
title: "[Feature] "
labels: enhancement
assignees: ""
---

# Feature Request

## Summary

Provide a concise description of the proposed feature or enhancement.

Examples:

- add a new interoperability profile
- introduce a new optional Wing trait
- add a new example workflow
- expand schema support for trace signatures
- improve guidance for edge / real-time execution

---

## Motivation

Why is this feature needed?

Explain the problem it solves, the limitation it addresses, or the implementation value it provides.

---

## Proposed Area

Which part of the repository does this affect?

- [ ] `spec/`
- [ ] `docs/`
- [ ] `schemas/`
- [ ] `examples/`
- [ ] `conformance`
- [ ] `security`
- [ ] `interoperability`
- [ ] `governance`
- [ ] other

---

## Proposal

Describe the feature in concrete terms.

Try to answer:

- What should be added or changed?
- How should it behave?
- Is it core or optional?
- Is it normative or informative?

---

## Expected Benefit

What improves if this feature is adopted?

Examples:

- better interoperability
- clearer conformance
- stronger auditability
- easier implementation
- improved extensibility
- better profile separation

---

## Scope

How broad is the proposed change?

- [ ] Small editorial enhancement
- [ ] Small schema enhancement
- [ ] New example or documentation addition
- [ ] Moderate protocol / model enhancement
- [ ] Significant architectural extension

---

## Compatibility Considerations

Does this proposal preserve compatibility with v0.1 core?

- [ ] Yes
- [ ] No
- [ ] Not sure

If compatibility may be affected, explain how.

---

## Core or Extension?

Should this proposal belong to:

- [ ] Core v0.1
- [ ] Future v0.x revision
- [ ] Optional profile
- [ ] Separate extension document

Please explain your choice.

---

## Alternatives Considered

Describe any alternatives you considered.

This is especially useful if the proposal introduces new structure rather than refining existing structure.

---

## Example (Optional)

Provide an example of how the feature might look in practice.

```json
{
  "example": "optional"
}

Or describe the example in prose.

Additional Context

Add any supporting context, related documents, or implementation observations.


---

## `.github/ISSUE_TEMPLATE/spec_change.md`

```md
---
name: Specification change
about: Propose a substantive change to the normative structure, terminology, lifecycle, schema expectations, or conformance language of the Multi-Wing standard
title: "[Spec Change] "
labels: spec-change
assignees: ""
---

# Specification Change Proposal

## Summary

Provide a concise summary of the proposed specification change.

This template is intended for changes that affect the meaning, shape, or expected behavior of the Multi-Wing standard.

Examples:

- change a core term definition
- revise the task lifecycle
- alter required message fields
- add or remove a core Wing type
- change conformance requirements
- refine profile boundaries

---

## Problem Statement

What is the current problem?

Describe the ambiguity, inconsistency, limitation, or structural weakness in the current draft.

---

## Affected Specification Area

Select the primary area affected by the proposal.

- [ ] Overview / Scope
- [ ] Terminology
- [ ] Core Model
- [ ] Wing Type System
- [ ] Coordination Principles
- [ ] Interaction Protocol
- [ ] Message Schema
- [ ] Shared Context
- [ ] Trace and Provenance
- [ ] Interoperability Profiles
- [ ] Security Considerations
- [ ] Conformance
- [ ] Extensibility
- [ ] Other

---

## Current State

Describe the current specification behavior or wording.

Where possible, reference exact sections or files.

Examples:

- Section 4.9 Composite Wing
- `schemas/message-envelope.schema.json`
- `docs/kazene-coordination-principles.md`

---

## Proposed Change

Describe the proposed new behavior, wording, or structure.

Be as concrete as possible.

---

## Rationale

Why is this change better?

Explain in terms such as:

- architectural coherence
- interoperability
- testability
- clarity
- auditability
- conformance stability
- implementation practicality

---

## Normative Impact

What kind of impact does this change have?

- [ ] Informative only
- [ ] Normative clarification
- [ ] Normative behavioral change
- [ ] Schema-impacting change
- [ ] Conformance-impacting change
- [ ] Profile-impacting change

Please explain briefly.

---

## Backward Compatibility

Does this proposal preserve backward compatibility?

- [ ] Yes
- [ ] No
- [ ] Partially
- [ ] Not sure

If not, describe the break clearly.

---

## Required File Updates

Which files would likely need to change?

- [ ] `README.md`
- [ ] `spec/multi-wing-standard-specification-v0.1.md`
- [ ] `docs/architecture-overview.md`
- [ ] `docs/wing-type-system.md`
- [ ] `docs/kazene-coordination-principles.md`
- [ ] `docs/relationship-to-mcp-a2a.md`
- [ ] `schemas/wing-type.schema.json`
- [ ] `schemas/message-envelope.schema.json`
- [ ] `schemas/shared-context.schema.json`
- [ ] `schemas/trace-reference.schema.json`
- [ ] `examples/`
- [ ] `CHANGELOG.md`
- [ ] other

---

## Proposed Conformance Interpretation

If adopted, how should implementers interpret this change?

Examples:

- as a new MUST requirement
- as a SHOULD-level clarification
- as an optional profile-specific feature
- as a non-normative explanatory improvement

---

## Example Before / After (Optional)

### Before

```text
Describe the current form here
After
Describe the proposed form here
Migration Notes (Optional)

If the proposal changes current behavior, describe how existing implementations or examples should migrate.

Additional Notes

Add any additional reasoning, implementation feedback, or related discussion.
