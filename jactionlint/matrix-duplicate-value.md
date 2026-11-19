Pattern: Duplicate matrix value

Issue: -

## Description

A matrix axis lists the same value more than once, creating duplicate job combinations.

Remove repeated values from the matrix.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    strategy:
      matrix:
        version: [18, 20, 20]
    runs-on: ubuntu-latest
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
        version: [18, 20]
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Matrix values](https://jactionlint.jdx.dev/checks#check-matrix-values)
* [jactionlint - matrix-duplicate-value](https://jactionlint.jdx.dev/rules#matrix-duplicate-value)
