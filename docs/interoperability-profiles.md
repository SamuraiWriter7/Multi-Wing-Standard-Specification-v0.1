# Interoperability Profiles

## Overview

This document defines the **Interoperability Profiles** for the **Multi-Wing Standard Specification**.

The purpose of an interoperability profile is to provide a structured way to express how a Multi-Wing implementation participates in the broader protocol and execution ecosystem without forcing all implementations into the same level of complexity.

A profile is not merely a label.  
It is a declared contract about:

- what the system can expose
- what the system can consume
- what lifecycle behavior it supports
- what trace depth it preserves
- what coordination guarantees it attempts to maintain
- what external interoperability surface it offers

In this sense, profiles are the bridge between:

- a common architectural standard
- multiple levels of implementation maturity
- different deployment environments
- different trust and governance requirements

---

## 1. Purpose

Interoperability Profiles exist to answer a practical standards question:

> How can different Multi-Wing implementations remain compatible even when they differ in rigor, runtime, trace depth, or deployment constraints?

Without profiles, interoperability claims tend to become vague.

A system may claim to be "compatible" while omitting:

- review behavior
- trace continuity
- escalation support
- external protocol mappings
- identity and policy controls
- degraded-mode behavior

Profiles solve this by making compatibility more explicit.

---

## 2. Scope

This document defines:

- the profile model
- core profile categories
- profile requirements
- profile negotiation principles
- profile composition rules
- profile progression guidance
- profile mapping to external ecosystems
- profile-specific conformance expectations

This document does **not** define:

- a mandatory transport protocol
- a specific MCP or A2A implementation
- a vendor certification program
- a full benchmark suite
- a complete legal compliance regime

Profiles are intended to express interoperability structure, not institutional certification.

---

## 3. Core Assumption

The Interoperability Profile model assumes that:

1. not all Multi-Wing systems need the same depth of coordination
2. not all systems need the same trace or governance surface
3. interoperability becomes stronger when capability is declared precisely
4. a portable standard should support progressive maturity
5. compatibility claims should be testable, not rhetorical

In operational terms:

> **A profile is a declared interoperability boundary with explicit behavioral expectations.**

---

## 4. Profile Model

Each profile defines a structured subset of Multi-Wing behavior across the following dimensions:

- **Structure Surface**  
  Wing typing, declared capabilities, role visibility

- **Protocol Surface**  
  lifecycle support, message compatibility, review behavior, escalation behavior

- **Context Surface**  
  shared context structure, freshness handling, conflict handling

- **Trace Surface**  
  provenance depth, revision continuity, review-chain continuity, authority trace

- **Execution Surface**  
  runtime assumptions, degraded-mode behavior, latency constraints, rebalancing support

- **Trust and Governance Surface**  
  identity controls, policy awareness, auditability, dispute hooks

A profile is therefore multi-dimensional.  
It describes how far a system goes in each area.

---

## 5. Profile Registry

The recommended profile registry for Multi-Wing v0.2-oriented implementations is:

- `minimal`
- `cooperative`
- `auditable`
- `edge-realtime`
- `enterprise`
- `signed-trace`
- `federated`

The first five are part of the original v0.1-aligned profile direction.  
The last two are v0.2-oriented extensions intended to support stronger external interoperability and distributed governance maturity.

---

## 6. Minimal Profile

### 6.1 Purpose

The `minimal` profile exists to define the lowest useful threshold for Multi-Wing interoperability.

It is appropriate for:

- early prototypes
- small local coordination systems
- internal experiments
- lightweight reference implementations

### 6.2 Expected Capabilities

A `minimal` implementation SHOULD support:

- explicit Wing typing
- basic task lifecycle progression
- structured message or artifact objects
- a continuity mechanism equivalent to shared context
- version identification
- explicit task or artifact references

### 6.3 Trace Expectations

A `minimal` implementation MAY support only shallow trace, but if it claims trace-aware behavior it SHOULD at least preserve:

- artifact reference
- acting Wing identity
- source or prior artifact reference, where applicable
- finalization identity, where finalization exists

### 6.4 Review Expectations

Review MAY be limited or optional in `minimal`, but the system SHOULD make it clear whether outputs are:

- provisional
- reviewed
- finalized without independent review

### 6.5 Suitable Use Cases

Typical `minimal` use cases include:

- local research loops
- prototype coordination experiments
- educational implementations
- low-risk internal tooling

---

## 7. Cooperative Profile

### 7.1 Purpose

The `cooperative` profile defines a more mature form of structured collaboration.

It is appropriate for systems where multiple Wings must cooperate in a visible and role-consistent way.

### 7.2 Expected Capabilities

A `cooperative` implementation SHOULD support:

- role discovery or equivalent capability advertisement
- explicit task assignment or routing semantics
- structured review flow
- revision-aware lifecycle progression
- richer shared context usage
- at least one rebalance or escalation path

### 7.3 Trace Expectations

A `cooperative` implementation SHOULD preserve:

- assignment trace
- execution trace
- review trace, where review occurs
- revision continuity, where revision occurs

### 7.4 Review Expectations

A `cooperative` implementation SHOULD support review as a path-altering event rather than a decorative annotation.

Review outcomes SHOULD be able to produce:

- acceptance
- rejection
- conditional acceptance
- revision request
- escalation request

### 7.5 Suitable Use Cases

Typical `cooperative` use cases include:

- co-creation workspaces
- structured writing pipelines
- multi-agent research workflows
- internal expert coordination systems

---

## 8. Auditable Profile

### 8.1 Purpose

The `auditable` profile defines a trace-strong and accountability-oriented interoperability level.

It is appropriate for systems where provenance, review continuity, and finalization authority matter materially.

### 8.2 Expected Capabilities

An `auditable` implementation SHOULD support:

- structured trace references
- review-chain continuity
- revision-chain continuity
- authority trace for finalization
- preservation of material lifecycle transitions
- dispute-ready event linkage or equivalent reconstructability

### 8.3 Governance Expectations

An `auditable` implementation SHOULD additionally support:

- inspectable review state
- inspectable finalization authority
- explicit trace omission or supersession behavior
- stronger retention expectations than `minimal` or `cooperative`

### 8.4 Suitable Use Cases

Typical `auditable` use cases include:

- editorial review systems
- policy-sensitive knowledge workflows
- provenance-aware research systems
- accountable AI collaboration environments

---

## 9. Edge / Real-Time Profile

### 9.1 Purpose

The `edge-realtime` profile defines how Multi-Wing interoperability behaves under latency-sensitive or resource-constrained conditions.

It is appropriate for:

- edge deployments
- low-latency decision loops
- constrained runtime environments
- intermittent connectivity conditions

### 9.2 Expected Capabilities

An `edge-realtime` implementation SHOULD support:

- bounded-latency coordination behavior
- constrained context handling
- degraded-mode visibility
- reduced but explicit review behavior
- rebalance or fallback behavior when full coordination is not possible

### 9.3 Trace Expectations

An `edge-realtime` implementation MAY preserve less trace detail than `auditable`, but it SHOULD still preserve:

- acting Wing identity
- artifact reference
- finalization or escalation identity
- explicit indication when trace depth is reduced

### 9.4 Degradation Expectations

An `edge-realtime` implementation MUST NOT silently present degraded coordination as if it were full-fidelity coordination.

If review is omitted or shortened due to runtime constraints, the system SHOULD expose that fact.

### 9.5 Suitable Use Cases

Typical `edge-realtime` use cases include:

- robotics coordination loops
- device-local assistance
- real-time moderation or routing paths
- low-latency operational decision systems

---

## 10. Enterprise Profile

### 10.1 Purpose

The `enterprise` profile defines a policy-aware, trust-aware, and integration-disciplined form of Multi-Wing interoperability.

It is appropriate for systems operating across institutional boundaries, policy regimes, or internal governance structures.

### 10.2 Expected Capabilities

An `enterprise` implementation SHOULD support:

- explicit identity controls
- authorization-aware context access
- policy-aware routing or review behavior
- operational audit expectations
- versioned interoperability declarations
- profile-specific deployment discipline

### 10.3 Governance Expectations

An `enterprise` implementation SHOULD preserve enough structure to answer:

- who was allowed to act
- which policy constraints were active
- who finalized or approved outputs
- what review boundaries existed
- how escalation crossed trust boundaries

### 10.4 Suitable Use Cases

Typical `enterprise` use cases include:

- internal knowledge operations
- regulated institutional workflows
- high-accountability collaboration environments
- organization-wide expert coordination systems

---

## 11. Signed-Trace Profile

### 11.1 Purpose

The `signed-trace` profile is a v0.2-oriented profile for systems that want stronger interoperability around authenticity, integrity, and non-trivial provenance assurance.

It is appropriate when trace is not only preserved, but needs stronger evidence of integrity.

### 11.2 Expected Capabilities

A `signed-trace` implementation SHOULD support:

- signature hooks on trace or event objects
- explicit signing metadata
- signed or attestable review events, where claimed
- explicit unsigned-state handling when signatures are absent
- a documented trust assumption for signed objects

### 11.3 Non-Requirement Clarification

This profile does **not** require:

- one specific cryptographic scheme
- a blockchain
- a universal identity standard
- legally binding signatures by default

It requires structural readiness for stronger integrity signaling.

### 11.4 Suitable Use Cases

Typical `signed-trace` use cases include:

- stronger provenance-aware publishing pipelines
- signed governance events
- trace integrity experiments
- dispute-ready collaboration records

---

## 12. Federated Profile

### 12.1 Purpose

The `federated` profile is a v0.2-oriented profile for systems that coordinate across multiple Multi-Wing domains, remote agent clusters, or external coordination boundaries.

It is appropriate when interoperability extends beyond a single deployment field.

### 12.2 Expected Capabilities

A `federated` implementation SHOULD support:

- remote or external Wing discovery
- explicit domain or boundary identifiers
- profile-aware cross-boundary coordination
- explicit escalation across domains
- trace-carrying handoff between internal and external paths
- trust-boundary-aware context exchange

### 12.3 Interoperability Expectations

A `federated` implementation SHOULD define:

- how remote participation is represented
- how authority changes across domains
- how trace is preserved across boundaries
- what minimum identity or capability declaration is required for external participants

### 12.4 Suitable Use Cases

Typical `federated` use cases include:

- distributed expert guilds
- cross-organization review workflows
- remote specialist agent integration
- protocol-bridged coordination environments

---

## 13. Profile Comparison Summary

### 13.1 Structural Maturity

- `minimal` focuses on typed existence
- `cooperative` focuses on structured collaboration
- `auditable` focuses on accountability continuity
- `edge-realtime` focuses on constrained operability
- `enterprise` focuses on policy and trust discipline
- `signed-trace` focuses on integrity-strengthened trace
- `federated` focuses on cross-boundary coordination

### 13.2 Progressive Interpretation

The profiles are not purely linear, but there is a practical maturity progression:

`minimal -> cooperative -> auditable`

with lateral specializations such as:

- `edge-realtime`
- `enterprise`
- `signed-trace`
- `federated`

This means some profiles deepen rigor, while others specialize the interoperability surface.

---

## 14. Profile Negotiation

### 14.1 Purpose

Profile negotiation allows systems to declare not only what they are, but what level of interoperability they can safely participate in.

### 14.2 Negotiation Inputs

A system SHOULD be able to declare:

- supported profile identifiers
- supported Wing types
- trace depth, if relevant
- review behavior, if relevant
- context-sharing constraints
- trust-boundary assumptions, where relevant

### 14.3 Negotiation Outcome

A negotiation result MAY conclude that systems are:

- fully compatible
- partially compatible
- compatible only under downgraded profile assumptions
- incompatible for the intended task

### 14.4 Downgrade Principle

If a higher-profile interaction cannot be supported, systems MAY negotiate downward to a shared lower profile, provided that:

- the downgrade is explicit
- any lost guarantees are visible
- outputs do not falsely claim the stronger profile

---

## 15. Profile Composition

### 15.1 General Rule

A system MAY support multiple profiles simultaneously.

For example:

- `cooperative + auditable`
- `enterprise + auditable`
- `edge-realtime + signed-trace`
- `federated + enterprise`

### 15.2 Composition Constraint

Profile composition MUST NOT create contradictory claims.

For example, a system SHOULD NOT simultaneously claim:

- deep auditability while silently dropping trace under normal operation
- enterprise-grade governance while lacking identity-aware access boundaries
- federated coordination while having no explicit cross-boundary handoff semantics

### 15.3 Strongest-Claim Principle

When profiles are combined, the implementation SHOULD satisfy the strongest relevant requirement for each claimed surface.

---

## 16. Mapping to External Ecosystems

### 16.1 MCP-Relevant Surface

Profiles that benefit strongly from standardized tool and context access include:

- `minimal`
- `cooperative`
- `enterprise`
- `federated`

These profiles often rely on clear system-boundary access to tools, data, or shared context services.

### 16.2 A2A-Relevant Surface

Profiles that benefit strongly from agent-to-agent interoperability include:

- `cooperative`
- `federated`
- `enterprise`
- `edge-realtime` in distributed constrained environments

These profiles often rely on discoverable external roles, remote participation, or federated escalation.

### 16.3 Trace-Relevant Surface

Profiles that depend strongly on trace depth include:

- `auditable`
- `signed-trace`
- `enterprise`
- `federated`

### 16.4 Architectural Interpretation

The profile model does not assume that all implementations must use external protocols directly.

Instead, it provides an architectural vocabulary that can align with them when needed.

---

## 17. Profile-Specific Conformance Expectations

### 17.1 Minimal
A `minimal` claim SHOULD demonstrate:

- Wing typing
- lifecycle presence
- structured messages or artifacts
- continuity mechanism
- version identification

### 17.2 Cooperative
A `cooperative` claim SHOULD additionally demonstrate:

- role discovery or capability advertisement
- review-capable progression
- revision-aware flow
- rebalance or escalation behavior

### 17.3 Auditable
An `auditable` claim SHOULD additionally demonstrate:

- trace continuity
- review-chain or equivalent review preservation
- revision-chain or equivalent revision preservation
- visible finalization authority

### 17.4 Edge / Real-Time
An `edge-realtime` claim SHOULD additionally demonstrate:

- constrained-latency behavior
- degraded-mode visibility
- bounded coordination under reduced resources

### 17.5 Enterprise
An `enterprise` claim SHOULD additionally demonstrate:

- identity-aware access control
- policy-aware coordination behavior
- stronger accountability structure

### 17.6 Signed-Trace
A `signed-trace` claim SHOULD additionally demonstrate:

- signature-aware trace structure
- explicit handling of signed versus unsigned states
- integrity-oriented trace semantics

### 17.7 Federated
A `federated` claim SHOULD additionally demonstrate:

- cross-boundary coordination semantics
- remote participation visibility
- trace-carrying boundary transfer
- escalatable trust-boundary handling

---

## 18. Profile Smells

The following are warning signs that a profile claim may be weak, inflated, or misleading:

- claiming `auditable` without preserving review continuity
- claiming `enterprise` without identity or policy boundaries
- claiming `edge-realtime` while hiding degraded operation
- claiming `signed-trace` with no distinction between signed and unsigned events
- claiming `federated` with no explicit cross-domain handoff semantics
- claiming multiple profiles without satisfying the strongest relevant obligations

These are not always proof of invalidity, but they are serious interoperability warnings.

---

## 19. Recommended Adoption Path

A practical adoption path for new implementations is:

### Stage 1
Start with:

- `minimal`

### Stage 2
Progress to:

- `cooperative`

### Stage 3
Deepen into one or more of:

- `auditable`
- `enterprise`
- `edge-realtime`

### Stage 4
For stronger external interoperability or assurance, add:

- `signed-trace`
- `federated`

This path supports progressive maturity without requiring premature complexity.

---

## 20. Reference Implementation Guidance

Reference implementations SHOULD declare:

- their supported profile identifiers
- the exact features used to justify those profile claims
- any downgraded behavior under constrained conditions
- any profile combinations in use

Reference implementations SHOULD also avoid claiming profiles aspirationally.  
A profile claim should reflect observable behavior, not future intent.

---

## 21. Minimal Profile Declaration Object

A profile declaration object SHOULD be able to express at least:

- specification version
- supported profile identifiers
- supported Wing types
- review support level
- trace support level
- degraded-mode behavior, if relevant
- cross-boundary support, if relevant

This MAY be expressed through future schema or implementation-specific metadata.

---

## 22. Operational Definition

The operational meaning of an Interoperability Profile may be stated as follows:

> **An Interoperability Profile is a declared compatibility boundary that specifies the level of structural, protocol, trace, execution, and governance behavior a Multi-Wing implementation can expose reliably to other systems.**

---

## 23. Final Note

A standard becomes useful not when every implementation looks the same, but when difference becomes legible.

That is the role of Interoperability Profiles.

They do not erase diversity of implementation.  
They make that diversity interoperable.
