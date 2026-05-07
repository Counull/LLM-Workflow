# Feature / Topic Index

Page Type: `index`

Lifecycle: `active`

Updated: YYYY-MM-DD

## FeatureName

Status Source: [status](../02_index/FeatureName_status.md)

Owner: OwnerName

Status: analysis

Entry Points: `path/to/module`

## Default Read Set

Keep this list to at most 3-4 pages after the index.

| Order | Page | Why |
|---:|---|---|
| 1 | [status](../02_index/FeatureName_status.md) | Current mutable state and next action. |
| 2 | [active-plan](../03_design/YYYY-MM-DD_FeatureName_plan.md) | Remaining implementation or maintenance work. |
| 3 | [source-digest](../01_requirements/YYYY-MM-DD_FeatureName_digest.md) | Short summary of long source material. |

## Optional Deep-Dive Docs

| Page | Use When |
|---|---|
| [design](../03_design/YYYY-MM-DD_FeatureName_design.md) | Need rationale or implementation trade-offs. |
| [testing](../06_testing/YYYY-MM-DD_FeatureName_test.md) | Need validation scope or acceptance records. |

## Source Docs

Source docs are not default context.

| Source | Type | Notes |
|---|---|---|
| [source-id](../00_inbox/source-id.md) | source | Exact original material; read only for traceability. |

## Archive Docs

Archive docs are not default context.

| Page | Reason |
|---|---|
| [old-plan](../99_archive/YYYY-MM-DD_FeatureName_old_plan.md) | Historical plan replaced by current status and plan. |

## Superseded Docs

Superseded docs are not default context and must link to replacement pages.

| Page | Replaced By |
|---|---|
| [old-digest](../99_archive/YYYY-MM-DD_FeatureName_old_digest.md) | [source-digest](../01_requirements/YYYY-MM-DD_FeatureName_digest.md) |

## Communication Docs

Communication docs are read only for communication tasks.

| Page | Use When |
|---|---|
| [communication-note](../10_communication/YYYY-MM-DD_FeatureName_questions.md) | Preparing stakeholder questions or meeting notes. |

## Status Suggestions

- `analysis`
- `design`
- `development`
- `integration`
- `testing`
- `published`
- `archived`
