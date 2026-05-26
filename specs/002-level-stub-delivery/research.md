# Phase 0 Research - Level Stub Delivery Foundation

## Decision 1: Canonical artifact naming is spec-defined and immutable for this feature
- Decision: Define and validate all required artifact names from a fixed canonical catalog (Levels 1-11 plus the four named ACA events).
- Rationale: Completeness checks and handoff reliability require deterministic name matching.
- Alternatives considered:
  - External naming source: rejected because it introduces dependency drift during this feature.
  - Flexible names with count-only checks: rejected because it cannot guarantee required coverage.

## Decision 2: Stub depth is section headings only
- Decision: Generate stubs that include required section headings only, with no guidance text.
- Rationale: Keeps starter files lightweight while preserving consistent structure for downstream authoring.
- Alternatives considered:
  - Title-only placeholders: rejected because they are too ambiguous for consistent authoring.
  - Headings plus guidance prompts: rejected for this iteration to minimize content assumptions.
  - Near-complete sample content: rejected because final instructional content is explicitly out of scope.

## Decision 3: Completeness summary contract is pass/fail plus missing artifact names
- Decision: Completeness summary exposes one pass/fail status and an explicit list of missing required names.
- Rationale: Fast coordinator triage requires both an aggregate status and exact remediation targets.
- Alternatives considered:
  - Pass/fail only: rejected because it hides what to fix.
  - Percentage-only output: rejected because it obscures critical omissions.
  - Free-form reviewer notes: rejected because it is non-deterministic.

## Decision 4: Constitution alignment for front/back and vector-first expectations
- Decision: Stub scaffolds will include headings that preserve front-side and back-side intent, including front-side SVG layout slots.
- Rationale: Constitution requires print-ready handout semantics and vector-first layouts.
- Alternatives considered:
  - Single undifferentiated stub body: rejected because it risks violating two-sided handout standards.
  - Raster-first visual placeholders: rejected because constitution mandates vector-first visuals.

## Decision 5: Validation approach uses file checks plus JSON Schema contracts
- Decision: Validate required artifacts by deterministic file presence and machine-readable schema validation for catalogs/summaries.
- Rationale: Structured contracts enable repeatable checks in local and CI workflows.
- Alternatives considered:
  - Manual checklist only: rejected because it is slower and less reproducible.
  - Ad hoc script output without schema: rejected because consumers cannot rely on strict structure.
