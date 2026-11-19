Pattern: Missing wait for background step

Issue: -

## Description

A step reads the outputs, outcome, or conclusion of a background step before it has finished. These expressions evaluate to an empty string until a `wait` or `wait-all` step waits for that background step.

Wait for the background step before reading its results.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - id: server
        run: echo 'x=1' >> "$GITHUB_OUTPUT"
        background: true
      - run: echo "${{ steps.server.outputs.x }}"
      - wait: server
      - run: echo "${{ steps.server.outputs.x }}"
```

## Further Reading

* [jactionlint - Background step results read before a wait](https://jactionlint.jdx.dev/checks#check-background-step-not-waited)
* [jactionlint - background-step-not-waited](https://jactionlint.jdx.dev/rules#background-step-not-waited)
