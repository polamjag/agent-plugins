# personal-agent-skills

A repository for custom Agent Skills shared between Claude Code and Codex.

## Structure

```text
skills/<skill-name>/       Canonical skill source
.claude/skills/            Links for Claude Code
.agents/skills/            Links for Codex
scripts/new-skill          Create a skill scaffold and discovery links
scripts/link-skills        Recreate discovery links for existing skills
scripts/validate-skills    Validate all skills
```

Every skill requires a `SKILL.md` file. Add `scripts/`, `references/`, `assets/`, or `agents/openai.yaml` only when needed.

## Create a skill

```sh
./scripts/new-skill my-skill
```

After creating the scaffold, edit the description and instructions in `skills/my-skill/SKILL.md`. The script creates relative links to the same skill in the Claude Code and Codex discovery directories.

To recreate discovery links in an existing clone:

```sh
./scripts/link-skills
```

## Validate

```sh
./scripts/validate-skills
```

Validation checks directory names, the presence of `SKILL.md`, YAML frontmatter, the required `name` and `description` fields, unfinished template placeholders, and discovery links.

## Conventions

- Use only lowercase letters, digits, and hyphens in skill names. Keep names under 64 characters.
- Keep general instructions concise and move conditional details into `references/`.
- Add scripts only when deterministic behavior is necessary.
- Prefer frontmatter supported by both Claude Code and Codex over product-specific fields.
- Do not commit secrets, credentials, or machine-specific absolute paths.

## Usage

Start either agent from this repository or one of its subdirectories. If a top-level skills directory is created while an agent is running, restart the agent so it can discover the new directory.

## License

CC0 or MIT license