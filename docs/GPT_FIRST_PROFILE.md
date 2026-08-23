# GPT-First Profile

Use this as the default profile when GPT-family tools are the main readers. It favors direct instructions and a small, explicit context over broad preloading.

## Default Read

For a normal task, read only:

1. the project entry/index;
2. the canonical current status page; and
3. one active plan, digest, or decision only when the task needs it.

Do not preload changelogs, archives, raw sources, or large decision ledgers. Follow links as needed for evidence; ask the user only when authority or required input is missing.

## Response Style

- Lead with the result; include a next action only when the user must act.
- Default to 1-3 short paragraphs or at most five bullets; expand when requested or needed for clarity, correctness, or safety.
- Use short headings, direct verbs, and bullets only when they clarify a choice.
- Keep necessary constraints, uncertainty, evidence, and blockers even when the answer is short.
- Do not repeat the request, narrate routine tool use, or restate the same conclusion in several formats.

## Knowledge Write-back

- Prefer a link over repeating the same status in multiple pages.
- Keep status pages short; move chronology to a changelog.
- Apply the protocol's Fast Path write-back rule.

## Optional ChatGPT Project Adapter

When using a ChatGPT Project, add the private entry/status pages as project sources and use a concise project instruction such as:

> Read the project entry and current status before answering. Lead with the result and stay concise unless detail is requested or needed for clarity, correctness, or safety. Read one linked page only when needed. Do not treat chat memory as the authority for project facts.

Project instructions and project sources are host-tool conveniences. The private entry and status documents remain the auditable source of truth.

Official reference: [Projects in ChatGPT](https://help.openai.com/en/articles/10169521-projects-in-chatgpt).
