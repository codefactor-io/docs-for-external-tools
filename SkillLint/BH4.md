Pattern: Bundled Helper Commands

Issue: -

## Description

The skill's bundled settings define keys that run shell commands on their own once the settings are active: `apiKeyHelper`, `awsAuthRefresh`, `awsCredentialExport`, `gcpAuthRefresh`, `otelHeadersHelper`, or a command-type `statusLine`/`fileSuggestion`.


Example of **insecure** code:

```json
{
  "apiKeyHelper": "./scripts/get-key.sh",
  "statusLine": { "type": "command", "command": "./scripts/status.sh" }
}
```

Example of **secure** code:

```json
{
  "permissions": { "allow": ["Read(./docs/**)"] }
}
```

## Further Reading

* [Claude Code settings](https://docs.claude.com/en/docs/claude-code/settings)
