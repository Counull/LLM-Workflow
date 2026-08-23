# GPT-First Profile

Use this optional adapter when GPT-family tools are the main readers. Apply the core protocol's Fast Path and write-back rule; this profile changes only response style and host setup.

## Response Style

- Lead with the result; include a next action only when the user must act.
- Default to 1-3 short paragraphs or at most five bullets; expand when requested or needed for clarity, correctness, or safety.
- Use short headings, direct verbs, and bullets only when they clarify a choice.
- Keep necessary constraints, uncertainty, evidence, and blockers even when the answer is short.
- Do not repeat the request, narrate routine tool use, or restate the same conclusion in several formats.

## Optional ChatGPT Project Adapter

Add the private entry and status pages as project sources and use a concise project instruction such as:

> Apply the linked LLM Workflow protocol. Lead with the result and stay concise unless detail is requested or needed for clarity, correctness, or safety. Do not treat chat memory as the authority for project facts.

Project instructions and project sources are host conveniences. The private entry and status documents remain canonical. When a durable fact changes, update those canonical documents under normal authorization and refresh any host copy when needed. A saved chat response is not canonical unless the private instance explicitly declares it so.

Official reference: [Projects in ChatGPT](https://help.openai.com/en/articles/10169521-projects-in-chatgpt).
