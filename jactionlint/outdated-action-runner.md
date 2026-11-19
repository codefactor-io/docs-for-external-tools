Pattern: Unsupported action runtime

Issue: -

## Description

An action version uses a runtime that GitHub Actions no longer supports, such as Node.js 16.

Update the action to a version that uses a supported runtime.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
```

## Further Reading

* [jactionlint - Popular actions with a runner that is too old](https://jactionlint.jdx.dev/checks#detect-outdated-popular-actions)
* [jactionlint - outdated-action-runner](https://jactionlint.jdx.dev/rules#outdated-action-runner)
