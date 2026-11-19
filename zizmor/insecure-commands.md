Pattern: Insecure workflow commands enabled

Issue: -

## Description

`ACTIONS_ALLOW_UNSECURE_COMMANDS` enables the deprecated `::set-env` and `::add-path` commands. These commands let output from a process change the environment of later steps, which can lead to code execution.

Remove this setting. Write environment variables to `$GITHUB_ENV` and paths to `$GITHUB_PATH` instead.

## Examples

Example of **incorrect** code:

```yaml
on: push

env:
  ACTIONS_ALLOW_UNSECURE_COMMANDS: true

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "::add-path::$HOME/tool/bin"
```

Example of **correct** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "$HOME/tool/bin" >> "$GITHUB_PATH"
```

## Further Reading

* [zizmor - insecure-commands](https://docs.zizmor.sh/audits/#insecure-commands)
