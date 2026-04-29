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
| `99_archive` | Inactive or historical materials. | Archived notes and old drafts. |

## 4. Standard Operations

### 4.1 Ingest

Use when adding a new source: requirement document, meeting transcript, web article, design note, commit diff, or external reference.

Steps:

1. Identify the source and record where it came from.
2. Keep the raw source in an instance-specific location.
3. Extract durable facts, decisions, open questions, and affected topics.
4. Create or update the relevant knowledge-layer pages.
5. Update the index.
6. Record source date, scope, confidence, and follow-up actions.

### 4.2 Query

Use when answering a question against the knowledge layer.

Steps:

1. Read the index first.
2. Open the most relevant pages.
3. Read raw sources only when the answer depends on exact wording or current facts.
4. Answer with clear source boundaries.
5. If the answer produces reusable insight, file it back into the knowledge layer.
6. Update the index if a new durable page was created.

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
5. Do not upload sensitive audio or transcripts to uncontrolled external services.

## 5. Index Rules

Each indexed feature or topic should include:

| Field | Requirement |
|---|---|
| Name | Stable feature or topic name. |
| Source | Original source or closest source reference. |
| Related Docs | Requirement, design, development log, recovery guide, test record, or meeting summary. |
| Entry Points | Code, config, tool, system, or other concrete implementation anchors. |
| Owner | Person or team responsible, if applicable. |
| Status | Short state such as `analysis`, `design`, `development`, `testing`, `published`, `archived`. |
| Updated | Last meaningful update date. |

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
| Date | When the page or decision was created. |
| Scope | Version, project, feature, topic, or time range the page applies to. |
| Source | Original document, meeting, diff, link, transcript, or other source reference. |
| Current Conclusion | The best current understanding. |
| Decision Rationale | Why this path was chosen over alternatives. |
| Risks | Known risks, edge cases, or blast radius. |
| Open Questions | Items that still require confirmation. |
| Follow-up | Validation, testing, implementation, or documentation actions. |

Keep reusable workflow files concise. Put instance-specific details in the private instance pages.

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
2. Keep raw sources separate from synthesized pages.
3. Write reusable conclusions into the appropriate knowledge-layer directory.
4. Update the index after adding durable pages.
5. Mark uncertainty explicitly.
6. Add a follow-up item instead of guessing when source context is missing.
7. Keep public workflow files free of private context.
