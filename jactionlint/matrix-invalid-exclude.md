Pattern: Invalid matrix exclude

Issue: -

## Description

An exclude entry of a matrix does not match the matrix.

The rules `matrix-duplicate-value` and `matrix-invalid-exclude` report a matrix that lists a value twice and an `exclude:` entry that matches nothing in the matrix.

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    strategy:
      matrix:
        node: [10, 12, 14, 14]
        os: [ubuntu-latest, macos-latest]
        exclude:
          - node: 13
            os: ubuntu-latest
          - node: 10
            platform: ubuntu-latest
    runs-on: ${{ matrix.os }}
    steps:
      - run: echo ...
```

## Further Reading

* [jactionlint - Matrix values](https://jactionlint.jdx.dev/checks#check-matrix-values)
* [jactionlint - matrix-invalid-exclude](https://jactionlint.jdx.dev/rules#matrix-invalid-exclude)
