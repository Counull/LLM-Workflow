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

## Good Candidates

- source ingest and digest creation
- meeting summary extraction
- link, lifecycle, and context-budget linting
- publication-boundary scanning
- route or index maintenance

Do not automate a one-off task merely to make the workflow look complete. Use the host's own documentation for discovery, installation, permissions, and local paths.
