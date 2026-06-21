# Sync Audit Trace Integration

**Sync Audit Trace Integration** is an integration layer for connecting synchronization audit records with trace receipts, AI search traces, unified trace receipt bundles, and cross-repository evidence bundles.

This repository continues the trace-integration work after the first completed arc of [`synchronization-audit-protocol`](https://github.com/SamuraiWriter7/synchronization-audit-protocol).

Where `synchronization-audit-protocol` defines how to audit structural similarity, this repository defines how those audit results can be connected to evidence routes, trace receipts, AI search trace receipts, unified trace receipt bundles, search records, and repository-level bundles.

## Purpose

`sync-audit-trace-integration` exists to answer the following question:

> Once a synchronization audit has been performed, how should its evidence path be connected, preserved, bundled, and referenced across trace systems?

This repository does not replace the original audit protocol.

Instead, it provides an integration layer for connecting synchronization audit records to:

* Trace Receipt records
* AI Search Trace Receipt records
* Unified Trace Receipt bundles
* Cross-repository audit evidence
* Multi-case synchronization graphs

## Relationship to Synchronization Audit Protocol

```text
synchronization-audit-protocol
= standard for auditing structural similarity

sync-audit-trace-integration
= integration layer for connecting audit records to trace evidence
```

In simpler terms:

```text
synchronization-audit-protocol
= ruler, classification, human review boundary

sync-audit-trace-integration
= evidence route, trace link, unified bundle wiring
```

The original audit protocol remains the constitutional layer.

This repository becomes the trace wiring and evidence bundling layer.

## Current Status

```text
v0.3.0-candidate
```

The repository now includes three validated integration models:

```text
v0.1 = Sync Audit Trace Link
v0.2 = AI Search Trace Receipt Integration
v0.3 = Unified Trace Receipt Integration
```

The schema examples are validated by both the local validation script and the GitHub Actions workflow.

```text
Status:
- v0.1 schema added
- v0.1 example added
- v0.2 schema added
- v0.2 example added
- v0.3 schema added
- v0.3 example added
- validation script updated
- GitHub Actions workflow added
- example validation passed
```

## v0.1 Scope

### v0.1 — Sync Audit Trace Link

v0.1 defines the first minimal object for linking a synchronization audit case to trace evidence.

It records:

* the source audit case
* the audit classification
* related trace receipt references
* related AI search trace references
* evidence route metadata
* integration status
* review boundary conditions

## v0.2 Scope

### v0.2 — AI Search Trace Receipt Integration

v0.2 connects synchronization audit trace links to AI Search Trace Receipt records.

It records:

* the parent sync audit trace link
* the related AI Search Trace Receipt
* search session metadata
* query purpose and query summary
* search terms used during the audit
* source evidence references
* sampled evidence references
* linkage assessment
* human review requirements
* search-result storage boundaries

This makes it possible to connect a synchronization audit judgment to the search path and reference evidence used during the audit.

```text
synchronization audit judgment
↓
sync audit trace link
↓
AI search trace receipt
↓
query route / source evidence / review boundary
```

## v0.3 Scope

### v0.3 — Unified Trace Receipt Integration

v0.3 connects synchronization audit trace links and AI Search Trace Receipt integrations to a Unified Trace Receipt bundle.

It records:

* the parent sync audit trace link
* the parent AI search trace integration
* the related synchronization audit case
* the unified trace receipt bundle reference
* component receipts included in the bundle
* aggregation model
* evidence alignment summary
* confidence level
* conflict notes
* human review requirements
* component payload storage boundaries

This makes it possible to treat multiple evidence routes as a single unified trace bundle.

```text
synchronization audit judgment
↓
sync audit trace link
↓
AI search trace receipt
↓
unified trace receipt bundle
↓
aggregated evidence / alignment / review boundary
```

## Repository Structure

```text
schemas/
  sync-audit-trace-link.schema.json
  ai-search-trace-integration.schema.json
  unified-trace-receipt-integration.schema.json

examples/
  sync-audit-trace-link.example.yaml
  ai-search-trace-integration.example.yaml
  unified-trace-receipt-integration.example.yaml

scripts/
  validate_examples.py

.github/
  workflows/
    validate-examples.yml
```

## Validation

Install dependencies:

```bash
pip install pyyaml jsonschema
```

Run validation locally:

```bash
python scripts/validate_examples.py
```

Expected result:

```text
[validate] Sync Audit Trace Link
  schema : schemas/sync-audit-trace-link.schema.json
  example: examples/sync-audit-trace-link.example.yaml
[ok] Sync Audit Trace Link example is valid
[validate] AI Search Trace Integration
  schema : schemas/ai-search-trace-integration.schema.json
  example: examples/ai-search-trace-integration.example.yaml
[ok] AI Search Trace Integration example is valid
[validate] Unified Trace Receipt Integration
  schema : schemas/unified-trace-receipt-integration.schema.json
  example: examples/unified-trace-receipt-integration.example.yaml
[ok] Unified Trace Receipt Integration example is valid
```

The GitHub Actions workflow also validates examples on:

* push to `main`
* pull requests to `main`
* manual workflow dispatch

## Design Boundary

This repository links evidence routes and bundles trace references.

It does not store full third-party source content by default.

It does not store complete search result pages by default.

It does not embed complete component payloads by default.

It should preserve references, receipts, fingerprints, query metadata, aggregation metadata, and review routes rather than duplicating source material.

```text
Audit protocol = decide what kind of similarity exists
Trace integration = preserve how the evidence path is connected
Search trace integration = preserve how the search route contributed to the audit
Unified trace integration = bundle related evidence routes into one reviewable trace unit
```

## Roadmap

```text
v0.1 = Sync Audit Trace Link
v0.2 = AI Search Trace Receipt Integration
v0.3 = Unified Trace Receipt Integration
v0.4 = Multi-case Synchronization Graph
v0.5 = Cross-repository Audit Bundle
```

## Design Principle

The original synchronization audit protocol should remain lightweight.

This repository exists so that trace integration, search receipt linkage, unified evidence bundling, multi-case graphing, and cross-repository evidence bundles can evolve without overloading the audit protocol itself.

```text
synchronization-audit-protocol
= the blade that classifies structural similarity

sync-audit-trace-integration
= the wind route that carries and bundles the evidence
```

## Status Summary

`v0.3.0-candidate` establishes the validated bridge between synchronization audit records, AI Search Trace Receipt records, and Unified Trace Receipt bundles.

The repository now connects audit classification, trace linkage, search-session evidence, unified receipt aggregation, and human review boundaries into a single integration layer.

