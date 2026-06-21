# Changelog

All notable changes to this project will be documented in this file.

## v0.2.0-candidate

### Status

Candidate release.

The v0.2 schema, example, and validator update have been added.

The GitHub Actions validation workflow has passed.

### Added

* Added `AI Search Trace Integration` as the second integration model.
* Added `schemas/ai-search-trace-integration.schema.json`.
* Added `examples/ai-search-trace-integration.example.yaml`.
* Updated `scripts/validate_examples.py` to validate both:

  * `Sync Audit Trace Link`
  * `AI Search Trace Integration`
* Updated README documentation to describe:

  * v0.2 scope
  * AI Search Trace Receipt linkage
  * query context
  * source evidence references
  * linkage assessment
  * search-result storage boundary
  * updated repository structure
  * updated validation expectations

### v0.2 Scope

v0.2 connects synchronization audit trace links to AI Search Trace Receipt records.

It establishes a structured bridge between:

* synchronization audit cases
* parent sync audit trace links
* AI Search Trace Receipt records
* search session metadata
* query purpose and query summary
* source evidence references
* sampled evidence references
* linkage assessment
* human review requirements
* search-result storage boundaries

### Purpose

This release makes it possible to connect a synchronization audit judgment to the search path and reference evidence used during the audit.

```text
synchronization audit judgment
↓
sync audit trace link
↓
AI search trace receipt
↓
query route / source evidence / review boundary
```

### Validation

The following validation path now covers both v0.1 and v0.2 examples:

```bash
python scripts/validate_examples.py
```

Expected validation targets:

```text
[validate] Sync Audit Trace Link
[validate] AI Search Trace Integration
```

The GitHub Actions workflow validates examples on:

* push to `main`
* pull request to `main`
* manual workflow dispatch

### Boundary

This repository does not replace the synchronization audit protocol.

It does not prove legal dependency by itself.

It does not store full third-party source content by default.

It does not store complete search result pages by default.

It links evidence routes, trace references, query metadata, fingerprints, search evidence summaries, and review metadata so that synchronization audit results can be connected to broader trace systems.

### Repository Role

```text
synchronization-audit-protocol
= ruler, classification, human review boundary

sync-audit-trace-integration
= evidence route, search trace link, integration wiring
```

### Next

Planned next step:

```text
v0.3 = Unified Trace Receipt Integration
```

## v0.1.0-candidate

### Status

Candidate release.

The initial schema, example, validation script, and GitHub Actions workflow have been added.

The GitHub Actions validation workflow has passed.

### Added

* Added `Sync Audit Trace Link` as the initial integration model.
* Added `schemas/sync-audit-trace-link.schema.json`.
* Added `examples/sync-audit-trace-link.example.yaml`.
* Added `scripts/validate_examples.py`.
* Added `.github/workflows/validate-examples.yml`.
* Added validation for schema/example consistency.
* Added README documentation describing the repository purpose, scope, relationship to `synchronization-audit-protocol`, and roadmap.

### v0.1 Scope

v0.1 establishes the minimum bridge between:

* synchronization audit cases
* trace receipt references
* AI search trace references
* unified trace bundles
* repository references
* evidence routes
* human review boundaries

### Purpose

This release separates trace integration work from the original `synchronization-audit-protocol`.

The original audit protocol remains focused on auditing structural similarity.

This repository provides the wiring layer for connecting audit results to trace evidence systems.

### Validation

The following validation path is available:

```bash
python scripts/validate_examples.py
```

The GitHub Actions workflow validates examples on:

* push to `main`
* pull request to `main`
* manual workflow dispatch

### Boundary

This repository does not replace the synchronization audit protocol.

It does not prove legal dependency by itself.

It does not store full third-party source content by default.

It links evidence routes, trace references, fingerprints, and review metadata so that synchronization audit results can be connected to broader trace systems.

### Repository Role

```text
synchronization-audit-protocol
= ruler, classification, human review boundary

sync-audit-trace-integration
= evidence route, trace link, integration wiring
```
