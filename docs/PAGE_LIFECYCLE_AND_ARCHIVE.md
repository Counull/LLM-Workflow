# Page Lifecycle and Archive Rules

Use lifecycle labels to prevent old facts from competing with current decisions.

## Lifecycle Labels

| Label | Meaning | Default Read? |
|---|---|---|
| `active` | Current working page for a topic. | Yes, only if listed in the default read set. |
| `draft` | Incomplete or unreviewed page. | Optional; read only when the task needs it. |
| `source-only` | Raw or exact source material. | No. |
| `superseded` | Replaced by a newer source, decision, or status. | No. |
| `archived` | Historical, inactive, or no longer part of current work. | No. |

Every maintained page should make its lifecycle clear in metadata or near the title.

## Active Page Rules

Active pages should describe the current working truth, not the full history of how it changed.

Keep active pages focused:

- `status`: current facts, blockers, risks, and next action
- `plan`: remaining work, blocked work, partial work, and risky work
- `digest`: concise summary of a source that is still relevant
- `decision`: stable rationale and accepted trade-offs

Do not keep long chronological append logs in active pages.

## Completed Work Compression

An active plan must not grow forever.

Recommended handling:

1. Keep incomplete, blocked, partial, or risky items in the active plan.
2. Collapse completed work to a short summary.
3. Move detailed completed records into a `changelog` or `archive` page.
4. Remove completed rows from status tables unless they still affect current risk or validation.

## Changelog and Archive

Use `changelog` for chronological history and `archive` for inactive content. These pages may be long, but they must be categorized as on-demand pages in the topic index.

Current pages should keep only the most recent meaningful change summary, with a link to the changelog for older entries.

## Superseded Content

When a newer source, decision, or status replaces older wording:

1. Mark the old page or section as `superseded`.
2. Link to the replacement page.
3. Remove the old wording from active pages when possible.
4. If the old wording must remain for audit, move it to archive or changelog.

Superseded content must not be included in the default read set.

## Prototype and Mock Expiry

Prototype, mock, greybox, or temporary validation pages must declare one of these:

- an expiry date
- a promotion condition
- a removal condition
- the formal path that replaces it

Once the formal path exists, keep only the minimal current details in active pages: entry point, control switch, cleanup condition, and remaining risk. Move process details, old assumptions, and exploration notes into archive.

## Communication Notes

Communication templates, meeting prep, confirmation wording, and temporary discussion notes should live in `communication` pages or communication-specific archives. They should not be in an active engineering plan unless the current task is communication work.

## Archive Trigger Checklist

Archive or compress content when any of these are true:

- the content is completed and no longer affects current action
- the content is replaced by a newer source or decision
- the content is only useful for history
- the page exceeds its size budget
- the same status fact appears in multiple pages
- a temporary prototype or mock has met its promotion or expiry condition
