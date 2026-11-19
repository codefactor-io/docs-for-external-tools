Pattern: Insecure workflow commands enabled

Issue: -

## Description

The deprecated set-env and add-path workflow commands are enabled, which allows code execution.

Workflow commands (like `::set-env` and `::add-path`) [were deprecated by GitHub](https://github.blog/changelog/2020-10-01-github-actions-deprecating-set-env-and-add-path-commands/) in 2020 due to their inherent weaknesses (e.g., allowing any command with the ability to emit to `stdout` to inject environment variables and therefore obtain code execution).

Example of **incorrect** code:

```yaml
env:
  ACTIONS_ALLOW_UNSECURE_COMMANDS: true
```

Example of **correct** code:

```yaml
- run: echo "TOOL_HOME=$HOME/tool" >> "$GITHUB_ENV"
```

## Further Reading

* [zizmor - insecure-commands](https://docs.zizmor.sh/audits/#insecure-commands)
