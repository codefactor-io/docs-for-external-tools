Pattern: Invalid reusable workflow call

Issue: -

## Description

A job's `uses` value does not follow a supported reusable workflow reference format. Remote references use `owner/repo/path/to/workflow.yml@ref`; local references use `./path/to/workflow.yml` or `$/path/to/workflow.yml`.

Do not append a ref to a local workflow path.

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
    uses: ./.github/workflows/build.yml@main
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
* [jactionlint - invalid-workflow-call](https://jactionlint.jdx.dev/rules#invalid-workflow-call)
