Pattern: Incompatible expression type

Issue: -

## Description

An expression uses a value of the wrong type, such as indexing an object with a number or reading a property from a string. Inserting an object, array, or `null` directly into text is also reported.

Use values of the expected type and select the property or element you need.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo '${{ env[0] }}'
      - run: echo '${{ github.repository.owner }}'
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo '${{ github.repository }}'
      - run: echo '${{ github.repository_owner }}'
```

## Further Reading

* [jactionlint - Type checks for expression syntax in ${{ }}](https://jactionlint.jdx.dev/checks#check-type-check-expression)
* [jactionlint - expression-type](https://jactionlint.jdx.dev/rules#expression-type)
