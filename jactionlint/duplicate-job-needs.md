Pattern: Duplicate job dependency

Issue: -

## Description

A job lists the same dependency more than once in `needs`. List each job ID only once.

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
    needs: [build, build]
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
* [jactionlint - duplicate-job-needs](https://jactionlint.jdx.dev/rules#duplicate-job-needs)
