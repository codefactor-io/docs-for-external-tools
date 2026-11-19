Pattern: Duplicate job ID

Issue: -

## Description

Two jobs use the same ID. Job IDs must be unique within a workflow and are compared without regard to case.

Give each job a different ID and update any references to it. Repeated job keys in workflow YAML are reported as `duplicate-key` before the `duplicate-job-id` check runs.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Job dependencies validation](https://jactionlint.jdx.dev/checks#check-job-deps)
* [jactionlint - duplicate-job-id](https://jactionlint.jdx.dev/rules#duplicate-job-id)
