# Changelog

All notable changes to this repository will be documented in this file.

This project follows a draft-stage specification model.  
Version numbers before 1.0 indicate an evolving standard and may include substantial structural changes.

The format is inspired by Keep a Changelog, adapted for specification repositories.

---

## [v0.1.0] - 2026-05-05

### Added
- Initial repository structure for **Multi-Wing Standard Specification**
- Initial `README.md`
- Canonical specification target:
  - `spec/multi-wing-standard-specification-v0.1.md`
- Supporting documentation targets:
  - `docs/one-page-overview.md`
  - `docs/architecture-overview.md`
  - `docs/wing-type-system.md`
  - `docs/kazene-coordination-principles.md`
  - `docs/interoperability-profiles.md`
  - `docs/relationship-to-mcp-a2a.md`
- Initial repository governance files:
  - `CONTRIBUTING.md`
  - `CHANGELOG.md`
  - `CITATION.cff`
- Initial schema targets:
  - `schemas/wing-type.schema.json`
  - `schemas/message-envelope.schema.json`
  - `schemas/shared-context.schema.json`
  - `schemas/trace-reference.schema.json`
- Initial example targets:
  - `examples/minimal-session.sample.json`
  - `examples/review-loop.sample.json`
  - `examples/trace-integrated.sample.json`
  - `examples/edge-execution.sample.json`

### Defined
- Project scope as an **open draft specification**
- Three-layer architecture:
  - Structure Layer
  - Protocol Layer
  - Execution Layer
- Core positioning of Multi-Wing as a standardizable abstraction for distributed intelligence
- Early terminology around:
  - Wing
  - Role
  - Capability
  - Shared Context
  - Trace Reference
  - Kazene coordination

### Notes
- v0.1.0 establishes the initial publication baseline
- Future revisions may refine terminology, schemas, conformance language, and interoperability mappings
- Backward compatibility is not guaranteed before 1.0
