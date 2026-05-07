# Context Budget and Compression Rules

LLM Wiki pages should optimize for the next agent's first useful read. Completeness and working usefulness belong in different layers.

## Size Budget

Recommended budgets are guidelines, not hard limits. If a page exceeds the budget, compress, split, or archive before adding more detail.

| Page Type | Suggested Size | Compression Target |
|---|---:|---|
| `index` | 50-120 lines | Route readers; do not summarize every page. |
| `status` | 80-120 lines | Current mutable truth only. |
| `plan` | Up to 150 lines | Incomplete, blocked, partial, and risky work. |
| `digest` | 50-100 lines | Durable facts and working implications from a source. |
| `decision` | 80-150 lines | Accepted decision, rationale, trade-offs, and consequences. |
| `changelog` | Unbounded but on-demand | Chronological audit trail. |
| `source` | Unbounded but source-only | Exact original material, not default context. |
| `archive` | Unbounded but on-demand | Historical or inactive material. |
| `communication` | Task-sized and on-demand | Meeting or stakeholder communication material. |

## Default Context Budget

For a normal topic task, the expected read path is:

1. topic index
2. default read set, at most 3-4 pages
3. optional deep-dive docs only when needed
4. source or archive only for traceability, contradiction resolution, or history work

If a task cannot be started without scanning many pages, the topic index or page layering needs maintenance.

## Compression Moves

Use these moves before adding more text to an active page:

| Problem | Preferred Move |
|---|---|
| Same current status appears in several pages | Keep it in `status`; replace copies with links. |
| Long source is repeatedly read | Create or refresh a `digest`; mark source as source-only. |
| Completed tasks dominate a plan | Summarize in one paragraph and move details to changelog. |
| Old wording appears in search results | Mark superseded and move to archive if possible. |
| Temporary prototype details distract from formal path | Keep only current switch, entry point, cleanup condition, and risk. |
| Communication drafts appear in engineering context | Move to communication notes or archive. |
| Every page feels like a main document | Split by page type and update the index read policy. |

## Writing for Reuse

Prefer links over repeated status snapshots. A page may include a one-line pointer to the canonical status source, but it should not duplicate the status table.

Prefer summaries over append-only logs in active pages. If history matters, link to the changelog.

Prefer source confidence labels over confident prose when a claim is inferred, old, or uncertain.

Prefer short current conclusions over replaying the whole analysis. Put deep rationale in design, decision, or archive pages.

## Maintenance Triggers

Run a compression pass when:

- a default read set grows beyond four pages
- a status page exceeds roughly 120 lines
- an active plan exceeds roughly 150 lines
- a digest exceeds roughly 100 lines
- source or archive pages are being read for routine tasks
- a small status update requires editing more than one canonical page
- search results surface multiple contradictory current states

The goal of compression is not to delete history. The goal is to keep current work small, routed, and traceable.
