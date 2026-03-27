# Architecture Decision Records — helix-tracing

## ADR-001 — OpenTelemetry as the Tracing Backend

**Status:** Accepted  
**Date:** 2026-03-27

### Context
The ecosystem needs a standard tracing backend compatible with Jaeger, Tempo, and cloud-native observability stacks. OpenTelemetry is the CNCF standard.

### Decision
helix-tracing wraps the OpenTelemetry Python SDK. The public API is helix-tracing specific; OpenTelemetry types are not exposed in the public surface.

### Consequences
- Upgrading the OTel SDK version does not require changes to callers.
- helix-tracing absorbs any OTel API breaking changes.

---

## ADR-002 — Package Rename from phenotype-tracing

**Status:** Accepted  
**Date:** 2026-03-27

### Context
The Phenotype Phase 6 productization plan renamed ecosystem-level packages from `phenotype-*` to their canonical names. Tracing is a cross-cutting concern for the Helix ecosystem, not Phenotype-specific.

### Decision
Package renamed from `phenotype_tracing` to `helix-tracing`. Old import paths are deprecated with a compatibility shim for one release cycle.

### Consequences
- All Phenotype services must update their imports.
- Migration guide published in ARCHIVED.md in the old repo.

---

## ADR-003 — No-Op Exporter for Testing

**Status:** Accepted  
**Date:** 2026-03-27

### Context
Tests that create spans should not require a running collector. A no-op exporter discards spans silently.

### Decision
Provide `helix_tracing.testing.NoOpExporter` that implements the OTel exporter interface but discards all spans.

### Consequences
- Tests run without any OTel infrastructure.
- Test assertions can inspect spans captured by an in-memory exporter (also provided).
