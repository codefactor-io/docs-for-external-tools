Pattern: Local action before checkout

Issue: -

## Description

A local action is used before any step checks out the repository.

The rule `local-action-checkout` reports the first local action of a job that no checkout step precedes in the same job. A local action (`uses: ./.github/actions/foo`) is loaded from the workspace of the runner. When the repository has not been checked out yet, the step fails at run time with "Can't find 'action.yml'".

Example of **incorrect** code:

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: ./.github/actions/foo
      - uses: actions/checkout@v4
```

## Further Reading

* [jactionlint - Local action used before checkout](https://jactionlint.jdx.dev/checks#check-local-action-checkout)
* [jactionlint - local-action-checkout](https://jactionlint.jdx.dev/rules#local-action-checkout)
