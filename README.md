# Agent Skills

Reusable agent skills distributed as purpose-specific portable Agent Plugins.
The repository marketplace makes each plugin available separately. Plugin
versions are managed independently; all start at `1.0.0`.

## Plugins and skills

| Plugin | Skill | Description |
| --- | --- | --- |
| [`conventional-commits`](plugins/conventional-commits/) | [`conventional-commits`](plugins/conventional-commits/skills/conventional-commits/SKILL.md) | Draft Conventional Commits messages
| [`explain-artifacts`](plugins/explain-artifacts/) | [`explain-artifacts`](plugins/explain-artifacts/skills/explain-artifacts/SKILL.md) | Explain artifacts in evidence-based standalone HTML
| [`github-workflows`](plugins/github-workflows/) | [`create-issue`](plugins/github-workflows/skills/create-issue/SKILL.md) | Help with Create Issue tasks
| [`github-workflows`](plugins/github-workflows/) | [`create-pull-request`](plugins/github-workflows/skills/create-pull-request/SKILL.md) | Help with Create Pull Request tasks
| [`github-workflows`](plugins/github-workflows/) | [`merge-pull-request`](plugins/github-workflows/skills/merge-pull-request/SKILL.md) | Help with Merge Pull Request tasks
| [`review`](plugins/review/) | [`multi-agent-review`](plugins/review/skills/multi-agent-review/SKILL.md) | Coordinate independent reviews and validation
| [`review`](plugins/review/) | [`pr-review-comments`](plugins/review/skills/pr-review-comments/SKILL.md) | Format and place PR review comments
| [`technical-writing`](plugins/technical-writing/) | [`technical-writing`](plugins/technical-writing/skills/technical-writing/SKILL.md) | Apply technical writing principles when creating or editing technical documentation, explanations, and error messages for a specific audience. |
| [`translation`](plugins/translation/) | [`proofread-non-native`](plugins/translation/skills/proofread-non-native/SKILL.md) | Review naturalness, consistency, and tone
| [`translation`](plugins/translation/) | [`reply-in-non-native`](plugins/translation/skills/reply-in-non-native/SKILL.md) | Translate incoming messages and outgoing replies
| [`translation`](plugins/translation/) | [`translate`](plugins/translation/skills/translate/SKILL.md) | Choose translation, proofreading, or reply support
| [`translation`](plugins/translation/) | [`translate-to-native`](plugins/translation/skills/translate-to-native/SKILL.md) | Understand text in your native language
| [`translation`](plugins/translation/) | [`translate-to-non-native`](plugins/translation/skills/translate-to-non-native/SKILL.md) | Express your text in another language

The `translate` coordinator uses the four other translation skills. The
`translation` plugin includes all of them, and each can also be used on its own.
See each `SKILL.md` for its purpose and instructions.

## Installation

The repository includes a marketplace at
[`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json). In a
supported Codex CLI, add the repository as a marketplace and install the desired
plugin:

```sh
codex plugin marketplace add kou64yama/agent-skills
codex plugin list --marketplace agent-skills
codex plugin add translation@agent-skills
```

Replace `translation` with any plugin name in the table. For local development,
run `codex plugin marketplace add .` from the repository root instead. The
marketplace can also be selected in the ChatGPT desktop app's Plugins Directory;
restart the app after adding a local marketplace. See the
[OpenAI plugin packaging documentation](https://developers.openai.com/plugins/build/plugins)
for supported clients and marketplace setup.

The former `npx skills add` repository-wide installation has not been verified
with this layout. Use the plugin marketplace for distribution.

## Usage

After installation, reference a skill by name in a request, for example:

```text
Use $translate to help with this task.
```

Some skills include agent-specific metadata under `agents/`.

## Repository layout and development

```text
.agents/plugins/marketplace.json
plugins/
  <plugin-name>/
    plugin.json
    skills/
      <skill-name>/
        SKILL.md
        agents/
        references/  # optional
        assets/      # optional
```

Each plugin owns its skills and portable root `plugin.json`. Keep related skills
that use relative links together. To add a skill, create its directory under the
appropriate plugin's `skills/` directory, add YAML front matter with a clear
`name` and `description`, and include any metadata or supporting files there.
For a new plugin, add a manifest and register its repository-root-relative path
in the marketplace. Update the table above and increment the affected plugin's
version when releasing changes.

When changing a skill, check its trigger, workflow, metadata, and relative links.
After changing a plugin, refresh its installed copy and restart the client before
testing discovery and behavior.

## License

MIT. See [LICENSE](./LICENSE) for details.
