Pattern: Expression type error

Issue: -

## Description

A ${{ }} expression has a type error.

The rules `expression-type` and `undefined-property` (both in the `correctness` profile) report an expression in `${{ }}` whose types do not fit: an index of the wrong type, a property read from a value that is not an object, a property that an object does not have, or an object, an array or null that is evaluated into text. jactionlint checks the types of every expression, and more strictly than GitHub Actions does at run time:

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: `env` is object. Index access object is invalid
      - run: echo '${{ env[0] }}'
      # ERROR: Properties in objects are strongly typed. Missing property can be caught
      - run: echo '${{ job.container.os }}'
      # ERROR: `github.repository` is string. Trying to access .owner property is invalid
      - run: echo '${{ github.repository.owner }}'
      # ERROR: Objects, arrays and null should not be evaluated at ${{ }} since the outputs are useless
      - run: echo '${{ env }}'
```

## Further Reading

* [jactionlint - Type checks for expression syntax in ${{ }}](https://jactionlint.jdx.dev/checks#check-type-check-expression)
* [jactionlint - expression-type](https://jactionlint.jdx.dev/rules#expression-type)
