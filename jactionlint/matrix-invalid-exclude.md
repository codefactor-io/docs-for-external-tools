Pattern: Invalid matrix `exclude` entry

Issue: -

## Description

A matrix `exclude` entry contains a key or value that does not match the matrix. It therefore cannot exclude the intended job combination.

Use the matrix's actual axis names and values.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    strategy:
      matrix:
        version: [18, 20]
        exclude:
          - version: 19
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
        exclude:
          - version: 18
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Matrix values](https://jactionlint.jdx.dev/checks#check-matrix-values)
* [jactionlint - matrix-invalid-exclude](https://jactionlint.jdx.dev/rules#matrix-invalid-exclude)
