# Contributing

Thank you for your interest in contributing to Agent Skills. Bug reports,
feature suggestions, documentation improvements, and code or skill changes are
welcome.

## Reporting issues

Search existing issues and pull requests before opening an issue. For a bug
report, include the steps to reproduce it, the expected and actual behavior,
and the relevant client and plugin versions. For a feature request, describe
the use case and the desired behavior.

For a substantial change or a new plugin, consider opening an issue first to
discuss the proposal.

## Pull requests

1. Fork the repository and clone your fork.
2. Create a branch from the repository's default branch.
3. Make and check your changes using the guidance below.
4. Push your branch to your fork and open a pull request against the default
   branch of this repository.

Keep each pull request focused. Describe the change and its purpose, link any
related issues, and explain how you verified it. Mention checks you could not
run. Respond to review feedback and push follow-up commits to the same branch.
Use a concise commit subject; Conventional Commit-style subjects such as
`docs: clarify skill setup` are welcome.

## Changes to skills and plugins

The [README](README.md) describes the repository layout and plugin installation.
When adding or changing a skill or plugin:

- Place each skill under `plugins/<plugin-name>/skills/<skill-name>/` with a
  `SKILL.md` containing YAML front matter with a clear `name` and `description`.
- Add `agents/openai.yaml` within each skill directory with an `interface`
  containing `display_name`, `short_description`, and `default_prompt`. Keep
  related skills and their relative links together, and place optional
  references and assets within the skill directory.
- For a new plugin, add a root `plugin.json`, register its repository-relative
  path in `.agents/plugins/marketplace.json`, and update the README's plugin
  table. Update the table when adding or removing skills or changing their
  `short_description`: use one row per skill, link to the plugin and skill,
  copy the `short_description` into the Description column, and sort by plugin
  name and then skill name in ascending order.
- Plugin versions are managed independently. Increment the affected plugin's
  version when releasing changes.
- Follow [`.editorconfig`](.editorconfig) for whitespace and file formatting.

## Checking changes

Review changed skills for clear triggers and instructions, valid metadata, and
working relative links. Check that referenced files exist, that README table
descriptions match their skill metadata, and that changed plugin and marketplace
manifests are valid JSON.

For local testing, add the checkout as a marketplace from the repository root
with `codex plugin marketplace add .` and install the relevant plugin as
described in the README. After changing a plugin, refresh its installed copy and
restart the client. Check that the skill is discoverable and exercise the
changed workflow with representative requests. There is no repository-wide
automated test suite.

## License

Contributions are subject to the repository's [MIT license](LICENSE).
