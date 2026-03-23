# .skills — AI Skills for Development

This folder is versioned together with the project.

## Installing a Skill

```bash
# Install from npm (globally)
npx skills add https://github.com/vercel-labs/skills --skill find-skills

# Or install into this folder
npx skills add https://github.com/vercel-labs/skills --skill find-skills --output-dir .skills
```

## Available Skills

| Skill | Description |
|-------|-------------|
| `find-skills/` | Discover and install AI skills from the open ecosystem |

## Usage

Before solving a task — check available skills in this folder.
Use the `find-skills` skill to find a suitable skill for the task.

Each skill contains `SKILL.md` with description and usage instructions.

## Adding New Skills

```bash
# Search for skills
npx skills find kubernetes-operator

# Install into project folder
npx skills add <owner/repo> --skill <skill-name> --output-dir .skills
```

Full skill catalog: https://skills.sh/
