# Wing Composition Rules

## Overview

This document defines the **composition rules** for Wings in the **Multi-Wing Standard Specification**.

The purpose of Wing Composition Rules is to make explicit how multiple Wings may be combined, sequenced, nested, or constrained without collapsing the architecture into an opaque monolith.

A Wing Type System is not sufficient by itself.  
An architecture also needs rules for:

- which Wing combinations are structurally sound
- which combinations are risky
- which combinations require review or governance safeguards
- which combinations should be avoided or prohibited

This document therefore describes how typed Wings may form larger coordination structures while preserving:

- role clarity
- reviewability
- trace continuity
- bounded authority
- interoperability

---

## 1. Purpose

Wing Composition Rules exist to answer a practical architectural question:

> Once Wings are typed, how may they be safely combined?

Without explicit composition rules, a Multi-Wing system risks drifting into one of two failure modes:

- over-fragmentation, where Wings are too isolated to cooperate effectively
- hidden recombination, where nominally separate Wings act as one untyped control center

The purpose of this document is to ensure that composition remains:

- legible
- bounded
- auditable
- coordination-compatible

---

## 2. Scope

This document defines:

- composition principles
- valid and recommended Wing pairings
- risky pairings
- guarded compositions
- composite Wing constraints
- sequencing rules
- review expectations by composition pattern
- governance implications of composition

This document does **not** define:

- implementation-specific orchestration code
- runtime scheduling algorithms
- a complete registry of all future Wing combinations
- domain-specific optimization strategies

These rules are architectural and normative in intent, not implementation-prescriptive in detail.

---

## 3. Core Assumption

A Wing is not meaningful merely because it is separately named.

A composition is considered structurally valid only when the participating Wings remain:

- functionally distinguishable
- operationally attributable
- review-compatible
- context-bounded
- trace-compatible where relevant

The central assumption is:

> **Composition is valid only when combining Wings increases coordination quality without destroying role clarity.**

---

## 4. Composition Principles

### 4.1 Principle of Explicit Role Boundaries

Any composed structure MUST preserve the distinguishability of participating roles.

A system MUST be able to answer:

- which Wing generated the artifact
- which Wing reviewed it
- which Wing routed it
- which Wing finalized it
- which Wing preserved or altered trace information

If these distinctions disappear in practice, the composition has become structurally opaque.

---

### 4.2 Principle of Non-Silent Authority Aggregation

A composition MUST NOT silently combine multiple critical authorities into one path without explicit declaration.

Critical authorities include:

- generation authority
- verification authority
- routing authority
- finalization authority
- governance authority

Such combinations MAY exist, but if they do, they SHOULD be declared explicitly and subject to stronger review or governance conditions.

---

### 4.3 Principle of Review Reachability

A valid composition SHOULD preserve reachable review paths for non-trivial outputs.

If a composition structurally prevents review, the system SHOULD either:

- restrict the authority of the resulting outputs, or
- explicitly declare the composition as non-reviewed and provisional

Review reachability is more important than nominal review capability.

---

### 4.4 Principle of Trace Continuity

If any composed Wings operate on trace-relevant artifacts, the composition SHOULD preserve trace continuity across the composition boundary.

Composition MUST NOT silently erase origin, revision, or contribution references if the system claims trace-aware behavior.

---

### 4.5 Principle of Bounded Composition

Composition SHOULD remain bounded in complexity.

If too many core roles are absorbed into one composite structure, the system risks reintroducing monolithic intelligence under a distributed label.

---

## 5. Composition Categories

Multi-Wing recognizes four high-level composition categories:

1. **Sequential Composition**
2. **Parallel Composition**
3. **Nested Composition**
4. **Composite Wing Composition**

---

## 6. Sequential Composition

### 6.1 Definition

Sequential Composition occurs when one Wing hands task responsibility or artifact flow to another in an ordered path.

Typical examples:

- Generation -> Verification
- Memory -> Generation
- Routing -> Generation -> Verification
- Verification -> Revision -> Verification

### 6.2 Validity Conditions

Sequential Composition is valid when:

1. each stage has a role-relevant purpose
2. the handoff is attributable
3. the next stage can inspect enough context to act meaningfully
4. review or escalation conditions are not bypassed silently

### 6.3 Recommended Sequential Patterns

Recommended patterns include:

- `memory -> generation`
- `generation -> verification`
- `routing -> generation`
- `routing -> verification`
- `verification -> revision`
- `routing -> governance`
- `governance -> finalization-check`

These patterns generally improve coordination legibility.

---

## 7. Parallel Composition

### 7.1 Definition

Parallel Composition occurs when multiple Wings act on the same task segment or artifact space concurrently or near-concurrently.

Examples:

- two Verification Wings performing different checks
- multiple Generation Wings producing alternative candidate drafts
- a Memory Wing and Governance Wing enriching context in parallel

### 7.2 Validity Conditions

Parallel Composition is valid when:

1. role overlap is intentional
2. outputs remain attributable
3. resolution logic exists for conflicts or divergences
4. shared context mutation is controlled
5. review or routing can interpret multiple outputs coherently

### 7.3 Risks

Parallel Composition becomes risky when:

- outputs overwrite each other without trace
- conflicting review results have no resolution path
- shared context becomes non-deterministic
- the system treats plurality as consensus without explicit evaluation

Parallelism is powerful, but it requires reconciliation discipline.

---

## 8. Nested Composition

### 8.1 Definition

Nested Composition occurs when a Wing or Wing cluster operates as a substructure inside a larger coordination field.

Examples:

- a specialized review cluster acting as one Verification unit externally
- a domain-specific Memory subgraph behind a single Memory-facing interface
- a composite expert module exposed through one Interface Wing

### 8.2 Validity Conditions

Nested Composition is valid when:

1. the outer coordination surface remains clear
2. inner composition does not falsify the declared outer role
3. accountability can still be reconstructed if necessary
4. escalation and failure signals can cross the nested boundary meaningfully

### 8.3 Guidance

Nested structures are acceptable when they improve modularity.  
They become problematic when nesting is used to hide effective monoliths behind a typed facade.

---

## 9. Composite Wing Composition

### 9.1 Definition

A **Composite Wing** is a declared Wing that combines multiple primary roles under one controlled unit.

Composite Wings are allowed in Multi-Wing, but they require stricter discipline than ordinary pairings.

### 9.2 Minimum Declaration Requirements

A Composite Wing MUST declare:

- component roles
- precedence or ordering rules
- any shared-context access implications
- any trace-preservation implications
- any review limitations introduced by the composition

### 9.3 Recommended Use Cases

Composite Wings are most reasonable when:

- latency constraints require tighter local coupling
- two roles are naturally adjacent and low-risk
- the composition remains small and legible
- the system explicitly documents the tradeoff

Examples:

- lightweight `generation + self-check`
- `routing + interface` for boundary mediation
- `memory + trace-preservation support`

### 9.4 Composite Risk Threshold

A Composite Wing SHOULD be considered high-risk when it combines three or more of the following without declared safeguards:

- generation
- verification
- routing
- governance
- finalization authority

At that point, the composite risks becoming a hidden control center.

---

## 10. Recommended Pairings

The following pairings are generally recommended.

### 10.1 Memory + Generation
Useful when retrieved context supports controlled synthesis.

### 10.2 Generation + Verification
One of the strongest standard pairings.  
Useful for reducing silent output drift.

### 10.3 Routing + Generation
Useful when routing decides when and where candidate generation should occur.

### 10.4 Routing + Verification
Useful for structured review flow and escalation management.

### 10.5 Governance + Verification
Useful when review results have policy, provenance, or accountability implications.

### 10.6 Interface + Routing
Useful for turning external requests into structured internal coordination.

### 10.7 Memory + Governance
Useful when context continuity and audit continuity must remain aligned.

These pairings generally strengthen coordination without over-concentrating authority.

---

## 11. Risky Pairings

The following pairings are not always forbidden, but they are structurally risky and SHOULD be treated carefully.

### 11.1 Generation + Finalization
Risk: candidate outputs may become final without meaningful review.

### 11.2 Routing + Finalization
Risk: path control and closure authority may concentrate silently.

### 11.3 Governance + Generation
Risk: accountability mechanisms may become content-producing authorities without proper separation.

### 11.4 Memory + Routing + Finalization
Risk: one path may dominate context, direction, and closure.

### 11.5 Verification + Finalization without Escalation Alternative
Risk: a checker becomes an unquestionable judge.

A risky pairing MAY still be valid if strong safeguards are declared.  
But risk must be visible.

---

## 12. Prohibited Silent Merges

The following composition patterns SHOULD be treated as prohibited unless explicitly declared and justified as a special profile or constrained deployment mode.

### 12.1 Silent Merge of Generation and Verification
A system MUST NOT present one hidden process as if generation and verification were separate when they are not distinguishable.

### 12.2 Silent Merge of Routing and Governance
A system MUST NOT hide the fact that coordination authority and accountability control are effectively the same path.

### 12.3 Silent Merge of Review and Finalization
A system MUST NOT imply independent review if the reviewing unit and finalizing authority are indistinguishable and undisclosed.

### 12.4 Silent Merge of Context Mutation and Audit Integrity
A system MUST NOT allow the same hidden path to rewrite context and certify its own audit trace without explicit safeguards.

The problem is not merging as such.  
The problem is **undisclosed merging that creates false structural expectations**.

---

## 13. Review Requirements by Composition Pattern

Different compositions imply different review expectations.

### 13.1 Generation-Only Path
Outputs SHOULD be treated as provisional.

### 13.2 Generation -> Verification Path
Outputs MAY be promoted in confidence after successful review.

### 13.3 Composite Generation + Self-Check
Outputs SHOULD remain lower-confidence than outputs reviewed by a distinct Verification Wing.

### 13.4 Governance-Influenced Output Path
If Governance Wings materially affect output content, additional review SHOULD be required unless the system clearly declares this as a controlled policy profile.

### 13.5 High-Concentration Composite Path
If three or more critical roles are combined, independent review or escalation SHOULD be strongly preferred.

---

## 14. Context Access Rules in Composition

Composition is not only about roles.  
It is also about context boundaries.

A composed pattern SHOULD define:

- which Wings may read shared context
- which Wings may write or append
- whether writes are gated by review
- whether any Wings may mutate policy or audit-relevant state
- whether context access expands through composition

A composition becomes more dangerous when context access grows silently across role boundaries.

---

## 15. Trace Obligations in Composition

When trace-aware behavior is claimed, a composition SHOULD preserve:

- source continuity
- revision continuity
- contributor continuity
- review continuity
- finalization authority continuity

The composition MUST NOT make it impossible in principle to determine:

- which role altered the artifact
- which role reviewed it
- which role approved its completion

Composite convenience does not justify provenance collapse.

---

## 16. Composition and Rebalancing

Wing composition interacts strongly with rebalancing.

A composition SHOULD be designed so that:

- one failing subpath can be bypassed or substituted where feasible
- review can be inserted if missing
- a composite may be decomposed under risk conditions
- routing may redirect to a less concentrated path

In Kazene terms, good composition is not only efficient.  
It is **reconfigurable under stress**.

---

## 17. Composition and Escalation

A valid composition SHOULD preserve escalation paths.

At minimum, the system should be able to answer:

- what happens if this composition cannot resolve a task?
- which Wing or external path receives the escalation?
- what context and trace are preserved when escalation occurs?

A composition without escalation semantics is brittle even if it works under ideal conditions.

---

## 18. Composition Smells

The following are useful warning signs that a composition has become unhealthy:

- one Composite Wing keeps absorbing new roles
- review exists formally but is unreachable in practice
- one Wing dominates generation, routing, and finalization across unrelated tasks
- the same path writes context, reviews outputs, and certifies provenance
- failures in one Wing repeatedly collapse the entire task lifecycle
- the system cannot explain why a given composition exists

These are not formal proof of invalidity, but they are strong design warnings.

---

## 19. Minimal Composition Conformance

A minimally conforming Multi-Wing implementation SHOULD be able to demonstrate:

1. at least one declared composition pattern
2. explicit participating Wing roles
3. at least one valid review-capable pairing or explicit provisional-only limitation
4. context access rules for composed behavior
5. trace-preservation expectations where trace-aware claims are made
6. escalation or rebalance compatibility for non-trivial paths

If a system composes Wings but cannot describe these points, the composition is not mature enough for standard-oriented interoperability.

---

## 20. Recommended Registry-Level Guidance

The following guidance is recommended for early implementations.

### Safe Starting Patterns
- `memory -> generation -> verification`
- `interface -> routing -> generation`
- `routing -> verification -> escalate-if-needed`
- `memory + governance` with explicit trace scope

### Guarded Composite Patterns
- `generation + self-check`
- `interface + routing`
- `memory + trace support`

### Avoid as Default
- `generation + verification + finalization`
- `routing + governance + finalization`
- `memory + routing + finalization`
- any undeclared multi-role concentration

This helps early implementations stay legible.

---

## 21. Operational Definition

The operational meaning of Wing Composition Rules may be stated as follows:

> **A Wing composition is valid when it combines role-specialized units in a way that improves coordination quality while preserving explicit responsibility, review reachability, trace continuity, and bounded authority.**

---

## 22. Final Note

A distributed architecture does not become stronger merely by having more parts.

It becomes stronger when the relations among those parts are disciplined enough to remain coherent under load, revision, and failure.

That is the purpose of Wing Composition Rules.

Without them, Multi-Wing risks becoming decorative plurality.  
With them, it becomes structured multiplicity.
