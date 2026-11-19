Pattern: Insufficient reusable workflow permissions

Issue: -

## Description

A calling job grants fewer token permissions than a job in the reusable workflow requires. A reusable workflow cannot increase the caller's permissions.

Grant the required permissions in the calling job, or reduce the called job's requirements.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
jobs:
  build:
    permissions:
      contents: write
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
    permissions:
      contents: read
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  build:
    uses: ./.github/workflows/build.yml
    permissions:
      contents: write
```

## Further Reading

* [jactionlint - Reusable workflows](https://jactionlint.jdx.dev/checks#check-reusable-workflows)
* [jactionlint - workflow-call-permissions](https://jactionlint.jdx.dev/rules#workflow-call-permissions)
