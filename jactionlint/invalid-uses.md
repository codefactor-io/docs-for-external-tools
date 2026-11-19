Pattern: Invalid `uses` reference

Issue: -

## Description

A `uses` reference does not follow the supported format for an action, reusable workflow, or Docker image.

Include an owner, repository, and ref for remote actions, start local action paths with `./`, and provide a valid Docker image reference.

## Examples

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
