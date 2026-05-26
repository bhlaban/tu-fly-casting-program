# Data Model - Level Stub Delivery Foundation

## Entity: CanonicalCatalog
- Purpose: Source of truth list for all required stubs in this feature scope.
- Fields:
  - version (string, required)
  - levels (array[string], required, exactly 11 entries)
  - acaEventCards (array[string], required, exactly 4 entries)
- Validation rules:
  - levels must contain unique canonical level names for Level 1 through Level 11.
  - acaEventCards must contain unique values and exactly:
    - ACA Dry Fly Event
    - ACA Trout Fly Event
    - ACA Bass Bugger Event
    - ACA Fly Angler's Distance Event

## Entity: StubArtifact
- Purpose: Represents one Markdown stub file to be authored later.
- Fields:
  - artifactId (string, required, unique)
  - artifactType (enum: level|aca-event, required)
  - canonicalName (string, required)
  - relativePath (string, required)
  - scaffoldDepth (enum: headings-only, required)
  - sideSections (array[enum: front|back], required, must contain both values)
  - status (enum: missing|present|validated, required)
- Validation rules:
  - canonicalName must exist in CanonicalCatalog.
  - relativePath must map to exactly one repository file.
  - sideSections must include front and back for constitution alignment.

## Entity: DeliveryBundle
- Purpose: Groups all stubs as one handoff unit.
- Fields:
  - bundleId (string, required)
  - generatedAt (datetime string, required)
  - artifacts (array[StubArtifact], required)
  - requiredCount (integer, required, expected 15)
  - presentCount (integer, required)
- Validation rules:
  - requiredCount must equal 15.
  - artifacts must contain unique artifactId values.
  - presentCount must equal count of artifacts with status != missing.

## Entity: CompletenessSummary
- Purpose: Coordinator-facing validation output.
- Fields:
  - bundleId (string, required)
  - status (enum: PASS|FAIL, required)
  - requiredArtifacts (array[string], required)
  - missingArtifacts (array[string], required)
  - validatedAt (datetime string, required)
- Validation rules:
  - status is PASS only when missingArtifacts is empty.
  - missingArtifacts values must be members of requiredArtifacts.

## Relationships
- CanonicalCatalog 1..1 -> 1..* StubArtifact (catalog constrains allowed stub names).
- DeliveryBundle 1..1 -> 15 StubArtifact (bundle contains all required stubs).
- DeliveryBundle 1..1 -> 1 CompletenessSummary (summary is computed from bundle state).

## State Transitions
### StubArtifact.status
- missing -> present: file created at canonical path.
- present -> validated: scaffold and naming checks pass.
- validated -> present: content changes invalidate prior validation until rechecked.

### CompletenessSummary.status
- FAIL -> PASS: missingArtifacts becomes empty after validation.
- PASS -> FAIL: any required artifact becomes missing or renamed.