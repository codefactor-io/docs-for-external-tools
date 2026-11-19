Pattern: Multiline `run` without block scalar

Issue: -

## Description

A `run` script spans several lines without a YAML block scalar (`|`). YAML folds those line breaks into spaces, so the shell may run one command instead of several.

Use `run: |` when each line should remain a separate shell command.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: without | YAML folds the lines into one, so this is one echo command
      - run: echo "building"
          npm ci
          npm test
      # OK: a block scalar keeps the lines
      - run: |
          echo "building"
          npm ci
          npm test
      # OK: one command wrapped over several lines
      - run: docker build
          --tag app
          .
```

## Further Reading

* [jactionlint - Scripts folded into one line](https://jactionlint.jdx.dev/checks#check-multiline-plain-run)
* [jactionlint - multiline-plain-run](https://jactionlint.jdx.dev/rules#multiline-plain-run)
