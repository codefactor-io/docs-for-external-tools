Pattern: Outdated action

Issue: -

## Description

An action runs on a runtime which GitHub Actions no longer supports.

The rule `outdated-action-runner` reports a popular action that runs on a runtime which GitHub Actions no longer supports. It is in the `correctness` profile.

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: actions/checkout@v3 is using the outdated runner 'node16'
      - uses: actions/checkout@v3
```

## Further Reading

* [jactionlint - Popular actions with a runner that is too old](https://jactionlint.jdx.dev/checks#detect-outdated-popular-actions)
* [jactionlint - outdated-action-runner](https://jactionlint.jdx.dev/rules#outdated-action-runner)
