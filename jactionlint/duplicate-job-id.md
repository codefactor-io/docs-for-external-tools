Pattern: Duplicate job ID

Issue: -

## Description

A job ID is defined more than once.

A job ID that is defined twice is reported as `duplicate-key` (see [Job ID and step ID uniqueness](https://jactionlint.jdx.dev/checks#check-job-step-ids)): the parser finds the repeated key before this check runs and drops the second job. The rule `duplicate-job-id` of this check is meant for the same mistake, but a repeated job ID of a workflow file never reaches it.

Example of **incorrect** code:

```yaml
on: push
jobs:
  prepare:
    needs: [build]
    runs-on: ubuntu-latest
    steps:
      - run: echo 'prepare'
  install:
    needs: [prepare]
    runs-on: ubuntu-latest
    steps:
      - run: echo 'install'
  build:
    needs: [install]
    runs-on: ubuntu-latest
    steps:
      - run: echo 'build'
```

## Further Reading

* [jactionlint - Job dependencies validation](https://jactionlint.jdx.dev/checks#check-job-deps)
* [jactionlint - duplicate-job-id](https://jactionlint.jdx.dev/rules#duplicate-job-id)
