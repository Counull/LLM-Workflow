# LLM Workflow

## 1. Goal

This workflow turns raw sources and conversations into a persistent Markdown knowledge layer maintained with help from LLM agents.

The goal is not to upload every file to an LLM and rediscover context on each question. The goal is to maintain reusable, indexed, source-aware documents that compound over time.

## 2. Layers

| Layer | Description | Mutability |
|---|---|---|
| Raw sources | Original documents, meeting audio, transcripts, diffs, screenshots, web clips, and links. | Immutable or append-only. |
| Knowledge layer | Requirements analysis, design notes, implementation logs, meeting summaries, test records, retrospectives, and indexes. | Maintained by human + LLM. |
| Rules and navigation | Agent instructions, workflow rules, templates, indexes, and publication guards. | Maintained carefully. |

## 3. Recommended Instance Directories

| Directory | Purpose | Typical Files |
|---|---|---|
| `00_inbox` | Temporary intake for unclassified materials. | Web clips, notes, raw snippets. |
| `01_requirements` | Requirement analysis and acceptance criteria. | Requirement breakdowns, scope, i18n key lists. |
| `02_index` | Single navigation entry for features or topics. | Feature index, topic index. |
| `03_design` | Technical plans and future recovery paths. | Designs, migration guides, recovery guides. |
| `04_research` | External research and feasibility notes. | Tool reviews, API research, comparisons. |
| `05_development-log` | Implementation and change records. | Commit summaries, diff reviews, decisions. |
| `06_testing` | Test plans, test data, and acceptance records. | Checklists, manual test logs, issue tables. |
| `07_retrospective` | Stable lessons and reusable knowledge. | Postmortems, lessons learned, playbooks. |
| `08_tools` | Debug commands, scripts, tool manuals. | Debug guides, command references. |
| `09_meetings` | Meeting audio references, transcripts, summaries. | `transcript.md`, `summary.md`. |
| `10_communication` | Communication drafts, meeting prep, stakeholder questions, and external-facing notes. | Confirmation scripts, review questions, outreach drafts. |
| `99_archive` | Inactive or historical materials. | Archived notes, old drafts, superseded pages, changelogs. |

### 3.1 Document Layering and Read Policy

Each feature or topic should be routed through one index page and a small default read set. The index tells a future agent which pages to read first and which pages are source-only, archived, superseded, or communication-only.

Core rules:

1. Every topic has an `index` page.
2. Every topic has exactly one canonical `status` page for current mutable facts.
3. Long original material belongs in `source` pages and is not default context.
4. Long sources that affect daily work should have short `digest` pages.
5. Current plans should include remaining, blocked, partial, and risky work, not complete history.
6. Communication material should be separated from engineering context.

See [docs/DOCUMENT_LAYERING_AND_READ_POLICY.md](docs/DOCUMENT_LAYERING_AND_READ_POLICY.md) for page types and read policy.

### 3.2 Runtime Entry and Local Registry

A workflow instance may be maintained through a runtime skill and a custom agent, but local machine paths must stay outside public workflow files.

Recommended split:

| Item | Recommended Place | Notes |
|---|---|---|
| Runtime skills | User-configured skills location, sourced from the skills repository. | Do not vendor skills into this workflow repository. |
| Custom agent template | Skills repository. | Bootstrap can install it into the VS Code user or workspace agents directory. |
| Installed custom agent | VS Code user `agents/` or workspace `.github/agents/`. | Keep it generic; do not hardcode a private instance path. |
| Local instance link | `~/.llm-wiki/instances.json`. | Machine-local registry that maps instance IDs to paths. |
| Human entry point | Private instance `README.md`. | Describe the instance without relying on an absolute local path. |

See [docs/INSTANCE_REGISTRY.md](docs/INSTANCE_REGISTRY.md) for the registry format.

## 4. Standard Operations

### 4.1 Ingest

Use when adding a new source: requirement document, meeting transcript, web article, design note, commit diff, or external reference.

Steps:

1. Identify the source and record where it came from.
2. Keep the raw source in an instance-specific source-only location.
3. If the source is long and relevant to daily work, create or update a short digest.
4. Extract durable facts, decisions, open questions, and affected topics.
5. Update the canonical status page when current mutable state changes.
6. Create or update the relevant knowledge-layer pages without duplicating status snapshots.
7. Update the topic index and its default read set.
8. Record source date, scope, confidence, and follow-up actions.

### 4.2 Query

Use when answering a question against the knowledge layer.

Steps:

1. Read the index first.
2. Read only the default read set unless the task requires deeper evidence.
3. Read optional deep-dive docs only when the default set is insufficient.
4. Read raw sources, archive, superseded, or communication pages only when the task explicitly needs exact wording, history, audit, contradiction resolution, or communication material.
5. Answer with clear source boundaries.
6. If the answer produces reusable insight, file it back into the correct page type.
7. Update the index if a new durable page was created.

### 4.3 Lint

Use periodically or before handoff.

Check for:

1. Broken links.
2. Stale claims superseded by newer sources.
3. Contradictions between pages.
4. Orphan pages with no index entry or backlinks.
5. Important topics without dedicated pages.
6. Private details accidentally added to reusable workflow files.
7. Missing test, acceptance, or decision records.
8. Current status duplicated across multiple pages.
9. Source or archive pages included in the default read set.
10. Active pages containing superseded wording.
11. Completed tasks causing active plans or status tables to grow without bound.
12. Changelog or communication material mixed into current engineering context.
13. Prototype or mock notes without expiry, promotion, or removal conditions.
14. Pages that all behave like main documents instead of having clear types.

See [docs/WORKFLOW_LINT_CHECKLIST.md](docs/WORKFLOW_LINT_CHECKLIST.md) for the expanded checklist.

### 4.4 Meeting Audio and Transcripts

Recommended split:

| Stage | Recommended Place | Notes |
|---|---|---|
| Recording | Mobile device, tablet, or meeting tool. | Prioritize complete audio and accurate meeting time. |
| Rough transcription | Device or later processing. | Device transcription is fine if quality is acceptable. |
| Trusted summary | Workflow instance. | Extract decisions, action items, risks, changed requirements, and open questions. |

Recommended meeting folder:

```text
09_meetings/YYYY-MM-DD_HHMM_topic/
  audio/              optional audio files or links
  transcript.md       raw transcript, with uncertainty markers preserved
  summary.md          decisions, action items, risks, related topics
```

Rules:

1. Treat audio and transcripts as raw sources.
2. Do not rewrite a transcript into a decision record without marking uncertainty.
3. In summaries, separate `Decisions`, `Discussion Tendencies`, `Action Items`, and `Open Questions`.
4. If a meeting changes a feature, requirement, design, or test criterion, update the index and related pages.
5. Do not put transcripts or full raw notes in the default read set. Use a digest or meeting summary for daily work.
6. Do not upload sensitive audio or transcripts to uncontrolled external services.

## 5. Index Rules

Each indexed feature or topic should include:

| Field | Requirement |
|---|---|
| Name | Stable feature or topic name. |
| Status Source | One canonical status page for current mutable facts. |
| Default Read Set | At most 3-4 pages to read after the index. |
| Optional Deep-Dive Docs | Requirement, design, development log, recovery guide, test record, or meeting summary used on demand. |
| Source Docs | Raw sources or source-only pages. Not default context. |
| Archive Docs | Historical or inactive pages. Not default context. |
| Superseded Docs | Replaced pages or sections. Not default context. |
| Communication Docs | Meeting prep, confirmation wording, or outward-facing drafts. Not default engineering context. |
| Entry Points | Code, config, tool, system, or other concrete implementation anchors. |
| Owner | Person or team responsible, if applicable. |
| Status | Short state such as `analysis`, `design`, `development`, `testing`, `published`, `archived`. |
| Updated | Last meaningful update date. |

The index is a router. It should point to the status source instead of copying the current status table.

## 6. Source Confidence

Use explicit confidence labels:

| Label | Meaning |
|---|---|
| Source-stated | Directly stated by a source. |
| Code-observed | Observed in implementation or configuration. |
| Meeting-decision | Explicitly decided in a meeting. |
| Inferred | Reasonable inference that still needs validation. |
| Superseded | Historical claim replaced by newer information. |

Do not present inferred or superseded claims as current facts.

## 7. Document Page Rules

Important knowledge-layer pages should include enough metadata for a future reader or agent to evaluate the claim without replaying the whole conversation.

Recommended fields:

| Field | Purpose |
|---|---|
| Page Type | `index`, `status`, `plan`, `digest`, `source`, `decision`, `changelog`, `archive`, or `communication`. |
| Lifecycle | `active`, `draft`, `source-only`, `superseded`, or `archived`. |
| Date | When the page or decision was created. |
| Scope | Version, project, feature, topic, or time range the page applies to. |
| Source | Original document, meeting, diff, link, transcript, or other source reference. |
| Status Source | Link to the canonical status page when this page is not the status source. |
| Current Conclusion | The best current understanding. |
| Decision Rationale | Why this path was chosen over alternatives. |
| Risks | Known risks, edge cases, or blast radius. |
| Open Questions | Items that still require confirmation. |
| Follow-up | Validation, testing, implementation, or documentation actions. |

Keep reusable workflow files concise. Put instance-specific details in the private instance pages.

See [docs/PAGE_LIFECYCLE_AND_ARCHIVE.md](docs/PAGE_LIFECYCLE_AND_ARCHIVE.md) for lifecycle rules and [docs/CONTEXT_BUDGET_AND_COMPRESSION.md](docs/CONTEXT_BUDGET_AND_COMPRESSION.md) for size budgets.

## 8. Assets and Images

Image handling is instance-specific, but these rules are portable:

| Case | Recommendation |
|---|---|
| Small image tightly bound to one private note | A base64 data URI can be acceptable if the instance owner values single-file portability. |
| Long-lived or reviewed documentation | Prefer an `assets/` folder and relative links. |
| Public reusable workflow files | Avoid embedding private screenshots or binary assets. Use abstract diagrams or placeholders. |
| External wiki tools | Test compatibility before relying on base64 or embedded HTML. |

If base64 is used in a private instance, keep images small and accept that diffs will be hard to review.

## 9. Public vs Private Boundary

Reusable workflow rules, templates, and generic examples can be public.

Instance-specific materials must stay private:

- Company names and internal project names.
- Customer, vendor, or partner data.
- Proprietary requirements, source code, diffs, commit IDs, and architecture details.
- Meeting audio, transcripts, and summaries.
- Private file paths or environment details.

See [docs/PUBLICATION_GUARD.md](docs/PUBLICATION_GUARD.md) before publishing changes.

## 10. Agent Rules

Agents maintaining an instance should:

1. Read the index before reading scattered pages.
2. Follow the index default read set before opening optional pages.
3. Treat the status page as the only current mutable status source.
4. Keep raw sources separate from digests and synthesized pages.
5. Avoid reading source, archive, superseded, or communication pages by default.
6. Write reusable conclusions into the appropriate page type.
7. Update the index after adding durable pages.
8. Mark uncertainty explicitly.
9. Add a follow-up item instead of guessing when source context is missing.
10. Compress, archive, or link content when active pages exceed their context budget.
11. Keep public workflow files free of private context.

## 11. Inspiration

This workflow is inspired by Andrej Karpathy's LLM Wiki pattern:

- Gist page: [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- Raw Markdown: [llm-wiki.md](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f/raw/ac46de1ad27f92b28ac95459c782c07f6b8c964a/llm-wiki.md)
