Pattern: Conflicting runner labels

Issue: -

## Description

The runner labels of a job conflict with each other.

The rules `unknown-runner-label` and `conflicting-runner-labels` check the labels at `runs-on:`: a label that no GitHub-hosted runner has (or that GitHub has retired), and a combination of labels that no runner can have. Both are in the `correctness` profile, so they run in every profile. The rule `invalid-label-pattern` reports a pattern in `self-hosted-runner.labels` of the configuration file that is not a valid glob.

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    strategy:
      matrix:
        runner:
          # OK
          - macos-latest
          # ERROR: Unknown runner
          - linux-latest
          # OK: Preset labels for self-hosted runner
          - [self-hosted, linux, x64]
          # OK: Single preset label for self-hosted runner
          - arm64
          # ERROR: Unknown label "gpu". Custom label must be defined in jactionlint.yaml config file
          - gpu
    runs-on: ${{ matrix.runner }}
    steps:
      - run: echo ...

  test2:
    # ERROR: Too old macOS worker
    runs-on: macos-10.13
    steps:
      - run: echo ...
```

## Further Reading

* [jactionlint - Runner labels](https://jactionlint.jdx.dev/checks#check-runner-labels)
* [jactionlint - conflicting-runner-labels](https://jactionlint.jdx.dev/rules#conflicting-runner-labels)
