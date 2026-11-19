Pattern: Background step not waited

Issue: -

## Description

Outputs or results of a background step are read before a wait step covers it.

The rule `background-step-not-waited` reports a read of `steps.<id>.outputs.*`, `steps.<id>.outcome` or `steps.<id>.conclusion` of a background step before a `wait` or `wait-all` step covers it. Such an expression evaluates to an empty string.

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
