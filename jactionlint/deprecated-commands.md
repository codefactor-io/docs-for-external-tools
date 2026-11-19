Pattern: Deprecated workflow command

Issue: -

## Description

A `run` script prints a deprecated workflow command, such as `::set-output`. Use the corresponding runner environment file instead, such as `$GITHUB_OUTPUT` for step outputs.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo '::set-output name=version::1.2.3'
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'version=1.2.3' >> "$GITHUB_OUTPUT"
```

## Further Reading

* [jactionlint - Deprecated workflow commands](https://jactionlint.jdx.dev/checks#check-deprecated-workflow-commands)
* [jactionlint - deprecated-commands](https://jactionlint.jdx.dev/rules#deprecated-commands)
