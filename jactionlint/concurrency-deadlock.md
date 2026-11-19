Pattern: Concurrency deadlock

Issue: -

## Description

The concurrency group of a workflow is the same as the group of a local reusable workflow it calls, so GitHub detects a deadlock and cancels the run.

`concurrency-deadlock` (in the `correctness` profile) reports a workflow whose `concurrency:` group is the same as the group of a reusable workflow that it calls, so GitHub detects a deadlock and cancels the run.

Example of **incorrect** code:

```yaml
# file: .github/workflows/ci.yml
# select: concurrency-deadlock
on: push

# ERROR: the called workflow has the same group
concurrency:
  group: ${{ github.workflow }}-${{ github.sha }}
  cancel-in-progress: true

jobs:
  build:
    uses: ./.github/workflows/build.yml
```

## Further Reading

* [jactionlint - Concurrency deadlock between a workflow and the workflow it calls](https://jactionlint.jdx.dev/checks#check-concurrency-deadlock)
* [jactionlint - concurrency-deadlock](https://jactionlint.jdx.dev/rules#concurrency-deadlock)
