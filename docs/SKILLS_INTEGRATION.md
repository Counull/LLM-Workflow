# Skills Integration

This workflow can be used alongside a separate skills repository.

## Repository Boundary

Keep workflow rules and skills separate:

| Repository | Purpose |
|---|---|
| `LLM-Workflow` | Workflow protocol, public-safe templates, indexing conventions, publication guard. |
| `UniSkills` | Reusable agent skills, each with its own `SKILL.md`, assets, and task-specific instructions. |

Public skills repository:

- <https://github.com/Counull/UniSkills.git>

Do not vendor skills into this workflow repository. Link to the skills repository and document how the workflow should call skills.

Runtime skills should live in the user's configured Copilot skills location, using `UniSkills` as the source of truth. A `skills/` folder inside a random project or workflow repository should be treated as documentation or staging only unless the host tool explicitly supports loading skills from that path.

## Runtime Agent Integration

The skills repository may also provide custom agent templates that are installed during bootstrap.

Recommended split:

| Asset | Source of Truth | Installed To |
|---|---|---|
| `llm-workflow-maintainer` skill | `UniSkills` | User-configured Copilot skills location. |
| `LLM Wiki Sync` agent template | `UniSkills` | VS Code user `agents/` or workspace `.github/agents/`. |
| Local instance registry | User machine | `~/.llm-wiki/instances.json`. |

The installed agent should resolve private instance paths through the registry. Do not hardcode an instance path in a public skill or a synced agent template.

## Skill Categories

Suggested public-safe skill categories:

| Skill Category | Purpose |
|---|---|
| source-ingest | Convert a source into a structured note. |
| meeting-summary | Turn transcripts into decisions, action items, and open questions. |
| workflow-lint | Check links, stale claims, orphan pages, and public/private boundary violations. |
| feature-index-update | Update a feature or topic index after new documents are created. |
| publication-scan | Scan public workflow changes for private context. |

Recommended concrete skill:

| Skill | Repository | Purpose |
|---|---|---|
| `llm-workflow-maintainer` | `UniSkills` | Thin execution layer for using this workflow, updating indexes, routing private/public content, and running publication checks. |

## Private vs Public Skills

Public skills may describe generic workflows and templates.

Private skills should stay outside public repositories when they include:

- Company-specific terminology.
- Proprietary source paths.
- Internal tool commands.
- Project-specific validation logic.
- Private document formats or data conventions.

## Agent Guidance

When maintaining this workflow:

1. Add generic reusable workflow rules here.
2. Add task-specific reusable procedures to the skills repository.
3. Keep project-specific skill variants in private workspace folders.
4. Mention skills by capability, not by private project context.
5. Run a publication scan before pushing either repository.

For bootstrapping a new private instance, see [BOOTSTRAP_NEW_INSTANCE.md](BOOTSTRAP_NEW_INSTANCE.md).
