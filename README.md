# Agent Skills

Personal Codex skill definitions and related agent metadata.

This repository is a home for reusable agent skills. Each skill lives in its
own directory and can include the skill definition, agent-specific metadata,
supporting prompts, scripts, or assets.

## Repository Layout

```text
skills/
  <skill-name>/
    SKILL.md
    agents/
      <agent>.yaml
```

Add new skills as sibling directories under `skills/`.

## Skills

Each subdirectory under `skills/` is an installable skill. See the `SKILL.md`
inside each skill directory for its purpose, trigger description, and operating
instructions.

| Skill | Description |
| --- | --- |
| [`conventional-commits`](skills/conventional-commits/SKILL.md) | Write and review commit messages using the Conventional Commits 1.0.0 specification. |
| [`multi-agent-review`](skills/multi-agent-review/SKILL.md) | Coordinate independent reviews and validate their findings. |
| [`proofread-non-native`](skills/proofread-non-native/SKILL.md) | Evaluate and improve non-native-language text, explaining revisions in the user's native language. |
| [`reply-in-non-native`](skills/reply-in-non-native/SKILL.md) | Translate incoming messages and outgoing replies using conversation context. |
| [`technical-writing-review`](skills/technical-writing-review/SKILL.md) | Review technical documents for clarity, structure, accuracy, and task success. |
| [`translate`](skills/translate/SKILL.md) | Select the appropriate translation skill and retain language, style, and conversation settings. |
| [`translate-to-native`](skills/translate-to-native/SKILL.md) | Translate foreign-language text into the user's native language with explanations of key choices. |
| [`translate-to-non-native`](skills/translate-to-non-native/SKILL.md) | Translate native-language text into another language with the requested style. |

The integrated `translate` workflow also requires the four standalone skills:
`translate-to-native`, `translate-to-non-native`, `proofread-non-native`, and
`reply-in-non-native`. Install them alongside `translate`; each standalone skill
can also be used independently.

## Installation

Install skills with the [`vercel-labs/skills`](https://github.com/vercel-labs/skills)
CLI:

```sh
npx skills add kou64yama/agent-skills -a codex
```

Install a specific skill by name:

```sh
npx skills add kou64yama/agent-skills -a codex --skill <skill-name>
```

Install globally so the skills are available across projects:

```sh
npx skills add kou64yama/agent-skills -a codex -g
```

List available skills without installing:

```sh
npx skills add kou64yama/agent-skills --list
```

The `skills` CLI can install from GitHub shorthand, full GitHub URLs, local
paths, and direct paths to a skill directory. Restart Codex after installing or
updating skills so it can discover the latest definitions.

## Usage

Reference the skill by name in a coding request:

```text
Use $<skill-name> to help with this task.
```

Some skills may also include agent-specific metadata under `agents/`, such as
display names, short descriptions, or default prompts.

## Development

Skill behavior lives in each skill's `SKILL.md`. Keep instructions concise,
action-oriented, and easy for an agent to apply during an active session.

When updating a skill, check that:

- the YAML front matter has a clear `name` and `description`;
- the usage trigger is specific enough to avoid accidental activation;
- the workflow gives practical guidance without over-constraining the agent;
- related agent metadata remains aligned with the skill.

When adding a new skill:

- create `skills/<skill-name>/SKILL.md`;
- include clear YAML front matter with `name` and `description`;
- add optional agent metadata under `skills/<skill-name>/agents/`;
- update this README with a short entry under [Skills](#skills).

## License

MIT. See [LICENSE](./LICENSE) for details.
