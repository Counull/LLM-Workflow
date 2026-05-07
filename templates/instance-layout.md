# Workflow Instance Layout

Use this as a private workspace layout. Do not commit private instances to the public workflow repository.

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
LLM_WORKFLOW.md      optional pointer only
```

## Instance Rules

1. Keep raw sources in the private instance.
2. Keep reusable rules in the public workflow repository.
3. Update the feature or topic index after adding durable documents.
4. Mark uncertainty and source confidence explicitly.
5. Do not publish instance-specific documents unless they are reviewed and fully sanitized.
6. Keep machine-local absolute paths in `~/.llm-wiki/instances.json`, not in public workflow files or synced agent templates.
7. Keep each topic index explicit about default read set, status source, source docs, archive docs, and superseded docs.
8. Keep communication notes outside the default engineering read set.
