# Document Layering and Default Read Policy

Use this policy to keep an LLM Wiki useful as it grows. The goal is for a new agent to enter a topic through a small, explicit route instead of scanning every related page.

## Core Rule

Every private instance needs one routing entry. Create a separate topic `index` only when that topic needs its own route. An entry must point to one status source; add source, archive, superseded, or communication groups only after those documents exist.

After reading the entry, an agent should read status and at most one relevant default page. Read deeper only for missing evidence, history, source verification, or communication work.

## Page Types

| Type | Purpose | Default Read? | Notes |
|---|---|---|---|
| `index` | Route a feature or topic. | First only when the route uses one. | Lists default and on-demand pages. |
| `status` | The canonical source for current mutable state in one route. | Usually yes. | Start with one project status; add a scoped topic status only with an independent topic route. |
| `plan` | Current implementation or maintenance plan. | Only when selected as the task's one relevant page. | Contains next actions, not repeated background. |
| `digest` | Short working summary of a long source. | Only when selected as the task's one relevant page. | Read this before the source. |
| `source` | Raw input or exact original material. | No. | Source-only; read only for exact wording or audit. |
| `decision` | Stable design or process decision. | Optional. | Should not duplicate active status tables. |
| `testing` | Real test, build, runtime, or acceptance evidence for one scope. | Only when the task needs that evidence. | Proves what was checked for that recorded scope and point in time; does not own current project status. |
| `changelog` | Chronological history. | No. | Used for audit and handoff history. |
| `archive` | Inactive, old, or replaced content. | No. | Must not shape current action unless explicitly requested. |
| `communication` | Meeting prep, confirmation wording, stakeholder notes, or external-facing drafts. | No. | Read only for communication tasks. |

## Canonical Status Source

Start with one project `status` page. Add a scoped topic `status` only when that topic has an independent route. A mutable fact must appear in exactly one status page.

Examples of mutable facts:

- current phase or readiness
- completed, blocked, or partially completed work
- missing fields, missing inputs, or open dependencies
- recommended next action
- current risks and validation state

Other pages may link to the status page, but they should not copy full status snapshots. If a plan, digest, decision, or testing record needs status context, use a short pointer such as `Current state: see <status-link>`.

## Default Read Set

An entry/index must declare the status source. Add the other groups only when corresponding documents exist:

| Group | Requirement |
|---|---|
| `Status Source` | One canonical status page. |
| `Default Read Set` | List at most 3-4 route links; a normal task opens status plus one relevant page. |
| `Optional Deep-Dive Docs` | Design, testing, research, or implementation pages used only when the question needs depth. |
| `Source Docs` | Raw source pages or source notes. Not default. |
| `Archive Docs` | Historical or inactive pages. Not default. |
| `Superseded Docs` | Replaced pages or sections. Not default and must be clearly marked. |
| `Communication Docs` | Meeting prep or outward-facing drafts. Not default for engineering tasks. |

The index may also list entry points, owners, and status labels, but those fields do not replace the status source.

## Source and Digest Split

When a long source affects routine work, use two layers:

1. `source`: complete original material, retained for traceability and marked `source-only`.
2. `digest`: short working summary with durable facts, decisions, risks, and open questions.

Keep rarely used material as source-only instead of creating an empty digest. When a digest exists, daily work should default to it; read the full source only when the digest is insufficient, exact wording matters, or a contradiction must be resolved.

## Communication Split

Communication notes are useful but should not become default engineering context. Put meeting prep, stakeholder questions, confirmation scripts, and outward-facing wording in `communication` pages or under an archive/communication area. Link them from the index as communication docs, not as default read set entries.

## Anti-Pattern

If every page answers "current status, next action, source summary, decisions, and history" at the same time, the topic has lost its routing structure. Split the content by page type, move history out of active pages, and point readers back to the index and status source.
