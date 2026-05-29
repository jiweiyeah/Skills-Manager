# One-Click Skill Sync Workflow

This document proposes a small product contract for syncing user-installed skills between AI coding assistants such as Claude Code and Codex. It is intended to make the next implementation easier to review once the application source is available.

## Goals

- Let users sync a skill from one assistant to another in one click.
- Prefer user-installed skills in the list, while keeping built-in or system skills visible lower down.
- Avoid duplicating skill folders when a symlink/shared-store workflow is available.
- Keep per-tool enablement explicit so a user can still disable a skill for one assistant.

## Default Paths

Skills Manager can keep its central store as the source of truth and link into detected tool directories:

| Tool | Default skill directory |
| --- | --- |
| Claude Code | `~/.claude/skills` |
| Codex | `~/.codex/skills` |

The UI can still allow custom tool paths for users with non-default installations.

## Suggested Data Shape

```json
{
  "id": "literature-review",
  "name": "literature-review",
  "source": "user",
  "storePath": "~/.skills-manager/skills/literature-review",
  "targets": {
    "claude": { "enabled": true, "path": "~/.claude/skills/literature-review" },
    "codex": { "enabled": true, "path": "~/.codex/skills/literature-review" }
  }
}
```

`source` should be one of:

- `user`: imported, installed, or edited by the user.
- `community`: installed from a community catalog.
- `system`: bundled with an assistant or managed by the assistant runtime.

## Sorting Rule

The default list should sort skills in this order:

1. `user`
2. `community`
3. `system`

Within each group, sort by `updatedAt` descending when available, then by name. This keeps personal and frequently edited skills easy to find without hiding built-in skills.

## One-Click Sync Behavior

When a skill is present for Claude Code but missing for Codex, show a `Sync to Codex` action. When it is present for Codex but missing for Claude Code, show `Sync to Claude`. When it is missing from multiple enabled tools, show `Sync to all`.

The action should:

1. Ensure the skill exists in the central store.
2. Create or refresh symlinks for the selected targets.
3. Report any permission errors with the exact target path.
4. Re-scan target directories and mark the skill as synced only after verification.

## Conflict Handling

If the target directory already has a different folder with the same skill id, show a conflict state and offer:

- Keep target version
- Replace with central version
- Import target as a separate skill

No automatic overwrite should happen without user confirmation.

