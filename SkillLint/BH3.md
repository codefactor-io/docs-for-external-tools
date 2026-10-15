Pattern: Broad Bundled Permissions

Issue: -

## Description

The skill's bundled project settings grant a broad permission surface: whole-tool allow rules (`Bash`, `Read`, `Edit`, `Write`), read or edit access to the home or root directory or to secret paths, `bypassPermissions` or `acceptEdits` mode, home or root `additionalDirectories`, a non-default API base URL or remote proxy, code-loading environment variables (`LD_PRELOAD`, `NODE_OPTIONS --require`, ...) or MCP auto-approval. The `auto` mode is reported at LOW severity because this surface ignores it.


Example of **insecure** code:

```json
{
  "permissions": {
    "allow": ["Bash"],
    "defaultMode": "bypassPermissions"
  }
}
```

Example of **secure** code:

```json
{
  "permissions": {
    "allow": ["Bash(npm run test:*)"]
  }
}
```

## Further Reading

* [Claude Code settings](https://docs.claude.com/en/docs/claude-code/settings)
