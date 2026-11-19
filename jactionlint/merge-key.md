Pattern: Unsupported YAML merge key

Issue: -

## Description

A workflow uses the YAML merge key `<<`, which GitHub Actions does not support.

Write the mapping entries explicitly. YAML anchors and aliases can reuse complete values without a merge key.

## Examples

Example of **incorrect** code:

```yaml
on: push
env: &defaults
  MESSAGE: hello
jobs:
  test:
    env:
      <<: *defaults
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on: push
env: &defaults
  MESSAGE: hello
jobs:
  test:
    env: *defaults
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - YAML anchors](https://jactionlint.jdx.dev/checks#yaml-anchors)
* [jactionlint - merge-key](https://jactionlint.jdx.dev/rules#merge-key)
