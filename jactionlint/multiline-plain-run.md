Pattern: Multi-line run without block scalar

Issue: -

## Description

A run: is written over several lines without |, so YAML folds the lines into one command.

The rule `multiline-plain-run` reports a `run:` that is written over several lines without a block scalar (`|`). YAML folds the line breaks of such a scalar into spaces, so the shell runs one long command instead of one command per line.

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
