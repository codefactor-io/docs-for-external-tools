Pattern: Concurrency deadlock

Issue: -

## Description

A workflow and a local reusable workflow it calls use the same concurrency group. GitHub detects a deadlock and cancels the run.

Use different concurrency groups for the calling and called workflows.

## Examples

Reusable workflow:

```yaml
# file: .github/workflows/build.yml
on:
  workflow_call:
jobs:
  build:
    concurrency:
      group: build
      cancel-in-progress: true
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **incorrect** code:

```yaml
# file: .github/workflows/ci.yml
on: push
concurrency:
  group: build
  cancel-in-progress: true
jobs:
  build:
    uses: ./.github/workflows/build.yml
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on: push
concurrency:
  group: ci
  cancel-in-progress: true
jobs:
  build:
    uses: ./.github/workflows/build.yml
```

## Further Reading

* [jactionlint - Concurrency deadlock between a workflow and the workflow it calls](https://jactionlint.jdx.dev/checks#check-concurrency-deadlock)
* [jactionlint - concurrency-deadlock](https://jactionlint.jdx.dev/rules#concurrency-deadlock)
