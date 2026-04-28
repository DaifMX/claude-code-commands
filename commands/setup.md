Link this claude-code-commands repository into Claude Code so all commands in it are available as slash commands.

## Instructions

### 1. Find the repo path

Ask the user:
> "What is the absolute path to your local clone of the claude-code-commands repo?
> Example: /Users/yourname/Code/claude-code-commands"

Wait for their answer. Call it `$REPO`.

The `commands/` subdirectory inside that path (`$REPO/commands`) is what will be linked.

### 2. Check for an existing ~/.claude/commands

Run:
```
ls -la ~/.claude/commands
```

Three possible states:

| State | What to do |
|-------|-----------|
| Does not exist | Proceed directly to step 3 |
| Already a symlink pointing to `$REPO/commands` | Tell the user it's already set up and stop |
| Already a symlink pointing elsewhere | Warn the user, ask if they want to replace it |
| A real directory with files | Offer to migrate: move files into `$REPO/commands/`, then replace with symlink |

For the "real directory" case, confirm with the user before moving any files.

### 3. Create the symlink

```bash
# Remove existing (empty dir or old symlink) if needed
rm -rf ~/.claude/commands 2>/dev/null || true

# Create the symlink
ln -s "$REPO/commands" ~/.claude/commands
```

### 4. Verify

Run:
```
ls -la ~/.claude/commands
```

Confirm:
- The output shows an `->` arrow pointing to `$REPO/commands`
- At least one `.md` file is visible inside it (the commands are loading)

### 5. Report

Tell the user:
- The symlink path: `~/.claude/commands -> $REPO/commands`
- How many command files are now available
- That they can add new commands by dropping `.md` files into `$REPO/commands/` and committing them to the repo
- That `/setup` itself lives in the repo, so anyone who clones it can run `/setup` to wire it up on their machine
