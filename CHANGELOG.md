# Changelog

All notable changes to this project will be documented in this file.

## v0.1.0-candidate

### Added

- Added `Sync Audit Trace Link` as the initial integration model.
- Added JSON Schema for linking synchronization audit records to trace evidence.
- Added YAML example for a minimal audit-to-trace connection.
- Added validation script for schema/example consistency.

### Purpose

v0.1 establishes the minimum bridge between:

- synchronization audit cases
- trace receipt references
- AI search trace references
- unified trace bundles
- cross-repository evidence routes

This version keeps the original `synchronization-audit-protocol` lightweight while moving trace integration work into a dedicated repository.

### Boundary

This repository does not replace the synchronization audit protocol.

It provides the wiring layer for evidence routes after an audit has been performed.

It should not store full third-party source content by default.
