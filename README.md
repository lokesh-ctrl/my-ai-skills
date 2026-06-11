# my-ai-skills

Personal Claude Code skills — portable across machines.

## Structure

```
my-ai-skills/
├── .claude-plugin/
│   └── marketplace.json      # Marketplace manifest
└── my-skills/                # The plugin
    ├── .claude-plugin/
    │   └── plugin.json       # Plugin manifest
    └── skills/
        └── <skill-name>/
            └── skill.md      # Skill instructions
```

## Install on a new machine

**Option A — local path** (if the repo is cloned locally):

```bash
claude plugin marketplace add /path/to/my-ai-skills
claude plugin install my-skills@my-ai-skills
```

**Option B — from GitHub** (once pushed to GitHub as `<user>/my-ai-skills`):

```bash
claude plugin marketplace add <user>/my-ai-skills
claude plugin install my-skills@my-ai-skills
```

Restart Claude Code after installing.

## Adding a new skill

1. Create a folder under `my-skills/skills/<skill-name>/`
2. Add a `skill.md` file with this header:

```markdown
---
name: skill-name
description: One-line description of what this skill does
---

# Skill Name

...instructions for Claude...
```

3. Commit and push.
4. On any machine, reinstall to pick up the new skill:
   ```bash
   claude plugin uninstall my-skills@my-ai-skills
   claude plugin install my-skills@my-ai-skills
   ```
   (Local directory plugins snapshot on install, so uninstall+reinstall is needed to sync new skills.)

## Using skills

Invoke with `/skill-name` in any Claude Code session (after the plugin is installed and Claude is restarted).
