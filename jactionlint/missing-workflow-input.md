Pattern: Missing reusable workflow input

Issue: -

## Description

A reusable workflow is called without an input that it declares as required under `on.workflow_call.inputs`.

Pass the input under the calling job's `with` setting.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
    inputs:
      target:
        type: string
        required: true
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
* [jactionlint - missing-workflow-input](https://jactionlint.jdx.dev/rules#missing-workflow-input)
