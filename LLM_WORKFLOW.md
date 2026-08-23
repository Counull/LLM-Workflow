# LLM Workflow

## Purpose

A model-neutral Markdown protocol for turning sources and conversations into persistent, auditable project knowledge.

This repository owns portable rules and templates. Each private instance owns its sources, facts, routes, and project constraints. Link across that seam; do not copy the protocol into the instance.

## Fast Path

1. Read the private project's entry or index.
2. Read its one canonical current `status` page.
3. Read at most one relevant active plan, digest, or decision.
4. Read history or raw sources only for missing evidence, exact wording, or contradiction resolution.
5. Write back only a material navigation or current-state change, durable decision, real validation result, or blocker.

The write-back rule defines what is worth recording, not permission to edit. User instructions plus project and host rules still control every write.

## Core Invariants

- Start with one project entry and one project `status` page.
- Add a topic index or scoped status only when that topic needs an independent route; each mutable fact has exactly one owner.
- Keep raw sources out of default context. Create a digest only when a long source affects routine work.
- Mark inferred, stale, disputed, or superseded claims; do not present them as current facts.
- Portable rules here take precedence over duplicated generic wording in an instance, but never override a genuine project-specific constraint.
- Skills, retrieval tools, registries, fixed directory trees, metadata, and automation are optional adapters, never prerequisites.

## Standard Operations

| Operation | Contract |
|---|---|
| Ingest | Preserve the source or its reference; extract durable facts, decisions, risks, and questions; update status or navigation only when they materially change. |
| Query | Follow the Fast Path; read deeper only when evidence requires it; answer with clear source boundaries; apply the write-back rule. |
| Lint | Check broken links, duplicate or contradictory status, raw/history leakage, private-context leakage, and pages that are too large to route quickly. |

## Optional Guides

| Need | Guide |
|---|---|
| Start a private instance. | [Bootstrap](docs/BOOTSTRAP_NEW_INSTANCE.md) and the [minimal templates](templates/project-entry.md). |
| Add topic routes, lifecycle, archives, or compression. | [Document layering](docs/DOCUMENT_LAYERING_AND_READ_POLICY.md), [lifecycle](docs/PAGE_LIFECYCLE_AND_ARCHIVE.md), and [context budget](docs/CONTEXT_BUDGET_AND_COMPRESSION.md). |
| Add skills, retrieval, automation, or multi-instance lookup. | [Host adapters](docs/SKILLS_INTEGRATION.md) and the optional [instance registry](docs/INSTANCE_REGISTRY.md). |
| Tune GPT-family response style or use a ChatGPT Project. | [GPT-First Profile](docs/GPT_FIRST_PROFILE.md). |
| Audit an instance or prepare a public change. | [Lint checklist](docs/WORKFLOW_LINT_CHECKLIST.md) and [publication guard](docs/PUBLICATION_GUARD.md). |

The expanded directory layout lives only in [templates/instance-layout.md](templates/instance-layout.md). Add it after entry and status are no longer enough.

## Public and Private

Keep reusable rules, abstract examples, and templates here. Keep private names, sources, paths, code, decisions, meetings, credentials, and environment details in the private instance.

If unsure, keep the content private and use the [publication guard](docs/PUBLICATION_GUARD.md).

## Inspiration

Inspired by Andrej Karpathy's [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).
