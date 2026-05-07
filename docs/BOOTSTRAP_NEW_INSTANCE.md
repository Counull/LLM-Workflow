# Bootstrap a New Workflow Instance

Use this checklist when starting a new private workflow instance for a project, client, research topic, or personal workspace.

## 1. Keep the Repository Roles Separate

| Place | Role |
|---|---|
| `LLM-Workflow` | Public canonical workflow rules, templates, and publication guard. |
| `UniSkills` | Runtime skills that agents can invoke. |
| Private instance | Project facts, raw sources, meeting notes, feature indexes, and implementation decisions. |

Do not copy private instance content into `LLM-Workflow` or `UniSkills`.

## 2. Install or Update Runtime Skills and Agent

Copilot skills are not automatically discovered just because a repository contains a `skills/` folder.

Keep runtime skills in the user's configured skills location, using `UniSkills` as the source of truth. Example locations:

```text
<user-home>/.copilot/skills/
<configured-copilot-skills-path>/
```

Recommended setup:

1. Clone or pull `UniSkills` into the user-level skills location.
2. Confirm the `llm-workflow-maintainer` skill exists there.
3. Install or update the LLM Wiki custom agent from the skills repository into the VS Code user agents directory, or into the target workspace `.github/agents/` when the agent should be project-scoped.
4. Keep the installed agent generic. It may know how to read an instance registry, but it must not hardcode a private instance path.
5. Do not vendor runtime skills into a project or workflow repository.

## 3. Register the Local Instance Link

The private instance path is machine-local state. Store it in a local registry instead of the public workflow repository or a synced agent template.

Default registry location:

```text
~/.llm-wiki/instances.json
```

Recommended shape:

```json
{
	"schemaVersion": 1,
	"defaultInstanceId": "instance-id",
	"instances": [
		{
			"id": "instance-id",
			"name": "Instance Display Name",
			"path": "path/to/private-instance",
			"scope": "private",
			"canonicalWorkflowRepo": "https://github.com/Counull/LLM-Workflow.git",
			"skillsRepo": "https://github.com/Counull/UniSkills.git",
			"createdAt": "YYYY-MM-DD",
			"updatedAt": "YYYY-MM-DD"
		}
	]
}
```

If multiple instances exist, the agent should ask for an instance ID unless `defaultInstanceId` is set.

## 4. Create a Private Instance Layout

Start from [templates/instance-layout.md](../templates/instance-layout.md), then localize names if needed.

Recommended roles:

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
10_communication/
99_archive/
AGENTS.md
README.md
```

Do not create a second full copy of `LLM_WORKFLOW.md` in the private instance unless it is only a tiny pointer file. Prefer linking to the canonical workflow document.

## 5. Add Instance Agent Instructions

The private instance `AGENTS.md` should include:

1. Link to the canonical workflow: `LLM-Workflow/LLM_WORKFLOW.md` or the public repository URL.
2. Link to the local index.
3. Link to the local README.
4. Private project constraints and source locations.
5. A public/private boundary rule: generic workflow changes go to `LLM-Workflow`; instance facts stay private.

Keep `AGENTS.md` short. It is an entry point, not the full workflow manual.

## 6. Create an Index First

Use [templates/feature-index.md](../templates/feature-index.md) or a localized equivalent.

The index should be the first place an agent reads when answering project-specific questions. It must declare the canonical status source, the default read set, source docs, archive docs, superseded docs, and communication docs. Keep the default read set to at most 3-4 pages.

Create or reserve a status page for each active topic before spreading status facts across plans, digests, or logs.

## 7. Publication Check

Before pushing reusable workflow or skill changes to a public repository, check for:

- Company, client, or project names.
- Private source paths or local machine paths.
- Proprietary requirements, code, diffs, issue IDs, or commit IDs.
- Meeting transcripts, meeting decisions, or participant data.
- Credentials, endpoints, accounts, or environment details.

If content only makes sense inside one private instance, keep it out of public repositories.
