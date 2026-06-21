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

## Installation

Install a skill by copying or symlinking its directory into your Codex skills
directory:

```sh
mkdir -p ~/.codex/skills
ln -s "$(pwd)/skills/<skill-name>" ~/.codex/skills/<skill-name>
```

Alternatively, copy the directory if you prefer a standalone local install:

```sh
mkdir -p ~/.codex/skills
cp -R skills/<skill-name> ~/.codex/skills/
```

Restart Codex after installing or updating skills so it can discover the latest
definitions.

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
