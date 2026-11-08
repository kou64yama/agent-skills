---
name: create-issue
description: Prepare or create a GitHub issue using repository issue templates and contribution rules.
---

# Create an Issue

Identify the target repository and retrieve its contribution guidelines and issue templates through the GitHub API, preferring GraphQL `contributingGuidelines` and `issueTemplates` over local files. Use what the API returns without separately resolving inherited defaults. Retrieve relevant YAML forms and `.github/ISSUE_TEMPLATE/config.yml` from the repository's default branch through the API when needed; distinguish chooser configuration from a form. State when a needed source cannot be checked.

Select the template matching the request; ask if multiple choices are plausible and intent does not resolve the choice. Follow its fields, required inputs, defaults, and applicable routing in `config.yml`. Render form responses as meaningful Markdown when creating through an interface that does not render the form. Ask for missing required information rather than inventing it. Respect external reporting routes and blank issue restrictions.

Draft when asked for a draft or advice; create the issue when creation is authorized.
