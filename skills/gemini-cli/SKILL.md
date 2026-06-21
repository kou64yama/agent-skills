---
name: gemini-cli
description: Invoke Gemini CLI from Codex for advisory help, second opinions, or persistent Gemini conversations. Use when Codex should send a prompt to Gemini, start a new Gemini CLI session with a UUID via --session-id, or continue a prior Gemini CLI conversation with --resume.
---

# Gemini CLI

Invoke `gemini` directly. Store the prompt in a shell variable when it contains
quotes, newlines, or other shell-sensitive text.

## Start A Session

Generate and keep a UUID for the session. Run:

```bash
session_id="$(uuidgen | tr '[:upper:]' '[:lower:]')"
gemini --skip-trust --session-id "$session_id" -p "$prompt"
```

Report the session ID when the user may want to continue the Gemini
conversation later.

## Resume A Session

Reuse the exact session ID from the earlier call. Run:

```bash
gemini --skip-trust --resume "$session_id" -p "$prompt"
```

For a short literal prompt, call the same commands with a quoted literal:

```bash
gemini --skip-trust --session-id "$session_id" -p '<prompt>'
gemini --skip-trust --resume "$session_id" -p '<prompt>'
```

## Optional Arguments

- `--model model`: Select the Gemini model to use. Replace `model` with the desired model name.
- `--approval-mode default|auto_edit|yolo|plan`: Select how Gemini handles tool approval.
  - `default`: Use the standard approval behavior.
  - `auto_edit`: Automatically approve edit operations.
  - `yolo`: Automatically approve all tool operations.
  - `plan`: Operate in planning mode without applying changes.
- `--output-format text|json|stream-json`: Select Gemini CLI output format.

Use optional arguments only when requested or needed for the task. Place them
before `-p`:

```bash
gemini --skip-trust --session-id "$session_id" \
  --model "$model" \
  --approval-mode "$approval_mode" \
  --output-format "$output_format" \
  -p "$prompt"
```

Prefer `default` when no approval behavior is specified.

Capture Gemini's standard output and report it to the user. Preserve the session ID when additional turns are likely. Treat Gemini's response as advisory: verify claims against the workspace before editing code or presenting factual conclusions.
