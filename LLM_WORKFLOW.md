# LLM Workflow

## 1. Goal

This workflow turns raw sources and conversations into a persistent Markdown knowledge layer maintained with help from LLM agents.

The goal is not to upload every file to an LLM and rediscover context on each question. The goal is to maintain reusable, indexed, source-aware documents that compound over time.

## 1.1 Fast Path

The default path is deliberately short:

1. Read the private project's entry or index page.
2. Read its one canonical current `status` page.
3. Read at most one relevant active plan, digest, or decision.
4. Read history or sources only when exact evidence is necessary.
5. Write back only a material navigation or current-state change, durable decision, real validation result, or blocker.

The protocol owns portable reading, status, and write-back rules. A private instance owns only private facts and project constraints. When an instance duplicates a portable rule, remove it or replace it with a pointer to this protocol; generic rules in this protocol take precedence over duplicated instance wording. This does not override a genuinely project-specific constraint.

Skills, custom agents, registries, fixed folder trees, metadata, and automation are optional adapters. They are never prerequisites for using this protocol.

## 2. Layers

| Layer | Description | Mutability |
|---|---|---|
| Raw sources | Original documents, meeting audio, transcripts, diffs, screenshots, web clips, and links. | Immutable or append-only. |
| Knowledge layer | Requirements analysis, design notes, implementation logs, meeting summaries, test records, retrospectives, and indexes. | Maintained by human + LLM. |
| Rules and navigation | Agent instructions, workflow rules, templates, indexes, and publication guards. | Maintained carefully. |

## 3. Optional Expanded Instance Directories

Use this expanded layout only after the minimal entry/status path no longer makes retrieval easy.

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

### 3.1 Optional Document Layering and Read Policy

Create a separate topic index only when that topic needs its own route. The index tells a future agent which pages are current and which are source-only, archived, superseded, or communication-only.

Core rules:

1. A project starts with one entry and one project `status` page.
2. Add a scoped topic index/status only when that topic needs an independent route; each mutable fact has exactly one owner.
3. Long original material belongs in `source` pages and is not default context.
4. Long sources that affect daily work should have short `digest` pages.
5. Current plans should include remaining, blocked, partial, and risky work, not complete history.
6. Communication material should be separated from engineering context.

See [docs/DOCUMENT_LAYERING_AND_READ_POLICY.md](docs/DOCUMENT_LAYERING_AND_READ_POLICY.md) for page types and read policy.

### 3.2 Optional Host Adapters

Skills, custom agents, registries, and automation are host-specific conveniences, not part of the core protocol. Add them only when the host or number of instances requires them, and keep private paths or mappings local.

See [docs/SKILLS_INTEGRATION.md](docs/SKILLS_INTEGRATION.md) and [docs/INSTANCE_REGISTRY.md](docs/INSTANCE_REGISTRY.md) only when such an adapter is needed.

## 4. Standard Operations

### 4.1 Ingest

Use when adding a new source: requirement document, meeting transcript, web article, design note, commit diff, or external reference.

Steps:

1. Keep the raw source in the private instance and record where it came from.
2. Extract durable facts, decisions, open questions, and affected topics.
3. Create a digest only if the long source will affect routine work.
4. Update status or the entry route only when current facts or navigation changed.

### 4.2 Query

Use when answering a question against the knowledge layer.

Steps:

1. Read entry, status, and at most one task-relevant page.
2. Read deeper only for missing evidence, exact wording, history, or contradiction resolution.
3. Answer with clear source boundaries.
4. Apply the Fast Path write-back rule.

### 4.3 Lint

Use periodically or before handoff.

Check for:

1. Broken links, duplicated status, or contradictory current claims.
2. History, sources, or communication leaking into default context.
3. Private facts leaking into this reusable repository.
4. Active pages that have become too long to route quickly.

See [docs/WORKFLOW_LINT_CHECKLIST.md](docs/WORKFLOW_LINT_CHECKLIST.md) for the expanded checklist.

### 4.4 Meetings (Optional)

Keep recordings and transcripts as private raw sources. Create a short summary only when decisions, actions, risks, or requirements affect current work; preserve uncertainty and link back to the source. Do not preload raw transcripts or publish sensitive media.

## 5. Index Rules

Use this fuller index only after a topic needs several documents. The required part is a status source and a small default read set; all other fields are optional.

| Field | Requirement |
|---|---|
| Name | Optional stable feature or topic name. |
| Status Source | One canonical status page for current mutable facts. |
| Default Read Set | List at most 3-4 route links; the Fast Path opens status plus one relevant page. |
| Optional Deep-Dive Docs | Add only after a design, test, source, history, or communication record exists. |
| Source Docs | Add only when raw sources exist; never default context. |
| Archive Docs | Add only when historical or inactive material exists. |
| Superseded Docs | Add only when a page or section was replaced. |
| Communication Docs | Add only for communication material; never default engineering context. |
| Entry Points | Optional concrete implementation anchors. |
| Owner | Optional person or team responsible. |
| Status | Optional short label such as `analysis`, `design`, `development`, `testing`, `published`, `archived`. |
| Updated | Optional last meaningful update date. |

The index is a router. It should point to the status source instead of copying the current status table.

## 6. Source Confidence

Use confidence labels when a claim is inferred, stale, disputed, or high-impact:

| Label | Meaning |
|---|---|
| Source-stated | Directly stated by a source. |
| Code-observed | Observed in implementation or configuration. |
| Meeting-decision | Explicitly decided in a meeting. |
| Inferred | Reasonable inference that still needs validation. |
| Superseded | Historical claim replaced by newer information. |

Do not present inferred or superseded claims as current facts.

## 7. Document Page Rules

Add metadata only when it helps a future reader evaluate the page. Common fields are page type, lifecycle, date, scope, source, and status source. A decision should state its conclusion and rationale; active work should state only relevant risks, open questions, and follow-up. Do not add empty fields for compliance.

Keep reusable workflow files concise. Put instance-specific details in the private instance pages.

See [docs/PAGE_LIFECYCLE_AND_ARCHIVE.md](docs/PAGE_LIFECYCLE_AND_ARCHIVE.md) for lifecycle rules and [docs/CONTEXT_BUDGET_AND_COMPRESSION.md](docs/CONTEXT_BUDGET_AND_COMPRESSION.md) for size budgets.

## 8. Assets and Images

Keep private assets in the private instance. Prefer an `assets/` folder and relative links for maintained documents; use base64 only for a small, private, self-contained note. Do not publish private screenshots or binaries, and verify host compatibility before relying on embedded formats.

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

1. Start from entry and status, not a directory scan.
2. Read one more page only when the task needs it.
3. Mark uncertainty instead of guessing.
4. Apply the Fast Path write-back rule.
5. Keep portable rules here and private facts in the instance.

## 11. Inspiration

This workflow is inspired by Andrej Karpathy's LLM Wiki pattern:

- Gist page: [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- Raw Markdown: [llm-wiki.md](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f/raw/ac46de1ad27f92b28ac95459c782c07f6b8c964a/llm-wiki.md)
