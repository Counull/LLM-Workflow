# Publication Guard

This repository is intended for public reuse. Every change must pass the public-safe test.

## Public-Safe Test

Before committing, ask:

1. Does this mention a real company, client, internal project, private repository, proprietary feature, issue ID, commit ID, or file path?
2. Would this sentence still make sense to someone outside the original workspace?
3. Could this reveal business plans, meeting content, architecture, customer information, credentials, or internal process details?
4. Is this a raw source or an instance-specific summary instead of a reusable rule or template?

If the answer is risky, do not commit it here.

## Allowed Content

- Generic workflow rules.
- Public-safe templates.
- Abstract examples.
- Links to public inspiration sources.
- Instructions for separating private instances from reusable workflow files.
- Integration notes for other public repositories.

## Disallowed Content

- Company-specific requirements, designs, logs, retrospectives, or test plans.
- Private meeting audio, transcripts, summaries, decisions, or participant lists.
- Proprietary code paths, commit hashes, diffs, issue IDs, branch names, build logs, or debug output.
- Screenshots of private tools or documents.
- Credentials, tokens, API keys, endpoint URLs, account names, or environment details.
- Real customer, vendor, partner, or employee information.

## Placeholder Style

Use placeholders instead of real private names:

| Private Context | Public Placeholder |
|---|---|
| Company or client name | `CompanyName` |
| Project name | `ProjectName` |
| Feature name | `FeatureName` |
| Person name | `OwnerName` |
| Date and time | `YYYY-MM-DD_HHMM` |
| Source document | `source-id` |
| Code path | `path/to/module` |

## Where Private Content Belongs

Private content belongs in a separate workflow instance, not this repository. A private instance can copy this workflow and add project-specific sources, indexes, summaries, and decisions.

## Agent Rule

If an AI agent is unsure whether content is public-safe, it must keep the content out of this repository and ask for review or place it in a private instance.
