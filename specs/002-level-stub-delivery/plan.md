# Implementation Plan: Level Stub Delivery Foundation

**Branch**: `[002-level-stub-delivery]` | **Date**: 2026-05-26 | **Spec**: [specs/002-level-stub-delivery/spec.md](specs/002-level-stub-delivery/spec.md)

**Input**: Feature specification from [specs/002-level-stub-delivery/spec.md](specs/002-level-stub-delivery/spec.md)

## Summary

Deliver a deterministic starter-content bundle that includes file stubs for Levels 1 through 11 and the four canonical ACA event cards. Stubs use section-headings-only scaffolds, enforce canonical naming, and expose a pass/fail completeness summary with explicit missing artifact names.

## Technical Context

**Language/Version**: Markdown (CommonMark), SVG 1.1+, JSON Schema draft 2020-12

**Primary Dependencies**: Pandoc (PDF export path), PowerShell 5.1+ for repository scripts, optional markdownlint for authoring consistency

**Storage**: Repository files (Markdown stubs, schema files, generated completeness summary artifact)

**Testing**: Contract validation (JSON Schema), deterministic file-presence checks, manual print-safety verification for generated PDF output

**Target Platform**: Windows and CI runners generating US Letter duplex long-edge PDF artifacts

**Project Type**: Documentation/content pipeline repository

**Performance Goals**: Completeness validation and summary review in under 3 minutes for a full 15-artifact set

**Constraints**: Markdown as source of truth, vector-first visuals, no clipping on US Letter duplex long-edge output, lamination-safe margins

**Scale/Scope**: 15 required stubs total (11 levels + 4 ACA events), one delivery bundle per release candidate

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- Gate 1 - Markdown source of truth: PASS. Design keeps canonical content as Markdown; PDFs remain generated artifacts.
- Gate 2 - Artifact pair expectations: PASS. Stub headings enforce front-side and back-side structure for level/event handouts.
- Gate 3 - Vector-first visuals: PASS. Front-side sections explicitly reserve SVG casting-box/target layout content.
- Gate 4 - Print reliability: PASS. Plan includes print-safety validation criteria for US Letter duplex long-edge output.
- Gate 5 - Reproducible publishing workflow: PASS. Plan assumes documented, deterministic generation path with Pandoc.

Post-design re-check (after Phase 1 artifacts): PASS. Research decisions, data model, contracts, and quickstart remain compliant with all constitution gates.

## Project Structure

### Documentation (this feature)

```text
specs/002-level-stub-delivery/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── contracts/
│   ├── canonical-catalog.schema.json
│   └── completeness-summary.schema.json
└── tasks.md
```

### Source Code (repository root)

```text
content/
├── levels/
│   ├── level-01.md
│   ├── level-02.md
│   ├── level-03.md
│   ├── level-04.md
│   ├── level-05.md
│   ├── level-06.md
│   ├── level-07.md
│   ├── level-08.md
│   ├── level-09.md
│   ├── level-10.md
│   └── level-11.md
└── events/
    ├── aca-dry-fly-event.md
    ├── aca-trout-fly-event.md
    ├── aca-bass-bugger-event.md
    └── aca-fly-anglers-distance-event.md

schemas/
├── canonical-catalog.schema.json
└── completeness-summary.schema.json

scripts/
└── validate-stub-delivery.ps1
```

**Structure Decision**: Use a documentation-first content tree (`content/`, `schemas/`, `scripts/`) because the feature is artifact-oriented and does not require an application runtime.

## Complexity Tracking

No constitution violations or justified exceptions.
