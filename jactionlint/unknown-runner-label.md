Pattern: Unknown or retired runner label

Issue: -

## Description

A `runs-on` label is unknown or belongs to a runner image that GitHub has retired. A job cannot start without a matching runner.

Choose a supported label, or register custom self-hosted runner labels in jactionlint's configuration.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: linux-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Runner labels](https://jactionlint.jdx.dev/checks#check-runner-labels)
* [jactionlint - unknown-runner-label](https://jactionlint.jdx.dev/rules#unknown-runner-label)
