Pattern: Deprecated workflow command

Issue: -

## Description

A deprecated workflow command such as ::set-output is used.

The rule `deprecated-commands` reports a `run:` script that prints a workflow command which GitHub deprecated. The finding names the replacement.

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: 'set-output' workflow command was deprecated
      - run: echo '::set-output name=foo::bar'
      # OK: Use this instead
      - run: echo "foo=bar" >> "$GITHUB_OUTPUT"
      # OK: 'debug' command is not deprecated
      - run: echo "::debug::Set the Octocat variable"
```

## Further Reading

* [jactionlint - Deprecated workflow commands](https://jactionlint.jdx.dev/checks#check-deprecated-workflow-commands)
* [jactionlint - deprecated-commands](https://jactionlint.jdx.dev/rules#deprecated-commands)
