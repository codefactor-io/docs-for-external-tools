Pattern: Invalid parallel step

Issue: -

## Description

A `wait` or `cancel` step refers to a step that is not an earlier background step, or a step is not allowed inside a `parallel` group.

Reference an earlier background step and use only the step types supported by the group.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - id: server
        run: echo start
        background: true
      - run: echo tests
      - cancel: serverr
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - id: server
        run: echo start
        background: true
      - run: echo tests
      - cancel: server
```

## Further Reading

* [jactionlint - Parallel steps](https://jactionlint.jdx.dev/checks#check-parallel-step-refs)
* [jactionlint - invalid-parallel-step](https://jactionlint.jdx.dev/rules#invalid-parallel-step)
