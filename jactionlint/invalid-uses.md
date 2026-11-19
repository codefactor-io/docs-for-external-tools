Pattern: Invalid uses reference

Issue: -

## Description

A uses: value does not follow the format of an action or a Docker image.

The rule `invalid-uses` reports a `uses:` value that does not follow the format of an action, a reusable workflow or a Docker image, and the rule `unpinned-uses` reports one that is not pinned to a commit. `invalid-uses` is in the `correctness` profile and `unpinned-uses` in the `default` profile.

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: ref is missing
      - uses: actions/checkout
      # ERROR: owner name is missing
      - uses: checkout@v2
      # ERROR: tag is empty
      - uses: 'docker://image:'
      # ERROR: local action must start with './'
      - uses: .github/my-actions/do-something
```

## Further Reading

* [jactionlint - Action format in uses:](https://jactionlint.jdx.dev/checks#check-action-format)
* [jactionlint - invalid-uses](https://jactionlint.jdx.dev/rules#invalid-uses)
