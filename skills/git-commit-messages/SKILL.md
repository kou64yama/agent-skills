---
name: git-commit-messages
description: Write, review, or improve readable Git commit messages based on common Git history conventions and Chris Beams' commit message guidance. Use when Codex needs to draft a plain Git commit message, add a useful body, evaluate subject/body style, or explain what makes a commit message good.
---

# Git Commit Messages

Use this skill to create commit messages that make project history useful to
future readers. Treat the diff as the record of what changed; use the message to
explain the change's intent, context, and consequences.

Primary source: Chris Beams, "How to Write a Git Commit Message":
https://cbea.ms/git-commit/

## Drafting Workflow

1. Inspect the change or user-provided summary.
2. Identify the single main intent of the commit.
3. Draft a concise subject line.
4. Add a body only when it provides context that the subject and diff cannot.
5. Review the result against the rules below.

If the change cannot be summarized as one coherent intent, recommend splitting
it into separate commits before polishing the message.

## Subject Rules

- Separate the subject from the body with one blank line when a body is present.
- Aim for a subject around 50 characters; treat 72 characters as the practical
  maximum before many tools truncate it.
- Start the subject with a capital letter.
- Do not end the subject with a period.
- Use imperative mood: write what applying the commit will do.
- Check the subject by reading it after "If applied, this commit will ...".

Examples of imperative subjects:

```text
Add retry handling for webhook delivery
Remove unused account migration path
Document cache invalidation behavior
```

Avoid subjects that merely describe past work or vague content:

```text
Fixed webhook retries
More cache docs
Various cleanup
```

## Body Guidance

Use a body when the reader needs motivation, trade-offs, or operational context.
Wrap body text at about 72 characters.

Good bodies explain:

- What changed at a higher level than the diff.
- Why the change is necessary.
- User-visible, operational, or compatibility impact.
- Important alternatives, constraints, or follow-up work.

Avoid using the body to narrate every implementation detail already visible in
the diff. Include how only when it clarifies a non-obvious decision.

## Review Checklist

- Does the subject summarize one coherent change?
- Is the subject short, imperative, and free of trailing punctuation?
- Is a blank line present between subject and body?
- Does the body explain why the change exists, not just how it was coded?
