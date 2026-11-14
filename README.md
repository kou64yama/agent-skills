# kou64yama-agent-plugins

Reusable agent skills distributed as purpose-specific portable Agent Plugins.
The repository marketplace makes each plugin available separately. Plugin
versions are managed independently.

## Plugins

| Plugin | Description |
| --- | --- |
| [`conventional-commits`](plugins/conventional-commits/) | Write and review Conventional Commits messages. |
| [`explain-artifacts`](plugins/explain-artifacts/) | Explain artifacts in a self-contained HTML page. |
| [`github-workflows`](plugins/github-workflows/) | Create issues and pull requests and merge pull requests using repository conventions. |
| [`review`](plugins/review/) | Coordinate independent reviews and format pull request review comments. |
| [`technical-writing`](plugins/technical-writing/) | Apply technical writing principles to documentation and error messages. |
| [`translation`](plugins/translation/) | Translation, proofreading, and multilingual reply workflows. |

## Installation

The repository includes a marketplace at
[`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json). In a
supported Codex CLI, add the repository as a marketplace and install the desired
plugin:

```sh
codex plugin marketplace add kou64yama/kou64yama-agent-plugins
codex plugin list --marketplace kou64yama-agent-plugins
codex plugin add translation@kou64yama-agent-plugins
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
