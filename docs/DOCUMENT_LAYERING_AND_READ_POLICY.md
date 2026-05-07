# Document Layering and Default Read Policy

Use this policy to keep an LLM Wiki useful as it grows. The goal is for a new agent to enter a topic through a small, explicit route instead of scanning every related page.

## Core Rule

Every topic must have an `index` page. The index is the routing entry and must declare the default read set, status source, source docs, archive docs, and superseded docs.

After reading the index, an agent should read only the default read set unless the task explicitly asks for history, source verification, or communication material.

## Page Types

| Type | Purpose | Default Read? | Notes |
|---|---|---|---|
| `index` | Route a feature or topic. | Always first. | Lists default and on-demand pages. |
| `status` | The only canonical source for current mutable state. | Usually yes. | Tracks current state, blockers, risks, missing inputs, and recommended next action. |
| `plan` | Current implementation or maintenance plan. | Yes, if active. | Contains next actions, not repeated background. |
| `digest` | Short working summary of a long source. | Yes, when relevant. | Read this before the source. |
| `source` | Raw input or exact original material. | No. | Source-only; read only for exact wording or audit. |
| `decision` | Stable design or process decision. | Optional. | Should not duplicate active status tables. |
| `changelog` | Chronological history. | No. | Used for audit and handoff history. |
| `archive` | Inactive, old, or replaced content. | No. | Must not shape current action unless explicitly requested. |
| `communication` | Meeting prep, confirmation wording, stakeholder notes, or external-facing drafts. | No. | Read only for communication tasks. |

## Canonical Status Source

Current mutable facts must live in exactly one `status` page per topic.

Examples of mutable facts:

- current phase or readiness
- completed, blocked, or partially completed work
- missing fields, missing inputs, or open dependencies
- recommended next action
- current risks and validation state

Other pages may link to the status page, but they should not copy full status snapshots. If a plan, digest, or decision needs status context, use a short link such as `Current state: see [status](path/to/status.md)`.

## Default Read Set

Each topic index must declare these groups:

| Group | Requirement |
|---|---|
| `Status Source` | One canonical status page. |
| `Default Read Set` | At most 3-4 pages to read after the index. Usually status, active plan, and one digest or decision. |
| `Optional Deep-Dive Docs` | Design, testing, research, or implementation pages used only when the question needs depth. |
| `Source Docs` | Raw source pages or source notes. Not default. |
| `Archive Docs` | Historical or inactive pages. Not default. |
| `Superseded Docs` | Replaced pages or sections. Not default and must be clearly marked. |
| `Communication Docs` | Meeting prep or outward-facing drafts. Not default for engineering tasks. |

The index may also list entry points, owners, and status labels, but those fields do not replace the status source.

## Source and Digest Split

Long sources must be split into two layers:

1. `source`: complete original material, retained for traceability and marked `source-only`.
2. `digest`: short working summary with durable facts, decisions, risks, and open questions.

Daily work should default to the digest. Read the full source only when the digest is insufficient, when exact wording matters, or when resolving a contradiction.

## Communication Split

Communication notes are useful but should not become default engineering context. Put meeting prep, stakeholder questions, confirmation scripts, and outward-facing wording in `communication` pages or under an archive/communication area. Link them from the index as communication docs, not as default read set entries.

## Anti-Pattern

If every page answers "current status, next action, source summary, decisions, and history" at the same time, the topic has lost its routing structure. Split the content by page type, move history out of active pages, and point readers back to the index and status source.
