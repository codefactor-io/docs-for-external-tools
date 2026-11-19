Pattern: Duplicate job dependency

Issue: -

## Description

A job ID is listed more than once in needs.

The rules `cyclic-job-needs`, `undefined-job-needs` and `duplicate-job-needs` report `needs:` lists that cannot work: jobs that need each other in a cycle, a needed job that does not exist and a job that is listed twice.

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
* [jactionlint - duplicate-job-needs](https://jactionlint.jdx.dev/rules#duplicate-job-needs)
