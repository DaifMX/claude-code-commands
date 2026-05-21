<div align="center">

# claude-code-commands

**A curated collection of slash commands for [Claude Code](https://claude.ai/code)**

Drop a `.md` file. Get a slash command. That's it.

</div>

---

## Commands

| Command | What it does |
|---------|--------------|
| [`/commit`](commands/commit.md) | Stages and commits changes with an Angular-style message satisfying semantic-release conventions. Offers to push when done. |

---

## Quick Start


```bash
git clone https://github.com/daif/claude-code-commands
ln -s $(pwd)/claude-code-commands/commands ~/.claude/commands
```

Every `.md` file in `commands/` is immediately available as a slash command — no restart required.

---

## Writing Your Own Commands

Commands are plain Markdown files. The filename becomes the slash command.

```
commands/
  my-command.md   →   /my-command
```

Inside the file, write whatever instructions you want Claude to follow when the command is invoked. Commit the file and it's live.

---

## How It Works

Claude Code loads custom commands from `~/.claude/commands/`. This repo symlinks that directory here, so your commands are version-controlled, portable, and shareable.

```
~/.claude/commands  →  ~/path/to/claude-code-commands/commands/
```
