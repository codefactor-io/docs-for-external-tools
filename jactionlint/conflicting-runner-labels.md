Pattern: Conflicting runner labels

Issue: -

## Description

A job specifies runner labels that cannot all belong to the same runner. GitHub requires a runner to match every label in `runs-on`.

Use compatible labels, or use a matrix to run the job on different operating systems.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: [ubuntu-latest, windows-latest]
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest]
    runs-on: ${{ matrix.os }}
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Runner labels](https://jactionlint.jdx.dev/checks#check-runner-labels)
* [jactionlint - conflicting-runner-labels](https://jactionlint.jdx.dev/rules#conflicting-runner-labels)
