Pattern: Undefined job dependency

Issue: -

## Description

A job's `needs` list references a job ID that is not defined in the workflow.

Correct the reference or define the missing job.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
  test:
    needs: [biuld]
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
    needs: [build]
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Job dependencies validation](https://jactionlint.jdx.dev/checks#check-job-deps)
* [jactionlint - undefined-job-needs](https://jactionlint.jdx.dev/rules#undefined-job-needs)
