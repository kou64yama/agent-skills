---
name: create-pull-request
description: Prepare or create a GitHub pull request using the full change history and repository conventions.
---

# Create a Pull Request

Identify the target repository, base, and head. Inspect the complete base-to-head commit log and diff to understand the change and write an accurate title and description. Include relevant verification and disclose checks not run.

Retrieve contribution guidelines and PR templates from the target repository's GitHub API, preferring GraphQL `contributingGuidelines` and `pullRequestTemplates` over local files. Use what the API returns without separately resolving inherited defaults. Note any information the API cannot retrieve. Select the applicable template; if multiple choices are plausible and intent does not resolve the choice, ask the user. Follow its structure and applicable repository instructions without inventing facts.

Draft when asked for a draft or advice; create the PR when creation is authorized. Do not split the PR or rename the branch as part of this workflow.
