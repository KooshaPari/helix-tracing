# PRD — helix-tracing

## Overview

`helix-tracing` is the distributed tracing library for the Helix/Phenotype ecosystem (formerly `phenotype-tracing`). It provides OpenTelemetry-compatible span creation, context propagation, and exporter adapters for services written in Python.

## Goals

- Provide a simple, opinionated tracing API that wraps OpenTelemetry without exposing its full complexity.
- Support automatic context propagation across HTTP, gRPC, and message-bus boundaries.
- Ship adapters for common exporters: OTLP/gRPC, OTLP/HTTP, Jaeger, stdout.

## Epics

### E1 — Tracing API
- E1.1 `trace(name, attributes)` context manager for creating spans.
- E1.2 `current_span()` accessor for adding events and attributes mid-span.
- E1.3 Automatic exception recording on context manager exit.

### E2 — Context Propagation
- E2.1 W3C TraceContext and Baggage header injection/extraction.
- E2.2 Helper for FastAPI/Starlette middleware auto-propagation.
- E2.3 Helper for aiohttp client request propagation.

### E3 — Exporters
- E3.1 OTLP/gRPC exporter adapter.
- E3.2 OTLP/HTTP exporter adapter.
- E3.3 Stdout/pretty-print exporter for development.
- E3.4 No-op exporter for testing.

### E4 — Configuration
- E4.1 Configure exporter, service name, and sampling rate via environment variables.
- E4.2 `TracingConfig` Pydantic model for programmatic configuration.
- E4.3 Auto-initialize on import when `OTEL_EXPORTER_OTLP_ENDPOINT` is set.

## Acceptance Criteria

- A span created with `trace("operation")` appears in the configured exporter.
- HTTP headers injected by one service are correctly extracted by a downstream service.
- Tests use the no-op exporter and produce zero external I/O.
