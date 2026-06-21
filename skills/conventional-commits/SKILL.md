---
name: conventional-commits
description: Write, review, explain, or repair commit messages using the Conventional Commits 1.0.0 specification. Use when Codex needs to draft commit messages, validate commit history, choose commit types/scopes, describe breaking changes, or make commits that should follow Conventional Commits.
---

# Conventional Commits

Use the Conventional Commits 1.0.0 specification as the source of truth:
https://www.conventionalcommits.org/en/v1.0.0/

## Message Shape

Use this structure:

```text
<type>[optional scope][!]: <description>

[optional body]

[optional footer(s)]
```

- Use `feat` for a new feature.
- Use `fix` for a bug fix.
- Use `!` before `:` or a `BREAKING CHANGE:` footer for breaking API changes.
- Use other types when they describe the work better, such as `docs`, `test`,
  `refactor`, `chore`, `ci`, `build`, `style`, or `perf`.
- Add a scope in parentheses only when it gives useful context, for example
  `feat(parser): support arrays`.

## Drafting Guidance

- Choose one primary type that reflects the user-visible or release-relevant
  intent of the change.
- Keep the description short, imperative, and lower-case unless a proper noun or
  code identifier requires capitalization.
- Use a body when the commit needs motivation, context, or implementation notes
  that do not fit in the description.
- Use footers for machine-readable metadata such as `Refs: #123`,
  `Reviewed-by: Name`, or `BREAKING CHANGE: description`.
- Split unrelated changes into multiple commits whenever possible instead of
  forcing several intents into one message.

## Reviewing Guidance

- Verify the message has a type, colon, space, and description.
- Verify `feat`, `fix`, and breaking-change markers match the actual change.
- Treat `BREAKING CHANGE` and `BREAKING-CHANGE` as equivalent footer tokens.
- Prefer project-local conventions when they are stricter than the base
  specification.
