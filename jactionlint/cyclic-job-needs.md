Pattern: Cyclic job dependencies

Issue: -

## Description

Jobs depend on each other in a cycle through `needs`. None of the jobs in the cycle can start because each is waiting for another.

Remove the circular dependency so the jobs can run in order.

## Examples

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
* [jactionlint - cyclic-job-needs](https://jactionlint.jdx.dev/rules#cyclic-job-needs)
