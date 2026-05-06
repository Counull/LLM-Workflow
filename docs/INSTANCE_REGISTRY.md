# Instance Registry

LLM Wiki agents need a way to resolve a private workflow instance from a short instance ID. The local path is machine-specific, so it belongs in a local registry rather than this public workflow repository or a synced agent template.

## Default Location

```text
~/.llm-wiki/instances.json
```

This file is local machine state. It can be backed up privately, but it should not be committed to public workflow or skills repositories.

## Registry Shape

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

## Fields

| Field | Requirement |
|---|---|
| `schemaVersion` | Registry schema version. Start with `1`. |
| `defaultInstanceId` | Optional default instance used when no instance ID is provided. |
| `instances[].id` | Stable short ID used in prompts and agent handoffs. |
| `instances[].name` | Human-readable name. |
| `instances[].path` | Local path to the private workflow instance. |
| `instances[].scope` | Usually `private`; other values are host-specific. |
| `instances[].canonicalWorkflowRepo` | Public workflow repository used by the instance. |
| `instances[].skillsRepo` | Runtime skills repository used by the instance. |
| `instances[].createdAt` | Creation date in `YYYY-MM-DD` format. |
| `instances[].updatedAt` | Last registry update date in `YYYY-MM-DD` format. |

Tools may preserve unknown fields so local teams can add private metadata without changing this public schema.

## Resolution Rules

1. If the user provides a path, use that path for the current task.
2. If the user provides an instance ID, look it up in the registry.
3. If no path or ID is provided and `defaultInstanceId` exists, use that instance.
4. If multiple instances exist and no default is set, ask the user to choose.
5. If the registry is missing, ask for a target path and offer to create the registry during bootstrap.

## Bootstrap Rules

During private instance bootstrap:

1. Create `~/.llm-wiki/instances.json` if missing.
2. Add or update the new instance entry.
3. Install or update the LLM Wiki custom agent from the skills repository.
4. Keep the custom agent generic; it reads the registry instead of embedding a path.
5. Write instance identity and workflow links into the private instance `README.md` and `AGENTS.md`.

## Boundary Rules

- Do not commit a real registry file to this public workflow repository.
- Do not include real local paths in examples.
- Do not put private instance paths into public skills.
- Do not put private instance paths into synced agent templates.
- If a path is needed for a private team, store it in a private registry or private instance document.
