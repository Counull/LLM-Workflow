# Optional Skills Integration

The protocol works without skills, custom agents, registries, or automation. Add a host adapter only when a stable, repeated operation benefits from one.

## Boundary

| Layer | Owns |
|---|---|
| Workflow protocol | Portable read, status, write-back, template, and publication rules. |
| Host adapter | A reusable execution procedure and host-specific configuration. |
| Private instance | Private facts, sources, paths, decisions, and project constraints. |

Keep host adapters in a host-supported location or a separate repository. Link to them instead of vendoring them into this protocol.

## Adapter Contract

1. Receive an explicit target path, entry page, or status page.
2. Follow the protocol's Fast Path and public/private boundary.
3. Read deeper only when the task needs evidence or history.
4. Apply the protocol's write-back rule and the host's authorization rules.
5. Never embed a private instance path or project semantics in a reusable adapter.

A registry is an independent optional adapter. A skill or custom agent must not require one when the target is already explicit.

## Optional Retrieval Adapter

A retrieval adapter may search project documents, history, or cached context without becoming a source of truth:

1. Return an exact original path or stable source link with each result.
2. Treat cache and model memory as locators, not authority; verify the original source before making a claim or taking action.
3. Resolve conflicts against the canonical source declared by the private instance and surface the contradiction.
4. A query never authorizes curation or write-back. User instructions plus project and host rules still control every write.
5. If retrieval is unavailable or returns no verifiable source, fall back to the Fast Path and report the limitation; optional retrieval must not block project work.

## Good Candidates

- source ingest and digest creation
- meeting summary extraction
- link, lifecycle, and context-budget linting
- publication-boundary scanning
- route or index maintenance

Do not automate a one-off task merely to make the workflow look complete. Use the host's own documentation for discovery, installation, permissions, and local paths.
