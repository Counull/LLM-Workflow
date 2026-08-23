# Workflow Lint Checklist

Use this checklist periodically, before handoff, or whenever a topic feels expensive for an agent to read.

## Baseline Checks

- A normal task can start from one entry/index, one status page, and at most one additional relevant page.
- History, raw sources, and communication are not part of that default read.
- A private instance keeps private facts only and points to this protocol for generic rules.
- This public repository contains no private project facts or paths.

Run the deeper sections only when a baseline check fails or the topic is still costly to navigate.

## Read Policy

- Every private instance has one routing entry; a feature or topic gets its own `index` only when it needs an independent route.
- Each entry or topic index declares one `Status Source`.
- The entry lists at most 3-4 route links; a normal task opens status plus one relevant page.
- Source, archive, superseded, and communication pages are not in the default read set.
- Optional deep-dive docs are categorized separately from default docs.
- A new agent can answer "what should I read first?" from the entry or topic index alone.

## Single Status Source

- Current mutable status exists in one canonical status page.
- Plans, digests, decisions, testing records, and logs link to status instead of copying full status tables.
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

- Entry and `status` pages should be reviewed once they exceed roughly 40 lines.
- Active plans are roughly 150 lines or less.
- Digests are roughly 50-100 lines.
- Index pages route rather than restating every document.
- No active page has become "half of the main document" by answering every question at once.

## Public and Private Boundary

- Public workflow files contain only generic rules, placeholders, and public-safe examples.
- Private instance facts, paths, project names, source details, meeting content, code paths, issue IDs, and commit IDs stay out of public repositories.
- If content only makes sense in one private instance, it is not reusable workflow content.

## Optional Retrieval Adapter

- Each result includes an original source path or stable link.
- Cached context and model memory are treated as locators, not authority.
- Conflicts are checked against the instance's canonical source and reported explicitly.
- Query access does not imply permission to curate or write back.
- Retrieval failure or missing verifiable sources falls back to the Fast Path instead of blocking work.

## Suggested Lint Output

For each finding, report:

| Field | Meaning |
|---|---|
| Severity | `blocking`, `high`, `medium`, or `low`. |
| Page | Page or section that needs maintenance. |
| Problem | What violates the workflow. |
| Fix | Link, compress, split, archive, mark superseded, or update index. |
