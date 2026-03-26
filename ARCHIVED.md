# ARCHIVED — phenotype-tracing

**Status:** This repository has been archived.

## What happened

The crate has been extracted and productized under a neutral name.

## Canonical location

```
https://github.com/phenotype-dev/tracing-helpers
```

Package name: `tracing-helpers`

## Migration

Replace in `Cargo.toml`:

```toml
# Old
phenotype_tracing = { path = "path/to/phenotype-tracing" }

# New
tracing-helpers = { git = "https://github.com/phenotype-dev/tracing-helpers" }
```

Replace in source code:

```rust
// Old
use phenotype_tracing::{TracingConfig, init_tracing};

// New
use tracing_helpers::{TracingConfig, init_tracing};
```

## Timeline

- Archived: 2026-03-26
- Phase 6 productization
