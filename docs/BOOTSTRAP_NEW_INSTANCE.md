# Bootstrap a New Workflow Instance

Use this checklist to start a private project, client, research, or personal instance.

## Two-Minute Start

1. Create one private entry page from [project-entry.md](../templates/project-entry.md).
2. Create one private status page from [status.md](../templates/status.md).
3. Set the status link, canonical workflow link, project routes, and project-specific constraints.
4. Follow the [Fast Path](../LLM_WORKFLOW.md#fast-path).

No registry, skill, custom agent, fixed directory tree, or copied protocol file is required.

## Thirty-Second Smoke Test

Open a fresh conversation in the private instance. The setup passes when the agent:

- finds the entry and canonical status without scanning the workspace;
- states `Now`, `Next`, and `Blocked` with the status path as evidence;
- does not preload raw sources or history without an evidence need; and
- identifies where a hypothetical durable update belongs but does not edit without authorization.

## Keep the Roles Separate

| Place | Content |
|---|---|
| `LLM-Workflow` | Portable protocol, templates, and publication guard. |
| Private instance | Private facts, sources, status, decisions, and project constraints. |
| Optional skills repository | Host-specific reusable execution helpers. |

Link across these boundaries; do not copy the full protocol or private content between them.

## Add Only When Needed

| Need | Optional Addition | Guide |
|---|---|---|
| A tool must select among several instances by ID. | Local registry. | [INSTANCE_REGISTRY.md](INSTANCE_REGISTRY.md) |
| A repeated operation benefits from automation. | Skill or custom agent. | [SKILLS_INTEGRATION.md](SKILLS_INTEGRATION.md) |
| Entry and status no longer route the project well. | Expanded layout or topic index. | [instance-layout.md](../templates/instance-layout.md), [feature-index.md](../templates/feature-index.md) |
| A host needs local instructions. | A short local instruction that links the canonical workflow and lists only private constraints. | Host documentation |

## Before Publishing

Check reusable changes for private names, paths, sources, code, issue IDs, commit IDs, meeting content, credentials, accounts, and environment details. If the content needs private context to make sense, keep it in the private instance. See [PUBLICATION_GUARD.md](PUBLICATION_GUARD.md).
