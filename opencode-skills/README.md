# Astral Tools Skills for Opencode

This directory contains opencode-compatible skills for working with Astral tools (uv, ruff, ty). These skills are adapted from the original [astral-sh/claude-code-plugins](https://github.com/astral-sh/claude-code-plugins) repository.

## Available Skills

### using-uv
**Guide for using uv, the Python package and project manager**

uv is an extremely fast Python package and project manager that replaces pip,
pip-tools, pipx, pyenv, virtualenv, poetry, etc.

**When to use:** Working with Python projects, scripts, packages, or tools

### using-ruff  
**Guide for using ruff, the Python linter and formatter**

Ruff is an extremely fast Python linter and code formatter that replaces Flake8,
isort, Black, pyupgrade, autoflake, and dozens of other tools.

**When to use:** Linting, formatting, or fixing Python code

### using-ty
**Guide for using ty, the Python type checker**

ty is an extremely fast Python type checker and language server that replaces
mypy, Pyright, and other type checkers.

**When to use:** Type checking Python code or setting up type checking in Python projects

## Installation

### For Personal Use

```bash
# Copy skills to personal opencode skills directory
mkdir -p ~/.config/opencode/skills/
cp *.md ~/.config/opencode/skills/

# Reorganize into skill directory structure
cd ~/.config/opencode/skills/
for skill in using-uv using-ruff using-ty; do
  mkdir -p $skill
  mv $skill.md $skill/SKILL.md 2>/dev/null
done
```

### For Project-Specific Use

```bash
# Copy skills to project .opencode directory
mkdir -p .opencode/skills/
cp *.md .opencode/skills/

# Reorganize into skill directory structure
cd .opencode/skills/
for skill in using-uv using-ruff using-ty; do
  mkdir -p $skill
  mv $skill.md $skill/SKILL.md 2>/dev/null
done
```

## Usage

After installation, restart opencode for the skills to be detected. Then:

1. Use `find_skills` to verify the skills are available
2. Use `use_skill` to load a specific skill:
   ```bash
   use_skill using-uv
   ```

## Skill Format

These skills follow the opencode skill format with YAML frontmatter:

```yaml
---
name: skill-name
description: Use when [specific triggering conditions]
---
```

## Source

Adapted from the official Astral Claude Code plugins:
- Original repository: https://github.com/astral-sh/claude-code-plugins
- Documentation: https://docs.astral.sh/

## License

These skills are adapted from the original Astral plugins and are subject to the same licenses (Apache-2.0, MIT). See the main repository for details.