# Quickstart - Level Stub Delivery Foundation

## Purpose
Create and validate the initial 15-stub delivery set (11 levels + 4 canonical ACA event cards) using headings-only scaffolds.

## Prerequisites
- Repository checked out on feature branch 002-level-stub-delivery.
- PowerShell 5.1+ available.
- Pandoc installed for downstream PDF validation workflows.

## 1. Confirm canonical catalog
Ensure these ACA names are used exactly:
- ACA Dry Fly Event
- ACA Trout Fly Event
- ACA Bass Bugger Event
- ACA Fly Angler's Distance Event

## 2. Create stubs
Create one Markdown file for each required artifact under planned content paths:
- content/levels/level-01.md ... content/levels/level-11.md
- content/events/aca-dry-fly-event.md
- content/events/aca-trout-fly-event.md
- content/events/aca-bass-bugger-event.md
- content/events/aca-fly-anglers-distance-event.md

Each file should include headings-only scaffold sections for front and back sides.

## 3. Run completeness validation
Run the planned validation script:

```powershell
pwsh scripts/validate-stub-delivery.ps1
```

Expected output contract:
- pass/fail status
- explicit list of missing artifact names (if any)

## 4. Review coordinator summary
Validate that summary output can be reviewed in under 3 minutes and names exactly match canonical requirements.

## 5. Optional print workflow smoke check
After stubs exist, run PDF generation path to ensure no future layout blockers for duplex US Letter output.
