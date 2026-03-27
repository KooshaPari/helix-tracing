# Functional Requirements — helix-tracing

## FR-API — Tracing API

| ID | Requirement |
|----|-------------|
| FR-API-001 | The library SHALL provide a trace(name, attributes) context manager for span creation. |
| FR-API-002 | The library SHALL provide a current_span() function for mid-span attribute and event recording. |
| FR-API-003 | The library SHALL automatically record exceptions as span events on context manager exit. |
| FR-API-004 | The library SHALL support nested spans with correct parent-child relationships. |

## FR-PROP — Context Propagation

| ID | Requirement |
|----|-------------|
| FR-PROP-001 | The library SHALL support W3C TraceContext header injection and extraction. |
| FR-PROP-002 | The library SHALL support W3C Baggage header injection and extraction. |
| FR-PROP-003 | The library SHALL provide a FastAPI/Starlette middleware for automatic propagation. |
| FR-PROP-004 | The library SHALL provide an aiohttp client session wrapper for outbound propagation. |

## FR-EXPORT — Exporters

| ID | Requirement |
|----|-------------|
| FR-EXPORT-001 | The library SHALL provide an OTLP/gRPC exporter adapter. |
| FR-EXPORT-002 | The library SHALL provide an OTLP/HTTP exporter adapter. |
| FR-EXPORT-003 | The library SHALL provide a stdout pretty-print exporter for development. |
| FR-EXPORT-004 | The library SHALL provide a no-op exporter for use in tests. |

## FR-CFG — Configuration

| ID | Requirement |
|----|-------------|
| FR-CFG-001 | The library SHALL configure the exporter via the OTEL_EXPORTER_OTLP_ENDPOINT environment variable. |
| FR-CFG-002 | The library SHALL configure the service name via OTEL_SERVICE_NAME. |
| FR-CFG-003 | The library SHALL support programmatic configuration via a TracingConfig model. |
| FR-CFG-004 | The library SHALL auto-initialize when OTEL_EXPORTER_OTLP_ENDPOINT is set at import time. |
