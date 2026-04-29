# LLM Workflow

A reusable Markdown workflow for building a personal or team knowledge layer with LLM agents.

This repository stores the portable workflow, templates, and maintenance rules only. It must not contain company documents, private meeting transcripts, proprietary code, customer data, project-specific decisions, or any other sensitive source material.

## Core Idea

The workflow separates knowledge work into three layers:

| Layer | Purpose |
|---|---|
| Raw sources | Original documents, meeting audio, transcripts, diffs, links, notes, and files. These remain immutable and instance-specific. |
| Knowledge layer | LLM-maintained Markdown summaries, decisions, designs, logs, and indexes. |
| Rules and navigation | Agent instructions, workflow rules, templates, indexes, and publication guards. |

The reusable part lives in this repository. Each company, project, or private workspace should keep its own instance outside this public repo.

## Repository Contents

| Path | Purpose |
|---|---|
| [LLM_WORKFLOW.md](LLM_WORKFLOW.md) | Portable workflow protocol. |
| [AGENTS.md](AGENTS.md) | Agent-facing rules for maintaining this repository. |
| [docs/PUBLICATION_GUARD.md](docs/PUBLICATION_GUARD.md) | Rules that prevent reusable workflow files from being polluted by private context. |
| [docs/SKILLS_INTEGRATION.md](docs/SKILLS_INTEGRATION.md) | How this workflow should interact with a separate skills repository. |
| [docs/BOOTSTRAP_NEW_INSTANCE.md](docs/BOOTSTRAP_NEW_INSTANCE.md) | Checklist for starting a new private workflow instance. |
| [templates/](templates/) | Public-safe templates for indexes, meetings, source notes, and workflow instances. |

## Recommended Instance Layout

Copy or adapt [templates/instance-layout.md](templates/instance-layout.md) into a private workspace:

```text
00_inbox/
01_requirements/
02_index/
03_design/
04_research/
05_development-log/
06_testing/
07_retrospective/
08_tools/
09_meetings/
99_archive/
```

The exact names can be localized. Keep the roles stable.

## GitHub Safety Rule

Before committing to this public repository, verify that the change is reusable without private context. If a sentence only makes sense inside one company, one client project, or one private codebase, it belongs in that private instance, not here.

## Related Repositories

- Skills repository: <https://github.com/Counull/UniSkills.git>
- Runtime skill: [llm-workflow-maintainer](https://github.com/Counull/UniSkills/tree/main/llm-workflow-maintainer)
- Workflow repository: <https://github.com/Counull/LLM-Workflow.git>

For new projects, follow [docs/BOOTSTRAP_NEW_INSTANCE.md](docs/BOOTSTRAP_NEW_INSTANCE.md).

## Inspiration

This workflow is inspired by Andrej Karpathy's LLM Wiki pattern:

- Gist page: [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- Raw Markdown: [llm-wiki.md](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f/raw/ac46de1ad27f92b28ac95459c782c07f6b8c964a/llm-wiki.md)

Embed snippet for systems that support GitHub Gist embedding:

```html
<script src="https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f.js"></script>
```

