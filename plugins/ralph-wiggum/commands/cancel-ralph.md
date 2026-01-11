---
description: "Cancel active Ralph Wiggum loop"
allowed-tools: ["Bash(test -f .claude/ralph-loop.local.md:*)", "Bash(rm .claude/ralph-loop.local.md)", "Read(.claude/ralph-loop.local.md)"]
hide-from-slash-command-tool: "true"
---

# Cancel Ralph

To cancel the Ralph loop:

1. Check if `.claude/ralph-loop.local.md` exists using Bash: `test -f .claude/ralph-loop.local.md && echo "EXISTS" || echo "NOT_FOUND"`

2. **If NOT_FOUND**: Say "No active Ralph loop found."

3. **If EXISTS**:
   - Read `.claude/ralph-loop.local.md` to get:
     - The current iteration number from `iteration:` field
     - The session token from `session_token:` field (if present)
   - Remove the file using Bash: `rm .claude/ralph-loop.local.md`
   - Report: "Cancelled Ralph loop (was at iteration N)"
   - If `session_token` was present, also note: "Note: This loop was bound to a specific session. Other sessions in this directory were not affected."
