Pattern: Unknown reusable workflow input

Issue: -

## Description

A reusable workflow receives an input that it does not declare under `on.workflow_call.inputs`.

Correct or remove the input name in the calling job's `with` setting.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
    inputs:
      target:
        type: string
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
      targte: production
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  build:
    uses: ./.github/workflows/build.yml
    with:
      target: production
```

## Further Reading

* [jactionlint - Reusable workflows](https://jactionlint.jdx.dev/checks#check-reusable-workflows)
* [jactionlint - unknown-workflow-input](https://jactionlint.jdx.dev/rules#unknown-workflow-input)
