# LLM Workflow Repository Agent Rules

## Purpose

This repository stores reusable workflow rules and templates for LLM-maintained Markdown knowledge bases.

It is public-facing and must remain independent from any single company, client, project, or proprietary codebase.

## Read First

When modifying this repository, read these files first:

1. [LLM_WORKFLOW.md](LLM_WORKFLOW.md)
2. [docs/PUBLICATION_GUARD.md](docs/PUBLICATION_GUARD.md)
3. [docs/SKILLS_INTEGRATION.md](docs/SKILLS_INTEGRATION.md)

## Non-Negotiable Publication Rules

- Do not add company names, internal project names, private file paths, customer names, issue trackers, commit IDs, meeting transcripts, business logic, or proprietary implementation details.
- Do not copy private instance documents into this repository.
- Do not include raw sources. Keep raw sources in private instances.
- Do not vendor skills from a separate skills repository. Link to the skills repository instead.
- Keep examples generic, using placeholders such as `ProjectName`, `FeatureName`, `YYYY-MM-DD`, and `source-id`.
- If a reusable rule needs an example, prefer an abstract example over a real one.
- If a change could leak private context, stop and move it to the private instance instead.

## Maintenance Rules

- Keep [LLM_WORKFLOW.md](LLM_WORKFLOW.md) concise and operational.
- Put detailed rationale in `docs/` only when it helps maintainers make decisions.
- Put reusable formats in `templates/`.
- Keep [README.md](README.md) as the human-facing entry point.
- Update [docs/PUBLICATION_GUARD.md](docs/PUBLICATION_GUARD.md) when adding new public/private boundary rules.
- Use UTF-8 without BOM for Markdown files.
- The main branch must be named `main`.
