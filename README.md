# Astral plugins for Claude Code

## Installation

### Add the marketplace

Add the Astral marketplace to Claude Code:

```bash
/plugin marketplace add astral-sh/claude-code-plugins
```

### Install the `astral` plugin

After adding the marketplace:

```bash
/plugin install astral@astral-sh
```

Or browse and install interactively:

```bash
/plugin
```

### Team installation

For team-wide plugin usage, add to your project's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "astral-sh": {
      "source": {
        "source": "github",
        "repo": "astral-sh/claude-code-plugins"
      }
    }
  },
  "enabledPlugins": {
    "astral@astral-sh": true
  }
}
```

Team members will be prompted to install the plugin when they trust the
repository.

## Usage

### Skills

The plugin provides skills for Astral tools.

Invoke skills with `/astral:<skill>`, e.g., `/astral:uv`.

Claude sometimes needs to be prompted to use skills. We recommend adding this
instruction to your `CLAUDE.md`:

> When working with Python, invoke the relevant `/astral:<skill>` for `uv`,
> `ty`, and `ruff` to ensure best practices are followed.

### LSP

The plugin also provides the ty LSP. It requires `uvx` to be available.

## Opencode Skills

This repository also includes opencode-compatible skill files in the `opencode-skills/` directory:

- **using-uv** – Guide for using uv, the Python package and project manager
- **using-ruff** – Guide for using ruff, the Python linter and formatter  
- **using-ty** – Guide for using ty, the Python type checker

These skills follow the opencode skill format (YAML frontmatter with `name` and `description`) and can be used with opencode agents. To use them, copy the skill files to your opencode skills directory and organize them into skill directories:

```bash
# For personal skills
mkdir -p ~/.config/opencode/skills/
cp opencode-skills/*.md ~/.config/opencode/skills/

# Reorganize into skill directory structure
cd ~/.config/opencode/skills/
for skill in using-uv using-ruff using-ty; do
  mkdir -p $skill
  mv $skill.md $skill/SKILL.md 2>/dev/null
done

# For project-specific skills
mkdir -p .opencode/skills/
cp opencode-skills/*.md .opencode/skills/
cd .opencode/skills/
for skill in using-uv using-ruff using-ty; do
  mkdir -p $skill
  mv $skill.md $skill/SKILL.md 2>/dev/null
done
```

**Note:** After adding skills, restart opencode for them to be detected. Use `find_skills` to verify availability and `use_skill` to load them.

## License

Licensed under either of:

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or
  http://www.apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for development setup and guidelines.

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.