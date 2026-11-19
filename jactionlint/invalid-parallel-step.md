Pattern: Invalid parallel step

Issue: -

## Description

A step is not allowed inside a parallel group or refers to a wrong step.

The rule `invalid-parallel-step` reports a `wait` or `cancel` step that names a step which is not an earlier background step, and a step that is not allowed inside a `parallel` group.

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Start server
        id: server
        run: echo 'start'
        background: true
      - run: echo 'tests'
      - cancel: serverr
```

## Further Reading

* [jactionlint - Parallel steps](https://jactionlint.jdx.dev/checks#check-parallel-step-refs)
* [jactionlint - invalid-parallel-step](https://jactionlint.jdx.dev/rules#invalid-parallel-step)
