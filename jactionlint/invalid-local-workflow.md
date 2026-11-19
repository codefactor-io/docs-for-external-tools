Pattern: Invalid local reusable workflow

Issue: -

## Description

A local reusable workflow referenced by `uses` cannot be loaded, cannot be parsed, or does not declare the `workflow_call` event.

Check the file path and ensure the called workflow is valid and supports `workflow_call`.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **incorrect** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  build:
    uses: ./.github/workflows/missing.yml
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  build:
    uses: ./.github/workflows/build.yml
```

## Further Reading

* [jactionlint - Reusable workflows](https://jactionlint.jdx.dev/checks#check-reusable-workflows)
* [jactionlint - invalid-local-workflow](https://jactionlint.jdx.dev/rules#invalid-local-workflow)
