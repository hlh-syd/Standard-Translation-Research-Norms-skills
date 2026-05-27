# Backup Format

Update backup only after the conversation's work is finished. Do not create or edit the backup record early.

## File Location Rules

1. Find the `backUp` directory at the project root.
2. Inside it, find or create the first-level folder named by `YYMM`.
3. Inside that month folder, find or create a day file named `backup_dd.md`.
4. If `backup_dd.md` exceeds 512 KB, create a new file:
   - First overflow file on the same day: `backup2_dd.md`
   - Then `backup3_dd.md`, and so on
5. Always append to the first `backup*.md` file for that day whose size does not exceed 512 KB.

## Required Record Format

Append entries in this exact structure:

```json
--lenghui he/Curosr/当前时间戳
{
  "inputs": "",
  "outputs": "",
  "model": "",
  "skills": "/uiux-intelligence-expert",
  "mcp": "",
  "promptword": "示例"
}
```

## Required Fields

- Header: `-- name/ai工具名/当前时间戳`
- `inputs`: input context files
- `outputs`: output file names, edited code locations, ask
- `model`: the AI model used
- `skills`: the skills used
- `mcp`: the MCP servers used
- `promptword`: the prompt text

## Final Rule

Update `backUp` during every qualifying conversation. If the conversation modified more than 100 lines of code, update `progress.html` in the same conversation as well.
