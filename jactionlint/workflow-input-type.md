Pattern: Invalid reusable workflow input type

Issue: -

## Description

A value passed to a reusable workflow has a different type from the input declared under `on.workflow_call.inputs`.

Pass a value of the declared `boolean`, `number`, or `string` type.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
    inputs:
      retries:
        type: number
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
    uses: ./.github/workflows/build.yml
    with:
      retries: true
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  build:
    uses: ./.github/workflows/build.yml
    with:
      retries: 3
```

## Further Reading

* [jactionlint - Reusable workflows](https://jactionlint.jdx.dev/checks#check-reusable-workflows)
* [jactionlint - workflow-input-type](https://jactionlint.jdx.dev/rules#workflow-input-type)
