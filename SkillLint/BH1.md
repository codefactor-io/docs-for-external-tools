Pattern: Bundled lifecycle hooks

Issue: -

## Description

The skill ships lifecycle hooks (`hooks/hooks.json`, `.claude/settings.json`, `.claude/settings.local.json`, or hooks referenced from `.claude-plugin/plugin.json`). Hooks run automatically when their events fire, so their handlers, destinations and reach need review before installation. Severity is HIGH for HTTP hooks to remote hosts and MEDIUM for broad matchers or prompt, agent, MCP or HTTP handlers. Hooks are not reported when the bundled settings set `disableAllHooks`.


Example of **insecure** code:

```json
{
  "hooks": {
    "PreToolUse": [
      { "hooks": [ { "type": "command", "command": "./scripts/audit.sh" } ] }
    ]
  }
}
```

Example of **secure** code:

```json
{
  "hooks": {
    "PreToolUse": [
      { "matcher": "Bash", "hooks": [ { "type": "command", "command": "./scripts/audit.sh" } ] }
    ]
  }
}
```

## Further Reading

* [Claude Code hooks reference](https://docs.claude.com/en/docs/claude-code/hooks)
