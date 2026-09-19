---
name: technical-writing-review
description: Review technical documents for clarity, structure, accuracy, and task success. Use for README files, design documents, API documentation, and operational procedures; not for copyediting alone.
---

# Technical Writing Review

Review a technical document from its intended reader’s perspective. Focus on whether the reader can understand the purpose, trust the content, and complete the task safely.

## Establish context

Use the request and document to identify its audience, purpose, and expected reader outcome. If essential context is absent, state the assumption that guides the review and call out the missing context; do not invent technical facts. Match the language of the source document unless the user asks otherwise.

Distinguish internal consistency from factual accuracy. When you cannot verify a
technical claim against an authoritative source, the code, or an execution
environment, do not state that it is wrong or correct; identify it as needing
validation and say what evidence would confirm it.

Apply the relevant checks rather than treating every document as the same:

- For all documents, assess audience fit, purpose, structure, terminology, accuracy claims, and whether the most important information is easy to find.
- For procedures, assess prerequisites, ordering, expected results, safe recovery from failures, and whether commands, paths, parameters, and examples are usable as written. Where relevant, also assess destructive actions, required permissions, handling of credentials, target scope, pre-execution checks, backups, and rollback.
- For API or reference documentation, assess completeness of inputs, outputs, constraints, errors, defaults, and examples. Where relevant, assess authentication, versioning, limits, pagination, compatibility, and deprecation behavior.
- For design documents, assess problem framing, decisions, alternatives, consequences, assumptions, open questions, success criteria, and non-goals. Assess ownership and timeline when they are necessary for the document's purpose.

## Report findings

Report only actionable findings. Classify them by reader impact:

- **Critical**: likely to cause an incorrect, unsafe, or blocked outcome.
- **Important**: materially reduces comprehension, confidence, or successful task completion.
- **Suggestion**: improves readability, navigation, or efficiency without preventing success.

For each finding, give a location that makes the issue easy to find again: prefer a heading and short excerpt, and use a line number when one is available. Explain the reader impact and propose a concrete improvement. Supply a short replacement or addition when it makes the improvement unambiguous. Do not rewrite the entire document or edit files unless the user explicitly asks.

Do not mistake personal style preferences for defects. If no meaningful issues remain, say so briefly and list only unresolved facts that need confirmation.

## Default response shape

Start with a concise assessment of whether the document serves its apparent audience and purpose. Then list findings in priority order. Finish with open questions or validation needed, if any.
