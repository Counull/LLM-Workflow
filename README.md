# LLM Workflow

A model-neutral Markdown workflow for persistent project knowledge maintained with help from LLM agents.

This public repository contains portable rules and templates only. Private facts, sources, decisions, code, and paths stay in separate project instances.

## Two-Minute Start

1. Create a private entry page from [project-entry.md](templates/project-entry.md).
2. Create its canonical status page from [status.md](templates/status.md).
3. Add only project routes and project-specific constraints.
4. Follow the [Fast Path](LLM_WORKFLOW.md#fast-path): `entry → status → at most one relevant page`.

No registry, skill installation, custom agent, fixed directory tree, or copied protocol file is required.

## Repository Roles

| Place | Owns |
|---|---|
| This repository | Portable read, status, write-back, template, and publication rules. |
| Private instance | Private sources, facts, routes, decisions, and project constraints. |
| Optional adapter | Host-specific skills, retrieval, automation, or multi-instance lookup. |

Link across these roles instead of copying generic rules or private content.

## Guides

- [LLM_WORKFLOW.md](LLM_WORKFLOW.md): the small protocol Interface.
- [BOOTSTRAP_NEW_INSTANCE.md](docs/BOOTSTRAP_NEW_INSTANCE.md): private-instance setup and smoke test.
- [GPT_FIRST_PROFILE.md](docs/GPT_FIRST_PROFILE.md): concise GPT-family responses and optional ChatGPT Project instructions.
- [DOCUMENT_LAYERING_AND_READ_POLICY.md](docs/DOCUMENT_LAYERING_AND_READ_POLICY.md): optional topic routing and source/digest split.
- [SKILLS_INTEGRATION.md](docs/SKILLS_INTEGRATION.md): optional host and retrieval Adapter contract.
- [WORKFLOW_LINT_CHECKLIST.md](docs/WORKFLOW_LINT_CHECKLIST.md): maintenance checks.
- [PUBLICATION_GUARD.md](docs/PUBLICATION_GUARD.md): public/private review before publication.

## Templates

Start with [project-entry.md](templates/project-entry.md) and [status.md](templates/status.md). Add the [expanded layout](templates/instance-layout.md), [topic index](templates/feature-index.md), source digest, or meeting summary only when the project needs them. Remove unused placeholders.

## Related Repositories

- Skills repository: <https://github.com/Counull/UniSkills.git>
- Runtime skill: [llm-workflow-maintainer](https://github.com/Counull/UniSkills/tree/main/llm-workflow-maintainer)
- Workflow repository: <https://github.com/Counull/LLM-Workflow.git>

## Inspiration

Inspired by Andrej Karpathy's [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).
