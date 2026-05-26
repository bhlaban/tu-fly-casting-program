# TU Fly Casting Program Constitution

## Core Principles

### I. Markdown Is The Source Of Truth
All coaching content MUST be authored and maintained in Markdown.
PDF files are release artifacts generated from Markdown and MUST NOT be manually edited as source.

### II. One Artifact Pair Per Level Or Event
Each level and each ACA event MUST have its own content unit with front-side and back-side outputs.
The front side MUST include the casting box and target layout visuals.
The back side MUST include clear textual instructions and evaluation criteria.

### III. Vector-First Visuals
Casting layouts MUST be SVG-based to preserve print quality at scale.
Raster-only diagrams are not allowed for canonical layouts unless explicitly approved for a temporary exception.

### IV. Print Reliability Is Non-Negotiable
Official outputs MUST target US Letter with duplex long-edge printing and lamination-safe margins.
A feature is not complete unless exported PDF pages are readable, unclipped, and print-safe.

### V. Reproducible Publishing Workflow
The repository MUST support deterministic PDF generation from Markdown in a documented build workflow.
Pandoc is the default exporter and SHOULD be used to keep local and CI outputs consistent.

## Approved Toolchain Policy

- Default path: Markdown + SVG + Pandoc-based PDF export.
- Alternate exporters are allowed only when they are documented and produce deterministic output.
- Any alternate exporter MUST pass all print quality gates defined in this constitution.
- If a toolchain change affects output fidelity, it MUST be introduced through a constitution amendment and validated on at least one level and one ACA event.

## Content And Layout Standards

- Canonical content model: one Markdown source per level/event with shared templates and reusable includes.
- Required scope: 11 levels plus 4 ACA events (Dry Fly, Trout Fly, Bass Bugger, Fly Angler's Distance).
- Every generated page set MUST map to coach-friendly laminated handouts.
- Terminology, units, and scoring language SHOULD remain consistent across all levels and events.

## Development Workflow And Quality Gates

- Use spec-kit lifecycle for feature work: specify, clarify, plan, tasks, analyze, implement.
- During planning and analysis, constitution violations are treated as blocking issues.
- Minimum acceptance for each completed level/event:
	- PDF export succeeds in automated or documented local workflow.
	- No clipping of SVG or text content at print boundaries.
	- Typography and diagrams are readable at printed size.

## Governance

This constitution supersedes conflicting conventions in feature specs, plans, and tasks.
Changes to print standards, source-of-truth rules, or required quality gates require an explicit constitution amendment.
All pull requests and implementation reviews MUST verify constitution compliance.

**Version**: 1.1.0 | **Ratified**: 2026-05-26 | **Last Amended**: 2026-05-26
