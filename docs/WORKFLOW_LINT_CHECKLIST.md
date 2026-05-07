# Workflow Lint Checklist

Use this checklist periodically, before handoff, or whenever a topic feels expensive for an agent to read.

## Read Policy

- Every active feature or topic has an `index` page.
- The index declares one `Status Source`.
- The index declares a `Default Read Set` with at most 3-4 pages.
- Source, archive, superseded, and communication pages are not in the default read set.
- Optional deep-dive docs are categorized separately from default docs.
- A new agent can answer "what should I read first?" from the index alone.

## Single Status Source

- Current mutable status exists in one canonical status page.
- Plans, digests, decisions, and logs link to status instead of copying full status tables.
- Current blockers, missing inputs, recommended next action, and risk state are not duplicated across pages.
- A small status change should not require editing many pages.

## Source and Digest Split

- Long raw sources are marked `source-only`.
- Long sources have a short `digest` when they affect daily work.
- Routine tasks read the digest first, not the raw source.
- Digest pages include source reference, scope, durable facts, decisions, risks, and open questions.
- Exact source reading is reserved for quote checks, audits, or contradiction resolution.

## Lifecycle and Archive

- Active pages do not contain large chronological logs.
- Old append-only history is moved to `changelog` or `archive`.
- Superseded pages or sections are marked `superseded` and link to replacement content.
- Archived and superseded content is excluded from default context.
- Communication templates, meeting prep, and outward-facing drafts are not mixed into active engineering pages.

## Completed Work

- Active plans focus on incomplete, blocked, partial, and risky work.
- Completed items are collapsed into a short summary.
- Detailed completed records live in `changelog` or `archive`.
- Status tables are not growing indefinitely with finished rows.

## Prototype and Mock Content

- Prototype, mock, greybox, or temporary validation docs declare expiry, promotion, or removal conditions.
- Once the formal path exists, active docs retain only current entry point, control switch, cleanup condition, and remaining risk.
- Detailed temporary process notes are archived.

## Context Budget

- `status` pages are roughly 80-120 lines.
- Active plans are roughly 150 lines or less.
- Digests are roughly 50-100 lines.
- Index pages route rather than restating every document.
- No active page has become "half of the main document" by answering every question at once.

## Public and Private Boundary

- Public workflow files contain only generic rules, placeholders, and public-safe examples.
- Private instance facts, paths, project names, source details, meeting content, code paths, issue IDs, and commit IDs stay out of public repositories.
- If content only makes sense in one private instance, it is not reusable workflow content.

## Suggested Lint Output

For each finding, report:

| Field | Meaning |
|---|---|
| Severity | `blocking`, `high`, `medium`, or `low`. |
| Page | Page or section that needs maintenance. |
| Problem | What violates the workflow. |
| Fix | Link, compress, split, archive, mark superseded, or update index. |
