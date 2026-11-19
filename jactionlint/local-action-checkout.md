Pattern: Local action before checkout

Issue: -

## Description

A step uses a local action before the repository has been checked out in the same job. Local actions are loaded from the runner's workspace, so their metadata is unavailable until checkout completes.

Run `actions/checkout` before using the local action.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: ./.github/actions/greet
      - uses: actions/checkout@v4
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ./.github/actions/greet
```

## Further Reading

* [jactionlint - Local action used before checkout](https://jactionlint.jdx.dev/checks#check-local-action-checkout)
* [jactionlint - local-action-checkout](https://jactionlint.jdx.dev/rules#local-action-checkout)
